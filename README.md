# PoC Typescript
Playground for learning about TypeScript

**Table of Contents**
- [General](#general)
- [TS from scratch](#ts-from-scratch)
- [Codely course: from JS to TS (2021)](#codely-course-from-js-to-ts-2021)
- [TypeScript for JS programmers](#typescript-for-js-programmers)
- [Pending readings](#pending-readings)
- [Currently reading](#currently-reading)
- [Already read](#already-read)
- [Interesting links](#interesting-links)


## General
- Developed by Microsoft
- Open-source: Apache License 2.0
- **First version: October 2012**
- Current version: [5.4.2](https://devblogs.microsoft.com/typescript/announcing-typescript-5-4/)
    - [TypeScript 5.5 Iteration Plan](https://github.com/microsoft/TypeScript/issues/57475)
- https://github.com/microsoft/TypeScript
    - [Good first issue](https://github.com/Microsoft/TypeScript/issues?q=is%3Aopen+is%3Aissue+label%3A%22help+wanted%22+label%3A%22Good+First+Issue%22)
- [Playground for TS](https://www.typescriptlang.org/play/)
- https://www.typescriptlang.org/
- [TypeScript Origins: The Documentary](https://www.youtube.com/watch?v=U6s2pdxebSo) - video, 80 minutes
- https://stateofjs.com/en-US
- https://en.wikipedia.org/wiki/TypeScript
- https://code.visualstudio.com/docs/typescript/typescript-tutorial
- TypeScript is a strongly typed programming language that builds on JavaScript
- TypeScript is a **strict superset of ECMAScript 2015**, which is itself a superset of ECMAScript 5, commonly referred to as JavaScript.
- The TypeScript compiler is itself written in TypeScript and compiled to JavaScript
- TypeScript supports definition files that can contain type information of existing JavaScript libraries, much like C++ header files can describe the structure of existing object files. 

## TS from scratch
- https://www.typescriptlang.org/docs/handbook/typescript-from-scratch.html
- TypeScript is a language that is a superset of JavaScript: JS syntax is therefore legal TS. Syntax refers to the way we write text to form a program.
- TypeScript is also a programming language that preserves the runtime behavior of JavaScript. 
    - This means that if you move code from JavaScript to TypeScript, it is **guaranteed** to run the same way.
- Roughly speaking, once TypeScript’s compiler is done with checking your code, **it erases the types** to produce the resulting "compiled" code. This means that once your code is compiled, the resulting plain JS code has no type information.
    - This also means that TypeScript never changes the behavior of your program based on the types it inferred
- TypeScript doesn’t provide any additional runtime libraries.


## Codely course: from JS to TS (2021)
- https://pro.codely.com/library/de-javascript-a-typescript-128106
    - @nuria_codes and @ismanapa
- https://github.com/CodelyTV/refactor-from-js-to-ts-course
-https://github.com/CodelyTV/typescript-basic-skeleton
- https://github.com/CodelyTV/refactor-from-js-to-ts-course
- Types do NOT exist in runtime.
    - e.g. el typeof de un objeto siempre será Object, no la interfaz que hemos definido.
- The [first step to add TS](https://github.com/CodelyTV/refactor-from-js-to-ts-course/tree/main/21-supporting-typescript) to a project is adding the file **tsconfig.json**
    - `npx tsc`
    - TS also does a downgrade
    - In Webpack we configure the ts-loader, extensions (e.g. adding ts), etc. []`webpack.common.js`](https://github.com/CodelyTV/refactor-from-js-to-ts-course/blob/main/21-supporting-typescript/webpack.common.js)
    - La opción `transpileOnly` nos permite compilar a pesar de que haya errores de TypeScript. Esto nos será útil en el proceso de refactor para poder seguir trabajando aunque haya errores de tipado.
- [Static type checking](https://github.com/CodelyTV/refactor-from-js-to-ts-course/tree/main/22-static-type-cheking)
- TS assigns a type to EVERYTHING even if we don't configure it explicitely.
- If TS can not infer a type, it will use `any`.
    - With ESLint we can mark `any` as warning instead of error, so that we can move on in baby steps with typing.
- We can type objects [using `interface`](https://github.com/CodelyTV/refactor-from-js-to-ts-course/tree/main/23-structural-typing)
- There are [interfaces specifically for the DOM](https://github.com/CodelyTV/refactor-from-js-to-ts-course/tree/main/31-dom-types)
    - `HTMLElementTagNameMap` can help us with the different DOM types (it maps HTML tags with interfaces)
- Las interfaces, igual que los prototipos de JavaScript, pueden tener herencia.
- **Union types**: a variable could be two or more types `Type1 | Type2 | Type3`
- `unknown` type:
    - [Code example](https://github.com/CodelyTV/refactor-from-js-to-ts-course/tree/main/33-unknown-type)
    - Added in TS 3.0 as a safe alternative to `any`
    - https://dmitripavlutin.com/typescript-unknown-vs-any/
- **Detecting errors in development time**
    - [Code example](https://github.com/CodelyTV/refactor-from-js-to-ts-course/tree/main/41-no-implicit-any)
    - [`strictChecks`](https://www.typescriptlang.org/tsconfig#strict)
        - https://www.carlrippon.com/controlling-type-checking-strictness-in-typescript/
        - `"noImplicitAny": true`: it forces us to define in an explicit way all the types from our code.
        - [No implicit any](https://www.typescriptlang.org/tsconfig#noImplicitAny)
    - `strictNullChecks`
        - `"strictNullChecks": true`:
        - [Code example](https://github.com/CodelyTV/refactor-from-js-to-ts-course/tree/main/42-strict-null-checks)
        - [Strict null checks](https://www.typescriptlang.org/tsconfig#strictNullChecks)
- **Using TS with external dependencies**
    - [Code example](https://github.com/CodelyTV/refactor-from-js-to-ts-course/tree/main/51-external-tool-types)
    - [Axios](https://github.com/axios/axios)
    - [Declaration files](https://github.com/axios/axios/blob/master/index.d.ts)
    - `"moduleResolution": "node"`, to define how we want to import external dependencies
    - [Open Source "Definitely Typed"](https://github.com/DefinitelyTyped/DefinitelyTyped): `d.ts`
    - Custom types: what to do when you use a library which does not have types?
        - [Code example for grade-js](https://github.com/CodelyTV/refactor-from-js-to-ts-course/tree/main/52-custom-lib-types)
        - We can either define from scratch a definition type or extend/fix an already existing one.
- **Testing and TypeScript**
    - [Code example](https://github.com/CodelyTV/refactor-from-js-to-ts-course/tree/main/53-testing-lib-types)
    - [ts-jest](https://github.com/kulshekhar/ts-jest)
    - For testing HTTP APIs: https://www.npmjs.com/package/supertest
    - Cypress:
        - It requires an extension to `tsconfig.json`
        - [Code example](https://github.com/CodelyTV/refactor-from-js-to-ts-course/tree/main/53-testing-lib-types)
        - https://docs.cypress.io/guides/tooling/typescript-support#Clashing-types-with-Jest
        - [Cypress and TS configuration](https://docs.cypress.io/guides/tooling/typescript-support#Configure-tsconfig-json)
- **React and TS**
    - [Code example](https://github.com/CodelyTV/refactor-from-js-to-ts-course/tree/main/71-react-frontend)
    - `npx create-react-app my-app --template typescript`
    - [React and TS](https://create-react-app.dev/docs/adding-typescript/)
    - [React TypeSript Cheatsheets](https://react-typescript-cheatsheet.netlify.app/)
    - Better not use CRA to start a new React app? Other options: [vite](https://carlosazaustre.es/react-vite)
    - Do NOT use [Function Components](https://react-typescript-cheatsheet.netlify.app/docs/basic/getting-started/function_components/)
- **Express API**
    - [Code example](https://github.com/CodelyTV/typescript-api-skeleton/blob/main/package.json#L8)
    - Deno directly works with TypeScript
- **Interfaces vs types**
    - https://www.typescriptlang.org/docs/handbook/2/everyday-types.html#differences-between-type-aliases-and-interfaces
        -  If you would like a heuristic, use `interface` until you need to use features from `type`.
        - A `type` cannot be re-opened to add new properties vs an `interface` which is always extendable.
    - [Code example](https://github.com/CodelyTV/refactor-from-js-to-ts-course/tree/main/81-types-vs-interfaces)
    - [Types vs Interfaces: What I Got Wrong In 2022](https://www.youtube.com/watch?v=e0AIkYrXAYE), 10 min. video
    - [Type vs Interface: Which Should You Use?](https://www.totaltypescript.com/type-vs-interface-which-should-you-use)
    - [interface vs type](https://pro.codely.tv/library/de-javascript-a-typescript-128106/347481/community/discussion/1788249/)
    - [Official documentation for Interfaces](https://www.typescriptlang.org/docs/handbook/interfaces.html)
    - [The Difference Between Type Aliases and Interfaces in TypeScript](https://blog.bitsrc.io/the-difference-between-type-aliases-and-interfaces-in-typescript-af5f34fe4309)
        - Type aliases are used to create new names for existing types, whereas interfaces are used to define the shape and behavior of an object.
    - [Playground example: Types vs Interfaces](https://www.typescriptlang.org/play/typescript/language-extensions/types-vs-interfaces.ts.html)
        - **We recommend you use interfaces over type aliases**. Specifically, because you will get better error messages
    - Both `implements` and `extends` can be done with both `types` and  `interfaces`
    - Things that can only be done with `types`, not with `interfaces`:
        - **Unions** 
        - Typing a Tuple
        - Typing a primitive
    - Things that can only be done with `interfaces`, not with `types`:
        - [Declaration merging](https://www.typescriptlang.org/docs/handbook/declaration-merging.html)
            - Use typescript-eslint `no-unsafe-declaration-merging"
    - Neither Interfaces nor Types exist when transpiling
        - The do not exist on runtime.
        - [Narrowing](https://www.typescriptlang.org/docs/handbook/2/narrowing.html) is a way to hack some things.
- **Experiences moving to TS**
    - https://dev.to/pincfloit/game-development-diary-v-moving-to-typescript-5a4k
    - Genially
        - Monorepo
        - Express with Responsibility Chain
        - ErrorHandlerMiddleware (catch exceptions - Domain, etc. - and return the corresponding HTTP Status codes, mesages, etc.)
        - Use of Sentry
        - Decorators in the Controllers, e.g. @Authorized() or @HttpCode(200)

    
## TypeScript for JS programmers
- https://www.typescriptlang.org/docs/handbook/typescript-in-5-minutes.html
- Visual Studio Code uses TypeScript under the hood to make it easier to work with JavaScript.
- You’ll see that there are two syntaxes for building types: Interfaces and Types. You should prefer interface. Use type when you need specific features.
- There is already a small set of primitive types available in JavaScript: boolean, bigint, null, number, string, symbol, and undefined, which you can use in an interface.
- One of TypeScript’s core principles is that type checking focuses on the shape that values have. This is sometimes called “duck typing” or “structural typing”.


## Pending readings
- [Slack: the transition from JS to TS](https://slack.engineering/typescript-at-slack/) - 2018
- [Everyday Types](https://www.typescriptlang.org/docs/handbook/2/everyday-types.html)
- https://react-typescript-cheatsheet.netlify.app/
- [TS Playground examples](https://www.typescriptlang.org/play?#code/PTAEHUFMBsGMHsC2lQBd5oBYoCoE8AHSAZVgCcBLA1UABWgEM8BzM+AVwDsATAGiwoBnUENANQAd0gAjQRVSQAUCEmYKsTKGYUAbpGF4OY0BoadYKdJMoL+gzAzIoz3UNEiPOofEVKVqAHSKymAAmkYI7NCuqGqcANag8ABmIjQUXrFOKBJMggBcISGgoAC0oACCbvCwDKgU8JkY7p7ehCTkVDQS2E6gnPCxGcwmZqDSTgzxxWWVoASMFmgYkAAeRJTInN3ymj4d-jSCeNsMq-wuoPaOltigAKoASgAywhK7SbGQZIIz5VWCFzSeCrZagNYbChbHaxUDcCjJZLfSDbExIAgUdxkUBIursJzCFJtXydajBBCcQQ0MwAUVWDEQC0gADVHBQGNJ3KAALygABEAAkYNAMOB4GRonzFBTBPB3AERcwABS0+mM9ysygc9wASmCKhwzQ8ZC8iHFzmB7BoXzcZmY7AYzEg-Fg0HUiQ58D0Ii8fLpDKZgj5SWxfPADlQAHJhAA5SASPlBFQAeS+ZHegmdWkgR1QjgUrmkeFATjNOmGWH0KAQiGhwkuNok4uiIgMHGxCyYrA4PCCJSAA)
- [JavaScript Module Cheatsheet](https://medium.com/dailyjs/javascript-module-cheatsheet-7bd474f1d829)

## Currently reading
- https://www.typescriptlang.org/docs/handbook/typescript-from-scratch.html


## How to migrate a project from JS to TS
- https://www.typescriptlang.org/docs/handbook/migrating-from-javascript.html
- https://pro.codely.com/library/de-javascript-a-typescript-128106/347481/path/step/131062671/
- https://github.com/CodelyTV/refactor-from-js-to-ts-course/tree/main/21-supporting-typescript
- https://www.digitalocean.com/community/tutorials/typescript-running-typescript-ts-node


## Interesting links
- [TSyringe: dependency injection](https://adrianferrera.dev/es/blog/tsyringe)
- [InversifyJS](https://github.com/inversify/InversifyJS): A powerful and lightweight inversion of control container for JavaScript & Node.js apps powered by TypeScript.
    - It uses constants to "hack" de fact that interfaces and types disappear after transpiling.
- [DIOD: Dependency Injection On Demand](https://github.com/artberri/diod): A very opinionated and lightweight (under 2kB minified and gzipped) inversion of control container and dependency injector for Node.js or browser apps.
    - It uses abstract classes to "hack" de fact that interfaces and types disappear after transpiling.
- [Branded Types in TypeScript](https://egghead.io/blog/using-branded-types-in-typescript)