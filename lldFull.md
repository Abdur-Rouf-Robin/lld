# LLD

## chapter 1 OOP pillars

- a class = a named shape. fields and methods
- an object = one value of that shape
- encapsulation = the fields that must stay valid are private. callers use a method
- inheritance = a subclass is a kind of the parent. we use it when the "is a" sentence is true
- polymorphism = the caller uses the parent type. the actual method depends on the object
- abstraction = the caller sees the operation, not every step inside
- in TypeScript we often use a type and functions, not a deep class tree. the four ideas still name the design

```ts
class Money {
  private constructor(private readonly cents: number) {}
  static fromDollars(dollars: number) {
    return new Money(Math.round(dollars * 100));
  }
  add(other: Money) {
    return new Money(this.cents + other.cents);
  }
  toDollars() {
    return this.cents / 100;
  }
}
```

- cents stay private so nobody stores 7,500.4 dollars by accident
- `fromDollars` is the door. the constructor is private
- a PortCall and a Match are different types. inheritance between them would be a lie

- homework of chapter 1
```ts
// 1a  which pillar keeps cents private
// 1b  a function that takes a Money and does not care if it was built from dollars
// 1c  why Match should not extend PortCall
```

## chapter 2 SOLID

- S = one reason to change. the laytime function does not also send email
- O = open for extension, closed for modification. a new fact type should not require editing a giant switch if we can add a handler
- L = a subtype can stand in for the parent. if it cannot, it is not a subtype
- I = small interfaces. a reader does not have to implement save
- D = depend on an abstraction. the service asks for a repository, and the test passes a fake

```ts
interface PortCallStore {
  find(id: string): Promise<{ allowedHours: number; usedHours: number } | null>;
}

class LaytimeService {
  constructor(private readonly store: PortCallStore) {}
  async quote(id: string, perDay: number) {
    const row = await this.store.find(id);
    if (!row) return null;
    return laytime({ ...row, demurragePerDay: perDay });
  }
}
```

- the service does not mention Prisma. the production store does
- a switch of 30 cases that we edit every week is the O being missed
- a "subtype" that throws on half the methods breaks L

- homework of chapter 2
```ts
// 2a  which letter is the fake store in a test
// 2b  which letter is "laytime does not send the socket event"
// 2c  split a UserStore that has save, sendEmail, and hashPassword into smaller interfaces
```

## chapter 3 DRY, KISS, YAGNI, and composition

- DRY = do not repeat the rule. one laytime function, not a copy in the worker and a copy in the controller
- repeating a string constant is fine. repeating a money rule is not
- KISS = the simplest design that holds the rule
- YAGNI = do not build the shard router, the plugin system, or the second database until a real case exists
- composition = an object has another object. "has a"
- inheritance = "is a"
- prefer composition when the relationship is "uses" or "has"
- a worker has a calculator. the worker is not a kind of calculator

```ts
class Worker {
  constructor(private readonly quote: (id: string) => Promise<number>) {}
  async run(id: string) {
    return this.quote(id);
  }
}
```

- the quote function can be the real laytime path or a fake in a test
- a five-level class tree for admin, operator, and viewer is inheritance doing a role's job. roles are data

- homework of chapter 3
```ts
// 3a  DRY or not: two copies of the 72/84/15000 example's formula
// 3b  has-a or is-a: a tournament has many matches
// 3c  a feature nobody has asked for. which saying tells us to wait
```

## chapter 4 UML class diagrams

- a box = a class or a type. the name, then the fields that matter
- a line with a diamond = has a
- a hollow triangle = inheritance
- a dashed arrow = uses
- multiplicity = how many. 1, 0..1, *
- draw the nouns. skip the getters
- one port call has many facts. one fact belongs to one port call

```text
PortCall  1 ---- *  StatementOfFact
PortCall  1 ---- 0..1  LaytimeResult
LaytimeCalculator ....> PortCall
```

- start with the nouns a person said, and the one-to-many
- add a method when we need to show who calculates
- a diagram of twenty boxes is hard to read. split it
- an arrow with no meaning is noise. inheritance where we meant "uses" is a wrong design, not a messy drawing

- homework of chapter 4
```text
// 4a  Tournament and Match. the multiplicity
// 4b  a dashed arrow from the worker to the calculator. what does dashed mean
// 4c  draw User and Role with a junction, not with inheritance
```

## chapter 5 Singleton

- a singleton = one instance in the process
- Nest services are singletons by default. one PortCallsService for the process
- that is safe when the service keeps no request data in fields
- a singleton that stores "the current user" in a field mixes two requests
- the database pool is a singleton. the request is not
- tests create their own instance and pass a fake. they do not reach for a global

```ts
@Injectable()
export class Clock {
  now() {
    return new Date();
  }
}
```

- Clock can be a singleton. it has no fields
- a class with `private static instance` is the textbook singleton. in Nest, the module system is that one instance
- if we put a cache Map on the service, say so, and bound its size. it is process memory, not a shared cache across processes

- homework of chapter 5
```ts
// 5a  why a singleton UserContext field breaks under two requests
// 5b  a service that is safe as a singleton
// 5c  where a test gets its own service
```

## chapter 6 Factory and abstract factory

- a factory = a function or class whose job is to build an object
- the caller does not see the constructor details
- we use one when building has a choice. a test clock or a real clock. a local file store or an object store
- an abstract factory = a family of builders that belong together
- example: a "test kit" that builds a fake mailer and a fake storage, and a "production kit" that builds the real ones
- if there is only one product, a single function is enough. the abstract factory is for a set that must match

```ts
function createStorage(env: "test" | "prod"): Storage {
  if (env === "test") return new MemoryStorage();
  return new ObjectStorage(process.env.BUCKET!);
}

interface AppKit {
  storage(): Storage;
  mailer(): Mailer;
}
```

- the controller asks the factory or receives the Storage in the constructor. it does not branch on env itself
- a switch that grows every week is a sign the factory should return an interface, and each branch is a class

- homework of chapter 6
```ts
// 6a  a factory for a Mailer that logs in tests and sends in production
// 6b  when an abstract factory is more than we need
// 6c  who should not contain the env if-statement
```

## chapter 7 Builder and prototype

- a builder = step by step construction when the object has many optional parts
- a constructor with eight optional arguments is hard to read. a builder names each step
- the build method checks that the required parts exist
- a prototype = an object we copy to make another
- in JavaScript, Object.create and the spread operator are the everyday copy
- copy deep when the nested object must not be shared. a shallow copy shares the inner arrays
- we use a prototype when the starting shape is expensive or fiddly, and each copy then changes a little

```ts
class PortCallBuilder {
  private vessel = "";
  private allowedHours = 0;
  vesselName(name: string) {
    this.vessel = name;
    return this;
  }
  hours(n: number) {
    this.allowedHours = n;
    return this;
  }
  build() {
    if (!this.vessel || this.allowedHours <= 0) throw new Error("incomplete");
    return { vesselName: this.vessel, allowedHours: this.allowedHours };
  }
}
```

```ts
const base = { limits: { loginPerMinute: 10 } };
const copy = { ...base, limits: { ...base.limits } };
```

- without the inner spread, `copy.limits.loginPerMinute = 1` would also change base
- a builder that can build an invalid object missed its job. the check is in build()

- homework of chapter 7
```ts
// 7a  build a match with home, away, and an optional court, using a builder
// 7b  show a shallow copy bug with a nested array
// 7c  the deep copy of that array
```

## chapter 8 Adapter, decorator, facade, and proxy

- adapter = a wrapper so a thing we do not control matches the interface we want
- a Stripe object becomes a PaymentGateway with charge() and refund()
- decorator = add behavior around an object, same interface
- a logging decorator calls the real store, then logs the id. the caller still sees PortCallStore
- this is not the same word as a TypeScript decorator. a TypeScript decorator is metadata, such as @Injectable. the pattern is a wrapper object
- facade = a simple front for several steps
- "publish a video" hides the object-store write, the database row, and the encode job
- proxy = a stand-in that controls access. a cache proxy, or a check that the caller may read
- the proxy has the same interface as the real object

```ts
class LoggingStore implements PortCallStore {
  constructor(private readonly inner: PortCallStore) {}
  async find(id: string) {
    const row = await this.inner.find(id);
    console.log("find", id, Boolean(row));
    return row;
  }
}
```

```ts
class PublishVideo {
  constructor(private readonly files: Storage, private readonly db: Db, private readonly jobs: Queue) {}
  async run(ownerId: string, bytes: Buffer) {
    const key = await this.files.put(bytes);
    const video = await this.db.video.create({ data: { ownerId, key } });
    await this.jobs.add("encode", { videoId: video.id });
    return video;
  }
}
```

- the adapter is at the edge, where a vendor type would otherwise leak into the service
- the facade is allowed to do several steps. it is not allowed to hide a money rule that nothing can test

- homework of chapter 8
```ts
// 8a  adapter or decorator: log every find
// 8b  adapter or decorator: wrap a vendor client
// 8c  a facade method name for "sign up and send the first code"
// 8d  a proxy that returns null when the role is viewer and the row is hidden
```

## chapter 9 Observer, strategy, command, and state

- observer = when something happens, tell the subscribers. they subscribed earlier
- Socket.IO rooms are this idea across a network. in one process it is a list of functions
- the subject does not know what the observers do
- strategy = a family of algorithms behind one interface. pick one and pass it in
- despatch at half rate, or despatch at zero, or despatch at the full rate. the laytime function takes the rule instead of a growing if
- command = an object that stands for an action. it can be queued, logged, and sometimes undone
- a job payload is a command. `{ type: "recalculate", portCallId }`
- state = the object changes behavior when its status changes
- a match moves scheduled -> live -> done. a done match does not accept a new score the same way a live one does
- the state can be an enum and a function, not a class per status, when the rules are small

```ts
type DespatchRule = (savedHours: number, perHour: number) => number;

const half: DespatchRule = (hours, perHour) => hours * perHour * 0.5;
const none: DespatchRule = () => 0;
```

```ts
type MatchStatus = "scheduled" | "live" | "done";

function canEditScore(status: MatchStatus): boolean {
  return status === "live" || status === "scheduled";
}
```

- half-rate despatch is only the rule when the contract says so. the strategy makes that a choice, not a hidden 0.5
- an observer that throws should not stop the others, or one slow screen handler takes down the save

- homework of chapter 9
```ts
// 9a  strategy: two despatch rules, pick one in the caller
// 9b  command: the fields of a recalculate job
// 9c  canEditScore("done")
// 9d  observer: who is told when a score is saved, in Bracket
```

## chapter 10 Thread safety

- thread safety = shared data stays correct when work overlaps
- Node's JavaScript does not run two lines at once on the main thread
- it does overlap at every await. two requests can both read, both wait, both write
- that is the bug from the database chapter. the fix is one SQL statement or a transaction
- a field on a singleton is shared by every request. do not store "the current id" there
- a local variable inside the function is safe. it belongs to that call
- worker threads and a second process do not share the heap. they share the database
- the database is the lock we already have. we do not add an in-process mutex and then run two processes

```ts
@Injectable()
export class BadCounter {
  n = 0;
  async bump() {
    const current = this.n;
    await Promise.resolve();
    this.n = current + 1;
  }
}
```

- two overlapping bump calls can both read 0 and both write 1
- the await is the gap, even though there is only one JavaScript thread
- a counter that matters is a row: `UPDATE ... SET n = n + 1`

- homework of chapter 10
```ts
// 10a  why the singleton field breaks and a local variable does not
// 10b  the SQL that does not lose a bump
// 10c  does a second Node process share this.n
```

## chapter 11 Machine coding

- machine coding = build a small working design, not a list of pattern names
- read the rules. name the types. write the one function that is easy to get wrong. then the edges
- a fair exercise from this work: single-elimination, or laytime with one paused hour
- keep a main path working before the extra cases
- a bracket node points at the next match. the winner is written onto this match and into the parent slot

```ts
type Match = {
  id: string;
  a?: string;
  b?: string;
  winner?: string;
  next?: string;
};

function winnerOf(matches: Map<string, Match>, id: string, player: "a" | "b") {
  const match = matches.get(id);
  if (!match || !match[player]) return;
  match.winner = match[player];
  if (!match.next) return;
  const parent = matches.get(match.next);
  if (!parent) return;
  if (!parent.a) parent.a = match.winner;
  else parent.b = match.winner;
}
```

- we did not build a class hierarchy. the type and the function are the design
- the edge we write next is "both players missing" and "parent already full"
- laytime's main path is the 72, 84, 15000 case. the paused hour is the next case, after the test for 7500 exists

- homework of chapter 11
```ts
// 11a  two matches, m1 next is m2. winner of m1 is player a, "Ada". what is m2.a
// 11b  the test for laytime 72, 84, 15000 before any pause rule
// 11c  one edge you would write second, not first
```

## chapter 12 A small design, end to end

- one screen saves a match winner. walk the objects
- the controller is thin
- the service loads the match, checks the status, writes the winner, fills the parent
- the store is an interface
- the status check is the state rule from chapter 9
- the parent fill is the function from chapter 11

```ts
async function recordWinner(store: MatchStore, matchId: string, player: "a" | "b") {
  const matches = await store.loadBracket(matchId);
  const match = matches.get(matchId);
  if (!match) throw new Error("missing");
  if (match.winner) throw new Error("already played");
  winnerOf(matches, matchId, player);
  await store.save(matches);
}
```

- "already played" is the state. we do not need a class named DoneMatch
- save is one transaction in the real store, so the match and the parent commit together
- this is the level of design we draw: nouns, one-to-many, the function that is easy to get wrong, the transaction

- homework of chapter 12
```ts
// 12a  the boxes: controller, service, store, Match
// 12b  why save is a transaction
// 12c  where the "already played" rule lives
// 12d  the UML line between Match and the next Match
```
