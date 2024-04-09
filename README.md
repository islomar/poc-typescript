# PoC Typescript
Playground for learning about TypeScript

## General
- https://github.com/microsoft/TypeScript
- [Playground for TS](https://www.typescriptlang.org/play/)
- https://www.typescriptlang.org/
- https://stateofjs.com/en-US
- https://en.wikipedia.org/wiki/TypeScript
- https://code.visualstudio.com/docs/typescript/typescript-tutorial
- Developed by Microsoft
- Open-source: Apache License 2.0
- **First version: October 2012**
- Current version: [5.4.2](https://devblogs.microsoft.com/typescript/announcing-typescript-5-4/)
    - [TypeScript 5.5 Iteration Plan](https://github.com/microsoft/TypeScript/issues/57475)
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
    

## Readings
- [Slack: the transition from JS to TS](https://slack.engineering/typescript-at-slack/) - 2018


## Currently reading
- https://www.typescriptlang.org/docs/handbook/typescript-from-scratch.html
- https://www.typescriptlang.org/docs/handbook/typescript-in-5-minutes.html


## Already read
- TBD