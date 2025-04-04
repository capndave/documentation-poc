## SQL

- Use single quotes instead of double quotes in stored procedures and views

## Application Performance (API and UI)

- When dependencies are used in only a few files, look for opportunities to migrate off of those dependencies
- Fewer lines of code are better than many lines of code
- Review code that uses loops to ensure that we aren't looping or performing more computation than necessary
- Keep dependency libraries up-to-date. This ensures that the latest fixes for performance, security, and compatibility are used in your project.

## Application Load Times (API and UI)

- When dependencies are used in only a few files, look for opportunities to migrate off of those dependencies
- Replace old library methods with built-in language features when they exist. Jquery and lodash, for example, were extremely popular JavaScriot libraries which are often no longer needed, because similar methods now exist natively in JavaScript. Similarly, it's permissable to use the native JavaScript fetch API instead of rest-call and the get, post , etc methods that were written in our UI projects.

## Code Readability

- Ensure that your editor is configured to use a linter. If you use the Cursor editor (recommended) or VSCode, most of this work is already done for you. Otherwise you will need to set up linting and code hints for yourself. If using Cursor or VSCode, look for a `.vscode/extensions.json` file in your repository. If it exists, install the browser extensions listed in it. Linting and code hints should then be enabled during local development
- Follow the KISS principle - Keep it Stupidly Simple. It should be easy to read your code and understand what it’s doing.
- Refactor often so that your code is as simple as possible. Don’t be afraid of refactoring or changing code, especially if you can also write tests for it. Refactoring code to make functions [pure](https://medium.com/javascript-scene/master-the-javascript-interview-what-is-a-pure-function-d1c076bec976) and responsible for only one task makes them both easier to reason about and to test.
- Move duplicate code into a shared location to reduce the total number of lines in a particular file. Strive for legibility and performance - it is not _always_ a good idea to reuse every possible line of code.
- Code should be self-documenting. Name a function that herds cats `herdCats` instead of something more verbose. Name a variable that is an array of cats, call it `cats` instead of `c`, `animalArray`, or anything else that is not obvious/descriptive.
- Break up large functions into smaller subcomponents. Let’s say you have a large function called `processCats` that herds cats (including getting a stick, running around, yelling, etc), cuts their hair (including buying clippers, holding each cat down, etc), and takes them to a cat show (including registering each cat in the cats array, putting gas in the truck, etc), consider changing the below:

```javascript 
function processCats()
    for (cat of cats) {
        const location = getLocation(cat.location)
        const stick = getStick()
        herdCatsStep1(stick, location)
        herdCatsStep2(stick, location)
        …lots of other steps
}
```
to
```
function processCats() {
    for (cat of cats) {
        herd(cat)
        cutHair(cat)
        show(cat)
    }
}
```
...where the `herd`, `cutHair`, and `show` functions are similarly simple.
- Use types when possible. This improves code hints in modern editors like Cursor and VSCode, so Engineers can look at the editor and understand quickly that a certain thing is an array, complex object, string, etc, without having to track down its definition in our code. Even without these editor-based tools, types in function declarations and elsewhere make it obvious what kind of data that function expects/requires. Types are native to Python, are implemented to some degree in our UI projects with `prop-types`, and can be extremely helpful if JavaScript files are replaced by TypeScript.

## UI / JavaScript

- Use JavaScript's [optional chaining](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Optional_chaining) to reduce code. Change `if (someThing && someThing.someProperty && someThing.someProperty.someSubProperty)...` to `if (someThing?.someProperty?.someSubProperty)...`
- Know the difference between [various types of loops](https://medium.com/@julienetienne/different-types-of-arrays-in-javascript-and-when-to-use-them-77f7843b71de) and array methods like [map](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Map), [reduce](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce), and [filter](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter). While you can often use multiple of these for a given task, selecting the most appropriate method will result in the simplest, minimal amount of code.

## API / Python

- Avoid using star imports so that Engineers know what is actually being used, and whether an import is necessary. Replace `from api.somePlace import *` with `from api.somePlace import thingYouNeed, anotherThingYouNeed`. 
- Use context managers when possible to silently do setup/teardown and to reduce the amount of code you see in a particular file. In particular, use the `SQLConnection` context manager in `serviceCommon` for DB operations.
- Prefer Python's `pathlib` over `sys` and `os` modules for most purposes




