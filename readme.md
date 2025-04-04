SQL
- Use single quotes instead of double quotes in stored procedures and views

Reducing Application Load Times
- When dependencies are used in only a few files, look for opportunities to migrate off of those dependencies
- Replace old library methods with built-in language features when they exist. Jquery or lodash, for example, were extremely popular JavaScriot libraries which are often no longer needed, because similar methods now exist natively in JavaScript. Similarly, it's permissable to use the native JavaScript fetch module instead of rest-call and the get, post , etc methods that were written in our UI projects.

Code Readability
- Ensure that your editor is configured to use a linter. If you use the Cursor editor (recommended) or VSCode, most of this work is already done for you. Otherwise you will need to set up linting and code hints for yourself. If using Cursor or VSCode, look for a `.vscode/extensions.json` file in your repository. If it exists, install the browser extensions listed in it. Linting and code hints should then be enabled during local development
- Follow the KISS principle - Keep it Stupidly Simple. It should be easy to read your code and understand what it’s doing.
- Refactor often so that your code is as simple as possible. Don’t be afraid of refactoring or changing code, especially if you can also write tests for it.
- Code should be self-documenting. If you have a function that herds cats, call it `herdCats`. If you have a variable that is an array of cats, call it `cats`. Let’s say you have a large function called processCats that herds cats (including getting a stick, running around, yelling, etc), cuts their hair (including buying clippers, holding each cat down, etc), and takes them to a cat show (including registering each cat in the cats array, putting gas in the truck, etc), consider breaking the processCats function up like so: ``` function processCats() 
-     For (cat of cats) {
    - herd(cat)
    - cutHair(cat)
    - show(cat)
    - }
- }

Rather than 
- function processCats() 
-     For (cat of cats) {
        let location = getLocation(cat.location)
        Const stick = getStick()
        herdCatsStep1(stick, location)
 herdCatsStep2(stick, location)
 herdCatsStep3(stick, location)
…a million other steps
    - }
- }


UI
