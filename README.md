# Conventions, Standards and Guidelines

<p>
  <a href="https://github.com/acfatah/conventions-standards-and-guidelines/commits/main">
    <img
      alt="GitHub last commit (by committer)"
      src="https://img.shields.io/github/last-commit/acfatah/conventions-standards-and-guidelines?display_timestamp=committer&style=flat-square"></a>
</p>

This repository contains a comprehensive set of conventions, standards and
guidelines that I have been using across numerous projects mainly in `TypeScript`
and `Vue`.

These are not strict rules but rather guidelines to help me write better code.
In certain cases, some guidelines may be broken. They may also change over time
based on trends, tools, platforms, or technologies.

<!-- TOC -->

- [Conventions, Standards and Guidelines](#conventions-standards-and-guidelines)
    - [Introduction](#introduction)
        - [Purpose](#purpose)
    - [Pillars of Quality Code](#pillars-of-quality-code)
        - [Readability](#readability)
        - [Reusability](#reusability)
        - [Refactorability Maintainability](#refactorability-maintainability)
        - [Reliability](#reliability)
        - [Efficiency](#efficiency)
    - [Core Programming Concepts](#core-programming-concepts)
        - [SOLID Principles](#solid-principles)
        - [Component-based Architecture](#component-based-architecture)
    - [General Principle](#general-principle)
        - [File Naming](#file-naming)
        - [Directory Structure](#directory-structure)
        - [Variable and Function Naming](#variable-and-function-naming)
        - [Function or Method Best Practices](#function-or-method-best-practices)
    - [RESTful API](#restful-api)
    - [Formatting and Styling](#formatting-and-styling)
    - [ECMA Script 6 ES6 or Javascript and Nodejs](#ecma-script-6-es6-or-javascript-and-nodejs)
        - [Path](#path)
    - [Vuejs Includes HTML and CSS](#vuejs-includes-html-and-css)
    - [Tooling, IDE Extensions and Configurations](#tooling-ide-extensions-and-configurations)
        - [Setting Up Linter and Formatter](#setting-up-linter-and-formatter)
    - [Software Versioning and Version Control](#software-versioning-and-version-control)
    - [Conclusion](#conclusion)
    - [Further Readings and Referrences](#further-readings-and-referrences)

<!-- /TOC -->


<!-- vscode-markdown-toc-config
	numbering=false
	autoSave=true
	/vscode-markdown-toc-config -->
<!-- /vscode-markdown-toc -->

## <a name='Introduction'></a>Introduction

These conventions aim to promote code readability, consistency, and maintainability.
They serve as a guide, not a set of strict rules, for writing clean and efficient code, enabling seamless collaboration among developers.

### Purpose

The purpose of having coding conventions, standards, and guidelines is to:

- Provide a uniform appearance to code written by different programmers and across different platforms.
- Improve code readability and maintainability while reducing complexity.
- Facilitate code reuse and make it easier to detect errors.
- Promote sound programming practices and increase programmer efficiency.

Everything should be **done automatically** without any mental cognitive load. Nowadays,
we can take advantage of tools such as linters, formatters, or AI to handle these things. Read more in the
[tooling section](#tooling) to learn how to set it up.

## <a name='PillarsofQualityCode'></a>Pillars of Quality Code

Five pillars of quality code are:

1. **Readability**
2. **Reusability**
3. **Refactorability (Maintainability)**
4. **Reliability**
5. **Efficiency**

### <a name='Readability'></a>Readability

Readability refers to how easily other developers (or even your future self) can
understand the code. Code that is easy to read reduces the time required to grasp
its functionality and logic.

Best Practices:

- **Clear Naming Conventions**: Use meaningful variable, function, and class
names that convey intent.

  - Use **camelCase** for variable and function names.
  - Use **PascalCase** for type and class names.
  - Use **SNAKE_CASE** for constant names.

- **Consistent Formatting**: Follow a consistent style guide for indentation,
spacing, and braces.

- **Commenting and Documentation**: Provide comments only where necessary that
explains "why". Focus more on writing self-explanatory code.

- **Avoid Deep Nesting**: Limit the levels of indentation to maximum of two to make
code more accessible and easier to follow. Use [guard clause](https://en.wikipedia.org/wiki/Guard_(computer_science)) to reduce number of
nesting.

### <a name='Reusability'></a>Reusability

Reusability is the ease with which code components can be used across different
parts of the application or even in different projects. Reusability allows us to
express new ideas with little pieces of the past.

Writing reusable code helps reduce redundancy and promotes consistency.

Best Practices:

- **Modular Design**: Break down functionality into small, self-contained modules
or functions that can be easily reused.

- **DRY Principle (Don’t Repeat Yourself)**: Extract common functionality that are repeated three times or more into
reusable utility functions or classes.

- **Parameterization**: Write functions and methods that are flexible through the
use of parameters, allowing them to handle various use cases.

- **Use of Libraries**: Where applicable, use well-established libraries or frameworks
that provide reusable functions or components.

Code should **NOT** be reusable when,

- If you can't define a good API yet, don't create a separate module . Duplication
is better than a bad foundation.

- The function or module are not expected to be reused in the near future.

- The duplication is **NOT** more than two. (See *Rule of Three* below)

### <a name='RefactorabilityMaintainability'></a>Refactorability (Maintainability)

Refactorability is the ease with which code can be improved, modified, or extended
without introducing defects. This pillar focuses on the long-term maintainability
of the codebase.

Things that we can do to make our code refactorable:

- Isolated side effects
- Tests
- Static types
- Rule of Three

A side effect occurs when a function or module modifies data outside its own scope,
for example, writing data to a disk, changing a global variable, or printing
something to the terminal.

A program consists of instructions that a computer executes to take data in and produce
data out. If a program has no side effects, it's essentially a black box.

While side effects are necessary to make a program useful (since it has to modify
something in the outside world), they should be carefully isolated.

Side effects make code hard to test because if a function's execution modifies
some data that another function depends on, we can't be certain that the function will
always produce the same output given the same input.

Side effects also introduce coupling between otherwise reusable modules. If module
A modifies global state that module B depends on, then A must be executed before B.

Side effects make systems unpredictable. If any function or module can manipulate
the application's state, it becomes difficult to predict how changing one part will
affect the entire system.

**To manage side effects**, isolate them by creating a centralized location to update the
global state of your application.

**The Rule of Three**:
Don't refactor code until it's been duplicated at least twice. The first instance is
acceptable, the second time you might copy, but by the third occurrence, it's time to refactor.
This approach helps avoid premature optimization and unnecessary abstraction.

**Best Practices:**
- **Loose Coupling**: Design components to be independent of each other so that changes
  in one area don't ripple through the entire codebase.
- **High Cohesion**: Group related functionality together, ensuring that each
  module or class has a clear, singular purpose.
- **Code Smells**: Regularly check for and refactor code to eliminate code smells such
  as long methods, large classes, and unnecessary complexity.
- **Version Control**: Use systems like Git to track changes and facilitate collaboration
  and refactoring.
- **Rule of Three**: Apply refactoring when the same logic or code is duplicated
  three times, ensuring patterns are worth abstracting without premature optimization.

### <a name='Reliability'></a>Reliability

Reliability is the degree to which code functions correctly and consistently under
expected conditions. Reliable code is robust and handles edge cases, errors, and
unexpected inputs gracefully.

Best Practices:

- **Error Handling**: Implement comprehensive error handling to manage exceptions
and unexpected situations without crashing.

- **Unit Testing**: Write unit tests to ensure that individual parts of the code
work as expected.

- **Integration Testing**: Use integration tests to verify that different modules
or services interact correctly.

- **Input Validation**: Always validate inputs to ensure they meet the expected
criteria before processing.

### <a name='Efficiency'></a>Efficiency

Efficiency refers to the optimization of code in terms of performance and resource
utilization. Efficient code executes quickly and uses minimal resources, such as
CPU, memory, and network bandwidth.

Best Practices:

- **Optimized Algorithms**: Choose or develop algorithms that are efficient in terms
of time and space complexity.

- **Lazy Loading**: Load resources only when they are needed to reduce initial load
time and memory usage.

- **Tree Shaking**: Remove unused code from the bundle. Code that is not imported or
used is not included in the final bundle, resulting in a smaller codebase.

- **Caching**: Implement caching strategies to store frequently accessed data, reducing
the need for repeated computations or database queries.

- **Profiling and Optimization**: Regularly profile the application to identify
and optimize performance bottlenecks.

## <a name='CoreProgrammingConcepts'></a>Core Programming Concepts

### <a name='solid-principles'></a>SOLID Principles

TBD

### <a name='Component-basedArchitecture'></a>Component-based Architecture

Think of a component as a Lego block.

You can choose various shapes, sizes, and colors when building a structure out of Legos. Some blocks are purpose-built to be doors, windows, and other structural elements. Each block has all the features it needs to connect to others, and adding or subtracting blocks generally has minimal impact on the structure.

5 features of components
Software components have five common characteristics;

1. **Reusability**: Components plug into a variety of applications without the need for modification or special accommodations.

2. **Extensibility**: Components combine with other components to create new behaviors.

3. **Replaceability**: Components with similar functionality can be swapped.

4. **Encapsulation**: Components are self-contained and expose functionality through interfaces while hiding the details of internal processes.

5. **Independence**: Components have minimal dependencies on other components and can operate in different environments and contexts.


## <a name='GeneralPrinciple'></a>General Principle

### <a name='FileNaming'></a>File Naming

- Use `kebab-case` for file names
- Use `LF` instead of ~~`CRLF`~~ for line ending

### <a name='directory-structure'></a>Directory Structure

- Directory name should already convey the files within.

Common directory names are:
  - **apps**: if a project have more than one applications (e.g: client, server, web, etc),
    we group them under `apps` and uses workspace to manage them
  - **bin**: contains executable binary files or programs
  - **config**: contains the application configuration files
  - **data**: contains hard-coded data files in various format such as csv, json,
    etc that are loaded at runtime
  - **dist**: contains compiled source and ready to be released, ignored by git
  - **docs**: contains the source documentations
  - **logs**: contain log files, ignored by git
  - **public**: contains static files and commonly served by http server
  - **res** or **resources**: contains all the non-code resources
  - **scripts**: contains scripts files
  - **src**: contains the application source files that are going to be compiled
  - **temp**: contains temporary files, ignored by git
  - **test**: contains the application tests such as unit tests, integration tests, etc
  - **uploads**: contains uploaded files, ignored by git
  - **vendor**: contains third-party libraries

Some common directory names specifically for web applications are:
  - **src/assets**: similar to `res`
  - **src/composables** or **src/hooks**: contains the application hooks (in Vue, it's commonly known as composables)
  - **src/components**: contains the application components
  - **src/lib**: contains the application libraries
  - **src/pages**: contains the application pages or views
  - **src/router** or **src/routes**: contains the application router or routes
  - **src/services**: contains the application services
  - **src/store**: contains the application store
  - **src/utils**: contains the application utils

### <a name='VariableandFunctionNaming'></a>Variable and Function Naming

1. **Readable and Searchable Names**
   - Use clear, descriptive names that make the code easy to understand and maintain.
   - Avoid abbreviations unless they are widely recognized (e.g., `id` for identifier).
   - Names should be meaningful and reflect the purpose or role of the variable.
   - Consistent across the entire codebase.

2. **Capitalization Conventions**
   - **Constants**: Use `UPPER_CASE_SNAKE_CASE` for constants (e.g., `MAX_RETRY_ATTEMPTS`).
   - **Variables**: Use `camelCase` for regular variables (e.g., `userName`, `totalAmount`).
   - **Class Names**: Use `PascalCase` for class names (e.g., `UserAccount`, `OrderProcessor`).
   - **Functions/Methods**: Name functions or methods as verbs using `camelCase` (e.g., `calculateTotal`, `fetchData`).

3. **Pluralization**
   - If a variable holds a collection (e.g., an array or a map), use the plural form of the noun (e.g., `users`, `productList`).
   - For a Boolean, prefix with `is`, `has`, or `should` (e.g., `isValid`, `hasPermission`, `shouldUpdate`).

4. **Contextual Clarity**
   - Avoid overly generic names like `data`, `item`, or `obj`. Add context to the name to clarify its use (e.g., `userData` instead of `data`).
   - Use descriptive names for temporary variables in loop and indices. **Avoid** `i`, `j`, `k`.

5. **Avoid Magic Numbers**
   - Replace magic numbers with named constants to improve readability (e.g., `const MAX_ITEMS_PER_PAGE = 10`).

6. **Avoid Hungarian Notation**
   - Do not prefix variable names with data types (e.g., avoid `strName`, `intCount`). Rely on TypeScript or other type-checking tools if needed.

7. **Avoid Reserved Words**
   - Do not use JavaScript reserved words for variable names (e.g., `class`, `enum`, `default`).


### <a name='FunctionorMethodBestPractices'></a>Function or Method Best Practices

- A function or method should do ONE thing, and ONE thing only.

- Guard Clause, don't write `else` unless it is a middleware.

- Consider extracting nested logic into separate functions. More than two levels of nesting can imply poor performance (in a loop), and it can be especially hard to read in long conditionals.

- **Limit Number of Function Arguments**
    - Limit number of arguments between 1-3.
    - 0 arguments implies side effect.

- **Use Underscore for Private or Unused Variables**
   - When dealing with private variables (especially in classes or modules), prefix them with an underscore (e.g., `_privateData`).

   - When defining a function that receives arguments, but some of them are not used, prefix the unused ones with an underscore.

     ```javascript
     function handleClick(event, _elementId) {
       // The `event` argument is used, but `_elementId` is not.
       console.log('Button clicked')
       // No use of `_elementId`
     }
     ```

   - When arrow Functions have unused arguments,

     ```javascript
     const numbers = [1, 2, 3]

     // We only care about the index, not the value.
     numbers.forEach((_value, index) => {
        console.log(index); // Outputs: 0, 1, 2
     })
     ```

   - When destructuring an array,

     ```javascript
     const colors = ['red', 'green', 'blue']

     // Destructure the array, but only the second element is used.
     const [_firstColor, secondColor, _thirdColor] = colors
     ```

## <a name='RESTfulAPI'></a>RESTful API

Please refer to [Rapid API Learning](https://rapidapi.com/learn/rest) for
comprehensive information about RESTful API.

## <a name='FormattingandStyling'></a>Formatting and Styling

Formatting and styling should be done automatically using linter. See Tooling
section for more information how to set it up.

- Use **spaces** instead of **tabs** for indentation. Use two spaces to indent.
- Separate programming logic or contexts using a new line.
- Add a new line before `return` statement.
- Add an empty line before the end of file. Use `LF` for file ending.

## <a name='ECMAScript6ES6orJavascriptandNodejs'></a>ECMA Script 6 (ES6) or Javascript and Nodejs

### <a name='Path'></a>Path

- Use relative path when related to browser so it can be imported using
  either npm, cdn link or importmap.
- Include file extension on file path when import a file, unless to an `index.js`<br>
  `import { formatDate } from 'src/utils/format-date.js'`<br>
  `import { formatDate } from 'src/utils   // utils directory has index.js`

## <a name='VuejsIncludesHTMLandCSS'></a>Vuejs (Includes HTML and CSS)

Tailwindcss principles and style guides:

- [eslint-plugin-better-tailwindcss](https://github.com/schoero/eslint-plugin-better-tailwindcss)

## <a name='ToolingIDEExtensionsandConfigurations'></a>Tooling, IDE Extensions and Configurations

Currently I'm using [eslint](https://eslint.org) (without Prettier) to lint and format my code following the antfu/eslint-config configuration. Folowing the link below for more information.

- [antfu/eslint-config](https://github.com/antfu/eslint-config)

By using pre-commit hooks, we can automatically lint and guard our code from code smells before committing. Currently using [simple-git-hooks](https://github.com/indrajeetmishra/simple-git-hooks).

### <a name='SettingUpLinter'></a>Setting Up Linter and Formatter

- Install the [ESLint extension](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint) for vscode.
- Install the `@commitlint/cli` and `@commitlint/config-conventional` packages.
- Install the [simple-git-hooks](https://github.com/indrajeetmishra/simple-git-hooks). Need to run `npx simple-git-hooks` to initialize it and update configuration.
  ```
  "commitlint": {
    "extends": [
      "@commitlint/config-conventional"
    ]
  },
  "simple-git-hooks": {
    "pre-commit": "npm run precommit",
    "commit-msg": "npm run commitlint --edit ${1}"
  }
  ```

## <a name='VersionControl'></a>Software Versioning and Version Control

Follow the conventional versioning systems:

- [Semantic Versioning](https://semver.org)
- [Calendar Versioning](https://calver.org)

Use [conventional commit](https://www.conventionalcommits.org) to write commit message. The advantage is that we can use tools like [changelogithub](https://github.com/antfu/changelogithub) to generate changelog based on commit messages.

## <a name='Conclusion'></a>Conclusion

TBD

## <a name='FurtherReadingsandReferrences'></a>Further Readings and Referrences

- https://en.wikipedia.org/wiki/Coding_conventions
- https://github.com/ryanmcdermott/clean-code-javascript
- https://github.com/ryanmcdermott/3rs-of-software-architecture
- https://github.com/antfu/eslint-config
- https://eslint.org/
- https://conventionalcommits.org/
- https://semver.org/
- https://keepachangelog.com/
- https://rapidapi.com/learn/rest
