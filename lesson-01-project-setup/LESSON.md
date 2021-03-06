## Project Setup

The goal of this section is to get to know your tools.

### Intro

TypeScript is "JavaScript with syntax for types" as [described on the official website](https://www.typescriptlang.org/). The fastest way to use it is online with the TypeScript Playground: https://www.typescriptlang.org/play

But since we're going to mimic using TS in real-life by building a real project, you'll want to know how to use it in your local development environment.

The first tool we need is the TypeScript compiler. You can install it globally as a dependency, or you can simply install it in a throwaway folder:

```shell
# With npm, globally
npm install -g typescript

# With yarn, globally
yarn global add typescript

# With npm, locally
npm install -D typescript

# With yarn, locally
yarn add -D typescript
```

We'll also be taking advantage of the included compiler CLI, `tsc`. For instance, run `yarn tsc --init` to create a basic `tsconfig.json` if you went with the local project route or `tsc --init` if you installed it globally.

Enough chatting though, let's give you a challenge to get your IDE ready for TypeScript'ing!

### Challenge

Set up your IDE for TypeScript development. Here are some guides for you to follow depending on what you use:

- VS Code: built-in
- JetBrains: built-in
- Sublime: [Getting started with TypeScript and Sublime Text](https://cmatskas.com/getting-started-with-typescript-and-sublime-text/)
- Vim: [Setting Up Vim For TypeScript in 2020](https://www.vimfromscratch.com/articles/setting-up-vim-for-typescript)
- Emacs: [Setting up emacs for typescript development](https://willschenk.com/articles/2021/setting_up_emacs_for_typescript_development/)

### Solution

To check that you've completed the challenge, follow these steps:

1. Create a file called `hello.ts`
2. Add the following code:

```typescript
function greet(name: string): string {
  return `Hello, ${name}!`
}

greet()
```

If you have your editor set up correctly, you should have some feedback (i.e. red squiggly line under `greet`) letting you know you forgot to pass an argument of type `string` to `greet()`.

#### Extra Credit

Research other plugins or extensions that people recommend for TypeScript development in your IDE. Be prepared to share with the group after!
