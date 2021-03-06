# Initializing a Streak Counter

The goal of this lesson is to write the logic to handle initializing a streak.

## Intro

Referencing our flow diagram, one of the parts of the flow is initializing the streak. This happens when a streak doesn't already exist.

One of the first TypeScript concepts we're going to discuss is one of the most common and frequently used, [Parameter Type Annotations](https://www.typescriptlang.org/docs/handbook/2/everyday-types.html#parameter-type-annotations). This is when you annotate function parameters. Here is a basic example from the docs:

```typescript
// `greet` is a function
// it takes one _parameter_ called `name`
// `name` is of type `string`
function greet(name: string) {
  console.log("Hello, " + name.toUpperCase() + "!!");
}
```

See how similar this is to JavaScript? The only difference is the `: string` used to annotate the type.

If you passed the wrong type, TypeScript would compile with an error:

```typescript
// Potential runtime error since .toUpperCase() doesn't exist on `number`
greet(42);
// Argument of type 'number' is not assignable to parameter of type 'string'.
```

The other thing I want to introduce you to is [Interfaces](https://www.typescriptlang.org/docs/handbook/2/everyday-types.html#interfaces). These are types for objects. See this example:

```typescript
// Taken straight from the TS docs
// Here we have an interface with two properties: x and y, both are which of type `number`
interface Point {
  x: number;
  y: number;
}

function printCoord(pt: Point) {
  console.log("The coordinate's x value is " + pt.x);
  console.log("The coordinate's y value is " + pt.y);
}

printCoord({ x: 100, y: 100 });
```

NOTE: later on you may hear talk about interfaces vs type aliases. Don't worry about that now, just keep it in mind for the future. If you're too eager to wait, read [this](https://www.typescriptlang.org/docs/handbook/2/everyday-types.html#differences-between-type-aliases-and-interfaces).

Great! We've discussed two basic concepts: parameter type annotations and interfaces. Let's put these to use and start working on our library!

### Challenge

Using TDD, start building the streak counter so that it initializes or returns a streak object.

You can copy these two files to get started:

```typescript
// File: src/index.ts
export function streakCounter(storage: Storage, date: Date) {
  return {};
}
```

```typescript
// File: __tests__/index.test.ts
import { JSDOM } from "jsdom";
import { streakCounter } from "../src/index";

export function formattedDate(date: Date): string {
  return date.toLocaleDateString("en-US");
}

describe("streakCounter", () => {
  let mockLocalStorage: Storage;

  beforeEach(() => {
    const mockJSDom = new JSDOM("", { url: "https://localhost" });

    mockLocalStorage = mockJSDom.window.localStorage;
  });

  it("should return a streak object with currentCount, startDate and lastLoginDate", () => {
    const date = new Date();
    const streak = streakCounter(mockLocalStorage, date);

    expect(streak.hasOwnProperty("currentCount")).toBe(true);
    expect(streak.hasOwnProperty("startDate")).toBe(true);
    expect(streak.hasOwnProperty("lastLoginDate")).toBe(true);
  });
  it("should return a streak starting at 1 and keep track of lastLoginDate", () => {
    const date = new Date();
    const streak = streakCounter(mockLocalStorage, date);

    const dateFormatted = formattedDate(date);

    expect(streak.currentCount).toBe(1);
    expect(streak.lastLoginDate).toBe(dateFormatted);
  });
});
```

**Don't forget to install `jsdom` and `@types/jsdom` as dev dependencies!**

Hints:

- Use this library for mocking `localStorage`: https://github.com/jsdom/jsdom
  - If you haven't worked with `localStorage` before, read more [here](https://developer.mozilla.org/en-US/docs/Web/API/Window/localStorage)
- If you get stuck, ask for help

NOTE: you might be wondering why we're not using `localStorage` yet in this lesson. Don't worry! We'll make use of it later. This just lays the groundwork for that.

### Solution

Here is what mine looks like: https://gist.github.com/jsjoeio/5ca8f8cc8b3135b95daba0d8f5869083

### Extra Credit

Imagine you're talking to a new JavaScript developer who is learning TypeScript. How would you explain _parameter type annotations_?
