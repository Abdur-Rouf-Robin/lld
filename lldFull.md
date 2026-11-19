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

- example 1. a small type for PortCalls
- encapsulation: the number stays private
- the caller uses a method, not the raw field
- PortCalls is not a subclass of an unrelated noun

```ts
class PortCallsAmount {
  private constructor(private readonly cents: number) {}
  static of(n: number) { return new PortCallsAmount(Math.round(n)); }
  add(other: PortCallsAmount) { return new PortCallsAmount(this.cents + other.cents); }
}
// id pc_12, label Ocean Star
```

- homework
```ts
// 1a  which pillar hides cents for pc_12
// 1b  polymorphism: a function accepts the amount and does not care how it was built
// 1c  do not write class PortCalls extends Unrelated
```

- example 2. a small type for Matches
- encapsulation: the number stays private
- the caller uses a method, not the raw field
- Matches is not a subclass of an unrelated noun

```ts
class MatchesAmount {
  private constructor(private readonly cents: number) {}
  static of(n: number) { return new MatchesAmount(Math.round(n)); }
  add(other: MatchesAmount) { return new MatchesAmount(this.cents + other.cents); }
}
// id m_1, label Ada
```

- homework
```ts
// 2a  which pillar hides cents for m_1
// 2b  polymorphism: a function accepts the amount and does not care how it was built
// 2c  do not write class Matches extends Unrelated
```

- example 3. a small type for Tournaments
- encapsulation: the number stays private
- the caller uses a method, not the raw field
- Tournaments is not a subclass of an unrelated noun

```ts
class TournamentsAmount {
  private constructor(private readonly cents: number) {}
  static of(n: number) { return new TournamentsAmount(Math.round(n)); }
  add(other: TournamentsAmount) { return new TournamentsAmount(this.cents + other.cents); }
}
// id t_9, label Rajshahi Open
```

- homework
```ts
// 3a  which pillar hides cents for t_9
// 3b  polymorphism: a function accepts the amount and does not care how it was built
// 3c  do not write class Tournaments extends Unrelated
```

- example 4. a small type for Videos
- encapsulation: the number stays private
- the caller uses a method, not the raw field
- Videos is not a subclass of an unrelated noun

```ts
class VideosAmount {
  private constructor(private readonly cents: number) {}
  static of(n: number) { return new VideosAmount(Math.round(n)); }
  add(other: VideosAmount) { return new VideosAmount(this.cents + other.cents); }
}
// id v_4, label Episode 1
```

- homework
```ts
// 4a  which pillar hides cents for v_4
// 4b  polymorphism: a function accepts the amount and does not care how it was built
// 4c  do not write class Videos extends Unrelated
```

- example 5. a small type for Facts
- encapsulation: the number stays private
- the caller uses a method, not the raw field
- Facts is not a subclass of an unrelated noun

```ts
class FactsAmount {
  private constructor(private readonly cents: number) {}
  static of(n: number) { return new FactsAmount(Math.round(n)); }
  add(other: FactsAmount) { return new FactsAmount(this.cents + other.cents); }
}
// id f_2, label NOR
```

- homework
```ts
// 5a  which pillar hides cents for f_2
// 5b  polymorphism: a function accepts the amount and does not care how it was built
// 5c  do not write class Facts extends Unrelated
```

- example 6. a small type for Users
- encapsulation: the number stays private
- the caller uses a method, not the raw field
- Users is not a subclass of an unrelated noun

```ts
class UsersAmount {
  private constructor(private readonly cents: number) {}
  static of(n: number) { return new UsersAmount(Math.round(n)); }
  add(other: UsersAmount) { return new UsersAmount(this.cents + other.cents); }
}
// id u_3, label a@example.com
```

- homework
```ts
// 6a  which pillar hides cents for u_3
// 6b  polymorphism: a function accepts the amount and does not care how it was built
// 6c  do not write class Users extends Unrelated
```

- example 7. a small type for Payments
- encapsulation: the number stays private
- the caller uses a method, not the raw field
- Payments is not a subclass of an unrelated noun

```ts
class PaymentsAmount {
  private constructor(private readonly cents: number) {}
  static of(n: number) { return new PaymentsAmount(Math.round(n)); }
  add(other: PaymentsAmount) { return new PaymentsAmount(this.cents + other.cents); }
}
// id pay_8, label evt_1
```

- homework
```ts
// 7a  which pillar hides cents for pay_8
// 7b  polymorphism: a function accepts the amount and does not care how it was built
// 7c  do not write class Payments extends Unrelated
```

- example 8. a small type for Rooms
- encapsulation: the number stays private
- the caller uses a method, not the raw field
- Rooms is not a subclass of an unrelated noun

```ts
class RoomsAmount {
  private constructor(private readonly cents: number) {}
  static of(n: number) { return new RoomsAmount(Math.round(n)); }
  add(other: RoomsAmount) { return new RoomsAmount(this.cents + other.cents); }
}
// id room_2, label s_9
```

- homework
```ts
// 8a  which pillar hides cents for room_2
// 8b  polymorphism: a function accepts the amount and does not care how it was built
// 8c  do not write class Rooms extends Unrelated
```

- example 9. a small type for Vessels
- encapsulation: the number stays private
- the caller uses a method, not the raw field
- Vessels is not a subclass of an unrelated noun

```ts
class VesselsAmount {
  private constructor(private readonly cents: number) {}
  static of(n: number) { return new VesselsAmount(Math.round(n)); }
  add(other: VesselsAmount) { return new VesselsAmount(this.cents + other.cents); }
}
// id vs_7, label North Wind
```

- homework
```ts
// 9a  which pillar hides cents for vs_7
// 9b  polymorphism: a function accepts the amount and does not care how it was built
// 9c  do not write class Vessels extends Unrelated
```

- example 10. a small type for Scores
- encapsulation: the number stays private
- the caller uses a method, not the raw field
- Scores is not a subclass of an unrelated noun

```ts
class ScoresAmount {
  private constructor(private readonly cents: number) {}
  static of(n: number) { return new ScoresAmount(Math.round(n)); }
  add(other: ScoresAmount) { return new ScoresAmount(this.cents + other.cents); }
}
// id sc_3, label 11
```

- homework
```ts
// 10a  which pillar hides cents for sc_3
// 10b  polymorphism: a function accepts the amount and does not care how it was built
// 10c  do not write class Scores extends Unrelated
```

- example 11. a small type for Teams
- encapsulation: the number stays private
- the caller uses a method, not the raw field
- Teams is not a subclass of an unrelated noun

```ts
class TeamsAmount {
  private constructor(private readonly cents: number) {}
  static of(n: number) { return new TeamsAmount(Math.round(n)); }
  add(other: TeamsAmount) { return new TeamsAmount(this.cents + other.cents); }
}
// id tm_2, label Blue
```

- homework
```ts
// 11a  which pillar hides cents for tm_2
// 11b  polymorphism: a function accepts the amount and does not care how it was built
// 11c  do not write class Teams extends Unrelated
```

- example 12. a small type for Uploads
- encapsulation: the number stays private
- the caller uses a method, not the raw field
- Uploads is not a subclass of an unrelated noun

```ts
class UploadsAmount {
  private constructor(private readonly cents: number) {}
  static of(n: number) { return new UploadsAmount(Math.round(n)); }
  add(other: UploadsAmount) { return new UploadsAmount(this.cents + other.cents); }
}
// id up_6, label videos/u_1/a.mp4
```

- homework
```ts
// 12a  which pillar hides cents for up_6
// 12b  polymorphism: a function accepts the amount and does not care how it was built
// 12c  do not write class Uploads extends Unrelated
```

- example 13. a small type for Standings
- encapsulation: the number stays private
- the caller uses a method, not the raw field
- Standings is not a subclass of an unrelated noun

```ts
class StandingsAmount {
  private constructor(private readonly cents: number) {}
  static of(n: number) { return new StandingsAmount(Math.round(n)); }
  add(other: StandingsAmount) { return new StandingsAmount(this.cents + other.cents); }
}
// id st_1, label player_a
```

- homework
```ts
// 13a  which pillar hides cents for st_1
// 13b  polymorphism: a function accepts the amount and does not care how it was built
// 13c  do not write class Standings extends Unrelated
```

- example 14. a small type for Notices
- encapsulation: the number stays private
- the caller uses a method, not the raw field
- Notices is not a subclass of an unrelated noun

```ts
class NoticesAmount {
  private constructor(private readonly cents: number) {}
  static of(n: number) { return new NoticesAmount(Math.round(n)); }
  add(other: NoticesAmount) { return new NoticesAmount(this.cents + other.cents); }
}
// id n_2, label Chattogram
```

- homework
```ts
// 14a  which pillar hides cents for n_2
// 14b  polymorphism: a function accepts the amount and does not care how it was built
// 14c  do not write class Notices extends Unrelated
```

- example 15. a small type for Brackets
- encapsulation: the number stays private
- the caller uses a method, not the raw field
- Brackets is not a subclass of an unrelated noun

```ts
class BracketsAmount {
  private constructor(private readonly cents: number) {}
  static of(n: number) { return new BracketsAmount(Math.round(n)); }
  add(other: BracketsAmount) { return new BracketsAmount(this.cents + other.cents); }
}
// id b_3, label semi
```

- homework
```ts
// 15a  which pillar hides cents for b_3
// 15b  polymorphism: a function accepts the amount and does not care how it was built
// 15c  do not write class Brackets extends Unrelated
```

- example 16. a small type for Sessions
- encapsulation: the number stays private
- the caller uses a method, not the raw field
- Sessions is not a subclass of an unrelated noun

```ts
class SessionsAmount {
  private constructor(private readonly cents: number) {}
  static of(n: number) { return new SessionsAmount(Math.round(n)); }
  add(other: SessionsAmount) { return new SessionsAmount(this.cents + other.cents); }
}
// id se_1, label u_3
```

- homework
```ts
// 16a  which pillar hides cents for se_1
// 16b  polymorphism: a function accepts the amount and does not care how it was built
// 16c  do not write class Sessions extends Unrelated
```

- example 17. a small type for Queues
- encapsulation: the number stays private
- the caller uses a method, not the raw field
- Queues is not a subclass of an unrelated noun

```ts
class QueuesAmount {
  private constructor(private readonly cents: number) {}
  static of(n: number) { return new QueuesAmount(Math.round(n)); }
  add(other: QueuesAmount) { return new QueuesAmount(this.cents + other.cents); }
}
// id q_1, label laytime
```

- homework
```ts
// 17a  which pillar hides cents for q_1
// 17b  polymorphism: a function accepts the amount and does not care how it was built
// 17c  do not write class Queues extends Unrelated
```

- example 18. a small type for Roles
- encapsulation: the number stays private
- the caller uses a method, not the raw field
- Roles is not a subclass of an unrelated noun

```ts
class RolesAmount {
  private constructor(private readonly cents: number) {}
  static of(n: number) { return new RolesAmount(Math.round(n)); }
  add(other: RolesAmount) { return new RolesAmount(this.cents + other.cents); }
}
// id r_1, label operator
```

- homework
```ts
// 18a  which pillar hides cents for r_1
// 18b  polymorphism: a function accepts the amount and does not care how it was built
// 18c  do not write class Roles extends Unrelated
```

- example 19. a small type for PortCalls
- encapsulation: the number stays private
- the caller uses a method, not the raw field
- PortCalls is not a subclass of an unrelated noun

```ts
class PortCallsAmount {
  private constructor(private readonly cents: number) {}
  static of(n: number) { return new PortCallsAmount(Math.round(n)); }
  add(other: PortCallsAmount) { return new PortCallsAmount(this.cents + other.cents); }
}
// id pc_12, label Ocean Star
```

- homework
```ts
// 19a  which pillar hides cents for pc_12
// 19b  polymorphism: a function accepts the amount and does not care how it was built
// 19c  do not write class PortCalls extends Unrelated
```

- example 20. a small type for Matches
- encapsulation: the number stays private
- the caller uses a method, not the raw field
- Matches is not a subclass of an unrelated noun

```ts
class MatchesAmount {
  private constructor(private readonly cents: number) {}
  static of(n: number) { return new MatchesAmount(Math.round(n)); }
  add(other: MatchesAmount) { return new MatchesAmount(this.cents + other.cents); }
}
// id m_1, label Ada
```

- homework
```ts
// 20a  which pillar hides cents for m_1
// 20b  polymorphism: a function accepts the amount and does not care how it was built
// 20c  do not write class Matches extends Unrelated
```

- example 21. a small type for Tournaments
- encapsulation: the number stays private
- the caller uses a method, not the raw field
- Tournaments is not a subclass of an unrelated noun

```ts
class TournamentsAmount {
  private constructor(private readonly cents: number) {}
  static of(n: number) { return new TournamentsAmount(Math.round(n)); }
  add(other: TournamentsAmount) { return new TournamentsAmount(this.cents + other.cents); }
}
// id t_9, label Rajshahi Open
```

- homework
```ts
// 21a  which pillar hides cents for t_9
// 21b  polymorphism: a function accepts the amount and does not care how it was built
// 21c  do not write class Tournaments extends Unrelated
```

- example 22. a small type for Videos
- encapsulation: the number stays private
- the caller uses a method, not the raw field
- Videos is not a subclass of an unrelated noun

```ts
class VideosAmount {
  private constructor(private readonly cents: number) {}
  static of(n: number) { return new VideosAmount(Math.round(n)); }
  add(other: VideosAmount) { return new VideosAmount(this.cents + other.cents); }
}
// id v_4, label Episode 1
```

- homework
```ts
// 22a  which pillar hides cents for v_4
// 22b  polymorphism: a function accepts the amount and does not care how it was built
// 22c  do not write class Videos extends Unrelated
```

- example 23. a small type for Facts
- encapsulation: the number stays private
- the caller uses a method, not the raw field
- Facts is not a subclass of an unrelated noun

```ts
class FactsAmount {
  private constructor(private readonly cents: number) {}
  static of(n: number) { return new FactsAmount(Math.round(n)); }
  add(other: FactsAmount) { return new FactsAmount(this.cents + other.cents); }
}
// id f_2, label NOR
```

- homework
```ts
// 23a  which pillar hides cents for f_2
// 23b  polymorphism: a function accepts the amount and does not care how it was built
// 23c  do not write class Facts extends Unrelated
```

- example 24. a small type for Users
- encapsulation: the number stays private
- the caller uses a method, not the raw field
- Users is not a subclass of an unrelated noun

```ts
class UsersAmount {
  private constructor(private readonly cents: number) {}
  static of(n: number) { return new UsersAmount(Math.round(n)); }
  add(other: UsersAmount) { return new UsersAmount(this.cents + other.cents); }
}
// id u_3, label a@example.com
```

- homework
```ts
// 24a  which pillar hides cents for u_3
// 24b  polymorphism: a function accepts the amount and does not care how it was built
// 24c  do not write class Users extends Unrelated
```

- example 25. a small type for Payments
- encapsulation: the number stays private
- the caller uses a method, not the raw field
- Payments is not a subclass of an unrelated noun

```ts
class PaymentsAmount {
  private constructor(private readonly cents: number) {}
  static of(n: number) { return new PaymentsAmount(Math.round(n)); }
  add(other: PaymentsAmount) { return new PaymentsAmount(this.cents + other.cents); }
}
// id pay_8, label evt_1
```

- homework
```ts
// 25a  which pillar hides cents for pay_8
// 25b  polymorphism: a function accepts the amount and does not care how it was built
// 25c  do not write class Payments extends Unrelated
```

- example 26. a small type for Rooms
- encapsulation: the number stays private
- the caller uses a method, not the raw field
- Rooms is not a subclass of an unrelated noun

```ts
class RoomsAmount {
  private constructor(private readonly cents: number) {}
  static of(n: number) { return new RoomsAmount(Math.round(n)); }
  add(other: RoomsAmount) { return new RoomsAmount(this.cents + other.cents); }
}
// id room_2, label s_9
```

- homework
```ts
// 26a  which pillar hides cents for room_2
// 26b  polymorphism: a function accepts the amount and does not care how it was built
// 26c  do not write class Rooms extends Unrelated
```

- example 27. a small type for Vessels
- encapsulation: the number stays private
- the caller uses a method, not the raw field
- Vessels is not a subclass of an unrelated noun

```ts
class VesselsAmount {
  private constructor(private readonly cents: number) {}
  static of(n: number) { return new VesselsAmount(Math.round(n)); }
  add(other: VesselsAmount) { return new VesselsAmount(this.cents + other.cents); }
}
// id vs_7, label North Wind
```

- homework
```ts
// 27a  which pillar hides cents for vs_7
// 27b  polymorphism: a function accepts the amount and does not care how it was built
// 27c  do not write class Vessels extends Unrelated
```

- example 28. a small type for Scores
- encapsulation: the number stays private
- the caller uses a method, not the raw field
- Scores is not a subclass of an unrelated noun

```ts
class ScoresAmount {
  private constructor(private readonly cents: number) {}
  static of(n: number) { return new ScoresAmount(Math.round(n)); }
  add(other: ScoresAmount) { return new ScoresAmount(this.cents + other.cents); }
}
// id sc_3, label 11
```

- homework
```ts
// 28a  which pillar hides cents for sc_3
// 28b  polymorphism: a function accepts the amount and does not care how it was built
// 28c  do not write class Scores extends Unrelated
```

- example 29. a small type for Teams
- encapsulation: the number stays private
- the caller uses a method, not the raw field
- Teams is not a subclass of an unrelated noun

```ts
class TeamsAmount {
  private constructor(private readonly cents: number) {}
  static of(n: number) { return new TeamsAmount(Math.round(n)); }
  add(other: TeamsAmount) { return new TeamsAmount(this.cents + other.cents); }
}
// id tm_2, label Blue
```

- homework
```ts
// 29a  which pillar hides cents for tm_2
// 29b  polymorphism: a function accepts the amount and does not care how it was built
// 29c  do not write class Teams extends Unrelated
```

- example 30. a small type for Uploads
- encapsulation: the number stays private
- the caller uses a method, not the raw field
- Uploads is not a subclass of an unrelated noun

```ts
class UploadsAmount {
  private constructor(private readonly cents: number) {}
  static of(n: number) { return new UploadsAmount(Math.round(n)); }
  add(other: UploadsAmount) { return new UploadsAmount(this.cents + other.cents); }
}
// id up_6, label videos/u_1/a.mp4
```

- homework
```ts
// 30a  which pillar hides cents for up_6
// 30b  polymorphism: a function accepts the amount and does not care how it was built
// 30c  do not write class Uploads extends Unrelated
```

- example 31. a small type for Standings
- encapsulation: the number stays private
- the caller uses a method, not the raw field
- Standings is not a subclass of an unrelated noun

```ts
class StandingsAmount {
  private constructor(private readonly cents: number) {}
  static of(n: number) { return new StandingsAmount(Math.round(n)); }
  add(other: StandingsAmount) { return new StandingsAmount(this.cents + other.cents); }
}
// id st_1, label player_a
```

- homework
```ts
// 31a  which pillar hides cents for st_1
// 31b  polymorphism: a function accepts the amount and does not care how it was built
// 31c  do not write class Standings extends Unrelated
```

- example 32. a small type for Notices
- encapsulation: the number stays private
- the caller uses a method, not the raw field
- Notices is not a subclass of an unrelated noun

```ts
class NoticesAmount {
  private constructor(private readonly cents: number) {}
  static of(n: number) { return new NoticesAmount(Math.round(n)); }
  add(other: NoticesAmount) { return new NoticesAmount(this.cents + other.cents); }
}
// id n_2, label Chattogram
```

- homework
```ts
// 32a  which pillar hides cents for n_2
// 32b  polymorphism: a function accepts the amount and does not care how it was built
// 32c  do not write class Notices extends Unrelated
```

- example 33. a small type for Brackets
- encapsulation: the number stays private
- the caller uses a method, not the raw field
- Brackets is not a subclass of an unrelated noun

```ts
class BracketsAmount {
  private constructor(private readonly cents: number) {}
  static of(n: number) { return new BracketsAmount(Math.round(n)); }
  add(other: BracketsAmount) { return new BracketsAmount(this.cents + other.cents); }
}
// id b_3, label semi
```

- homework
```ts
// 33a  which pillar hides cents for b_3
// 33b  polymorphism: a function accepts the amount and does not care how it was built
// 33c  do not write class Brackets extends Unrelated
```

- example 34. a small type for Sessions
- encapsulation: the number stays private
- the caller uses a method, not the raw field
- Sessions is not a subclass of an unrelated noun

```ts
class SessionsAmount {
  private constructor(private readonly cents: number) {}
  static of(n: number) { return new SessionsAmount(Math.round(n)); }
  add(other: SessionsAmount) { return new SessionsAmount(this.cents + other.cents); }
}
// id se_1, label u_3
```

- homework
```ts
// 34a  which pillar hides cents for se_1
// 34b  polymorphism: a function accepts the amount and does not care how it was built
// 34c  do not write class Sessions extends Unrelated
```

- example 35. a small type for Queues
- encapsulation: the number stays private
- the caller uses a method, not the raw field
- Queues is not a subclass of an unrelated noun

```ts
class QueuesAmount {
  private constructor(private readonly cents: number) {}
  static of(n: number) { return new QueuesAmount(Math.round(n)); }
  add(other: QueuesAmount) { return new QueuesAmount(this.cents + other.cents); }
}
// id q_1, label laytime
```

- homework
```ts
// 35a  which pillar hides cents for q_1
// 35b  polymorphism: a function accepts the amount and does not care how it was built
// 35c  do not write class Queues extends Unrelated
```

- example 36. a small type for Roles
- encapsulation: the number stays private
- the caller uses a method, not the raw field
- Roles is not a subclass of an unrelated noun

```ts
class RolesAmount {
  private constructor(private readonly cents: number) {}
  static of(n: number) { return new RolesAmount(Math.round(n)); }
  add(other: RolesAmount) { return new RolesAmount(this.cents + other.cents); }
}
// id r_1, label operator
```

- homework
```ts
// 36a  which pillar hides cents for r_1
// 36b  polymorphism: a function accepts the amount and does not care how it was built
// 36c  do not write class Roles extends Unrelated
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

- example 1. SOLID on a store for pc_12
- the service depends on an interface
- the test passes a fake that returns Ocean Star
- one reason to change: this service does not also send mail

```ts
interface Store {
  find(id: string): Promise<{ vesselName: string } | null>;
}
class Service {
  constructor(private readonly store: Store) {}
  async load() { return this.store.find("pc_12"); }
}
```

- homework
```ts
// 1a  D is the fake store for pc_12
// 1b  S is "do not also email inside load"
// 1c  a subtype that throws on find breaks L
```

- example 2. SOLID on a store for m_1
- the service depends on an interface
- the test passes a fake that returns Ada
- one reason to change: this service does not also send mail

```ts
interface Store {
  find(id: string): Promise<{ home: string } | null>;
}
class Service {
  constructor(private readonly store: Store) {}
  async load() { return this.store.find("m_1"); }
}
```

- homework
```ts
// 2a  D is the fake store for m_1
// 2b  S is "do not also email inside load"
// 2c  a subtype that throws on find breaks L
```

- example 3. SOLID on a store for t_9
- the service depends on an interface
- the test passes a fake that returns Rajshahi Open
- one reason to change: this service does not also send mail

```ts
interface Store {
  find(id: string): Promise<{ name: string } | null>;
}
class Service {
  constructor(private readonly store: Store) {}
  async load() { return this.store.find("t_9"); }
}
```

- homework
```ts
// 3a  D is the fake store for t_9
// 3b  S is "do not also email inside load"
// 3c  a subtype that throws on find breaks L
```

- example 4. SOLID on a store for v_4
- the service depends on an interface
- the test passes a fake that returns Episode 1
- one reason to change: this service does not also send mail

```ts
interface Store {
  find(id: string): Promise<{ title: string } | null>;
}
class Service {
  constructor(private readonly store: Store) {}
  async load() { return this.store.find("v_4"); }
}
```

- homework
```ts
// 4a  D is the fake store for v_4
// 4b  S is "do not also email inside load"
// 4c  a subtype that throws on find breaks L
```

- example 5. SOLID on a store for f_2
- the service depends on an interface
- the test passes a fake that returns NOR
- one reason to change: this service does not also send mail

```ts
interface Store {
  find(id: string): Promise<{ kind: string } | null>;
}
class Service {
  constructor(private readonly store: Store) {}
  async load() { return this.store.find("f_2"); }
}
```

- homework
```ts
// 5a  D is the fake store for f_2
// 5b  S is "do not also email inside load"
// 5c  a subtype that throws on find breaks L
```

- example 6. SOLID on a store for u_3
- the service depends on an interface
- the test passes a fake that returns a@example.com
- one reason to change: this service does not also send mail

```ts
interface Store {
  find(id: string): Promise<{ email: string } | null>;
}
class Service {
  constructor(private readonly store: Store) {}
  async load() { return this.store.find("u_3"); }
}
```

- homework
```ts
// 6a  D is the fake store for u_3
// 6b  S is "do not also email inside load"
// 6c  a subtype that throws on find breaks L
```

- example 7. SOLID on a store for pay_8
- the service depends on an interface
- the test passes a fake that returns evt_1
- one reason to change: this service does not also send mail

```ts
interface Store {
  find(id: string): Promise<{ eventId: string } | null>;
}
class Service {
  constructor(private readonly store: Store) {}
  async load() { return this.store.find("pay_8"); }
}
```

- homework
```ts
// 7a  D is the fake store for pay_8
// 7b  S is "do not also email inside load"
// 7c  a subtype that throws on find breaks L
```

- example 8. SOLID on a store for room_2
- the service depends on an interface
- the test passes a fake that returns s_9
- one reason to change: this service does not also send mail

```ts
interface Store {
  find(id: string): Promise<{ sessionId: string } | null>;
}
class Service {
  constructor(private readonly store: Store) {}
  async load() { return this.store.find("room_2"); }
}
```

- homework
```ts
// 8a  D is the fake store for room_2
// 8b  S is "do not also email inside load"
// 8c  a subtype that throws on find breaks L
```

- example 9. SOLID on a store for vs_7
- the service depends on an interface
- the test passes a fake that returns North Wind
- one reason to change: this service does not also send mail

```ts
interface Store {
  find(id: string): Promise<{ name: string } | null>;
}
class Service {
  constructor(private readonly store: Store) {}
  async load() { return this.store.find("vs_7"); }
}
```

- homework
```ts
// 9a  D is the fake store for vs_7
// 9b  S is "do not also email inside load"
// 9c  a subtype that throws on find breaks L
```

- example 10. SOLID on a store for sc_3
- the service depends on an interface
- the test passes a fake that returns 11
- one reason to change: this service does not also send mail

```ts
interface Store {
  find(id: string): Promise<{ points: string } | null>;
}
class Service {
  constructor(private readonly store: Store) {}
  async load() { return this.store.find("sc_3"); }
}
```

- homework
```ts
// 10a  D is the fake store for sc_3
// 10b  S is "do not also email inside load"
// 10c  a subtype that throws on find breaks L
```

- example 11. SOLID on a store for tm_2
- the service depends on an interface
- the test passes a fake that returns Blue
- one reason to change: this service does not also send mail

```ts
interface Store {
  find(id: string): Promise<{ name: string } | null>;
}
class Service {
  constructor(private readonly store: Store) {}
  async load() { return this.store.find("tm_2"); }
}
```

- homework
```ts
// 11a  D is the fake store for tm_2
// 11b  S is "do not also email inside load"
// 11c  a subtype that throws on find breaks L
```

- example 12. SOLID on a store for up_6
- the service depends on an interface
- the test passes a fake that returns videos/u_1/a.mp4
- one reason to change: this service does not also send mail

```ts
interface Store {
  find(id: string): Promise<{ key: string } | null>;
}
class Service {
  constructor(private readonly store: Store) {}
  async load() { return this.store.find("up_6"); }
}
```

- homework
```ts
// 12a  D is the fake store for up_6
// 12b  S is "do not also email inside load"
// 12c  a subtype that throws on find breaks L
```

- example 13. SOLID on a store for st_1
- the service depends on an interface
- the test passes a fake that returns player_a
- one reason to change: this service does not also send mail

```ts
interface Store {
  find(id: string): Promise<{ player: string } | null>;
}
class Service {
  constructor(private readonly store: Store) {}
  async load() { return this.store.find("st_1"); }
}
```

- homework
```ts
// 13a  D is the fake store for st_1
// 13b  S is "do not also email inside load"
// 13c  a subtype that throws on find breaks L
```

- example 14. SOLID on a store for n_2
- the service depends on an interface
- the test passes a fake that returns Chattogram
- one reason to change: this service does not also send mail

```ts
interface Store {
  find(id: string): Promise<{ port: string } | null>;
}
class Service {
  constructor(private readonly store: Store) {}
  async load() { return this.store.find("n_2"); }
}
```

- homework
```ts
// 14a  D is the fake store for n_2
// 14b  S is "do not also email inside load"
// 14c  a subtype that throws on find breaks L
```

- example 15. SOLID on a store for b_3
- the service depends on an interface
- the test passes a fake that returns semi
- one reason to change: this service does not also send mail

```ts
interface Store {
  find(id: string): Promise<{ round: string } | null>;
}
class Service {
  constructor(private readonly store: Store) {}
  async load() { return this.store.find("b_3"); }
}
```

- homework
```ts
// 15a  D is the fake store for b_3
// 15b  S is "do not also email inside load"
// 15c  a subtype that throws on find breaks L
```

- example 16. SOLID on a store for se_1
- the service depends on an interface
- the test passes a fake that returns u_3
- one reason to change: this service does not also send mail

```ts
interface Store {
  find(id: string): Promise<{ userId: string } | null>;
}
class Service {
  constructor(private readonly store: Store) {}
  async load() { return this.store.find("se_1"); }
}
```

- homework
```ts
// 16a  D is the fake store for se_1
// 16b  S is "do not also email inside load"
// 16c  a subtype that throws on find breaks L
```

- example 17. SOLID on a store for q_1
- the service depends on an interface
- the test passes a fake that returns laytime
- one reason to change: this service does not also send mail

```ts
interface Store {
  find(id: string): Promise<{ name: string } | null>;
}
class Service {
  constructor(private readonly store: Store) {}
  async load() { return this.store.find("q_1"); }
}
```

- homework
```ts
// 17a  D is the fake store for q_1
// 17b  S is "do not also email inside load"
// 17c  a subtype that throws on find breaks L
```

- example 18. SOLID on a store for r_1
- the service depends on an interface
- the test passes a fake that returns operator
- one reason to change: this service does not also send mail

```ts
interface Store {
  find(id: string): Promise<{ name: string } | null>;
}
class Service {
  constructor(private readonly store: Store) {}
  async load() { return this.store.find("r_1"); }
}
```

- homework
```ts
// 18a  D is the fake store for r_1
// 18b  S is "do not also email inside load"
// 18c  a subtype that throws on find breaks L
```

- example 19. SOLID on a store for pc_12
- the service depends on an interface
- the test passes a fake that returns Ocean Star
- one reason to change: this service does not also send mail

```ts
interface Store {
  find(id: string): Promise<{ vesselName: string } | null>;
}
class Service {
  constructor(private readonly store: Store) {}
  async load() { return this.store.find("pc_12"); }
}
```

- homework
```ts
// 19a  D is the fake store for pc_12
// 19b  S is "do not also email inside load"
// 19c  a subtype that throws on find breaks L
```

- example 20. SOLID on a store for m_1
- the service depends on an interface
- the test passes a fake that returns Ada
- one reason to change: this service does not also send mail

```ts
interface Store {
  find(id: string): Promise<{ home: string } | null>;
}
class Service {
  constructor(private readonly store: Store) {}
  async load() { return this.store.find("m_1"); }
}
```

- homework
```ts
// 20a  D is the fake store for m_1
// 20b  S is "do not also email inside load"
// 20c  a subtype that throws on find breaks L
```

- example 21. SOLID on a store for t_9
- the service depends on an interface
- the test passes a fake that returns Rajshahi Open
- one reason to change: this service does not also send mail

```ts
interface Store {
  find(id: string): Promise<{ name: string } | null>;
}
class Service {
  constructor(private readonly store: Store) {}
  async load() { return this.store.find("t_9"); }
}
```

- homework
```ts
// 21a  D is the fake store for t_9
// 21b  S is "do not also email inside load"
// 21c  a subtype that throws on find breaks L
```

- example 22. SOLID on a store for v_4
- the service depends on an interface
- the test passes a fake that returns Episode 1
- one reason to change: this service does not also send mail

```ts
interface Store {
  find(id: string): Promise<{ title: string } | null>;
}
class Service {
  constructor(private readonly store: Store) {}
  async load() { return this.store.find("v_4"); }
}
```

- homework
```ts
// 22a  D is the fake store for v_4
// 22b  S is "do not also email inside load"
// 22c  a subtype that throws on find breaks L
```

- example 23. SOLID on a store for f_2
- the service depends on an interface
- the test passes a fake that returns NOR
- one reason to change: this service does not also send mail

```ts
interface Store {
  find(id: string): Promise<{ kind: string } | null>;
}
class Service {
  constructor(private readonly store: Store) {}
  async load() { return this.store.find("f_2"); }
}
```

- homework
```ts
// 23a  D is the fake store for f_2
// 23b  S is "do not also email inside load"
// 23c  a subtype that throws on find breaks L
```

- example 24. SOLID on a store for u_3
- the service depends on an interface
- the test passes a fake that returns a@example.com
- one reason to change: this service does not also send mail

```ts
interface Store {
  find(id: string): Promise<{ email: string } | null>;
}
class Service {
  constructor(private readonly store: Store) {}
  async load() { return this.store.find("u_3"); }
}
```

- homework
```ts
// 24a  D is the fake store for u_3
// 24b  S is "do not also email inside load"
// 24c  a subtype that throws on find breaks L
```

- example 25. SOLID on a store for pay_8
- the service depends on an interface
- the test passes a fake that returns evt_1
- one reason to change: this service does not also send mail

```ts
interface Store {
  find(id: string): Promise<{ eventId: string } | null>;
}
class Service {
  constructor(private readonly store: Store) {}
  async load() { return this.store.find("pay_8"); }
}
```

- homework
```ts
// 25a  D is the fake store for pay_8
// 25b  S is "do not also email inside load"
// 25c  a subtype that throws on find breaks L
```

- example 26. SOLID on a store for room_2
- the service depends on an interface
- the test passes a fake that returns s_9
- one reason to change: this service does not also send mail

```ts
interface Store {
  find(id: string): Promise<{ sessionId: string } | null>;
}
class Service {
  constructor(private readonly store: Store) {}
  async load() { return this.store.find("room_2"); }
}
```

- homework
```ts
// 26a  D is the fake store for room_2
// 26b  S is "do not also email inside load"
// 26c  a subtype that throws on find breaks L
```

- example 27. SOLID on a store for vs_7
- the service depends on an interface
- the test passes a fake that returns North Wind
- one reason to change: this service does not also send mail

```ts
interface Store {
  find(id: string): Promise<{ name: string } | null>;
}
class Service {
  constructor(private readonly store: Store) {}
  async load() { return this.store.find("vs_7"); }
}
```

- homework
```ts
// 27a  D is the fake store for vs_7
// 27b  S is "do not also email inside load"
// 27c  a subtype that throws on find breaks L
```

- example 28. SOLID on a store for sc_3
- the service depends on an interface
- the test passes a fake that returns 11
- one reason to change: this service does not also send mail

```ts
interface Store {
  find(id: string): Promise<{ points: string } | null>;
}
class Service {
  constructor(private readonly store: Store) {}
  async load() { return this.store.find("sc_3"); }
}
```

- homework
```ts
// 28a  D is the fake store for sc_3
// 28b  S is "do not also email inside load"
// 28c  a subtype that throws on find breaks L
```

- example 29. SOLID on a store for tm_2
- the service depends on an interface
- the test passes a fake that returns Blue
- one reason to change: this service does not also send mail

```ts
interface Store {
  find(id: string): Promise<{ name: string } | null>;
}
class Service {
  constructor(private readonly store: Store) {}
  async load() { return this.store.find("tm_2"); }
}
```

- homework
```ts
// 29a  D is the fake store for tm_2
// 29b  S is "do not also email inside load"
// 29c  a subtype that throws on find breaks L
```

- example 30. SOLID on a store for up_6
- the service depends on an interface
- the test passes a fake that returns videos/u_1/a.mp4
- one reason to change: this service does not also send mail

```ts
interface Store {
  find(id: string): Promise<{ key: string } | null>;
}
class Service {
  constructor(private readonly store: Store) {}
  async load() { return this.store.find("up_6"); }
}
```

- homework
```ts
// 30a  D is the fake store for up_6
// 30b  S is "do not also email inside load"
// 30c  a subtype that throws on find breaks L
```

- example 31. SOLID on a store for st_1
- the service depends on an interface
- the test passes a fake that returns player_a
- one reason to change: this service does not also send mail

```ts
interface Store {
  find(id: string): Promise<{ player: string } | null>;
}
class Service {
  constructor(private readonly store: Store) {}
  async load() { return this.store.find("st_1"); }
}
```

- homework
```ts
// 31a  D is the fake store for st_1
// 31b  S is "do not also email inside load"
// 31c  a subtype that throws on find breaks L
```

- example 32. SOLID on a store for n_2
- the service depends on an interface
- the test passes a fake that returns Chattogram
- one reason to change: this service does not also send mail

```ts
interface Store {
  find(id: string): Promise<{ port: string } | null>;
}
class Service {
  constructor(private readonly store: Store) {}
  async load() { return this.store.find("n_2"); }
}
```

- homework
```ts
// 32a  D is the fake store for n_2
// 32b  S is "do not also email inside load"
// 32c  a subtype that throws on find breaks L
```

- example 33. SOLID on a store for b_3
- the service depends on an interface
- the test passes a fake that returns semi
- one reason to change: this service does not also send mail

```ts
interface Store {
  find(id: string): Promise<{ round: string } | null>;
}
class Service {
  constructor(private readonly store: Store) {}
  async load() { return this.store.find("b_3"); }
}
```

- homework
```ts
// 33a  D is the fake store for b_3
// 33b  S is "do not also email inside load"
// 33c  a subtype that throws on find breaks L
```

- example 34. SOLID on a store for se_1
- the service depends on an interface
- the test passes a fake that returns u_3
- one reason to change: this service does not also send mail

```ts
interface Store {
  find(id: string): Promise<{ userId: string } | null>;
}
class Service {
  constructor(private readonly store: Store) {}
  async load() { return this.store.find("se_1"); }
}
```

- homework
```ts
// 34a  D is the fake store for se_1
// 34b  S is "do not also email inside load"
// 34c  a subtype that throws on find breaks L
```

- example 35. SOLID on a store for q_1
- the service depends on an interface
- the test passes a fake that returns laytime
- one reason to change: this service does not also send mail

```ts
interface Store {
  find(id: string): Promise<{ name: string } | null>;
}
class Service {
  constructor(private readonly store: Store) {}
  async load() { return this.store.find("q_1"); }
}
```

- homework
```ts
// 35a  D is the fake store for q_1
// 35b  S is "do not also email inside load"
// 35c  a subtype that throws on find breaks L
```

- example 36. SOLID on a store for r_1
- the service depends on an interface
- the test passes a fake that returns operator
- one reason to change: this service does not also send mail

```ts
interface Store {
  find(id: string): Promise<{ name: string } | null>;
}
class Service {
  constructor(private readonly store: Store) {}
  async load() { return this.store.find("r_1"); }
}
```

- homework
```ts
// 36a  D is the fake store for r_1
// 36b  S is "do not also email inside load"
// 36c  a subtype that throws on find breaks L
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

- example 1. one function, not two copies, for pc_12
- DRY the rule. a repeated string is fine
- the worker has a calculator. it is not a kind of calculator
- YAGNI: do not add a plugin system for a single port-calls

```ts
class Worker {
  constructor(private readonly quote: (id: string) => Promise<number>) {}
  run() { return this.quote("pc_12"); }
}
```

- homework
```ts
// 1a  one laytime function used for pc_12
// 1b  has-a: worker has a quote function
// 1c  do not build a shard router for port-calls yet
```

- example 2. one function, not two copies, for m_1
- DRY the rule. a repeated string is fine
- the worker has a calculator. it is not a kind of calculator
- YAGNI: do not add a plugin system for a single matches

```ts
class Worker {
  constructor(private readonly quote: (id: string) => Promise<number>) {}
  run() { return this.quote("m_1"); }
}
```

- homework
```ts
// 2a  one laytime function used for m_1
// 2b  has-a: worker has a quote function
// 2c  do not build a shard router for matches yet
```

- example 3. one function, not two copies, for t_9
- DRY the rule. a repeated string is fine
- the worker has a calculator. it is not a kind of calculator
- YAGNI: do not add a plugin system for a single tournaments

```ts
class Worker {
  constructor(private readonly quote: (id: string) => Promise<number>) {}
  run() { return this.quote("t_9"); }
}
```

- homework
```ts
// 3a  one laytime function used for t_9
// 3b  has-a: worker has a quote function
// 3c  do not build a shard router for tournaments yet
```

- example 4. one function, not two copies, for v_4
- DRY the rule. a repeated string is fine
- the worker has a calculator. it is not a kind of calculator
- YAGNI: do not add a plugin system for a single videos

```ts
class Worker {
  constructor(private readonly quote: (id: string) => Promise<number>) {}
  run() { return this.quote("v_4"); }
}
```

- homework
```ts
// 4a  one laytime function used for v_4
// 4b  has-a: worker has a quote function
// 4c  do not build a shard router for videos yet
```

- example 5. one function, not two copies, for f_2
- DRY the rule. a repeated string is fine
- the worker has a calculator. it is not a kind of calculator
- YAGNI: do not add a plugin system for a single facts

```ts
class Worker {
  constructor(private readonly quote: (id: string) => Promise<number>) {}
  run() { return this.quote("f_2"); }
}
```

- homework
```ts
// 5a  one laytime function used for f_2
// 5b  has-a: worker has a quote function
// 5c  do not build a shard router for facts yet
```

- example 6. one function, not two copies, for u_3
- DRY the rule. a repeated string is fine
- the worker has a calculator. it is not a kind of calculator
- YAGNI: do not add a plugin system for a single users

```ts
class Worker {
  constructor(private readonly quote: (id: string) => Promise<number>) {}
  run() { return this.quote("u_3"); }
}
```

- homework
```ts
// 6a  one laytime function used for u_3
// 6b  has-a: worker has a quote function
// 6c  do not build a shard router for users yet
```

- example 7. one function, not two copies, for pay_8
- DRY the rule. a repeated string is fine
- the worker has a calculator. it is not a kind of calculator
- YAGNI: do not add a plugin system for a single payments

```ts
class Worker {
  constructor(private readonly quote: (id: string) => Promise<number>) {}
  run() { return this.quote("pay_8"); }
}
```

- homework
```ts
// 7a  one laytime function used for pay_8
// 7b  has-a: worker has a quote function
// 7c  do not build a shard router for payments yet
```

- example 8. one function, not two copies, for room_2
- DRY the rule. a repeated string is fine
- the worker has a calculator. it is not a kind of calculator
- YAGNI: do not add a plugin system for a single rooms

```ts
class Worker {
  constructor(private readonly quote: (id: string) => Promise<number>) {}
  run() { return this.quote("room_2"); }
}
```

- homework
```ts
// 8a  one laytime function used for room_2
// 8b  has-a: worker has a quote function
// 8c  do not build a shard router for rooms yet
```

- example 9. one function, not two copies, for vs_7
- DRY the rule. a repeated string is fine
- the worker has a calculator. it is not a kind of calculator
- YAGNI: do not add a plugin system for a single vessels

```ts
class Worker {
  constructor(private readonly quote: (id: string) => Promise<number>) {}
  run() { return this.quote("vs_7"); }
}
```

- homework
```ts
// 9a  one laytime function used for vs_7
// 9b  has-a: worker has a quote function
// 9c  do not build a shard router for vessels yet
```

- example 10. one function, not two copies, for sc_3
- DRY the rule. a repeated string is fine
- the worker has a calculator. it is not a kind of calculator
- YAGNI: do not add a plugin system for a single scores

```ts
class Worker {
  constructor(private readonly quote: (id: string) => Promise<number>) {}
  run() { return this.quote("sc_3"); }
}
```

- homework
```ts
// 10a  one laytime function used for sc_3
// 10b  has-a: worker has a quote function
// 10c  do not build a shard router for scores yet
```

- example 11. one function, not two copies, for tm_2
- DRY the rule. a repeated string is fine
- the worker has a calculator. it is not a kind of calculator
- YAGNI: do not add a plugin system for a single teams

```ts
class Worker {
  constructor(private readonly quote: (id: string) => Promise<number>) {}
  run() { return this.quote("tm_2"); }
}
```

- homework
```ts
// 11a  one laytime function used for tm_2
// 11b  has-a: worker has a quote function
// 11c  do not build a shard router for teams yet
```

- example 12. one function, not two copies, for up_6
- DRY the rule. a repeated string is fine
- the worker has a calculator. it is not a kind of calculator
- YAGNI: do not add a plugin system for a single uploads

```ts
class Worker {
  constructor(private readonly quote: (id: string) => Promise<number>) {}
  run() { return this.quote("up_6"); }
}
```

- homework
```ts
// 12a  one laytime function used for up_6
// 12b  has-a: worker has a quote function
// 12c  do not build a shard router for uploads yet
```

- example 13. one function, not two copies, for st_1
- DRY the rule. a repeated string is fine
- the worker has a calculator. it is not a kind of calculator
- YAGNI: do not add a plugin system for a single standings

```ts
class Worker {
  constructor(private readonly quote: (id: string) => Promise<number>) {}
  run() { return this.quote("st_1"); }
}
```

- homework
```ts
// 13a  one laytime function used for st_1
// 13b  has-a: worker has a quote function
// 13c  do not build a shard router for standings yet
```

- example 14. one function, not two copies, for n_2
- DRY the rule. a repeated string is fine
- the worker has a calculator. it is not a kind of calculator
- YAGNI: do not add a plugin system for a single notices

```ts
class Worker {
  constructor(private readonly quote: (id: string) => Promise<number>) {}
  run() { return this.quote("n_2"); }
}
```

- homework
```ts
// 14a  one laytime function used for n_2
// 14b  has-a: worker has a quote function
// 14c  do not build a shard router for notices yet
```

- example 15. one function, not two copies, for b_3
- DRY the rule. a repeated string is fine
- the worker has a calculator. it is not a kind of calculator
- YAGNI: do not add a plugin system for a single brackets

```ts
class Worker {
  constructor(private readonly quote: (id: string) => Promise<number>) {}
  run() { return this.quote("b_3"); }
}
```

- homework
```ts
// 15a  one laytime function used for b_3
// 15b  has-a: worker has a quote function
// 15c  do not build a shard router for brackets yet
```

- example 16. one function, not two copies, for se_1
- DRY the rule. a repeated string is fine
- the worker has a calculator. it is not a kind of calculator
- YAGNI: do not add a plugin system for a single sessions

```ts
class Worker {
  constructor(private readonly quote: (id: string) => Promise<number>) {}
  run() { return this.quote("se_1"); }
}
```

- homework
```ts
// 16a  one laytime function used for se_1
// 16b  has-a: worker has a quote function
// 16c  do not build a shard router for sessions yet
```

- example 17. one function, not two copies, for q_1
- DRY the rule. a repeated string is fine
- the worker has a calculator. it is not a kind of calculator
- YAGNI: do not add a plugin system for a single queues

```ts
class Worker {
  constructor(private readonly quote: (id: string) => Promise<number>) {}
  run() { return this.quote("q_1"); }
}
```

- homework
```ts
// 17a  one laytime function used for q_1
// 17b  has-a: worker has a quote function
// 17c  do not build a shard router for queues yet
```

- example 18. one function, not two copies, for r_1
- DRY the rule. a repeated string is fine
- the worker has a calculator. it is not a kind of calculator
- YAGNI: do not add a plugin system for a single roles

```ts
class Worker {
  constructor(private readonly quote: (id: string) => Promise<number>) {}
  run() { return this.quote("r_1"); }
}
```

- homework
```ts
// 18a  one laytime function used for r_1
// 18b  has-a: worker has a quote function
// 18c  do not build a shard router for roles yet
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

- example 1. boxes for PortCalls and its child
- 1 to many
- a dashed arrow means uses
- skip the getters

```text
PortCalls 1 ---- * Child
PortCalls id pc_12
label vesselName = Ocean Star
Calculator ....> PortCalls
```

- homework
```text
// 1a  multiplicity for pc_12
// 1b  dashed arrow is uses, not inheritance
// 1c  a junction for users and roles, not extends
```

- example 2. boxes for Matches and its child
- 1 to many
- a dashed arrow means uses
- skip the getters

```text
Matches 1 ---- * Child
Matches id m_1
label home = Ada
Calculator ....> Matches
```

- homework
```text
// 2a  multiplicity for m_1
// 2b  dashed arrow is uses, not inheritance
// 2c  a junction for users and roles, not extends
```

- example 3. boxes for Tournaments and its child
- 1 to many
- a dashed arrow means uses
- skip the getters

```text
Tournaments 1 ---- * Child
Tournaments id t_9
label name = Rajshahi Open
Calculator ....> Tournaments
```

- homework
```text
// 3a  multiplicity for t_9
// 3b  dashed arrow is uses, not inheritance
// 3c  a junction for users and roles, not extends
```

- example 4. boxes for Videos and its child
- 1 to many
- a dashed arrow means uses
- skip the getters

```text
Videos 1 ---- * Child
Videos id v_4
label title = Episode 1
Calculator ....> Videos
```

- homework
```text
// 4a  multiplicity for v_4
// 4b  dashed arrow is uses, not inheritance
// 4c  a junction for users and roles, not extends
```

- example 5. boxes for Facts and its child
- 1 to many
- a dashed arrow means uses
- skip the getters

```text
Facts 1 ---- * Child
Facts id f_2
label kind = NOR
Calculator ....> Facts
```

- homework
```text
// 5a  multiplicity for f_2
// 5b  dashed arrow is uses, not inheritance
// 5c  a junction for users and roles, not extends
```

- example 6. boxes for Users and its child
- 1 to many
- a dashed arrow means uses
- skip the getters

```text
Users 1 ---- * Child
Users id u_3
label email = a@example.com
Calculator ....> Users
```

- homework
```text
// 6a  multiplicity for u_3
// 6b  dashed arrow is uses, not inheritance
// 6c  a junction for users and roles, not extends
```

- example 7. boxes for Payments and its child
- 1 to many
- a dashed arrow means uses
- skip the getters

```text
Payments 1 ---- * Child
Payments id pay_8
label eventId = evt_1
Calculator ....> Payments
```

- homework
```text
// 7a  multiplicity for pay_8
// 7b  dashed arrow is uses, not inheritance
// 7c  a junction for users and roles, not extends
```

- example 8. boxes for Rooms and its child
- 1 to many
- a dashed arrow means uses
- skip the getters

```text
Rooms 1 ---- * Child
Rooms id room_2
label sessionId = s_9
Calculator ....> Rooms
```

- homework
```text
// 8a  multiplicity for room_2
// 8b  dashed arrow is uses, not inheritance
// 8c  a junction for users and roles, not extends
```

- example 9. boxes for Vessels and its child
- 1 to many
- a dashed arrow means uses
- skip the getters

```text
Vessels 1 ---- * Child
Vessels id vs_7
label name = North Wind
Calculator ....> Vessels
```

- homework
```text
// 9a  multiplicity for vs_7
// 9b  dashed arrow is uses, not inheritance
// 9c  a junction for users and roles, not extends
```

- example 10. boxes for Scores and its child
- 1 to many
- a dashed arrow means uses
- skip the getters

```text
Scores 1 ---- * Child
Scores id sc_3
label points = 11
Calculator ....> Scores
```

- homework
```text
// 10a  multiplicity for sc_3
// 10b  dashed arrow is uses, not inheritance
// 10c  a junction for users and roles, not extends
```

- example 11. boxes for Teams and its child
- 1 to many
- a dashed arrow means uses
- skip the getters

```text
Teams 1 ---- * Child
Teams id tm_2
label name = Blue
Calculator ....> Teams
```

- homework
```text
// 11a  multiplicity for tm_2
// 11b  dashed arrow is uses, not inheritance
// 11c  a junction for users and roles, not extends
```

- example 12. boxes for Uploads and its child
- 1 to many
- a dashed arrow means uses
- skip the getters

```text
Uploads 1 ---- * Child
Uploads id up_6
label key = videos/u_1/a.mp4
Calculator ....> Uploads
```

- homework
```text
// 12a  multiplicity for up_6
// 12b  dashed arrow is uses, not inheritance
// 12c  a junction for users and roles, not extends
```

- example 13. boxes for Standings and its child
- 1 to many
- a dashed arrow means uses
- skip the getters

```text
Standings 1 ---- * Child
Standings id st_1
label player = player_a
Calculator ....> Standings
```

- homework
```text
// 13a  multiplicity for st_1
// 13b  dashed arrow is uses, not inheritance
// 13c  a junction for users and roles, not extends
```

- example 14. boxes for Notices and its child
- 1 to many
- a dashed arrow means uses
- skip the getters

```text
Notices 1 ---- * Child
Notices id n_2
label port = Chattogram
Calculator ....> Notices
```

- homework
```text
// 14a  multiplicity for n_2
// 14b  dashed arrow is uses, not inheritance
// 14c  a junction for users and roles, not extends
```

- example 15. boxes for Brackets and its child
- 1 to many
- a dashed arrow means uses
- skip the getters

```text
Brackets 1 ---- * Child
Brackets id b_3
label round = semi
Calculator ....> Brackets
```

- homework
```text
// 15a  multiplicity for b_3
// 15b  dashed arrow is uses, not inheritance
// 15c  a junction for users and roles, not extends
```

- example 16. boxes for Sessions and its child
- 1 to many
- a dashed arrow means uses
- skip the getters

```text
Sessions 1 ---- * Child
Sessions id se_1
label userId = u_3
Calculator ....> Sessions
```

- homework
```text
// 16a  multiplicity for se_1
// 16b  dashed arrow is uses, not inheritance
// 16c  a junction for users and roles, not extends
```

- example 17. boxes for Queues and its child
- 1 to many
- a dashed arrow means uses
- skip the getters

```text
Queues 1 ---- * Child
Queues id q_1
label name = laytime
Calculator ....> Queues
```

- homework
```text
// 17a  multiplicity for q_1
// 17b  dashed arrow is uses, not inheritance
// 17c  a junction for users and roles, not extends
```

- example 18. boxes for Roles and its child
- 1 to many
- a dashed arrow means uses
- skip the getters

```text
Roles 1 ---- * Child
Roles id r_1
label name = operator
Calculator ....> Roles
```

- homework
```text
// 18a  multiplicity for r_1
// 18b  dashed arrow is uses, not inheritance
// 18c  a junction for users and roles, not extends
```

- example 19. boxes for PortCalls and its child
- 1 to many
- a dashed arrow means uses
- skip the getters

```text
PortCalls 1 ---- * Child
PortCalls id pc_12
label vesselName = Ocean Star
Calculator ....> PortCalls
```

- homework
```text
// 19a  multiplicity for pc_12
// 19b  dashed arrow is uses, not inheritance
// 19c  a junction for users and roles, not extends
```

- example 20. boxes for Matches and its child
- 1 to many
- a dashed arrow means uses
- skip the getters

```text
Matches 1 ---- * Child
Matches id m_1
label home = Ada
Calculator ....> Matches
```

- homework
```text
// 20a  multiplicity for m_1
// 20b  dashed arrow is uses, not inheritance
// 20c  a junction for users and roles, not extends
```

- example 21. boxes for Tournaments and its child
- 1 to many
- a dashed arrow means uses
- skip the getters

```text
Tournaments 1 ---- * Child
Tournaments id t_9
label name = Rajshahi Open
Calculator ....> Tournaments
```

- homework
```text
// 21a  multiplicity for t_9
// 21b  dashed arrow is uses, not inheritance
// 21c  a junction for users and roles, not extends
```

- example 22. boxes for Videos and its child
- 1 to many
- a dashed arrow means uses
- skip the getters

```text
Videos 1 ---- * Child
Videos id v_4
label title = Episode 1
Calculator ....> Videos
```

- homework
```text
// 22a  multiplicity for v_4
// 22b  dashed arrow is uses, not inheritance
// 22c  a junction for users and roles, not extends
```

- example 23. boxes for Facts and its child
- 1 to many
- a dashed arrow means uses
- skip the getters

```text
Facts 1 ---- * Child
Facts id f_2
label kind = NOR
Calculator ....> Facts
```

- homework
```text
// 23a  multiplicity for f_2
// 23b  dashed arrow is uses, not inheritance
// 23c  a junction for users and roles, not extends
```

- example 24. boxes for Users and its child
- 1 to many
- a dashed arrow means uses
- skip the getters

```text
Users 1 ---- * Child
Users id u_3
label email = a@example.com
Calculator ....> Users
```

- homework
```text
// 24a  multiplicity for u_3
// 24b  dashed arrow is uses, not inheritance
// 24c  a junction for users and roles, not extends
```

- example 25. boxes for Payments and its child
- 1 to many
- a dashed arrow means uses
- skip the getters

```text
Payments 1 ---- * Child
Payments id pay_8
label eventId = evt_1
Calculator ....> Payments
```

- homework
```text
// 25a  multiplicity for pay_8
// 25b  dashed arrow is uses, not inheritance
// 25c  a junction for users and roles, not extends
```

- example 26. boxes for Rooms and its child
- 1 to many
- a dashed arrow means uses
- skip the getters

```text
Rooms 1 ---- * Child
Rooms id room_2
label sessionId = s_9
Calculator ....> Rooms
```

- homework
```text
// 26a  multiplicity for room_2
// 26b  dashed arrow is uses, not inheritance
// 26c  a junction for users and roles, not extends
```

- example 27. boxes for Vessels and its child
- 1 to many
- a dashed arrow means uses
- skip the getters

```text
Vessels 1 ---- * Child
Vessels id vs_7
label name = North Wind
Calculator ....> Vessels
```

- homework
```text
// 27a  multiplicity for vs_7
// 27b  dashed arrow is uses, not inheritance
// 27c  a junction for users and roles, not extends
```

- example 28. boxes for Scores and its child
- 1 to many
- a dashed arrow means uses
- skip the getters

```text
Scores 1 ---- * Child
Scores id sc_3
label points = 11
Calculator ....> Scores
```

- homework
```text
// 28a  multiplicity for sc_3
// 28b  dashed arrow is uses, not inheritance
// 28c  a junction for users and roles, not extends
```

- example 29. boxes for Teams and its child
- 1 to many
- a dashed arrow means uses
- skip the getters

```text
Teams 1 ---- * Child
Teams id tm_2
label name = Blue
Calculator ....> Teams
```

- homework
```text
// 29a  multiplicity for tm_2
// 29b  dashed arrow is uses, not inheritance
// 29c  a junction for users and roles, not extends
```

- example 30. boxes for Uploads and its child
- 1 to many
- a dashed arrow means uses
- skip the getters

```text
Uploads 1 ---- * Child
Uploads id up_6
label key = videos/u_1/a.mp4
Calculator ....> Uploads
```

- homework
```text
// 30a  multiplicity for up_6
// 30b  dashed arrow is uses, not inheritance
// 30c  a junction for users and roles, not extends
```

- example 31. boxes for Standings and its child
- 1 to many
- a dashed arrow means uses
- skip the getters

```text
Standings 1 ---- * Child
Standings id st_1
label player = player_a
Calculator ....> Standings
```

- homework
```text
// 31a  multiplicity for st_1
// 31b  dashed arrow is uses, not inheritance
// 31c  a junction for users and roles, not extends
```

- example 32. boxes for Notices and its child
- 1 to many
- a dashed arrow means uses
- skip the getters

```text
Notices 1 ---- * Child
Notices id n_2
label port = Chattogram
Calculator ....> Notices
```

- homework
```text
// 32a  multiplicity for n_2
// 32b  dashed arrow is uses, not inheritance
// 32c  a junction for users and roles, not extends
```

- example 33. boxes for Brackets and its child
- 1 to many
- a dashed arrow means uses
- skip the getters

```text
Brackets 1 ---- * Child
Brackets id b_3
label round = semi
Calculator ....> Brackets
```

- homework
```text
// 33a  multiplicity for b_3
// 33b  dashed arrow is uses, not inheritance
// 33c  a junction for users and roles, not extends
```

- example 34. boxes for Sessions and its child
- 1 to many
- a dashed arrow means uses
- skip the getters

```text
Sessions 1 ---- * Child
Sessions id se_1
label userId = u_3
Calculator ....> Sessions
```

- homework
```text
// 34a  multiplicity for se_1
// 34b  dashed arrow is uses, not inheritance
// 34c  a junction for users and roles, not extends
```

- example 35. boxes for Queues and its child
- 1 to many
- a dashed arrow means uses
- skip the getters

```text
Queues 1 ---- * Child
Queues id q_1
label name = laytime
Calculator ....> Queues
```

- homework
```text
// 35a  multiplicity for q_1
// 35b  dashed arrow is uses, not inheritance
// 35c  a junction for users and roles, not extends
```

- example 36. boxes for Roles and its child
- 1 to many
- a dashed arrow means uses
- skip the getters

```text
Roles 1 ---- * Child
Roles id r_1
label name = operator
Calculator ....> Roles
```

- homework
```text
// 36a  multiplicity for r_1
// 36b  dashed arrow is uses, not inheritance
// 36c  a junction for users and roles, not extends
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

- example 1. one Nest service, no per-request field
- a singleton that stores current id pc_12 mixes two requests
- a service with no fields is safe to share
- the test builds its own instance

```ts
@Injectable()
export class Clock {
  now() { return new Date(); }
}
// do not add currentId = "pc_12" as a field
```

- homework
```ts
// 1a  why a field current = "pc_12" is unsafe
// 1b  Clock is safe
// 1c  the test does not use a global for port-calls
```

- example 2. one Nest service, no per-request field
- a singleton that stores current id m_1 mixes two requests
- a service with no fields is safe to share
- the test builds its own instance

```ts
@Injectable()
export class Clock {
  now() { return new Date(); }
}
// do not add currentId = "m_1" as a field
```

- homework
```ts
// 2a  why a field current = "m_1" is unsafe
// 2b  Clock is safe
// 2c  the test does not use a global for matches
```

- example 3. one Nest service, no per-request field
- a singleton that stores current id t_9 mixes two requests
- a service with no fields is safe to share
- the test builds its own instance

```ts
@Injectable()
export class Clock {
  now() { return new Date(); }
}
// do not add currentId = "t_9" as a field
```

- homework
```ts
// 3a  why a field current = "t_9" is unsafe
// 3b  Clock is safe
// 3c  the test does not use a global for tournaments
```

- example 4. one Nest service, no per-request field
- a singleton that stores current id v_4 mixes two requests
- a service with no fields is safe to share
- the test builds its own instance

```ts
@Injectable()
export class Clock {
  now() { return new Date(); }
}
// do not add currentId = "v_4" as a field
```

- homework
```ts
// 4a  why a field current = "v_4" is unsafe
// 4b  Clock is safe
// 4c  the test does not use a global for videos
```

- example 5. one Nest service, no per-request field
- a singleton that stores current id f_2 mixes two requests
- a service with no fields is safe to share
- the test builds its own instance

```ts
@Injectable()
export class Clock {
  now() { return new Date(); }
}
// do not add currentId = "f_2" as a field
```

- homework
```ts
// 5a  why a field current = "f_2" is unsafe
// 5b  Clock is safe
// 5c  the test does not use a global for facts
```

- example 6. one Nest service, no per-request field
- a singleton that stores current id u_3 mixes two requests
- a service with no fields is safe to share
- the test builds its own instance

```ts
@Injectable()
export class Clock {
  now() { return new Date(); }
}
// do not add currentId = "u_3" as a field
```

- homework
```ts
// 6a  why a field current = "u_3" is unsafe
// 6b  Clock is safe
// 6c  the test does not use a global for users
```

- example 7. one Nest service, no per-request field
- a singleton that stores current id pay_8 mixes two requests
- a service with no fields is safe to share
- the test builds its own instance

```ts
@Injectable()
export class Clock {
  now() { return new Date(); }
}
// do not add currentId = "pay_8" as a field
```

- homework
```ts
// 7a  why a field current = "pay_8" is unsafe
// 7b  Clock is safe
// 7c  the test does not use a global for payments
```

- example 8. one Nest service, no per-request field
- a singleton that stores current id room_2 mixes two requests
- a service with no fields is safe to share
- the test builds its own instance

```ts
@Injectable()
export class Clock {
  now() { return new Date(); }
}
// do not add currentId = "room_2" as a field
```

- homework
```ts
// 8a  why a field current = "room_2" is unsafe
// 8b  Clock is safe
// 8c  the test does not use a global for rooms
```

- example 9. one Nest service, no per-request field
- a singleton that stores current id vs_7 mixes two requests
- a service with no fields is safe to share
- the test builds its own instance

```ts
@Injectable()
export class Clock {
  now() { return new Date(); }
}
// do not add currentId = "vs_7" as a field
```

- homework
```ts
// 9a  why a field current = "vs_7" is unsafe
// 9b  Clock is safe
// 9c  the test does not use a global for vessels
```

- example 10. one Nest service, no per-request field
- a singleton that stores current id sc_3 mixes two requests
- a service with no fields is safe to share
- the test builds its own instance

```ts
@Injectable()
export class Clock {
  now() { return new Date(); }
}
// do not add currentId = "sc_3" as a field
```

- homework
```ts
// 10a  why a field current = "sc_3" is unsafe
// 10b  Clock is safe
// 10c  the test does not use a global for scores
```

- example 11. one Nest service, no per-request field
- a singleton that stores current id tm_2 mixes two requests
- a service with no fields is safe to share
- the test builds its own instance

```ts
@Injectable()
export class Clock {
  now() { return new Date(); }
}
// do not add currentId = "tm_2" as a field
```

- homework
```ts
// 11a  why a field current = "tm_2" is unsafe
// 11b  Clock is safe
// 11c  the test does not use a global for teams
```

- example 12. one Nest service, no per-request field
- a singleton that stores current id up_6 mixes two requests
- a service with no fields is safe to share
- the test builds its own instance

```ts
@Injectable()
export class Clock {
  now() { return new Date(); }
}
// do not add currentId = "up_6" as a field
```

- homework
```ts
// 12a  why a field current = "up_6" is unsafe
// 12b  Clock is safe
// 12c  the test does not use a global for uploads
```

- example 13. one Nest service, no per-request field
- a singleton that stores current id st_1 mixes two requests
- a service with no fields is safe to share
- the test builds its own instance

```ts
@Injectable()
export class Clock {
  now() { return new Date(); }
}
// do not add currentId = "st_1" as a field
```

- homework
```ts
// 13a  why a field current = "st_1" is unsafe
// 13b  Clock is safe
// 13c  the test does not use a global for standings
```

- example 14. one Nest service, no per-request field
- a singleton that stores current id n_2 mixes two requests
- a service with no fields is safe to share
- the test builds its own instance

```ts
@Injectable()
export class Clock {
  now() { return new Date(); }
}
// do not add currentId = "n_2" as a field
```

- homework
```ts
// 14a  why a field current = "n_2" is unsafe
// 14b  Clock is safe
// 14c  the test does not use a global for notices
```

- example 15. one Nest service, no per-request field
- a singleton that stores current id b_3 mixes two requests
- a service with no fields is safe to share
- the test builds its own instance

```ts
@Injectable()
export class Clock {
  now() { return new Date(); }
}
// do not add currentId = "b_3" as a field
```

- homework
```ts
// 15a  why a field current = "b_3" is unsafe
// 15b  Clock is safe
// 15c  the test does not use a global for brackets
```

- example 16. one Nest service, no per-request field
- a singleton that stores current id se_1 mixes two requests
- a service with no fields is safe to share
- the test builds its own instance

```ts
@Injectable()
export class Clock {
  now() { return new Date(); }
}
// do not add currentId = "se_1" as a field
```

- homework
```ts
// 16a  why a field current = "se_1" is unsafe
// 16b  Clock is safe
// 16c  the test does not use a global for sessions
```

- example 17. one Nest service, no per-request field
- a singleton that stores current id q_1 mixes two requests
- a service with no fields is safe to share
- the test builds its own instance

```ts
@Injectable()
export class Clock {
  now() { return new Date(); }
}
// do not add currentId = "q_1" as a field
```

- homework
```ts
// 17a  why a field current = "q_1" is unsafe
// 17b  Clock is safe
// 17c  the test does not use a global for queues
```

- example 18. one Nest service, no per-request field
- a singleton that stores current id r_1 mixes two requests
- a service with no fields is safe to share
- the test builds its own instance

```ts
@Injectable()
export class Clock {
  now() { return new Date(); }
}
// do not add currentId = "r_1" as a field
```

- homework
```ts
// 18a  why a field current = "r_1" is unsafe
// 18b  Clock is safe
// 18c  the test does not use a global for roles
```

- example 19. one Nest service, no per-request field
- a singleton that stores current id pc_12 mixes two requests
- a service with no fields is safe to share
- the test builds its own instance

```ts
@Injectable()
export class Clock {
  now() { return new Date(); }
}
// do not add currentId = "pc_12" as a field
```

- homework
```ts
// 19a  why a field current = "pc_12" is unsafe
// 19b  Clock is safe
// 19c  the test does not use a global for port-calls
```

- example 20. one Nest service, no per-request field
- a singleton that stores current id m_1 mixes two requests
- a service with no fields is safe to share
- the test builds its own instance

```ts
@Injectable()
export class Clock {
  now() { return new Date(); }
}
// do not add currentId = "m_1" as a field
```

- homework
```ts
// 20a  why a field current = "m_1" is unsafe
// 20b  Clock is safe
// 20c  the test does not use a global for matches
```

- example 21. one Nest service, no per-request field
- a singleton that stores current id t_9 mixes two requests
- a service with no fields is safe to share
- the test builds its own instance

```ts
@Injectable()
export class Clock {
  now() { return new Date(); }
}
// do not add currentId = "t_9" as a field
```

- homework
```ts
// 21a  why a field current = "t_9" is unsafe
// 21b  Clock is safe
// 21c  the test does not use a global for tournaments
```

- example 22. one Nest service, no per-request field
- a singleton that stores current id v_4 mixes two requests
- a service with no fields is safe to share
- the test builds its own instance

```ts
@Injectable()
export class Clock {
  now() { return new Date(); }
}
// do not add currentId = "v_4" as a field
```

- homework
```ts
// 22a  why a field current = "v_4" is unsafe
// 22b  Clock is safe
// 22c  the test does not use a global for videos
```

- example 23. one Nest service, no per-request field
- a singleton that stores current id f_2 mixes two requests
- a service with no fields is safe to share
- the test builds its own instance

```ts
@Injectable()
export class Clock {
  now() { return new Date(); }
}
// do not add currentId = "f_2" as a field
```

- homework
```ts
// 23a  why a field current = "f_2" is unsafe
// 23b  Clock is safe
// 23c  the test does not use a global for facts
```

- example 24. one Nest service, no per-request field
- a singleton that stores current id u_3 mixes two requests
- a service with no fields is safe to share
- the test builds its own instance

```ts
@Injectable()
export class Clock {
  now() { return new Date(); }
}
// do not add currentId = "u_3" as a field
```

- homework
```ts
// 24a  why a field current = "u_3" is unsafe
// 24b  Clock is safe
// 24c  the test does not use a global for users
```

- example 25. one Nest service, no per-request field
- a singleton that stores current id pay_8 mixes two requests
- a service with no fields is safe to share
- the test builds its own instance

```ts
@Injectable()
export class Clock {
  now() { return new Date(); }
}
// do not add currentId = "pay_8" as a field
```

- homework
```ts
// 25a  why a field current = "pay_8" is unsafe
// 25b  Clock is safe
// 25c  the test does not use a global for payments
```

- example 26. one Nest service, no per-request field
- a singleton that stores current id room_2 mixes two requests
- a service with no fields is safe to share
- the test builds its own instance

```ts
@Injectable()
export class Clock {
  now() { return new Date(); }
}
// do not add currentId = "room_2" as a field
```

- homework
```ts
// 26a  why a field current = "room_2" is unsafe
// 26b  Clock is safe
// 26c  the test does not use a global for rooms
```

- example 27. one Nest service, no per-request field
- a singleton that stores current id vs_7 mixes two requests
- a service with no fields is safe to share
- the test builds its own instance

```ts
@Injectable()
export class Clock {
  now() { return new Date(); }
}
// do not add currentId = "vs_7" as a field
```

- homework
```ts
// 27a  why a field current = "vs_7" is unsafe
// 27b  Clock is safe
// 27c  the test does not use a global for vessels
```

- example 28. one Nest service, no per-request field
- a singleton that stores current id sc_3 mixes two requests
- a service with no fields is safe to share
- the test builds its own instance

```ts
@Injectable()
export class Clock {
  now() { return new Date(); }
}
// do not add currentId = "sc_3" as a field
```

- homework
```ts
// 28a  why a field current = "sc_3" is unsafe
// 28b  Clock is safe
// 28c  the test does not use a global for scores
```

- example 29. one Nest service, no per-request field
- a singleton that stores current id tm_2 mixes two requests
- a service with no fields is safe to share
- the test builds its own instance

```ts
@Injectable()
export class Clock {
  now() { return new Date(); }
}
// do not add currentId = "tm_2" as a field
```

- homework
```ts
// 29a  why a field current = "tm_2" is unsafe
// 29b  Clock is safe
// 29c  the test does not use a global for teams
```

- example 30. one Nest service, no per-request field
- a singleton that stores current id up_6 mixes two requests
- a service with no fields is safe to share
- the test builds its own instance

```ts
@Injectable()
export class Clock {
  now() { return new Date(); }
}
// do not add currentId = "up_6" as a field
```

- homework
```ts
// 30a  why a field current = "up_6" is unsafe
// 30b  Clock is safe
// 30c  the test does not use a global for uploads
```

- example 31. one Nest service, no per-request field
- a singleton that stores current id st_1 mixes two requests
- a service with no fields is safe to share
- the test builds its own instance

```ts
@Injectable()
export class Clock {
  now() { return new Date(); }
}
// do not add currentId = "st_1" as a field
```

- homework
```ts
// 31a  why a field current = "st_1" is unsafe
// 31b  Clock is safe
// 31c  the test does not use a global for standings
```

- example 32. one Nest service, no per-request field
- a singleton that stores current id n_2 mixes two requests
- a service with no fields is safe to share
- the test builds its own instance

```ts
@Injectable()
export class Clock {
  now() { return new Date(); }
}
// do not add currentId = "n_2" as a field
```

- homework
```ts
// 32a  why a field current = "n_2" is unsafe
// 32b  Clock is safe
// 32c  the test does not use a global for notices
```

- example 33. one Nest service, no per-request field
- a singleton that stores current id b_3 mixes two requests
- a service with no fields is safe to share
- the test builds its own instance

```ts
@Injectable()
export class Clock {
  now() { return new Date(); }
}
// do not add currentId = "b_3" as a field
```

- homework
```ts
// 33a  why a field current = "b_3" is unsafe
// 33b  Clock is safe
// 33c  the test does not use a global for brackets
```

- example 34. one Nest service, no per-request field
- a singleton that stores current id se_1 mixes two requests
- a service with no fields is safe to share
- the test builds its own instance

```ts
@Injectable()
export class Clock {
  now() { return new Date(); }
}
// do not add currentId = "se_1" as a field
```

- homework
```ts
// 34a  why a field current = "se_1" is unsafe
// 34b  Clock is safe
// 34c  the test does not use a global for sessions
```

- example 35. one Nest service, no per-request field
- a singleton that stores current id q_1 mixes two requests
- a service with no fields is safe to share
- the test builds its own instance

```ts
@Injectable()
export class Clock {
  now() { return new Date(); }
}
// do not add currentId = "q_1" as a field
```

- homework
```ts
// 35a  why a field current = "q_1" is unsafe
// 35b  Clock is safe
// 35c  the test does not use a global for queues
```

- example 36. one Nest service, no per-request field
- a singleton that stores current id r_1 mixes two requests
- a service with no fields is safe to share
- the test builds its own instance

```ts
@Injectable()
export class Clock {
  now() { return new Date(); }
}
// do not add currentId = "r_1" as a field
```

- homework
```ts
// 36a  why a field current = "r_1" is unsafe
// 36b  Clock is safe
// 36c  the test does not use a global for roles
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

- example 1. factory chooses a store for port-calls
- test returns memory. production returns the real store
- an abstract factory is a matching set. one product only needs a function

```ts
function createStore(env: "test" | "prod") {
  if (env === "test") return { find: async () => ({ vesselName: "Ocean Star" }) };
  return { find: async (id: string) => db.item.findUnique({ where: { id } }) };
}
```

- homework
```ts
// 1a  createStore("test").find("pc_12")
// 1b  the controller does not branch on env
// 1c  abstract factory only if mailer and storage must match
```

- example 2. factory chooses a store for matches
- test returns memory. production returns the real store
- an abstract factory is a matching set. one product only needs a function

```ts
function createStore(env: "test" | "prod") {
  if (env === "test") return { find: async () => ({ home: "Ada" }) };
  return { find: async (id: string) => db.item.findUnique({ where: { id } }) };
}
```

- homework
```ts
// 2a  createStore("test").find("m_1")
// 2b  the controller does not branch on env
// 2c  abstract factory only if mailer and storage must match
```

- example 3. factory chooses a store for tournaments
- test returns memory. production returns the real store
- an abstract factory is a matching set. one product only needs a function

```ts
function createStore(env: "test" | "prod") {
  if (env === "test") return { find: async () => ({ name: "Rajshahi Open" }) };
  return { find: async (id: string) => db.item.findUnique({ where: { id } }) };
}
```

- homework
```ts
// 3a  createStore("test").find("t_9")
// 3b  the controller does not branch on env
// 3c  abstract factory only if mailer and storage must match
```

- example 4. factory chooses a store for videos
- test returns memory. production returns the real store
- an abstract factory is a matching set. one product only needs a function

```ts
function createStore(env: "test" | "prod") {
  if (env === "test") return { find: async () => ({ title: "Episode 1" }) };
  return { find: async (id: string) => db.item.findUnique({ where: { id } }) };
}
```

- homework
```ts
// 4a  createStore("test").find("v_4")
// 4b  the controller does not branch on env
// 4c  abstract factory only if mailer and storage must match
```

- example 5. factory chooses a store for facts
- test returns memory. production returns the real store
- an abstract factory is a matching set. one product only needs a function

```ts
function createStore(env: "test" | "prod") {
  if (env === "test") return { find: async () => ({ kind: "NOR" }) };
  return { find: async (id: string) => db.item.findUnique({ where: { id } }) };
}
```

- homework
```ts
// 5a  createStore("test").find("f_2")
// 5b  the controller does not branch on env
// 5c  abstract factory only if mailer and storage must match
```

- example 6. factory chooses a store for users
- test returns memory. production returns the real store
- an abstract factory is a matching set. one product only needs a function

```ts
function createStore(env: "test" | "prod") {
  if (env === "test") return { find: async () => ({ email: "a@example.com" }) };
  return { find: async (id: string) => db.item.findUnique({ where: { id } }) };
}
```

- homework
```ts
// 6a  createStore("test").find("u_3")
// 6b  the controller does not branch on env
// 6c  abstract factory only if mailer and storage must match
```

- example 7. factory chooses a store for payments
- test returns memory. production returns the real store
- an abstract factory is a matching set. one product only needs a function

```ts
function createStore(env: "test" | "prod") {
  if (env === "test") return { find: async () => ({ eventId: "evt_1" }) };
  return { find: async (id: string) => db.item.findUnique({ where: { id } }) };
}
```

- homework
```ts
// 7a  createStore("test").find("pay_8")
// 7b  the controller does not branch on env
// 7c  abstract factory only if mailer and storage must match
```

- example 8. factory chooses a store for rooms
- test returns memory. production returns the real store
- an abstract factory is a matching set. one product only needs a function

```ts
function createStore(env: "test" | "prod") {
  if (env === "test") return { find: async () => ({ sessionId: "s_9" }) };
  return { find: async (id: string) => db.item.findUnique({ where: { id } }) };
}
```

- homework
```ts
// 8a  createStore("test").find("room_2")
// 8b  the controller does not branch on env
// 8c  abstract factory only if mailer and storage must match
```

- example 9. factory chooses a store for vessels
- test returns memory. production returns the real store
- an abstract factory is a matching set. one product only needs a function

```ts
function createStore(env: "test" | "prod") {
  if (env === "test") return { find: async () => ({ name: "North Wind" }) };
  return { find: async (id: string) => db.item.findUnique({ where: { id } }) };
}
```

- homework
```ts
// 9a  createStore("test").find("vs_7")
// 9b  the controller does not branch on env
// 9c  abstract factory only if mailer and storage must match
```

- example 10. factory chooses a store for scores
- test returns memory. production returns the real store
- an abstract factory is a matching set. one product only needs a function

```ts
function createStore(env: "test" | "prod") {
  if (env === "test") return { find: async () => ({ points: "11" }) };
  return { find: async (id: string) => db.item.findUnique({ where: { id } }) };
}
```

- homework
```ts
// 10a  createStore("test").find("sc_3")
// 10b  the controller does not branch on env
// 10c  abstract factory only if mailer and storage must match
```

- example 11. factory chooses a store for teams
- test returns memory. production returns the real store
- an abstract factory is a matching set. one product only needs a function

```ts
function createStore(env: "test" | "prod") {
  if (env === "test") return { find: async () => ({ name: "Blue" }) };
  return { find: async (id: string) => db.item.findUnique({ where: { id } }) };
}
```

- homework
```ts
// 11a  createStore("test").find("tm_2")
// 11b  the controller does not branch on env
// 11c  abstract factory only if mailer and storage must match
```

- example 12. factory chooses a store for uploads
- test returns memory. production returns the real store
- an abstract factory is a matching set. one product only needs a function

```ts
function createStore(env: "test" | "prod") {
  if (env === "test") return { find: async () => ({ key: "videos/u_1/a.mp4" }) };
  return { find: async (id: string) => db.item.findUnique({ where: { id } }) };
}
```

- homework
```ts
// 12a  createStore("test").find("up_6")
// 12b  the controller does not branch on env
// 12c  abstract factory only if mailer and storage must match
```

- example 13. factory chooses a store for standings
- test returns memory. production returns the real store
- an abstract factory is a matching set. one product only needs a function

```ts
function createStore(env: "test" | "prod") {
  if (env === "test") return { find: async () => ({ player: "player_a" }) };
  return { find: async (id: string) => db.item.findUnique({ where: { id } }) };
}
```

- homework
```ts
// 13a  createStore("test").find("st_1")
// 13b  the controller does not branch on env
// 13c  abstract factory only if mailer and storage must match
```

- example 14. factory chooses a store for notices
- test returns memory. production returns the real store
- an abstract factory is a matching set. one product only needs a function

```ts
function createStore(env: "test" | "prod") {
  if (env === "test") return { find: async () => ({ port: "Chattogram" }) };
  return { find: async (id: string) => db.item.findUnique({ where: { id } }) };
}
```

- homework
```ts
// 14a  createStore("test").find("n_2")
// 14b  the controller does not branch on env
// 14c  abstract factory only if mailer and storage must match
```

- example 15. factory chooses a store for brackets
- test returns memory. production returns the real store
- an abstract factory is a matching set. one product only needs a function

```ts
function createStore(env: "test" | "prod") {
  if (env === "test") return { find: async () => ({ round: "semi" }) };
  return { find: async (id: string) => db.item.findUnique({ where: { id } }) };
}
```

- homework
```ts
// 15a  createStore("test").find("b_3")
// 15b  the controller does not branch on env
// 15c  abstract factory only if mailer and storage must match
```

- example 16. factory chooses a store for sessions
- test returns memory. production returns the real store
- an abstract factory is a matching set. one product only needs a function

```ts
function createStore(env: "test" | "prod") {
  if (env === "test") return { find: async () => ({ userId: "u_3" }) };
  return { find: async (id: string) => db.item.findUnique({ where: { id } }) };
}
```

- homework
```ts
// 16a  createStore("test").find("se_1")
// 16b  the controller does not branch on env
// 16c  abstract factory only if mailer and storage must match
```

- example 17. factory chooses a store for queues
- test returns memory. production returns the real store
- an abstract factory is a matching set. one product only needs a function

```ts
function createStore(env: "test" | "prod") {
  if (env === "test") return { find: async () => ({ name: "laytime" }) };
  return { find: async (id: string) => db.item.findUnique({ where: { id } }) };
}
```

- homework
```ts
// 17a  createStore("test").find("q_1")
// 17b  the controller does not branch on env
// 17c  abstract factory only if mailer and storage must match
```

- example 18. factory chooses a store for roles
- test returns memory. production returns the real store
- an abstract factory is a matching set. one product only needs a function

```ts
function createStore(env: "test" | "prod") {
  if (env === "test") return { find: async () => ({ name: "operator" }) };
  return { find: async (id: string) => db.item.findUnique({ where: { id } }) };
}
```

- homework
```ts
// 18a  createStore("test").find("r_1")
// 18b  the controller does not branch on env
// 18c  abstract factory only if mailer and storage must match
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

- example 1. builder for vesselName and a copy
- build() rejects an empty vesselName
- a shallow copy shares the inner object. spread the inner object too

```ts
class Builder {
  private value = "";
  set(v: string) { this.value = v; return this; }
  build() {
    if (!this.value) throw new Error("incomplete");
    return { id: "pc_12", vesselName: this.value };
  }
}
const made = new Builder().set("Ocean Star").build();
```

- homework
```ts
// 1a  build Ocean Star for pc_12
// 1b  build() with "" throws
// 1c  copy limits with an inner spread so later edits do not touch the base
```

- example 2. builder for home and a copy
- build() rejects an empty home
- a shallow copy shares the inner object. spread the inner object too

```ts
class Builder {
  private value = "";
  set(v: string) { this.value = v; return this; }
  build() {
    if (!this.value) throw new Error("incomplete");
    return { id: "m_1", home: this.value };
  }
}
const made = new Builder().set("Ada").build();
```

- homework
```ts
// 2a  build Ada for m_1
// 2b  build() with "" throws
// 2c  copy limits with an inner spread so later edits do not touch the base
```

- example 3. builder for name and a copy
- build() rejects an empty name
- a shallow copy shares the inner object. spread the inner object too

```ts
class Builder {
  private value = "";
  set(v: string) { this.value = v; return this; }
  build() {
    if (!this.value) throw new Error("incomplete");
    return { id: "t_9", name: this.value };
  }
}
const made = new Builder().set("Rajshahi Open").build();
```

- homework
```ts
// 3a  build Rajshahi Open for t_9
// 3b  build() with "" throws
// 3c  copy limits with an inner spread so later edits do not touch the base
```

- example 4. builder for title and a copy
- build() rejects an empty title
- a shallow copy shares the inner object. spread the inner object too

```ts
class Builder {
  private value = "";
  set(v: string) { this.value = v; return this; }
  build() {
    if (!this.value) throw new Error("incomplete");
    return { id: "v_4", title: this.value };
  }
}
const made = new Builder().set("Episode 1").build();
```

- homework
```ts
// 4a  build Episode 1 for v_4
// 4b  build() with "" throws
// 4c  copy limits with an inner spread so later edits do not touch the base
```

- example 5. builder for kind and a copy
- build() rejects an empty kind
- a shallow copy shares the inner object. spread the inner object too

```ts
class Builder {
  private value = "";
  set(v: string) { this.value = v; return this; }
  build() {
    if (!this.value) throw new Error("incomplete");
    return { id: "f_2", kind: this.value };
  }
}
const made = new Builder().set("NOR").build();
```

- homework
```ts
// 5a  build NOR for f_2
// 5b  build() with "" throws
// 5c  copy limits with an inner spread so later edits do not touch the base
```

- example 6. builder for email and a copy
- build() rejects an empty email
- a shallow copy shares the inner object. spread the inner object too

```ts
class Builder {
  private value = "";
  set(v: string) { this.value = v; return this; }
  build() {
    if (!this.value) throw new Error("incomplete");
    return { id: "u_3", email: this.value };
  }
}
const made = new Builder().set("a@example.com").build();
```

- homework
```ts
// 6a  build a@example.com for u_3
// 6b  build() with "" throws
// 6c  copy limits with an inner spread so later edits do not touch the base
```

- example 7. builder for eventId and a copy
- build() rejects an empty eventId
- a shallow copy shares the inner object. spread the inner object too

```ts
class Builder {
  private value = "";
  set(v: string) { this.value = v; return this; }
  build() {
    if (!this.value) throw new Error("incomplete");
    return { id: "pay_8", eventId: this.value };
  }
}
const made = new Builder().set("evt_1").build();
```

- homework
```ts
// 7a  build evt_1 for pay_8
// 7b  build() with "" throws
// 7c  copy limits with an inner spread so later edits do not touch the base
```

- example 8. builder for sessionId and a copy
- build() rejects an empty sessionId
- a shallow copy shares the inner object. spread the inner object too

```ts
class Builder {
  private value = "";
  set(v: string) { this.value = v; return this; }
  build() {
    if (!this.value) throw new Error("incomplete");
    return { id: "room_2", sessionId: this.value };
  }
}
const made = new Builder().set("s_9").build();
```

- homework
```ts
// 8a  build s_9 for room_2
// 8b  build() with "" throws
// 8c  copy limits with an inner spread so later edits do not touch the base
```

- example 9. builder for name and a copy
- build() rejects an empty name
- a shallow copy shares the inner object. spread the inner object too

```ts
class Builder {
  private value = "";
  set(v: string) { this.value = v; return this; }
  build() {
    if (!this.value) throw new Error("incomplete");
    return { id: "vs_7", name: this.value };
  }
}
const made = new Builder().set("North Wind").build();
```

- homework
```ts
// 9a  build North Wind for vs_7
// 9b  build() with "" throws
// 9c  copy limits with an inner spread so later edits do not touch the base
```

- example 10. builder for points and a copy
- build() rejects an empty points
- a shallow copy shares the inner object. spread the inner object too

```ts
class Builder {
  private value = "";
  set(v: string) { this.value = v; return this; }
  build() {
    if (!this.value) throw new Error("incomplete");
    return { id: "sc_3", points: this.value };
  }
}
const made = new Builder().set("11").build();
```

- homework
```ts
// 10a  build 11 for sc_3
// 10b  build() with "" throws
// 10c  copy limits with an inner spread so later edits do not touch the base
```

- example 11. builder for name and a copy
- build() rejects an empty name
- a shallow copy shares the inner object. spread the inner object too

```ts
class Builder {
  private value = "";
  set(v: string) { this.value = v; return this; }
  build() {
    if (!this.value) throw new Error("incomplete");
    return { id: "tm_2", name: this.value };
  }
}
const made = new Builder().set("Blue").build();
```

- homework
```ts
// 11a  build Blue for tm_2
// 11b  build() with "" throws
// 11c  copy limits with an inner spread so later edits do not touch the base
```

- example 12. builder for key and a copy
- build() rejects an empty key
- a shallow copy shares the inner object. spread the inner object too

```ts
class Builder {
  private value = "";
  set(v: string) { this.value = v; return this; }
  build() {
    if (!this.value) throw new Error("incomplete");
    return { id: "up_6", key: this.value };
  }
}
const made = new Builder().set("videos/u_1/a.mp4").build();
```

- homework
```ts
// 12a  build videos/u_1/a.mp4 for up_6
// 12b  build() with "" throws
// 12c  copy limits with an inner spread so later edits do not touch the base
```

- example 13. builder for player and a copy
- build() rejects an empty player
- a shallow copy shares the inner object. spread the inner object too

```ts
class Builder {
  private value = "";
  set(v: string) { this.value = v; return this; }
  build() {
    if (!this.value) throw new Error("incomplete");
    return { id: "st_1", player: this.value };
  }
}
const made = new Builder().set("player_a").build();
```

- homework
```ts
// 13a  build player_a for st_1
// 13b  build() with "" throws
// 13c  copy limits with an inner spread so later edits do not touch the base
```

- example 14. builder for port and a copy
- build() rejects an empty port
- a shallow copy shares the inner object. spread the inner object too

```ts
class Builder {
  private value = "";
  set(v: string) { this.value = v; return this; }
  build() {
    if (!this.value) throw new Error("incomplete");
    return { id: "n_2", port: this.value };
  }
}
const made = new Builder().set("Chattogram").build();
```

- homework
```ts
// 14a  build Chattogram for n_2
// 14b  build() with "" throws
// 14c  copy limits with an inner spread so later edits do not touch the base
```

- example 15. builder for round and a copy
- build() rejects an empty round
- a shallow copy shares the inner object. spread the inner object too

```ts
class Builder {
  private value = "";
  set(v: string) { this.value = v; return this; }
  build() {
    if (!this.value) throw new Error("incomplete");
    return { id: "b_3", round: this.value };
  }
}
const made = new Builder().set("semi").build();
```

- homework
```ts
// 15a  build semi for b_3
// 15b  build() with "" throws
// 15c  copy limits with an inner spread so later edits do not touch the base
```

- example 16. builder for userId and a copy
- build() rejects an empty userId
- a shallow copy shares the inner object. spread the inner object too

```ts
class Builder {
  private value = "";
  set(v: string) { this.value = v; return this; }
  build() {
    if (!this.value) throw new Error("incomplete");
    return { id: "se_1", userId: this.value };
  }
}
const made = new Builder().set("u_3").build();
```

- homework
```ts
// 16a  build u_3 for se_1
// 16b  build() with "" throws
// 16c  copy limits with an inner spread so later edits do not touch the base
```

- example 17. builder for name and a copy
- build() rejects an empty name
- a shallow copy shares the inner object. spread the inner object too

```ts
class Builder {
  private value = "";
  set(v: string) { this.value = v; return this; }
  build() {
    if (!this.value) throw new Error("incomplete");
    return { id: "q_1", name: this.value };
  }
}
const made = new Builder().set("laytime").build();
```

- homework
```ts
// 17a  build laytime for q_1
// 17b  build() with "" throws
// 17c  copy limits with an inner spread so later edits do not touch the base
```

- example 18. builder for name and a copy
- build() rejects an empty name
- a shallow copy shares the inner object. spread the inner object too

```ts
class Builder {
  private value = "";
  set(v: string) { this.value = v; return this; }
  build() {
    if (!this.value) throw new Error("incomplete");
    return { id: "r_1", name: this.value };
  }
}
const made = new Builder().set("operator").build();
```

- homework
```ts
// 18a  build operator for r_1
// 18b  build() with "" throws
// 18c  copy limits with an inner spread so later edits do not touch the base
```

- example 19. builder for vesselName and a copy
- build() rejects an empty vesselName
- a shallow copy shares the inner object. spread the inner object too

```ts
class Builder {
  private value = "";
  set(v: string) { this.value = v; return this; }
  build() {
    if (!this.value) throw new Error("incomplete");
    return { id: "pc_12", vesselName: this.value };
  }
}
const made = new Builder().set("Ocean Star").build();
```

- homework
```ts
// 19a  build Ocean Star for pc_12
// 19b  build() with "" throws
// 19c  copy limits with an inner spread so later edits do not touch the base
```

- example 20. builder for home and a copy
- build() rejects an empty home
- a shallow copy shares the inner object. spread the inner object too

```ts
class Builder {
  private value = "";
  set(v: string) { this.value = v; return this; }
  build() {
    if (!this.value) throw new Error("incomplete");
    return { id: "m_1", home: this.value };
  }
}
const made = new Builder().set("Ada").build();
```

- homework
```ts
// 20a  build Ada for m_1
// 20b  build() with "" throws
// 20c  copy limits with an inner spread so later edits do not touch the base
```

- example 21. builder for name and a copy
- build() rejects an empty name
- a shallow copy shares the inner object. spread the inner object too

```ts
class Builder {
  private value = "";
  set(v: string) { this.value = v; return this; }
  build() {
    if (!this.value) throw new Error("incomplete");
    return { id: "t_9", name: this.value };
  }
}
const made = new Builder().set("Rajshahi Open").build();
```

- homework
```ts
// 21a  build Rajshahi Open for t_9
// 21b  build() with "" throws
// 21c  copy limits with an inner spread so later edits do not touch the base
```

- example 22. builder for title and a copy
- build() rejects an empty title
- a shallow copy shares the inner object. spread the inner object too

```ts
class Builder {
  private value = "";
  set(v: string) { this.value = v; return this; }
  build() {
    if (!this.value) throw new Error("incomplete");
    return { id: "v_4", title: this.value };
  }
}
const made = new Builder().set("Episode 1").build();
```

- homework
```ts
// 22a  build Episode 1 for v_4
// 22b  build() with "" throws
// 22c  copy limits with an inner spread so later edits do not touch the base
```

- example 23. builder for kind and a copy
- build() rejects an empty kind
- a shallow copy shares the inner object. spread the inner object too

```ts
class Builder {
  private value = "";
  set(v: string) { this.value = v; return this; }
  build() {
    if (!this.value) throw new Error("incomplete");
    return { id: "f_2", kind: this.value };
  }
}
const made = new Builder().set("NOR").build();
```

- homework
```ts
// 23a  build NOR for f_2
// 23b  build() with "" throws
// 23c  copy limits with an inner spread so later edits do not touch the base
```

- example 24. builder for email and a copy
- build() rejects an empty email
- a shallow copy shares the inner object. spread the inner object too

```ts
class Builder {
  private value = "";
  set(v: string) { this.value = v; return this; }
  build() {
    if (!this.value) throw new Error("incomplete");
    return { id: "u_3", email: this.value };
  }
}
const made = new Builder().set("a@example.com").build();
```

- homework
```ts
// 24a  build a@example.com for u_3
// 24b  build() with "" throws
// 24c  copy limits with an inner spread so later edits do not touch the base
```

- example 25. builder for eventId and a copy
- build() rejects an empty eventId
- a shallow copy shares the inner object. spread the inner object too

```ts
class Builder {
  private value = "";
  set(v: string) { this.value = v; return this; }
  build() {
    if (!this.value) throw new Error("incomplete");
    return { id: "pay_8", eventId: this.value };
  }
}
const made = new Builder().set("evt_1").build();
```

- homework
```ts
// 25a  build evt_1 for pay_8
// 25b  build() with "" throws
// 25c  copy limits with an inner spread so later edits do not touch the base
```

- example 26. builder for sessionId and a copy
- build() rejects an empty sessionId
- a shallow copy shares the inner object. spread the inner object too

```ts
class Builder {
  private value = "";
  set(v: string) { this.value = v; return this; }
  build() {
    if (!this.value) throw new Error("incomplete");
    return { id: "room_2", sessionId: this.value };
  }
}
const made = new Builder().set("s_9").build();
```

- homework
```ts
// 26a  build s_9 for room_2
// 26b  build() with "" throws
// 26c  copy limits with an inner spread so later edits do not touch the base
```

- example 27. builder for name and a copy
- build() rejects an empty name
- a shallow copy shares the inner object. spread the inner object too

```ts
class Builder {
  private value = "";
  set(v: string) { this.value = v; return this; }
  build() {
    if (!this.value) throw new Error("incomplete");
    return { id: "vs_7", name: this.value };
  }
}
const made = new Builder().set("North Wind").build();
```

- homework
```ts
// 27a  build North Wind for vs_7
// 27b  build() with "" throws
// 27c  copy limits with an inner spread so later edits do not touch the base
```

- example 28. builder for points and a copy
- build() rejects an empty points
- a shallow copy shares the inner object. spread the inner object too

```ts
class Builder {
  private value = "";
  set(v: string) { this.value = v; return this; }
  build() {
    if (!this.value) throw new Error("incomplete");
    return { id: "sc_3", points: this.value };
  }
}
const made = new Builder().set("11").build();
```

- homework
```ts
// 28a  build 11 for sc_3
// 28b  build() with "" throws
// 28c  copy limits with an inner spread so later edits do not touch the base
```

- example 29. builder for name and a copy
- build() rejects an empty name
- a shallow copy shares the inner object. spread the inner object too

```ts
class Builder {
  private value = "";
  set(v: string) { this.value = v; return this; }
  build() {
    if (!this.value) throw new Error("incomplete");
    return { id: "tm_2", name: this.value };
  }
}
const made = new Builder().set("Blue").build();
```

- homework
```ts
// 29a  build Blue for tm_2
// 29b  build() with "" throws
// 29c  copy limits with an inner spread so later edits do not touch the base
```

- example 30. builder for key and a copy
- build() rejects an empty key
- a shallow copy shares the inner object. spread the inner object too

```ts
class Builder {
  private value = "";
  set(v: string) { this.value = v; return this; }
  build() {
    if (!this.value) throw new Error("incomplete");
    return { id: "up_6", key: this.value };
  }
}
const made = new Builder().set("videos/u_1/a.mp4").build();
```

- homework
```ts
// 30a  build videos/u_1/a.mp4 for up_6
// 30b  build() with "" throws
// 30c  copy limits with an inner spread so later edits do not touch the base
```

- example 31. builder for player and a copy
- build() rejects an empty player
- a shallow copy shares the inner object. spread the inner object too

```ts
class Builder {
  private value = "";
  set(v: string) { this.value = v; return this; }
  build() {
    if (!this.value) throw new Error("incomplete");
    return { id: "st_1", player: this.value };
  }
}
const made = new Builder().set("player_a").build();
```

- homework
```ts
// 31a  build player_a for st_1
// 31b  build() with "" throws
// 31c  copy limits with an inner spread so later edits do not touch the base
```

- example 32. builder for port and a copy
- build() rejects an empty port
- a shallow copy shares the inner object. spread the inner object too

```ts
class Builder {
  private value = "";
  set(v: string) { this.value = v; return this; }
  build() {
    if (!this.value) throw new Error("incomplete");
    return { id: "n_2", port: this.value };
  }
}
const made = new Builder().set("Chattogram").build();
```

- homework
```ts
// 32a  build Chattogram for n_2
// 32b  build() with "" throws
// 32c  copy limits with an inner spread so later edits do not touch the base
```

- example 33. builder for round and a copy
- build() rejects an empty round
- a shallow copy shares the inner object. spread the inner object too

```ts
class Builder {
  private value = "";
  set(v: string) { this.value = v; return this; }
  build() {
    if (!this.value) throw new Error("incomplete");
    return { id: "b_3", round: this.value };
  }
}
const made = new Builder().set("semi").build();
```

- homework
```ts
// 33a  build semi for b_3
// 33b  build() with "" throws
// 33c  copy limits with an inner spread so later edits do not touch the base
```

- example 34. builder for userId and a copy
- build() rejects an empty userId
- a shallow copy shares the inner object. spread the inner object too

```ts
class Builder {
  private value = "";
  set(v: string) { this.value = v; return this; }
  build() {
    if (!this.value) throw new Error("incomplete");
    return { id: "se_1", userId: this.value };
  }
}
const made = new Builder().set("u_3").build();
```

- homework
```ts
// 34a  build u_3 for se_1
// 34b  build() with "" throws
// 34c  copy limits with an inner spread so later edits do not touch the base
```

- example 35. builder for name and a copy
- build() rejects an empty name
- a shallow copy shares the inner object. spread the inner object too

```ts
class Builder {
  private value = "";
  set(v: string) { this.value = v; return this; }
  build() {
    if (!this.value) throw new Error("incomplete");
    return { id: "q_1", name: this.value };
  }
}
const made = new Builder().set("laytime").build();
```

- homework
```ts
// 35a  build laytime for q_1
// 35b  build() with "" throws
// 35c  copy limits with an inner spread so later edits do not touch the base
```

- example 36. builder for name and a copy
- build() rejects an empty name
- a shallow copy shares the inner object. spread the inner object too

```ts
class Builder {
  private value = "";
  set(v: string) { this.value = v; return this; }
  build() {
    if (!this.value) throw new Error("incomplete");
    return { id: "r_1", name: this.value };
  }
}
const made = new Builder().set("operator").build();
```

- homework
```ts
// 36a  build operator for r_1
// 36b  build() with "" throws
// 36c  copy limits with an inner spread so later edits do not touch the base
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

- example 1. wrapper and facade around pc_12
- adapter hides a vendor type
- decorator logs and still returns the same shape
- facade runs put, insert, and enqueue
- proxy can refuse a viewer

```ts
class LogStore {
  constructor(private readonly inner: { find(id: string): Promise<unknown> }) {}
  async find(id: string) {
    const row = await this.inner.find(id);
    return row;
  }
}
// find("pc_12") logs and returns the row whose vesselName is Ocean Star
```

- homework
```ts
// 1a  decorator logs find("pc_12")
// 1b  adapter wraps a vendor client
// 1c  facade method publish for an upload
// 1d  a TypeScript @Injectable is metadata, not this wrapper pattern
```

- example 2. wrapper and facade around m_1
- adapter hides a vendor type
- decorator logs and still returns the same shape
- facade runs put, insert, and enqueue
- proxy can refuse a viewer

```ts
class LogStore {
  constructor(private readonly inner: { find(id: string): Promise<unknown> }) {}
  async find(id: string) {
    const row = await this.inner.find(id);
    return row;
  }
}
// find("m_1") logs and returns the row whose home is Ada
```

- homework
```ts
// 2a  decorator logs find("m_1")
// 2b  adapter wraps a vendor client
// 2c  facade method publish for an upload
// 2d  a TypeScript @Injectable is metadata, not this wrapper pattern
```

- example 3. wrapper and facade around t_9
- adapter hides a vendor type
- decorator logs and still returns the same shape
- facade runs put, insert, and enqueue
- proxy can refuse a viewer

```ts
class LogStore {
  constructor(private readonly inner: { find(id: string): Promise<unknown> }) {}
  async find(id: string) {
    const row = await this.inner.find(id);
    return row;
  }
}
// find("t_9") logs and returns the row whose name is Rajshahi Open
```

- homework
```ts
// 3a  decorator logs find("t_9")
// 3b  adapter wraps a vendor client
// 3c  facade method publish for an upload
// 3d  a TypeScript @Injectable is metadata, not this wrapper pattern
```

- example 4. wrapper and facade around v_4
- adapter hides a vendor type
- decorator logs and still returns the same shape
- facade runs put, insert, and enqueue
- proxy can refuse a viewer

```ts
class LogStore {
  constructor(private readonly inner: { find(id: string): Promise<unknown> }) {}
  async find(id: string) {
    const row = await this.inner.find(id);
    return row;
  }
}
// find("v_4") logs and returns the row whose title is Episode 1
```

- homework
```ts
// 4a  decorator logs find("v_4")
// 4b  adapter wraps a vendor client
// 4c  facade method publish for an upload
// 4d  a TypeScript @Injectable is metadata, not this wrapper pattern
```

- example 5. wrapper and facade around f_2
- adapter hides a vendor type
- decorator logs and still returns the same shape
- facade runs put, insert, and enqueue
- proxy can refuse a viewer

```ts
class LogStore {
  constructor(private readonly inner: { find(id: string): Promise<unknown> }) {}
  async find(id: string) {
    const row = await this.inner.find(id);
    return row;
  }
}
// find("f_2") logs and returns the row whose kind is NOR
```

- homework
```ts
// 5a  decorator logs find("f_2")
// 5b  adapter wraps a vendor client
// 5c  facade method publish for an upload
// 5d  a TypeScript @Injectable is metadata, not this wrapper pattern
```

- example 6. wrapper and facade around u_3
- adapter hides a vendor type
- decorator logs and still returns the same shape
- facade runs put, insert, and enqueue
- proxy can refuse a viewer

```ts
class LogStore {
  constructor(private readonly inner: { find(id: string): Promise<unknown> }) {}
  async find(id: string) {
    const row = await this.inner.find(id);
    return row;
  }
}
// find("u_3") logs and returns the row whose email is a@example.com
```

- homework
```ts
// 6a  decorator logs find("u_3")
// 6b  adapter wraps a vendor client
// 6c  facade method publish for an upload
// 6d  a TypeScript @Injectable is metadata, not this wrapper pattern
```

- example 7. wrapper and facade around pay_8
- adapter hides a vendor type
- decorator logs and still returns the same shape
- facade runs put, insert, and enqueue
- proxy can refuse a viewer

```ts
class LogStore {
  constructor(private readonly inner: { find(id: string): Promise<unknown> }) {}
  async find(id: string) {
    const row = await this.inner.find(id);
    return row;
  }
}
// find("pay_8") logs and returns the row whose eventId is evt_1
```

- homework
```ts
// 7a  decorator logs find("pay_8")
// 7b  adapter wraps a vendor client
// 7c  facade method publish for an upload
// 7d  a TypeScript @Injectable is metadata, not this wrapper pattern
```

- example 8. wrapper and facade around room_2
- adapter hides a vendor type
- decorator logs and still returns the same shape
- facade runs put, insert, and enqueue
- proxy can refuse a viewer

```ts
class LogStore {
  constructor(private readonly inner: { find(id: string): Promise<unknown> }) {}
  async find(id: string) {
    const row = await this.inner.find(id);
    return row;
  }
}
// find("room_2") logs and returns the row whose sessionId is s_9
```

- homework
```ts
// 8a  decorator logs find("room_2")
// 8b  adapter wraps a vendor client
// 8c  facade method publish for an upload
// 8d  a TypeScript @Injectable is metadata, not this wrapper pattern
```

- example 9. wrapper and facade around vs_7
- adapter hides a vendor type
- decorator logs and still returns the same shape
- facade runs put, insert, and enqueue
- proxy can refuse a viewer

```ts
class LogStore {
  constructor(private readonly inner: { find(id: string): Promise<unknown> }) {}
  async find(id: string) {
    const row = await this.inner.find(id);
    return row;
  }
}
// find("vs_7") logs and returns the row whose name is North Wind
```

- homework
```ts
// 9a  decorator logs find("vs_7")
// 9b  adapter wraps a vendor client
// 9c  facade method publish for an upload
// 9d  a TypeScript @Injectable is metadata, not this wrapper pattern
```

- example 10. wrapper and facade around sc_3
- adapter hides a vendor type
- decorator logs and still returns the same shape
- facade runs put, insert, and enqueue
- proxy can refuse a viewer

```ts
class LogStore {
  constructor(private readonly inner: { find(id: string): Promise<unknown> }) {}
  async find(id: string) {
    const row = await this.inner.find(id);
    return row;
  }
}
// find("sc_3") logs and returns the row whose points is 11
```

- homework
```ts
// 10a  decorator logs find("sc_3")
// 10b  adapter wraps a vendor client
// 10c  facade method publish for an upload
// 10d  a TypeScript @Injectable is metadata, not this wrapper pattern
```

- example 11. wrapper and facade around tm_2
- adapter hides a vendor type
- decorator logs and still returns the same shape
- facade runs put, insert, and enqueue
- proxy can refuse a viewer

```ts
class LogStore {
  constructor(private readonly inner: { find(id: string): Promise<unknown> }) {}
  async find(id: string) {
    const row = await this.inner.find(id);
    return row;
  }
}
// find("tm_2") logs and returns the row whose name is Blue
```

- homework
```ts
// 11a  decorator logs find("tm_2")
// 11b  adapter wraps a vendor client
// 11c  facade method publish for an upload
// 11d  a TypeScript @Injectable is metadata, not this wrapper pattern
```

- example 12. wrapper and facade around up_6
- adapter hides a vendor type
- decorator logs and still returns the same shape
- facade runs put, insert, and enqueue
- proxy can refuse a viewer

```ts
class LogStore {
  constructor(private readonly inner: { find(id: string): Promise<unknown> }) {}
  async find(id: string) {
    const row = await this.inner.find(id);
    return row;
  }
}
// find("up_6") logs and returns the row whose key is videos/u_1/a.mp4
```

- homework
```ts
// 12a  decorator logs find("up_6")
// 12b  adapter wraps a vendor client
// 12c  facade method publish for an upload
// 12d  a TypeScript @Injectable is metadata, not this wrapper pattern
```

- example 13. wrapper and facade around st_1
- adapter hides a vendor type
- decorator logs and still returns the same shape
- facade runs put, insert, and enqueue
- proxy can refuse a viewer

```ts
class LogStore {
  constructor(private readonly inner: { find(id: string): Promise<unknown> }) {}
  async find(id: string) {
    const row = await this.inner.find(id);
    return row;
  }
}
// find("st_1") logs and returns the row whose player is player_a
```

- homework
```ts
// 13a  decorator logs find("st_1")
// 13b  adapter wraps a vendor client
// 13c  facade method publish for an upload
// 13d  a TypeScript @Injectable is metadata, not this wrapper pattern
```

- example 14. wrapper and facade around n_2
- adapter hides a vendor type
- decorator logs and still returns the same shape
- facade runs put, insert, and enqueue
- proxy can refuse a viewer

```ts
class LogStore {
  constructor(private readonly inner: { find(id: string): Promise<unknown> }) {}
  async find(id: string) {
    const row = await this.inner.find(id);
    return row;
  }
}
// find("n_2") logs and returns the row whose port is Chattogram
```

- homework
```ts
// 14a  decorator logs find("n_2")
// 14b  adapter wraps a vendor client
// 14c  facade method publish for an upload
// 14d  a TypeScript @Injectable is metadata, not this wrapper pattern
```

- example 15. wrapper and facade around b_3
- adapter hides a vendor type
- decorator logs and still returns the same shape
- facade runs put, insert, and enqueue
- proxy can refuse a viewer

```ts
class LogStore {
  constructor(private readonly inner: { find(id: string): Promise<unknown> }) {}
  async find(id: string) {
    const row = await this.inner.find(id);
    return row;
  }
}
// find("b_3") logs and returns the row whose round is semi
```

- homework
```ts
// 15a  decorator logs find("b_3")
// 15b  adapter wraps a vendor client
// 15c  facade method publish for an upload
// 15d  a TypeScript @Injectable is metadata, not this wrapper pattern
```

- example 16. wrapper and facade around se_1
- adapter hides a vendor type
- decorator logs and still returns the same shape
- facade runs put, insert, and enqueue
- proxy can refuse a viewer

```ts
class LogStore {
  constructor(private readonly inner: { find(id: string): Promise<unknown> }) {}
  async find(id: string) {
    const row = await this.inner.find(id);
    return row;
  }
}
// find("se_1") logs and returns the row whose userId is u_3
```

- homework
```ts
// 16a  decorator logs find("se_1")
// 16b  adapter wraps a vendor client
// 16c  facade method publish for an upload
// 16d  a TypeScript @Injectable is metadata, not this wrapper pattern
```

- example 17. wrapper and facade around q_1
- adapter hides a vendor type
- decorator logs and still returns the same shape
- facade runs put, insert, and enqueue
- proxy can refuse a viewer

```ts
class LogStore {
  constructor(private readonly inner: { find(id: string): Promise<unknown> }) {}
  async find(id: string) {
    const row = await this.inner.find(id);
    return row;
  }
}
// find("q_1") logs and returns the row whose name is laytime
```

- homework
```ts
// 17a  decorator logs find("q_1")
// 17b  adapter wraps a vendor client
// 17c  facade method publish for an upload
// 17d  a TypeScript @Injectable is metadata, not this wrapper pattern
```

- example 18. wrapper and facade around r_1
- adapter hides a vendor type
- decorator logs and still returns the same shape
- facade runs put, insert, and enqueue
- proxy can refuse a viewer

```ts
class LogStore {
  constructor(private readonly inner: { find(id: string): Promise<unknown> }) {}
  async find(id: string) {
    const row = await this.inner.find(id);
    return row;
  }
}
// find("r_1") logs and returns the row whose name is operator
```

- homework
```ts
// 18a  decorator logs find("r_1")
// 18b  adapter wraps a vendor client
// 18c  facade method publish for an upload
// 18d  a TypeScript @Injectable is metadata, not this wrapper pattern
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

- example 1. pick a rule, record a command, respect status
- strategy: half despatch or zero. half only when the contract says so
- command: type recalculate, id pc_12
- state: a done match does not take another score
- observers are told after the save. one throw should not stop the others

```ts
type Rule = (hours: number, perHour: number) => number;
const half: Rule = (h, p) => h * p * 0.5;
const none: Rule = () => 0;
const command = { type: "recalculate", id: "pc_12" };
function canEdit(status: "scheduled" | "live" | "done") {
  return status !== "done";
}
```

- homework
```ts
// 1a  none() ignores hours
// 1b  command id is pc_12
// 1c  canEdit("done") is false
// 1d  Socket.IO room is the observer across the network
```

- example 2. pick a rule, record a command, respect status
- strategy: half despatch or zero. half only when the contract says so
- command: type recalculate, id m_1
- state: a done match does not take another score
- observers are told after the save. one throw should not stop the others

```ts
type Rule = (hours: number, perHour: number) => number;
const half: Rule = (h, p) => h * p * 0.5;
const none: Rule = () => 0;
const command = { type: "recalculate", id: "m_1" };
function canEdit(status: "scheduled" | "live" | "done") {
  return status !== "done";
}
```

- homework
```ts
// 2a  none() ignores hours
// 2b  command id is m_1
// 2c  canEdit("done") is false
// 2d  Socket.IO room is the observer across the network
```

- example 3. pick a rule, record a command, respect status
- strategy: half despatch or zero. half only when the contract says so
- command: type recalculate, id t_9
- state: a done match does not take another score
- observers are told after the save. one throw should not stop the others

```ts
type Rule = (hours: number, perHour: number) => number;
const half: Rule = (h, p) => h * p * 0.5;
const none: Rule = () => 0;
const command = { type: "recalculate", id: "t_9" };
function canEdit(status: "scheduled" | "live" | "done") {
  return status !== "done";
}
```

- homework
```ts
// 3a  none() ignores hours
// 3b  command id is t_9
// 3c  canEdit("done") is false
// 3d  Socket.IO room is the observer across the network
```

- example 4. pick a rule, record a command, respect status
- strategy: half despatch or zero. half only when the contract says so
- command: type recalculate, id v_4
- state: a done match does not take another score
- observers are told after the save. one throw should not stop the others

```ts
type Rule = (hours: number, perHour: number) => number;
const half: Rule = (h, p) => h * p * 0.5;
const none: Rule = () => 0;
const command = { type: "recalculate", id: "v_4" };
function canEdit(status: "scheduled" | "live" | "done") {
  return status !== "done";
}
```

- homework
```ts
// 4a  none() ignores hours
// 4b  command id is v_4
// 4c  canEdit("done") is false
// 4d  Socket.IO room is the observer across the network
```

- example 5. pick a rule, record a command, respect status
- strategy: half despatch or zero. half only when the contract says so
- command: type recalculate, id f_2
- state: a done match does not take another score
- observers are told after the save. one throw should not stop the others

```ts
type Rule = (hours: number, perHour: number) => number;
const half: Rule = (h, p) => h * p * 0.5;
const none: Rule = () => 0;
const command = { type: "recalculate", id: "f_2" };
function canEdit(status: "scheduled" | "live" | "done") {
  return status !== "done";
}
```

- homework
```ts
// 5a  none() ignores hours
// 5b  command id is f_2
// 5c  canEdit("done") is false
// 5d  Socket.IO room is the observer across the network
```

- example 6. pick a rule, record a command, respect status
- strategy: half despatch or zero. half only when the contract says so
- command: type recalculate, id u_3
- state: a done match does not take another score
- observers are told after the save. one throw should not stop the others

```ts
type Rule = (hours: number, perHour: number) => number;
const half: Rule = (h, p) => h * p * 0.5;
const none: Rule = () => 0;
const command = { type: "recalculate", id: "u_3" };
function canEdit(status: "scheduled" | "live" | "done") {
  return status !== "done";
}
```

- homework
```ts
// 6a  none() ignores hours
// 6b  command id is u_3
// 6c  canEdit("done") is false
// 6d  Socket.IO room is the observer across the network
```

- example 7. pick a rule, record a command, respect status
- strategy: half despatch or zero. half only when the contract says so
- command: type recalculate, id pay_8
- state: a done match does not take another score
- observers are told after the save. one throw should not stop the others

```ts
type Rule = (hours: number, perHour: number) => number;
const half: Rule = (h, p) => h * p * 0.5;
const none: Rule = () => 0;
const command = { type: "recalculate", id: "pay_8" };
function canEdit(status: "scheduled" | "live" | "done") {
  return status !== "done";
}
```

- homework
```ts
// 7a  none() ignores hours
// 7b  command id is pay_8
// 7c  canEdit("done") is false
// 7d  Socket.IO room is the observer across the network
```

- example 8. pick a rule, record a command, respect status
- strategy: half despatch or zero. half only when the contract says so
- command: type recalculate, id room_2
- state: a done match does not take another score
- observers are told after the save. one throw should not stop the others

```ts
type Rule = (hours: number, perHour: number) => number;
const half: Rule = (h, p) => h * p * 0.5;
const none: Rule = () => 0;
const command = { type: "recalculate", id: "room_2" };
function canEdit(status: "scheduled" | "live" | "done") {
  return status !== "done";
}
```

- homework
```ts
// 8a  none() ignores hours
// 8b  command id is room_2
// 8c  canEdit("done") is false
// 8d  Socket.IO room is the observer across the network
```

- example 9. pick a rule, record a command, respect status
- strategy: half despatch or zero. half only when the contract says so
- command: type recalculate, id vs_7
- state: a done match does not take another score
- observers are told after the save. one throw should not stop the others

```ts
type Rule = (hours: number, perHour: number) => number;
const half: Rule = (h, p) => h * p * 0.5;
const none: Rule = () => 0;
const command = { type: "recalculate", id: "vs_7" };
function canEdit(status: "scheduled" | "live" | "done") {
  return status !== "done";
}
```

- homework
```ts
// 9a  none() ignores hours
// 9b  command id is vs_7
// 9c  canEdit("done") is false
// 9d  Socket.IO room is the observer across the network
```

- example 10. pick a rule, record a command, respect status
- strategy: half despatch or zero. half only when the contract says so
- command: type recalculate, id sc_3
- state: a done match does not take another score
- observers are told after the save. one throw should not stop the others

```ts
type Rule = (hours: number, perHour: number) => number;
const half: Rule = (h, p) => h * p * 0.5;
const none: Rule = () => 0;
const command = { type: "recalculate", id: "sc_3" };
function canEdit(status: "scheduled" | "live" | "done") {
  return status !== "done";
}
```

- homework
```ts
// 10a  none() ignores hours
// 10b  command id is sc_3
// 10c  canEdit("done") is false
// 10d  Socket.IO room is the observer across the network
```

- example 11. pick a rule, record a command, respect status
- strategy: half despatch or zero. half only when the contract says so
- command: type recalculate, id tm_2
- state: a done match does not take another score
- observers are told after the save. one throw should not stop the others

```ts
type Rule = (hours: number, perHour: number) => number;
const half: Rule = (h, p) => h * p * 0.5;
const none: Rule = () => 0;
const command = { type: "recalculate", id: "tm_2" };
function canEdit(status: "scheduled" | "live" | "done") {
  return status !== "done";
}
```

- homework
```ts
// 11a  none() ignores hours
// 11b  command id is tm_2
// 11c  canEdit("done") is false
// 11d  Socket.IO room is the observer across the network
```

- example 12. pick a rule, record a command, respect status
- strategy: half despatch or zero. half only when the contract says so
- command: type recalculate, id up_6
- state: a done match does not take another score
- observers are told after the save. one throw should not stop the others

```ts
type Rule = (hours: number, perHour: number) => number;
const half: Rule = (h, p) => h * p * 0.5;
const none: Rule = () => 0;
const command = { type: "recalculate", id: "up_6" };
function canEdit(status: "scheduled" | "live" | "done") {
  return status !== "done";
}
```

- homework
```ts
// 12a  none() ignores hours
// 12b  command id is up_6
// 12c  canEdit("done") is false
// 12d  Socket.IO room is the observer across the network
```

- example 13. pick a rule, record a command, respect status
- strategy: half despatch or zero. half only when the contract says so
- command: type recalculate, id st_1
- state: a done match does not take another score
- observers are told after the save. one throw should not stop the others

```ts
type Rule = (hours: number, perHour: number) => number;
const half: Rule = (h, p) => h * p * 0.5;
const none: Rule = () => 0;
const command = { type: "recalculate", id: "st_1" };
function canEdit(status: "scheduled" | "live" | "done") {
  return status !== "done";
}
```

- homework
```ts
// 13a  none() ignores hours
// 13b  command id is st_1
// 13c  canEdit("done") is false
// 13d  Socket.IO room is the observer across the network
```

- example 14. pick a rule, record a command, respect status
- strategy: half despatch or zero. half only when the contract says so
- command: type recalculate, id n_2
- state: a done match does not take another score
- observers are told after the save. one throw should not stop the others

```ts
type Rule = (hours: number, perHour: number) => number;
const half: Rule = (h, p) => h * p * 0.5;
const none: Rule = () => 0;
const command = { type: "recalculate", id: "n_2" };
function canEdit(status: "scheduled" | "live" | "done") {
  return status !== "done";
}
```

- homework
```ts
// 14a  none() ignores hours
// 14b  command id is n_2
// 14c  canEdit("done") is false
// 14d  Socket.IO room is the observer across the network
```

- example 15. pick a rule, record a command, respect status
- strategy: half despatch or zero. half only when the contract says so
- command: type recalculate, id b_3
- state: a done match does not take another score
- observers are told after the save. one throw should not stop the others

```ts
type Rule = (hours: number, perHour: number) => number;
const half: Rule = (h, p) => h * p * 0.5;
const none: Rule = () => 0;
const command = { type: "recalculate", id: "b_3" };
function canEdit(status: "scheduled" | "live" | "done") {
  return status !== "done";
}
```

- homework
```ts
// 15a  none() ignores hours
// 15b  command id is b_3
// 15c  canEdit("done") is false
// 15d  Socket.IO room is the observer across the network
```

- example 16. pick a rule, record a command, respect status
- strategy: half despatch or zero. half only when the contract says so
- command: type recalculate, id se_1
- state: a done match does not take another score
- observers are told after the save. one throw should not stop the others

```ts
type Rule = (hours: number, perHour: number) => number;
const half: Rule = (h, p) => h * p * 0.5;
const none: Rule = () => 0;
const command = { type: "recalculate", id: "se_1" };
function canEdit(status: "scheduled" | "live" | "done") {
  return status !== "done";
}
```

- homework
```ts
// 16a  none() ignores hours
// 16b  command id is se_1
// 16c  canEdit("done") is false
// 16d  Socket.IO room is the observer across the network
```

- example 17. pick a rule, record a command, respect status
- strategy: half despatch or zero. half only when the contract says so
- command: type recalculate, id q_1
- state: a done match does not take another score
- observers are told after the save. one throw should not stop the others

```ts
type Rule = (hours: number, perHour: number) => number;
const half: Rule = (h, p) => h * p * 0.5;
const none: Rule = () => 0;
const command = { type: "recalculate", id: "q_1" };
function canEdit(status: "scheduled" | "live" | "done") {
  return status !== "done";
}
```

- homework
```ts
// 17a  none() ignores hours
// 17b  command id is q_1
// 17c  canEdit("done") is false
// 17d  Socket.IO room is the observer across the network
```

- example 18. pick a rule, record a command, respect status
- strategy: half despatch or zero. half only when the contract says so
- command: type recalculate, id r_1
- state: a done match does not take another score
- observers are told after the save. one throw should not stop the others

```ts
type Rule = (hours: number, perHour: number) => number;
const half: Rule = (h, p) => h * p * 0.5;
const none: Rule = () => 0;
const command = { type: "recalculate", id: "r_1" };
function canEdit(status: "scheduled" | "live" | "done") {
  return status !== "done";
}
```

- homework
```ts
// 18a  none() ignores hours
// 18b  command id is r_1
// 18c  canEdit("done") is false
// 18d  Socket.IO room is the observer across the network
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

- example 1. a shared field versus a local for pc_12
- one JavaScript thread still overlaps at await
- both reads of 72 can both write 72+1
- a local variable belongs to that call only
- a second process does not share this.n. it shares Postgres

```ts
async function bad() {
  const current = shared;
  await Promise.resolve();
  shared = current + 1;
}
await db.$executeRaw`UPDATE counters SET n = n + 1 WHERE id = ${id}`;
```

- homework
```ts
// 1a  the local that holds "pc_12" is safe
// 1b  the singleton field is not
// 1c  the SQL update does not lose a bump
```

- example 2. a shared field versus a local for m_1
- one JavaScript thread still overlaps at await
- both reads of 3 can both write 3+1
- a local variable belongs to that call only
- a second process does not share this.n. it shares Postgres

```ts
async function bad() {
  const current = shared;
  await Promise.resolve();
  shared = current + 1;
}
await db.$executeRaw`UPDATE counters SET n = n + 1 WHERE id = ${id}`;
```

- homework
```ts
// 2a  the local that holds "m_1" is safe
// 2b  the singleton field is not
// 2c  the SQL update does not lose a bump
```

- example 3. a shared field versus a local for t_9
- one JavaScript thread still overlaps at await
- both reads of 16 can both write 16+1
- a local variable belongs to that call only
- a second process does not share this.n. it shares Postgres

```ts
async function bad() {
  const current = shared;
  await Promise.resolve();
  shared = current + 1;
}
await db.$executeRaw`UPDATE counters SET n = n + 1 WHERE id = ${id}`;
```

- homework
```ts
// 3a  the local that holds "t_9" is safe
// 3b  the singleton field is not
// 3c  the SQL update does not lose a bump
```

- example 4. a shared field versus a local for v_4
- one JavaScript thread still overlaps at await
- both reads of 6 can both write 6+1
- a local variable belongs to that call only
- a second process does not share this.n. it shares Postgres

```ts
async function bad() {
  const current = shared;
  await Promise.resolve();
  shared = current + 1;
}
await db.$executeRaw`UPDATE counters SET n = n + 1 WHERE id = ${id}`;
```

- homework
```ts
// 4a  the local that holds "v_4" is safe
// 4b  the singleton field is not
// 4c  the SQL update does not lose a bump
```

- example 5. a shared field versus a local for f_2
- one JavaScript thread still overlaps at await
- both reads of 1 can both write 1+1
- a local variable belongs to that call only
- a second process does not share this.n. it shares Postgres

```ts
async function bad() {
  const current = shared;
  await Promise.resolve();
  shared = current + 1;
}
await db.$executeRaw`UPDATE counters SET n = n + 1 WHERE id = ${id}`;
```

- homework
```ts
// 5a  the local that holds "f_2" is safe
// 5b  the singleton field is not
// 5c  the SQL update does not lose a bump
```

- example 6. a shared field versus a local for u_3
- one JavaScript thread still overlaps at await
- both reads of 1 can both write 1+1
- a local variable belongs to that call only
- a second process does not share this.n. it shares Postgres

```ts
async function bad() {
  const current = shared;
  await Promise.resolve();
  shared = current + 1;
}
await db.$executeRaw`UPDATE counters SET n = n + 1 WHERE id = ${id}`;
```

- homework
```ts
// 6a  the local that holds "u_3" is safe
// 6b  the singleton field is not
// 6c  the SQL update does not lose a bump
```

- example 7. a shared field versus a local for pay_8
- one JavaScript thread still overlaps at await
- both reads of 15000 can both write 15000+1
- a local variable belongs to that call only
- a second process does not share this.n. it shares Postgres

```ts
async function bad() {
  const current = shared;
  await Promise.resolve();
  shared = current + 1;
}
await db.$executeRaw`UPDATE counters SET n = n + 1 WHERE id = ${id}`;
```

- homework
```ts
// 7a  the local that holds "pay_8" is safe
// 7b  the singleton field is not
// 7c  the SQL update does not lose a bump
```

- example 8. a shared field versus a local for room_2
- one JavaScript thread still overlaps at await
- both reads of 12 can both write 12+1
- a local variable belongs to that call only
- a second process does not share this.n. it shares Postgres

```ts
async function bad() {
  const current = shared;
  await Promise.resolve();
  shared = current + 1;
}
await db.$executeRaw`UPDATE counters SET n = n + 1 WHERE id = ${id}`;
```

- homework
```ts
// 8a  the local that holds "room_2" is safe
// 8b  the singleton field is not
// 8c  the SQL update does not lose a bump
```

- example 9. a shared field versus a local for vs_7
- one JavaScript thread still overlaps at await
- both reads of 48 can both write 48+1
- a local variable belongs to that call only
- a second process does not share this.n. it shares Postgres

```ts
async function bad() {
  const current = shared;
  await Promise.resolve();
  shared = current + 1;
}
await db.$executeRaw`UPDATE counters SET n = n + 1 WHERE id = ${id}`;
```

- homework
```ts
// 9a  the local that holds "vs_7" is safe
// 9b  the singleton field is not
// 9c  the SQL update does not lose a bump
```

- example 10. a shared field versus a local for sc_3
- one JavaScript thread still overlaps at await
- both reads of 11 can both write 11+1
- a local variable belongs to that call only
- a second process does not share this.n. it shares Postgres

```ts
async function bad() {
  const current = shared;
  await Promise.resolve();
  shared = current + 1;
}
await db.$executeRaw`UPDATE counters SET n = n + 1 WHERE id = ${id}`;
```

- homework
```ts
// 10a  the local that holds "sc_3" is safe
// 10b  the singleton field is not
// 10c  the SQL update does not lose a bump
```

- example 11. a shared field versus a local for tm_2
- one JavaScript thread still overlaps at await
- both reads of 2 can both write 2+1
- a local variable belongs to that call only
- a second process does not share this.n. it shares Postgres

```ts
async function bad() {
  const current = shared;
  await Promise.resolve();
  shared = current + 1;
}
await db.$executeRaw`UPDATE counters SET n = n + 1 WHERE id = ${id}`;
```

- homework
```ts
// 11a  the local that holds "tm_2" is safe
// 11b  the singleton field is not
// 11c  the SQL update does not lose a bump
```

- example 12. a shared field versus a local for up_6
- one JavaScript thread still overlaps at await
- both reads of 200 can both write 200+1
- a local variable belongs to that call only
- a second process does not share this.n. it shares Postgres

```ts
async function bad() {
  const current = shared;
  await Promise.resolve();
  shared = current + 1;
}
await db.$executeRaw`UPDATE counters SET n = n + 1 WHERE id = ${id}`;
```

- homework
```ts
// 12a  the local that holds "up_6" is safe
// 12b  the singleton field is not
// 12c  the SQL update does not lose a bump
```

- example 13. a shared field versus a local for st_1
- one JavaScript thread still overlaps at await
- both reads of 1500 can both write 1500+1
- a local variable belongs to that call only
- a second process does not share this.n. it shares Postgres

```ts
async function bad() {
  const current = shared;
  await Promise.resolve();
  shared = current + 1;
}
await db.$executeRaw`UPDATE counters SET n = n + 1 WHERE id = ${id}`;
```

- homework
```ts
// 13a  the local that holds "st_1" is safe
// 13b  the singleton field is not
// 13c  the SQL update does not lose a bump
```

- example 14. a shared field versus a local for n_2
- one JavaScript thread still overlaps at await
- both reads of 24 can both write 24+1
- a local variable belongs to that call only
- a second process does not share this.n. it shares Postgres

```ts
async function bad() {
  const current = shared;
  await Promise.resolve();
  shared = current + 1;
}
await db.$executeRaw`UPDATE counters SET n = n + 1 WHERE id = ${id}`;
```

- homework
```ts
// 14a  the local that holds "n_2" is safe
// 14b  the singleton field is not
// 14c  the SQL update does not lose a bump
```

- example 15. a shared field versus a local for b_3
- one JavaScript thread still overlaps at await
- both reads of 4 can both write 4+1
- a local variable belongs to that call only
- a second process does not share this.n. it shares Postgres

```ts
async function bad() {
  const current = shared;
  await Promise.resolve();
  shared = current + 1;
}
await db.$executeRaw`UPDATE counters SET n = n + 1 WHERE id = ${id}`;
```

- homework
```ts
// 15a  the local that holds "b_3" is safe
// 15b  the singleton field is not
// 15c  the SQL update does not lose a bump
```

- example 16. a shared field versus a local for se_1
- one JavaScript thread still overlaps at await
- both reads of 15 can both write 15+1
- a local variable belongs to that call only
- a second process does not share this.n. it shares Postgres

```ts
async function bad() {
  const current = shared;
  await Promise.resolve();
  shared = current + 1;
}
await db.$executeRaw`UPDATE counters SET n = n + 1 WHERE id = ${id}`;
```

- homework
```ts
// 16a  the local that holds "se_1" is safe
// 16b  the singleton field is not
// 16c  the SQL update does not lose a bump
```

- example 17. a shared field versus a local for q_1
- one JavaScript thread still overlaps at await
- both reads of 10 can both write 10+1
- a local variable belongs to that call only
- a second process does not share this.n. it shares Postgres

```ts
async function bad() {
  const current = shared;
  await Promise.resolve();
  shared = current + 1;
}
await db.$executeRaw`UPDATE counters SET n = n + 1 WHERE id = ${id}`;
```

- homework
```ts
// 17a  the local that holds "q_1" is safe
// 17b  the singleton field is not
// 17c  the SQL update does not lose a bump
```

- example 18. a shared field versus a local for r_1
- one JavaScript thread still overlaps at await
- both reads of 2 can both write 2+1
- a local variable belongs to that call only
- a second process does not share this.n. it shares Postgres

```ts
async function bad() {
  const current = shared;
  await Promise.resolve();
  shared = current + 1;
}
await db.$executeRaw`UPDATE counters SET n = n + 1 WHERE id = ${id}`;
```

- homework
```ts
// 18a  the local that holds "r_1" is safe
// 18b  the singleton field is not
// 18c  the SQL update does not lose a bump
```

- example 19. a shared field versus a local for pc_12
- one JavaScript thread still overlaps at await
- both reads of 72 can both write 72+1
- a local variable belongs to that call only
- a second process does not share this.n. it shares Postgres

```ts
async function bad() {
  const current = shared;
  await Promise.resolve();
  shared = current + 1;
}
await db.$executeRaw`UPDATE counters SET n = n + 1 WHERE id = ${id}`;
```

- homework
```ts
// 19a  the local that holds "pc_12" is safe
// 19b  the singleton field is not
// 19c  the SQL update does not lose a bump
```

- example 20. a shared field versus a local for m_1
- one JavaScript thread still overlaps at await
- both reads of 3 can both write 3+1
- a local variable belongs to that call only
- a second process does not share this.n. it shares Postgres

```ts
async function bad() {
  const current = shared;
  await Promise.resolve();
  shared = current + 1;
}
await db.$executeRaw`UPDATE counters SET n = n + 1 WHERE id = ${id}`;
```

- homework
```ts
// 20a  the local that holds "m_1" is safe
// 20b  the singleton field is not
// 20c  the SQL update does not lose a bump
```

- example 21. a shared field versus a local for t_9
- one JavaScript thread still overlaps at await
- both reads of 16 can both write 16+1
- a local variable belongs to that call only
- a second process does not share this.n. it shares Postgres

```ts
async function bad() {
  const current = shared;
  await Promise.resolve();
  shared = current + 1;
}
await db.$executeRaw`UPDATE counters SET n = n + 1 WHERE id = ${id}`;
```

- homework
```ts
// 21a  the local that holds "t_9" is safe
// 21b  the singleton field is not
// 21c  the SQL update does not lose a bump
```

- example 22. a shared field versus a local for v_4
- one JavaScript thread still overlaps at await
- both reads of 6 can both write 6+1
- a local variable belongs to that call only
- a second process does not share this.n. it shares Postgres

```ts
async function bad() {
  const current = shared;
  await Promise.resolve();
  shared = current + 1;
}
await db.$executeRaw`UPDATE counters SET n = n + 1 WHERE id = ${id}`;
```

- homework
```ts
// 22a  the local that holds "v_4" is safe
// 22b  the singleton field is not
// 22c  the SQL update does not lose a bump
```

- example 23. a shared field versus a local for f_2
- one JavaScript thread still overlaps at await
- both reads of 1 can both write 1+1
- a local variable belongs to that call only
- a second process does not share this.n. it shares Postgres

```ts
async function bad() {
  const current = shared;
  await Promise.resolve();
  shared = current + 1;
}
await db.$executeRaw`UPDATE counters SET n = n + 1 WHERE id = ${id}`;
```

- homework
```ts
// 23a  the local that holds "f_2" is safe
// 23b  the singleton field is not
// 23c  the SQL update does not lose a bump
```

- example 24. a shared field versus a local for u_3
- one JavaScript thread still overlaps at await
- both reads of 1 can both write 1+1
- a local variable belongs to that call only
- a second process does not share this.n. it shares Postgres

```ts
async function bad() {
  const current = shared;
  await Promise.resolve();
  shared = current + 1;
}
await db.$executeRaw`UPDATE counters SET n = n + 1 WHERE id = ${id}`;
```

- homework
```ts
// 24a  the local that holds "u_3" is safe
// 24b  the singleton field is not
// 24c  the SQL update does not lose a bump
```

- example 25. a shared field versus a local for pay_8
- one JavaScript thread still overlaps at await
- both reads of 15000 can both write 15000+1
- a local variable belongs to that call only
- a second process does not share this.n. it shares Postgres

```ts
async function bad() {
  const current = shared;
  await Promise.resolve();
  shared = current + 1;
}
await db.$executeRaw`UPDATE counters SET n = n + 1 WHERE id = ${id}`;
```

- homework
```ts
// 25a  the local that holds "pay_8" is safe
// 25b  the singleton field is not
// 25c  the SQL update does not lose a bump
```

- example 26. a shared field versus a local for room_2
- one JavaScript thread still overlaps at await
- both reads of 12 can both write 12+1
- a local variable belongs to that call only
- a second process does not share this.n. it shares Postgres

```ts
async function bad() {
  const current = shared;
  await Promise.resolve();
  shared = current + 1;
}
await db.$executeRaw`UPDATE counters SET n = n + 1 WHERE id = ${id}`;
```

- homework
```ts
// 26a  the local that holds "room_2" is safe
// 26b  the singleton field is not
// 26c  the SQL update does not lose a bump
```

- example 27. a shared field versus a local for vs_7
- one JavaScript thread still overlaps at await
- both reads of 48 can both write 48+1
- a local variable belongs to that call only
- a second process does not share this.n. it shares Postgres

```ts
async function bad() {
  const current = shared;
  await Promise.resolve();
  shared = current + 1;
}
await db.$executeRaw`UPDATE counters SET n = n + 1 WHERE id = ${id}`;
```

- homework
```ts
// 27a  the local that holds "vs_7" is safe
// 27b  the singleton field is not
// 27c  the SQL update does not lose a bump
```

- example 28. a shared field versus a local for sc_3
- one JavaScript thread still overlaps at await
- both reads of 11 can both write 11+1
- a local variable belongs to that call only
- a second process does not share this.n. it shares Postgres

```ts
async function bad() {
  const current = shared;
  await Promise.resolve();
  shared = current + 1;
}
await db.$executeRaw`UPDATE counters SET n = n + 1 WHERE id = ${id}`;
```

- homework
```ts
// 28a  the local that holds "sc_3" is safe
// 28b  the singleton field is not
// 28c  the SQL update does not lose a bump
```

- example 29. a shared field versus a local for tm_2
- one JavaScript thread still overlaps at await
- both reads of 2 can both write 2+1
- a local variable belongs to that call only
- a second process does not share this.n. it shares Postgres

```ts
async function bad() {
  const current = shared;
  await Promise.resolve();
  shared = current + 1;
}
await db.$executeRaw`UPDATE counters SET n = n + 1 WHERE id = ${id}`;
```

- homework
```ts
// 29a  the local that holds "tm_2" is safe
// 29b  the singleton field is not
// 29c  the SQL update does not lose a bump
```

- example 30. a shared field versus a local for up_6
- one JavaScript thread still overlaps at await
- both reads of 200 can both write 200+1
- a local variable belongs to that call only
- a second process does not share this.n. it shares Postgres

```ts
async function bad() {
  const current = shared;
  await Promise.resolve();
  shared = current + 1;
}
await db.$executeRaw`UPDATE counters SET n = n + 1 WHERE id = ${id}`;
```

- homework
```ts
// 30a  the local that holds "up_6" is safe
// 30b  the singleton field is not
// 30c  the SQL update does not lose a bump
```

- example 31. a shared field versus a local for st_1
- one JavaScript thread still overlaps at await
- both reads of 1500 can both write 1500+1
- a local variable belongs to that call only
- a second process does not share this.n. it shares Postgres

```ts
async function bad() {
  const current = shared;
  await Promise.resolve();
  shared = current + 1;
}
await db.$executeRaw`UPDATE counters SET n = n + 1 WHERE id = ${id}`;
```

- homework
```ts
// 31a  the local that holds "st_1" is safe
// 31b  the singleton field is not
// 31c  the SQL update does not lose a bump
```

- example 32. a shared field versus a local for n_2
- one JavaScript thread still overlaps at await
- both reads of 24 can both write 24+1
- a local variable belongs to that call only
- a second process does not share this.n. it shares Postgres

```ts
async function bad() {
  const current = shared;
  await Promise.resolve();
  shared = current + 1;
}
await db.$executeRaw`UPDATE counters SET n = n + 1 WHERE id = ${id}`;
```

- homework
```ts
// 32a  the local that holds "n_2" is safe
// 32b  the singleton field is not
// 32c  the SQL update does not lose a bump
```

- example 33. a shared field versus a local for b_3
- one JavaScript thread still overlaps at await
- both reads of 4 can both write 4+1
- a local variable belongs to that call only
- a second process does not share this.n. it shares Postgres

```ts
async function bad() {
  const current = shared;
  await Promise.resolve();
  shared = current + 1;
}
await db.$executeRaw`UPDATE counters SET n = n + 1 WHERE id = ${id}`;
```

- homework
```ts
// 33a  the local that holds "b_3" is safe
// 33b  the singleton field is not
// 33c  the SQL update does not lose a bump
```

- example 34. a shared field versus a local for se_1
- one JavaScript thread still overlaps at await
- both reads of 15 can both write 15+1
- a local variable belongs to that call only
- a second process does not share this.n. it shares Postgres

```ts
async function bad() {
  const current = shared;
  await Promise.resolve();
  shared = current + 1;
}
await db.$executeRaw`UPDATE counters SET n = n + 1 WHERE id = ${id}`;
```

- homework
```ts
// 34a  the local that holds "se_1" is safe
// 34b  the singleton field is not
// 34c  the SQL update does not lose a bump
```

- example 35. a shared field versus a local for q_1
- one JavaScript thread still overlaps at await
- both reads of 10 can both write 10+1
- a local variable belongs to that call only
- a second process does not share this.n. it shares Postgres

```ts
async function bad() {
  const current = shared;
  await Promise.resolve();
  shared = current + 1;
}
await db.$executeRaw`UPDATE counters SET n = n + 1 WHERE id = ${id}`;
```

- homework
```ts
// 35a  the local that holds "q_1" is safe
// 35b  the singleton field is not
// 35c  the SQL update does not lose a bump
```

- example 36. a shared field versus a local for r_1
- one JavaScript thread still overlaps at await
- both reads of 2 can both write 2+1
- a local variable belongs to that call only
- a second process does not share this.n. it shares Postgres

```ts
async function bad() {
  const current = shared;
  await Promise.resolve();
  shared = current + 1;
}
await db.$executeRaw`UPDATE counters SET n = n + 1 WHERE id = ${id}`;
```

- homework
```ts
// 36a  the local that holds "r_1" is safe
// 36b  the singleton field is not
// 36c  the SQL update does not lose a bump
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

- example 1. write the winner into the next match
- main path first. edges after
- match pc_12 points at next
- the parent fills a, then b

```ts
type Match = { id: string; a?: string; b?: string; winner?: string; next?: string };
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
winnerOf(map, "pc_12", "a");
```

- homework
```ts
// 1a  winner "Ocean Star" moves into the parent
// 1b  the laytime test for 7500 exists before a pause rule
// 1c  both players missing is the second case, not the first
```

- example 2. write the winner into the next match
- main path first. edges after
- match m_1 points at next
- the parent fills a, then b

```ts
type Match = { id: string; a?: string; b?: string; winner?: string; next?: string };
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
winnerOf(map, "m_1", "a");
```

- homework
```ts
// 2a  winner "Ada" moves into the parent
// 2b  the laytime test for 7500 exists before a pause rule
// 2c  both players missing is the second case, not the first
```

- example 3. write the winner into the next match
- main path first. edges after
- match t_9 points at next
- the parent fills a, then b

```ts
type Match = { id: string; a?: string; b?: string; winner?: string; next?: string };
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
winnerOf(map, "t_9", "a");
```

- homework
```ts
// 3a  winner "Rajshahi Open" moves into the parent
// 3b  the laytime test for 7500 exists before a pause rule
// 3c  both players missing is the second case, not the first
```

- example 4. write the winner into the next match
- main path first. edges after
- match v_4 points at next
- the parent fills a, then b

```ts
type Match = { id: string; a?: string; b?: string; winner?: string; next?: string };
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
winnerOf(map, "v_4", "a");
```

- homework
```ts
// 4a  winner "Episode 1" moves into the parent
// 4b  the laytime test for 7500 exists before a pause rule
// 4c  both players missing is the second case, not the first
```

- example 5. write the winner into the next match
- main path first. edges after
- match f_2 points at next
- the parent fills a, then b

```ts
type Match = { id: string; a?: string; b?: string; winner?: string; next?: string };
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
winnerOf(map, "f_2", "a");
```

- homework
```ts
// 5a  winner "NOR" moves into the parent
// 5b  the laytime test for 7500 exists before a pause rule
// 5c  both players missing is the second case, not the first
```

- example 6. write the winner into the next match
- main path first. edges after
- match u_3 points at next
- the parent fills a, then b

```ts
type Match = { id: string; a?: string; b?: string; winner?: string; next?: string };
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
winnerOf(map, "u_3", "a");
```

- homework
```ts
// 6a  winner "a@example.com" moves into the parent
// 6b  the laytime test for 7500 exists before a pause rule
// 6c  both players missing is the second case, not the first
```

- example 7. write the winner into the next match
- main path first. edges after
- match pay_8 points at next
- the parent fills a, then b

```ts
type Match = { id: string; a?: string; b?: string; winner?: string; next?: string };
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
winnerOf(map, "pay_8", "a");
```

- homework
```ts
// 7a  winner "evt_1" moves into the parent
// 7b  the laytime test for 7500 exists before a pause rule
// 7c  both players missing is the second case, not the first
```

- example 8. write the winner into the next match
- main path first. edges after
- match room_2 points at next
- the parent fills a, then b

```ts
type Match = { id: string; a?: string; b?: string; winner?: string; next?: string };
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
winnerOf(map, "room_2", "a");
```

- homework
```ts
// 8a  winner "s_9" moves into the parent
// 8b  the laytime test for 7500 exists before a pause rule
// 8c  both players missing is the second case, not the first
```

- example 9. write the winner into the next match
- main path first. edges after
- match vs_7 points at next
- the parent fills a, then b

```ts
type Match = { id: string; a?: string; b?: string; winner?: string; next?: string };
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
winnerOf(map, "vs_7", "a");
```

- homework
```ts
// 9a  winner "North Wind" moves into the parent
// 9b  the laytime test for 7500 exists before a pause rule
// 9c  both players missing is the second case, not the first
```

- example 10. write the winner into the next match
- main path first. edges after
- match sc_3 points at next
- the parent fills a, then b

```ts
type Match = { id: string; a?: string; b?: string; winner?: string; next?: string };
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
winnerOf(map, "sc_3", "a");
```

- homework
```ts
// 10a  winner "11" moves into the parent
// 10b  the laytime test for 7500 exists before a pause rule
// 10c  both players missing is the second case, not the first
```

- example 11. write the winner into the next match
- main path first. edges after
- match tm_2 points at next
- the parent fills a, then b

```ts
type Match = { id: string; a?: string; b?: string; winner?: string; next?: string };
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
winnerOf(map, "tm_2", "a");
```

- homework
```ts
// 11a  winner "Blue" moves into the parent
// 11b  the laytime test for 7500 exists before a pause rule
// 11c  both players missing is the second case, not the first
```

- example 12. write the winner into the next match
- main path first. edges after
- match up_6 points at next
- the parent fills a, then b

```ts
type Match = { id: string; a?: string; b?: string; winner?: string; next?: string };
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
winnerOf(map, "up_6", "a");
```

- homework
```ts
// 12a  winner "videos/u_1/a.mp4" moves into the parent
// 12b  the laytime test for 7500 exists before a pause rule
// 12c  both players missing is the second case, not the first
```

- example 13. write the winner into the next match
- main path first. edges after
- match st_1 points at next
- the parent fills a, then b

```ts
type Match = { id: string; a?: string; b?: string; winner?: string; next?: string };
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
winnerOf(map, "st_1", "a");
```

- homework
```ts
// 13a  winner "player_a" moves into the parent
// 13b  the laytime test for 7500 exists before a pause rule
// 13c  both players missing is the second case, not the first
```

- example 14. write the winner into the next match
- main path first. edges after
- match n_2 points at next
- the parent fills a, then b

```ts
type Match = { id: string; a?: string; b?: string; winner?: string; next?: string };
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
winnerOf(map, "n_2", "a");
```

- homework
```ts
// 14a  winner "Chattogram" moves into the parent
// 14b  the laytime test for 7500 exists before a pause rule
// 14c  both players missing is the second case, not the first
```

- example 15. write the winner into the next match
- main path first. edges after
- match b_3 points at next
- the parent fills a, then b

```ts
type Match = { id: string; a?: string; b?: string; winner?: string; next?: string };
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
winnerOf(map, "b_3", "a");
```

- homework
```ts
// 15a  winner "semi" moves into the parent
// 15b  the laytime test for 7500 exists before a pause rule
// 15c  both players missing is the second case, not the first
```

- example 16. write the winner into the next match
- main path first. edges after
- match se_1 points at next
- the parent fills a, then b

```ts
type Match = { id: string; a?: string; b?: string; winner?: string; next?: string };
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
winnerOf(map, "se_1", "a");
```

- homework
```ts
// 16a  winner "u_3" moves into the parent
// 16b  the laytime test for 7500 exists before a pause rule
// 16c  both players missing is the second case, not the first
```

- example 17. write the winner into the next match
- main path first. edges after
- match q_1 points at next
- the parent fills a, then b

```ts
type Match = { id: string; a?: string; b?: string; winner?: string; next?: string };
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
winnerOf(map, "q_1", "a");
```

- homework
```ts
// 17a  winner "laytime" moves into the parent
// 17b  the laytime test for 7500 exists before a pause rule
// 17c  both players missing is the second case, not the first
```

- example 18. write the winner into the next match
- main path first. edges after
- match r_1 points at next
- the parent fills a, then b

```ts
type Match = { id: string; a?: string; b?: string; winner?: string; next?: string };
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
winnerOf(map, "r_1", "a");
```

- homework
```ts
// 18a  winner "operator" moves into the parent
// 18b  the laytime test for 7500 exists before a pause rule
// 18c  both players missing is the second case, not the first
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

- example 1. controller, service, store for pc_12
- already played is a state check, not a class hierarchy
- save is one transaction so the match and the parent commit together

```ts
async function record(store: { load(id: string): Promise<Map<string, any>>; save(m: Map<string, any>): Promise<void> }) {
  const matches = await store.load("pc_12");
  const match = matches.get("pc_12");
  if (!match) throw new Error("missing");
  if (match.winner) throw new Error("already played");
  match.winner = "Ocean Star";
  await store.save(matches);
}
```

- homework
```ts
// 1a  missing pc_12 throws missing
// 1b  a second call throws already played
// 1c  save is a transaction
// 1d  UML: Match 1 to 0..1 next Match
```

- example 2. controller, service, store for m_1
- already played is a state check, not a class hierarchy
- save is one transaction so the match and the parent commit together

```ts
async function record(store: { load(id: string): Promise<Map<string, any>>; save(m: Map<string, any>): Promise<void> }) {
  const matches = await store.load("m_1");
  const match = matches.get("m_1");
  if (!match) throw new Error("missing");
  if (match.winner) throw new Error("already played");
  match.winner = "Ada";
  await store.save(matches);
}
```

- homework
```ts
// 2a  missing m_1 throws missing
// 2b  a second call throws already played
// 2c  save is a transaction
// 2d  UML: Match 1 to 0..1 next Match
```

- example 3. controller, service, store for t_9
- already played is a state check, not a class hierarchy
- save is one transaction so the match and the parent commit together

```ts
async function record(store: { load(id: string): Promise<Map<string, any>>; save(m: Map<string, any>): Promise<void> }) {
  const matches = await store.load("t_9");
  const match = matches.get("t_9");
  if (!match) throw new Error("missing");
  if (match.winner) throw new Error("already played");
  match.winner = "Rajshahi Open";
  await store.save(matches);
}
```

- homework
```ts
// 3a  missing t_9 throws missing
// 3b  a second call throws already played
// 3c  save is a transaction
// 3d  UML: Match 1 to 0..1 next Match
```

- example 4. controller, service, store for v_4
- already played is a state check, not a class hierarchy
- save is one transaction so the match and the parent commit together

```ts
async function record(store: { load(id: string): Promise<Map<string, any>>; save(m: Map<string, any>): Promise<void> }) {
  const matches = await store.load("v_4");
  const match = matches.get("v_4");
  if (!match) throw new Error("missing");
  if (match.winner) throw new Error("already played");
  match.winner = "Episode 1";
  await store.save(matches);
}
```

- homework
```ts
// 4a  missing v_4 throws missing
// 4b  a second call throws already played
// 4c  save is a transaction
// 4d  UML: Match 1 to 0..1 next Match
```

- example 5. controller, service, store for f_2
- already played is a state check, not a class hierarchy
- save is one transaction so the match and the parent commit together

```ts
async function record(store: { load(id: string): Promise<Map<string, any>>; save(m: Map<string, any>): Promise<void> }) {
  const matches = await store.load("f_2");
  const match = matches.get("f_2");
  if (!match) throw new Error("missing");
  if (match.winner) throw new Error("already played");
  match.winner = "NOR";
  await store.save(matches);
}
```

- homework
```ts
// 5a  missing f_2 throws missing
// 5b  a second call throws already played
// 5c  save is a transaction
// 5d  UML: Match 1 to 0..1 next Match
```

- example 6. controller, service, store for u_3
- already played is a state check, not a class hierarchy
- save is one transaction so the match and the parent commit together

```ts
async function record(store: { load(id: string): Promise<Map<string, any>>; save(m: Map<string, any>): Promise<void> }) {
  const matches = await store.load("u_3");
  const match = matches.get("u_3");
  if (!match) throw new Error("missing");
  if (match.winner) throw new Error("already played");
  match.winner = "a@example.com";
  await store.save(matches);
}
```

- homework
```ts
// 6a  missing u_3 throws missing
// 6b  a second call throws already played
// 6c  save is a transaction
// 6d  UML: Match 1 to 0..1 next Match
```

- example 7. controller, service, store for pay_8
- already played is a state check, not a class hierarchy
- save is one transaction so the match and the parent commit together

```ts
async function record(store: { load(id: string): Promise<Map<string, any>>; save(m: Map<string, any>): Promise<void> }) {
  const matches = await store.load("pay_8");
  const match = matches.get("pay_8");
  if (!match) throw new Error("missing");
  if (match.winner) throw new Error("already played");
  match.winner = "evt_1";
  await store.save(matches);
}
```

- homework
```ts
// 7a  missing pay_8 throws missing
// 7b  a second call throws already played
// 7c  save is a transaction
// 7d  UML: Match 1 to 0..1 next Match
```

- example 8. controller, service, store for room_2
- already played is a state check, not a class hierarchy
- save is one transaction so the match and the parent commit together

```ts
async function record(store: { load(id: string): Promise<Map<string, any>>; save(m: Map<string, any>): Promise<void> }) {
  const matches = await store.load("room_2");
  const match = matches.get("room_2");
  if (!match) throw new Error("missing");
  if (match.winner) throw new Error("already played");
  match.winner = "s_9";
  await store.save(matches);
}
```

- homework
```ts
// 8a  missing room_2 throws missing
// 8b  a second call throws already played
// 8c  save is a transaction
// 8d  UML: Match 1 to 0..1 next Match
```

- example 9. controller, service, store for vs_7
- already played is a state check, not a class hierarchy
- save is one transaction so the match and the parent commit together

```ts
async function record(store: { load(id: string): Promise<Map<string, any>>; save(m: Map<string, any>): Promise<void> }) {
  const matches = await store.load("vs_7");
  const match = matches.get("vs_7");
  if (!match) throw new Error("missing");
  if (match.winner) throw new Error("already played");
  match.winner = "North Wind";
  await store.save(matches);
}
```

- homework
```ts
// 9a  missing vs_7 throws missing
// 9b  a second call throws already played
// 9c  save is a transaction
// 9d  UML: Match 1 to 0..1 next Match
```

- example 10. controller, service, store for sc_3
- already played is a state check, not a class hierarchy
- save is one transaction so the match and the parent commit together

```ts
async function record(store: { load(id: string): Promise<Map<string, any>>; save(m: Map<string, any>): Promise<void> }) {
  const matches = await store.load("sc_3");
  const match = matches.get("sc_3");
  if (!match) throw new Error("missing");
  if (match.winner) throw new Error("already played");
  match.winner = "11";
  await store.save(matches);
}
```

- homework
```ts
// 10a  missing sc_3 throws missing
// 10b  a second call throws already played
// 10c  save is a transaction
// 10d  UML: Match 1 to 0..1 next Match
```

- example 11. controller, service, store for tm_2
- already played is a state check, not a class hierarchy
- save is one transaction so the match and the parent commit together

```ts
async function record(store: { load(id: string): Promise<Map<string, any>>; save(m: Map<string, any>): Promise<void> }) {
  const matches = await store.load("tm_2");
  const match = matches.get("tm_2");
  if (!match) throw new Error("missing");
  if (match.winner) throw new Error("already played");
  match.winner = "Blue";
  await store.save(matches);
}
```

- homework
```ts
// 11a  missing tm_2 throws missing
// 11b  a second call throws already played
// 11c  save is a transaction
// 11d  UML: Match 1 to 0..1 next Match
```

- example 12. controller, service, store for up_6
- already played is a state check, not a class hierarchy
- save is one transaction so the match and the parent commit together

```ts
async function record(store: { load(id: string): Promise<Map<string, any>>; save(m: Map<string, any>): Promise<void> }) {
  const matches = await store.load("up_6");
  const match = matches.get("up_6");
  if (!match) throw new Error("missing");
  if (match.winner) throw new Error("already played");
  match.winner = "videos/u_1/a.mp4";
  await store.save(matches);
}
```

- homework
```ts
// 12a  missing up_6 throws missing
// 12b  a second call throws already played
// 12c  save is a transaction
// 12d  UML: Match 1 to 0..1 next Match
```

- example 13. controller, service, store for st_1
- already played is a state check, not a class hierarchy
- save is one transaction so the match and the parent commit together

```ts
async function record(store: { load(id: string): Promise<Map<string, any>>; save(m: Map<string, any>): Promise<void> }) {
  const matches = await store.load("st_1");
  const match = matches.get("st_1");
  if (!match) throw new Error("missing");
  if (match.winner) throw new Error("already played");
  match.winner = "player_a";
  await store.save(matches);
}
```

- homework
```ts
// 13a  missing st_1 throws missing
// 13b  a second call throws already played
// 13c  save is a transaction
// 13d  UML: Match 1 to 0..1 next Match
```

- example 14. controller, service, store for n_2
- already played is a state check, not a class hierarchy
- save is one transaction so the match and the parent commit together

```ts
async function record(store: { load(id: string): Promise<Map<string, any>>; save(m: Map<string, any>): Promise<void> }) {
  const matches = await store.load("n_2");
  const match = matches.get("n_2");
  if (!match) throw new Error("missing");
  if (match.winner) throw new Error("already played");
  match.winner = "Chattogram";
  await store.save(matches);
}
```

- homework
```ts
// 14a  missing n_2 throws missing
// 14b  a second call throws already played
// 14c  save is a transaction
// 14d  UML: Match 1 to 0..1 next Match
```

- example 15. controller, service, store for b_3
- already played is a state check, not a class hierarchy
- save is one transaction so the match and the parent commit together

```ts
async function record(store: { load(id: string): Promise<Map<string, any>>; save(m: Map<string, any>): Promise<void> }) {
  const matches = await store.load("b_3");
  const match = matches.get("b_3");
  if (!match) throw new Error("missing");
  if (match.winner) throw new Error("already played");
  match.winner = "semi";
  await store.save(matches);
}
```

- homework
```ts
// 15a  missing b_3 throws missing
// 15b  a second call throws already played
// 15c  save is a transaction
// 15d  UML: Match 1 to 0..1 next Match
```

- example 16. controller, service, store for se_1
- already played is a state check, not a class hierarchy
- save is one transaction so the match and the parent commit together

```ts
async function record(store: { load(id: string): Promise<Map<string, any>>; save(m: Map<string, any>): Promise<void> }) {
  const matches = await store.load("se_1");
  const match = matches.get("se_1");
  if (!match) throw new Error("missing");
  if (match.winner) throw new Error("already played");
  match.winner = "u_3";
  await store.save(matches);
}
```

- homework
```ts
// 16a  missing se_1 throws missing
// 16b  a second call throws already played
// 16c  save is a transaction
// 16d  UML: Match 1 to 0..1 next Match
```

- example 17. controller, service, store for q_1
- already played is a state check, not a class hierarchy
- save is one transaction so the match and the parent commit together

```ts
async function record(store: { load(id: string): Promise<Map<string, any>>; save(m: Map<string, any>): Promise<void> }) {
  const matches = await store.load("q_1");
  const match = matches.get("q_1");
  if (!match) throw new Error("missing");
  if (match.winner) throw new Error("already played");
  match.winner = "laytime";
  await store.save(matches);
}
```

- homework
```ts
// 17a  missing q_1 throws missing
// 17b  a second call throws already played
// 17c  save is a transaction
// 17d  UML: Match 1 to 0..1 next Match
```

- example 18. controller, service, store for r_1
- already played is a state check, not a class hierarchy
- save is one transaction so the match and the parent commit together

```ts
async function record(store: { load(id: string): Promise<Map<string, any>>; save(m: Map<string, any>): Promise<void> }) {
  const matches = await store.load("r_1");
  const match = matches.get("r_1");
  if (!match) throw new Error("missing");
  if (match.winner) throw new Error("already played");
  match.winner = "operator";
  await store.save(matches);
}
```

- homework
```ts
// 18a  missing r_1 throws missing
// 18b  a second call throws already played
// 18c  save is a transaction
// 18d  UML: Match 1 to 0..1 next Match
```

- example 19. controller, service, store for pc_12
- already played is a state check, not a class hierarchy
- save is one transaction so the match and the parent commit together

```ts
async function record(store: { load(id: string): Promise<Map<string, any>>; save(m: Map<string, any>): Promise<void> }) {
  const matches = await store.load("pc_12");
  const match = matches.get("pc_12");
  if (!match) throw new Error("missing");
  if (match.winner) throw new Error("already played");
  match.winner = "Ocean Star";
  await store.save(matches);
}
```

- homework
```ts
// 19a  missing pc_12 throws missing
// 19b  a second call throws already played
// 19c  save is a transaction
// 19d  UML: Match 1 to 0..1 next Match
```

- example 20. controller, service, store for m_1
- already played is a state check, not a class hierarchy
- save is one transaction so the match and the parent commit together

```ts
async function record(store: { load(id: string): Promise<Map<string, any>>; save(m: Map<string, any>): Promise<void> }) {
  const matches = await store.load("m_1");
  const match = matches.get("m_1");
  if (!match) throw new Error("missing");
  if (match.winner) throw new Error("already played");
  match.winner = "Ada";
  await store.save(matches);
}
```

- homework
```ts
// 20a  missing m_1 throws missing
// 20b  a second call throws already played
// 20c  save is a transaction
// 20d  UML: Match 1 to 0..1 next Match
```

- example 21. controller, service, store for t_9
- already played is a state check, not a class hierarchy
- save is one transaction so the match and the parent commit together

```ts
async function record(store: { load(id: string): Promise<Map<string, any>>; save(m: Map<string, any>): Promise<void> }) {
  const matches = await store.load("t_9");
  const match = matches.get("t_9");
  if (!match) throw new Error("missing");
  if (match.winner) throw new Error("already played");
  match.winner = "Rajshahi Open";
  await store.save(matches);
}
```

- homework
```ts
// 21a  missing t_9 throws missing
// 21b  a second call throws already played
// 21c  save is a transaction
// 21d  UML: Match 1 to 0..1 next Match
```

- example 22. controller, service, store for v_4
- already played is a state check, not a class hierarchy
- save is one transaction so the match and the parent commit together

```ts
async function record(store: { load(id: string): Promise<Map<string, any>>; save(m: Map<string, any>): Promise<void> }) {
  const matches = await store.load("v_4");
  const match = matches.get("v_4");
  if (!match) throw new Error("missing");
  if (match.winner) throw new Error("already played");
  match.winner = "Episode 1";
  await store.save(matches);
}
```

- homework
```ts
// 22a  missing v_4 throws missing
// 22b  a second call throws already played
// 22c  save is a transaction
// 22d  UML: Match 1 to 0..1 next Match
```

- example 23. controller, service, store for f_2
- already played is a state check, not a class hierarchy
- save is one transaction so the match and the parent commit together

```ts
async function record(store: { load(id: string): Promise<Map<string, any>>; save(m: Map<string, any>): Promise<void> }) {
  const matches = await store.load("f_2");
  const match = matches.get("f_2");
  if (!match) throw new Error("missing");
  if (match.winner) throw new Error("already played");
  match.winner = "NOR";
  await store.save(matches);
}
```

- homework
```ts
// 23a  missing f_2 throws missing
// 23b  a second call throws already played
// 23c  save is a transaction
// 23d  UML: Match 1 to 0..1 next Match
```

- example 24. controller, service, store for u_3
- already played is a state check, not a class hierarchy
- save is one transaction so the match and the parent commit together

```ts
async function record(store: { load(id: string): Promise<Map<string, any>>; save(m: Map<string, any>): Promise<void> }) {
  const matches = await store.load("u_3");
  const match = matches.get("u_3");
  if (!match) throw new Error("missing");
  if (match.winner) throw new Error("already played");
  match.winner = "a@example.com";
  await store.save(matches);
}
```

- homework
```ts
// 24a  missing u_3 throws missing
// 24b  a second call throws already played
// 24c  save is a transaction
// 24d  UML: Match 1 to 0..1 next Match
```

- example 25. controller, service, store for pay_8
- already played is a state check, not a class hierarchy
- save is one transaction so the match and the parent commit together

```ts
async function record(store: { load(id: string): Promise<Map<string, any>>; save(m: Map<string, any>): Promise<void> }) {
  const matches = await store.load("pay_8");
  const match = matches.get("pay_8");
  if (!match) throw new Error("missing");
  if (match.winner) throw new Error("already played");
  match.winner = "evt_1";
  await store.save(matches);
}
```

- homework
```ts
// 25a  missing pay_8 throws missing
// 25b  a second call throws already played
// 25c  save is a transaction
// 25d  UML: Match 1 to 0..1 next Match
```

- example 26. controller, service, store for room_2
- already played is a state check, not a class hierarchy
- save is one transaction so the match and the parent commit together

```ts
async function record(store: { load(id: string): Promise<Map<string, any>>; save(m: Map<string, any>): Promise<void> }) {
  const matches = await store.load("room_2");
  const match = matches.get("room_2");
  if (!match) throw new Error("missing");
  if (match.winner) throw new Error("already played");
  match.winner = "s_9";
  await store.save(matches);
}
```

- homework
```ts
// 26a  missing room_2 throws missing
// 26b  a second call throws already played
// 26c  save is a transaction
// 26d  UML: Match 1 to 0..1 next Match
```

- example 27. controller, service, store for vs_7
- already played is a state check, not a class hierarchy
- save is one transaction so the match and the parent commit together

```ts
async function record(store: { load(id: string): Promise<Map<string, any>>; save(m: Map<string, any>): Promise<void> }) {
  const matches = await store.load("vs_7");
  const match = matches.get("vs_7");
  if (!match) throw new Error("missing");
  if (match.winner) throw new Error("already played");
  match.winner = "North Wind";
  await store.save(matches);
}
```

- homework
```ts
// 27a  missing vs_7 throws missing
// 27b  a second call throws already played
// 27c  save is a transaction
// 27d  UML: Match 1 to 0..1 next Match
```

- example 28. controller, service, store for sc_3
- already played is a state check, not a class hierarchy
- save is one transaction so the match and the parent commit together

```ts
async function record(store: { load(id: string): Promise<Map<string, any>>; save(m: Map<string, any>): Promise<void> }) {
  const matches = await store.load("sc_3");
  const match = matches.get("sc_3");
  if (!match) throw new Error("missing");
  if (match.winner) throw new Error("already played");
  match.winner = "11";
  await store.save(matches);
}
```

- homework
```ts
// 28a  missing sc_3 throws missing
// 28b  a second call throws already played
// 28c  save is a transaction
// 28d  UML: Match 1 to 0..1 next Match
```

- example 29. controller, service, store for tm_2
- already played is a state check, not a class hierarchy
- save is one transaction so the match and the parent commit together

```ts
async function record(store: { load(id: string): Promise<Map<string, any>>; save(m: Map<string, any>): Promise<void> }) {
  const matches = await store.load("tm_2");
  const match = matches.get("tm_2");
  if (!match) throw new Error("missing");
  if (match.winner) throw new Error("already played");
  match.winner = "Blue";
  await store.save(matches);
}
```

- homework
```ts
// 29a  missing tm_2 throws missing
// 29b  a second call throws already played
// 29c  save is a transaction
// 29d  UML: Match 1 to 0..1 next Match
```

- example 30. controller, service, store for up_6
- already played is a state check, not a class hierarchy
- save is one transaction so the match and the parent commit together

```ts
async function record(store: { load(id: string): Promise<Map<string, any>>; save(m: Map<string, any>): Promise<void> }) {
  const matches = await store.load("up_6");
  const match = matches.get("up_6");
  if (!match) throw new Error("missing");
  if (match.winner) throw new Error("already played");
  match.winner = "videos/u_1/a.mp4";
  await store.save(matches);
}
```

- homework
```ts
// 30a  missing up_6 throws missing
// 30b  a second call throws already played
// 30c  save is a transaction
// 30d  UML: Match 1 to 0..1 next Match
```

- example 31. controller, service, store for st_1
- already played is a state check, not a class hierarchy
- save is one transaction so the match and the parent commit together

```ts
async function record(store: { load(id: string): Promise<Map<string, any>>; save(m: Map<string, any>): Promise<void> }) {
  const matches = await store.load("st_1");
  const match = matches.get("st_1");
  if (!match) throw new Error("missing");
  if (match.winner) throw new Error("already played");
  match.winner = "player_a";
  await store.save(matches);
}
```

- homework
```ts
// 31a  missing st_1 throws missing
// 31b  a second call throws already played
// 31c  save is a transaction
// 31d  UML: Match 1 to 0..1 next Match
```

- example 32. controller, service, store for n_2
- already played is a state check, not a class hierarchy
- save is one transaction so the match and the parent commit together

```ts
async function record(store: { load(id: string): Promise<Map<string, any>>; save(m: Map<string, any>): Promise<void> }) {
  const matches = await store.load("n_2");
  const match = matches.get("n_2");
  if (!match) throw new Error("missing");
  if (match.winner) throw new Error("already played");
  match.winner = "Chattogram";
  await store.save(matches);
}
```

- homework
```ts
// 32a  missing n_2 throws missing
// 32b  a second call throws already played
// 32c  save is a transaction
// 32d  UML: Match 1 to 0..1 next Match
```

- example 33. controller, service, store for b_3
- already played is a state check, not a class hierarchy
- save is one transaction so the match and the parent commit together

```ts
async function record(store: { load(id: string): Promise<Map<string, any>>; save(m: Map<string, any>): Promise<void> }) {
  const matches = await store.load("b_3");
  const match = matches.get("b_3");
  if (!match) throw new Error("missing");
  if (match.winner) throw new Error("already played");
  match.winner = "semi";
  await store.save(matches);
}
```

- homework
```ts
// 33a  missing b_3 throws missing
// 33b  a second call throws already played
// 33c  save is a transaction
// 33d  UML: Match 1 to 0..1 next Match
```

- example 34. controller, service, store for se_1
- already played is a state check, not a class hierarchy
- save is one transaction so the match and the parent commit together

```ts
async function record(store: { load(id: string): Promise<Map<string, any>>; save(m: Map<string, any>): Promise<void> }) {
  const matches = await store.load("se_1");
  const match = matches.get("se_1");
  if (!match) throw new Error("missing");
  if (match.winner) throw new Error("already played");
  match.winner = "u_3";
  await store.save(matches);
}
```

- homework
```ts
// 34a  missing se_1 throws missing
// 34b  a second call throws already played
// 34c  save is a transaction
// 34d  UML: Match 1 to 0..1 next Match
```

- example 35. controller, service, store for q_1
- already played is a state check, not a class hierarchy
- save is one transaction so the match and the parent commit together

```ts
async function record(store: { load(id: string): Promise<Map<string, any>>; save(m: Map<string, any>): Promise<void> }) {
  const matches = await store.load("q_1");
  const match = matches.get("q_1");
  if (!match) throw new Error("missing");
  if (match.winner) throw new Error("already played");
  match.winner = "laytime";
  await store.save(matches);
}
```

- homework
```ts
// 35a  missing q_1 throws missing
// 35b  a second call throws already played
// 35c  save is a transaction
// 35d  UML: Match 1 to 0..1 next Match
```

- example 36. controller, service, store for r_1
- already played is a state check, not a class hierarchy
- save is one transaction so the match and the parent commit together

```ts
async function record(store: { load(id: string): Promise<Map<string, any>>; save(m: Map<string, any>): Promise<void> }) {
  const matches = await store.load("r_1");
  const match = matches.get("r_1");
  if (!match) throw new Error("missing");
  if (match.winner) throw new Error("already played");
  match.winner = "operator";
  await store.save(matches);
}
```

- homework
```ts
// 36a  missing r_1 throws missing
// 36b  a second call throws already played
// 36c  save is a transaction
// 36d  UML: Match 1 to 0..1 next Match
```
