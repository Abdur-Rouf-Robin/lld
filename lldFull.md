# LLD

Study notes for this card. Same shape as the JavaScript notes: a fact, the mechanism, code you can type, a spoken answer, then homework.

Read one concept out loud. Close the file. Type the example. Answer the question without looking.

A line the play button covered on the photo is filled in here as the usual concept for that number.

## 01 OOP pillars

- The four pillars are encapsulation, abstraction, inheritance, and polymorphism.

- Encapsulation hides the fields. Callers use methods. The password hash has no setter that takes a raw string from a controller.
- Abstraction is the small surface. A PaymentGateway has charge(). Stripe's HTTP is behind it.
- Inheritance is an is-a relationship. Use it rarely.
- Polymorphism means the caller uses the surface, and the object behaves according to its real type.

```typescript
interface PaymentGateway { charge(amount: number): Promise<string> }
class StripeGateway implements PaymentGateway { /* HTTP here */ }
```

Question. Which pillar do you use most?

Say this. Encapsulation and a small interface. Inheritance is the one I reach for last. A tournament and a friendly match can share a function. They do not need a deep class tree.

Teach it. Encapsulation is a counter with a window. You ask for a ticket. You do not walk in and edit the ledger.

The mistake. A base class of ten subclasses because a tutorial did it that way.

### homework

- Close the page and answer out loud: Which pillar do you use most?

## 02 SOLID

- SOLID is five tests for a class that has started to rot.

- S: one reason to change. The laytime function does not also send email.
- O: add a new payment provider by adding a class, not by editing a switch in five files.
- L: a subtype must be usable anywhere the parent was promised. A 'preview gateway' that throws on charge breaks callers.
- I: small interfaces. Do not make a read model implement a write method.
- D: depend on the interface. The service asks for PaymentGateway, not for StripeGateway.

```typescript
constructor(private readonly payments: PaymentGateway) {}
```

Question. Give one SOLID break you have seen.

Say this. A controller that calculates money, writes SQL, and sends mail. Three reasons to change. I would leave the controller as HTTP, the service as the rule, and the mail on a queue.

Teach it. Each letter is a way of asking 'if this changes, what else breaks?'.

The mistake. Reciting the five words with no example from your code.

### homework

- Close the page and answer out loud: Give one SOLID break you have seen.

## 03 DRY, KISS, YAGNI

- DRY is don't repeat knowledge. KISS is keep it simple. YAGNI is you aren't gonna need it.

- Two copies of the Elo formula will disagree after one fix. That is the DRY that matters. Two similar lines of UI are not a crisis.
- KISS: a sorted array is enough until a heap has a measured job.
- YAGNI: do not build sharding, plugins, and a rules engine for a tournament that has one format.
- The tested shared package for laytime is DRY across the API and the worker.

```typescript
one laytime() used by the API and the worker
no second copy in the React page
```

Question. When would you copy code on purpose?

Say this. When the two copies will change for different reasons. A PDF layout and an email layout can look similar today and diverge. Forcing them into one template makes both worse.

Teach it. DRY is one recipe, not one spoon. KISS is the smallest recipe that feeds the guest. YAGNI is not buying a second oven.

The mistake. A shared helper that takes twelve flags to serve two callers.

### homework

- Close the page and answer out loud: When would you copy code on purpose?

## 04 Composition over inheritance

- Composition means an object holds another object and delegates. Inheritance means it is a subclass.

- A bracket 'has a' scheduler. It is not a subclass of scheduler.
- Inheritance couples the child to the parent's private habits.
- Compose when the behaviour is a part. Inherit when you truly have an is-a and a stable parent, which is rare.
- React does this with components inside components, not with class hierarchies.

```typescript
class Bracket {
  constructor(private readonly rating: Elo) {}
}
```

Question. Why not a BaseService?

Say this. It becomes a drawer of unrelated helpers, and every service inherits mail, cache, and logging it does not use. I inject the logger and the mailer.

Teach it. Inheritance is welding. Composition is bolting on a part you can unbolt.

The mistake. A five-level class tree for user, admin, operator, viewer.

### homework

- Close the page and answer out loud: Why not a BaseService?

## 05 UML class diagrams

- A class diagram names the types, their fields, and who holds whom.

- A box is a class. A line with a diamond is 'has a'. A triangle arrow is inheritance.
- Multiplicity matters: one port call has many facts. Write 1 and *.
- Do not draw every getter. Draw the nouns in the problem.
- In a viva I draw PortCall, StatementOfFact, and LaytimeResult, and the arrow from the worker to the pure function.

```
PortCall 1 ---- * StatementOfFact
PortCall ---- LaytimeResult
LaytimeCalculator ....> PortCall
```

Question. What do you draw first?

Say this. The nouns the user said, and the one-to-many. I add methods only when the interviewer asks who calculates. A diagram of twenty classes in five minutes is unread.

Teach it. The diagram is a map of who owns what. It is not the code.

The mistake. Arrows that mean nothing, or inheritance where you meant 'uses'.

### homework

- Close the page and answer out loud: What do you draw first?

## 06 Singleton

- A singleton is one instance in the process. Nest services are singletons by default.

- The logger, the Prisma client, and the Redis connection are singletons. You do not open a new database pool per request.
- A singleton that holds request data is a bug. The user of request 1 must not leak into request 2.
- Tests can replace the singleton because Nest injects it. A hand-rolled getInstance() hidden in a module is harder to replace.
- One per process is not one in the world. PM2 cluster means several Prisma clients, and that is correct.

```typescript
@Injectable() // one instance for the process
export class PrismaService {}
```

Question. Is a singleton global state?

Say this. The connection is fine. A mutable user on that service is global state and will mix two requests. Keep request data on the request.

Teach it. One telephone for the office is a singleton. Writing the caller's name on the telephone itself is the bug.

The mistake. A mutable cache field on a singleton with no lock and no bound.

### homework

- Close the page and answer out loud: Is a singleton global state?

## 07 Factory

- A factory is a function or class whose job is to build the right object.

- The caller asks for a notifier. The factory returns email or SMS based on a setting.
- The caller does not import every concrete class.
- A simple function is enough. A class named Factory is not more object-oriented.
- Nest providers are factories.

```typescript
function notifier(kind: "email" | "sms"): Notifier {
  return kind === "sms" ? new SmsNotifier() : new EmailNotifier();
}
```

Question. Factory or a switch in the service?

Say this. A switch of two cases in one place is fine. A switch copied in five services is a factory waiting to exist.

Teach it. A factory is the person at the counter who hands you the right form. You do not walk into every office.

The mistake. A factory that also sends the message and writes the database.

### homework

- Close the page and answer out loud: Factory or a switch in the service?

## 08 Abstract factory

- An abstract factory builds a family of objects that belong together.

- A 'Stripe family' might build a charger and a refunder that share a key.
- A 'fake family' builds a fake charger and a fake refunder for tests.
- You need it when objects must match. A Stripe charger with a manual refunder is a bug.
- If you have one object, a normal factory is enough. Do not jump here.

```typescript
interface Billing { charger(): Charger; refunder(): Refunder }
```

Question. Have you used one?

Say this. The idea shows up as a test double that replaces a whole integration. I would not introduce the pattern until two related objects must be swapped together.

Teach it. It is a set of matching furniture. You do not buy the table from one house and the chairs from another.

The mistake. Naming a simple constructor an abstract factory.

### homework

- Close the page and answer out loud: Have you used one?

## 09 Builder

- A builder constructs an object over several steps when a constructor would have a dozen arguments.

- A query or a test fixture is the usual place.
- Each method returns this, and build() returns the finished object.
- The unfinished object is not visible. Callers cannot forget a field if build checks.
- For a DTO with three fields, a constructor is clearer.

```typescript
const call = portCall().vessel("MV Star").arrived(at).build();
```

Question. Builder or options object?

Say this. An options object is the builder I use in TypeScript most days. A builder class earns its place when the steps have order and checks, such as a test fixture.

Teach it. A builder is assembling a form line by line and only handing it over when it is complete.

The mistake. A builder for an object with two fields.

### homework

- Close the page and answer out loud: Builder or options object?

## 10 Prototype

- A prototype copies an existing object to make a new one.

- JavaScript's prototype chain is how objects inherit behaviour. That is the language feature.
- The pattern is clone. A bracket template cloned for a new tournament.
- A shallow copy shares nested objects. A deep copy does not. Know which you did.
- structuredClone or an explicit copy beats hoping spread syntax is deep.

```typescript
const next = structuredClone(template);
next.id = newId();
```

Question. What does {...obj} copy?

Say this. The top level. Nested objects are still shared. Mutating next.rounds[0] mutates the template. I say shallow, and I use a deep clone when the nest must diverge.

Teach it. A prototype is a filled-in form you photocopy. If you only copy the top page, the carbon underneath is still the original.

The mistake. Spread syntax described as a deep copy.

### homework

- Close the page and answer out loud: What does {...obj} copy?

## 11 Adapter

- An adapter wraps a thing so it fits the interface you already have.

- Stripe's SDK is not your PaymentGateway. A small class adapts it.
- The rest of the app never imports Stripe.
- A second provider is a second adapter.
- The adapter translates types and errors. It does not contain the fee rule.

```typescript
class StripeAdapter implements PaymentGateway {
  async charge(amount: number) { /* stripe SDK */ return id; }
}
```

Question. Adapter or rewriting the caller?

Say this. If one outside library has a different shape, wrap it. Do not sprinkle the SDK through the services.

Teach it. An adapter is a travel plug. The device stays the same. The pins change.

The mistake. An adapter that also calculates tax and sends email.

### homework

- Close the page and answer out loud: Adapter or rewriting the caller?

## 12 Decorator

- A decorator wraps an object and adds behaviour, and it still looks like the same interface.

- Logging around a repository. Timing around a client. Retry around a call.
- Nest's @Get and @UseGuards are decorators in the TypeScript sense: functions that attach metadata.
- The pattern and the keyword are related and not identical. Be able to say both.
- Wrapping is how you add behaviour without editing the original class.

```typescript
class LoggingRepo implements PortCalls {
  constructor(private inner: PortCalls, private log: Logger) {}
  find(id: string) {
    this.log.info(id);
    return this.inner.find(id);
  }
}
```

Question. What does @Injectable do?

Say this. It is a TypeScript decorator that marks the class so Nest can inject it. It is metadata. It is not the GoF decorator pattern, and I can explain both if they ask.

Teach it. A decorator is a jacket on the same person. The bouncer still sees a person. The jacket adds pockets.

The mistake. Editing the original class for every cross-cutting concern.

### homework

- Close the page and answer out loud: What does @Injectable do?

## 13 Facade

- A facade is a simple front over several calls.

- Starting a tournament might create the row, seed the bracket, and enqueue a mail. One method does those steps.
- The caller does not learn the order.
- The facade does not hide so much that you cannot test the pieces.
- A Nest service method is often a small facade.

```typescript
start(input) {
  const t = await this.db.create(input);
  await this.bracket.seed(t.id);
  await this.mail.enqueue(t.id);
  return t;
}
```

Question. Facade or god class?

Say this. A facade is thin. It orders the steps. If the fee math moves into it, it has stopped being a facade.

Teach it. A facade is the one button that turns on the lights, the screen, and the sound. The equipment is still separate.

The mistake. A class named Facade that contains the business rules.

### homework

- Close the page and answer out loud: Facade or god class?

## 14 Proxy

- A proxy stands in front of an object and controls access.

- A lazy proxy opens the database connection on the first query.
- A protection proxy checks the role before the real method.
- Nest guards are a form of this at the route, which is usually the better place.
- A proxy that does real work becomes a surprise.

```typescript
class Guarded implements PortCalls {
  find(id: string, user: User) {
    if (!user.roles.includes("operator")) throw new Forbidden();
    return this.inner.find(id);
  }
}
```

Question. Proxy or guard?

Say this. For HTTP, a guard. For a client you do not control, a proxy. I do not hide authorisation only inside a proxy that one caller can forget to use.

Teach it. A proxy is a receptionist who may refuse you before you see the person you asked for.

The mistake. Authorisation only in the React page, which is neither a proxy nor a guard on the server.

### homework

- Close the page and answer out loud: Proxy or guard?

## 15 Observer

- An observer subscribes to a subject. When the subject changes, the observers hear it.

- EventEmitter in Nest is this.
- The subject does not import every listener.
- Listeners must be idempotent if the event can fire twice.
- Socket.IO clients are observers of a room.

```typescript
emitter.emit("laytime.calculated", result);
emitter.on("laytime.calculated", (result) => gateway.push(result));
```

Question. Observer or a direct call?

Say this. A direct call when there is one known next step and the user is waiting. An event when several optional listeners exist, such as a socket push and a metric.

Teach it. An observer is a mailing list. The writer does not visit each house.

The mistake. A listener that throws and stops the others, with no isolation.

### homework

- Close the page and answer out loud: Observer or a direct call?

## 16 Strategy

- A strategy is a swappable algorithm behind one interface.

- Single elimination and double elimination are two strategies with the same 'build bracket' surface.
- The caller picks one. It does not contain both as a switch of two hundred lines.
- This is the open/closed principle in practice.
- A function value is a strategy. A class is optional.

```typescript
const builders = { single: singleElim, double: doubleElim };
return builders[format](players);
```

Question. Strategy or if statements?

Say this. If there are two short branches, if is clearer. If each branch is a page, or a third format is coming, I extract a strategy.

Teach it. A strategy is a lens you can change. The camera stays. The lens does the optics.

The mistake. A strategy interface with one implementation and no second in sight.

### homework

- Close the page and answer out loud: Strategy or if statements?

## 17 Command

- A command is an object that represents an action, so you can queue it, log it, or undo it.

- The command has the data it needs: port call id, not a live request.
- A queue job is a command.
- Undo is another command, or a compensate method, if you truly need it.
- Do not make a command hierarchy for every POST.

```typescript
type Recalculate = { type: "recalculate-laytime"; portCallId: string };
await queue.add(cmd.type, cmd);
```

Question. Is every request a command?

Say this. In the CQRS sense, a write is a command and a read is a query. I do not need the framework. I do need the job object to contain ids, not sockets.

Teach it. A command is a written order that can sit on a spike. The cook does not need the customer in the kitchen.

The mistake. Putting a database client inside the queued payload. It will not survive the trip.

### homework

- Close the page and answer out loud: Is every request a command?

## 18 State

- The state pattern makes an object's behaviour depend on an explicit state, and the transitions are named.

- A match is scheduled, live, or final. A final match does not accept a score edit the same way.
- The illegal transition is a thrown error, not a silent no-op you will forget.
- A column with a check constraint backs the state.
- A pile of booleans, isLive and isFinal, will disagree. One enum will not.

```typescript
type MatchState = "scheduled" | "live" | "final";
function start(state: MatchState): MatchState {
  if (state !== "scheduled") throw new Error("cannot start");
  return "live";
}
```

Question. Where is this on Bracket?

Say this. A match and a payment. A payment is pending, paid, or failed. The webhook may set paid only from pending. A second webhook sees paid and stops.

Teach it. State is a turnstile. It accepts a push in one position and not in another.

The mistake. Two booleans that can both be true.

### homework

- Close the page and answer out loud: Where is this on Bracket?

## 19 Thread safety

- Thread safety means shared data stays correct when two workers touch it.

- On one Node process, two requests interleave at await. That is a race even with one thread.
- A shared mutable object on a singleton is the hazard.
- Atomic database updates and Redis commands are the fix.
- PM2 workers do not share JavaScript objects. They share the database. The race moves there.

```sql
await db.$executeRaw`
  UPDATE berths SET ship_id = ${ship}
  WHERE id = ${id} AND ship_id IS NULL`;
```

Question. Can two requests corrupt a number in one Node process?

Say this. Not by running two JavaScript lines at once. Yes by both reading a value, awaiting, and both writing. The await is the gap. I close the gap with one UPDATE that checks the old value.

Teach it. One cashier with one pen is safe until they put the pen down mid-sum and serve someone else.

The mistake. Assuming await means 'this block is locked'.

### homework

- Close the page and answer out loud: Can two requests corrupt a number in one Node process?

## 20 Machine coding

- Machine coding is building a small working design in the interview, not reciting pattern names.

- Clarify the rules for five minutes. Ask what done means.
- Name the types. Write the state transitions. Then the one function that is easy to get wrong.
- Keep a main path working before you add features.
- Talk while you type. A silent perfect solution is worse than a narrated simple one.
- A fair exercise from your life: a single-elimination bracket, or a laytime function with one exception such as a paused hour.

```typescript
type Match = { id: string; a?: string; b?: string; winner?: string; next?: string };
function report(matches: Match[], id: string, winner: string) {
  const match = matches.find((m) => m.id === id);
  if (!match || match.winner) throw new Error("bad match");
  match.winner = winner;
  const parent = matches.find((m) => m.id === match.next);
  if (!parent) return;
  if (!parent.a) parent.a = winner; else parent.b = winner;
}
```

Question. How do you start?

Say this. I repeat the rules, write the types, and do the happy path. Then I ask about the tie, the replay, and the empty bracket. I do not start with a class diagram of fifteen boxes.

Teach it. It is a small shop you open before the paint is dry. The door works. The decoration waits.

The mistake. Spending forty minutes on folders and interfaces and having nothing that runs.

### homework

- Close the page and answer out loud: How do you start?

## Homework for the whole file

1. Read the twenty titles out loud with the file closed.
2. Pick three and write the example from memory.
3. Teach one concept to an empty chair in under a minute.
