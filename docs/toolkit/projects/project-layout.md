---
title: Program File Structure
sidebarSortOrder: 8
sidebarLabel: Project layout
seoTitle: "How to structure a Solana program and repo"
description:
  "Best practices for Solana program repo and file structure when developing
  Solana programs"
keywords:
  - solana program development
  - program file structure
  - best practices
---

> This is a beta version of the [Solana Toolkit](/docs/toolkit/index.md), and is
> still a WIP. Please post all feedback as a GitHub issue
> [here](https://github.com/solana-foundation/developer-content/issues/new?title=%5Btoolkit%5D%20).

Typically Solana smart contracts (aka [programs](/docs/core/programs.md))
workspaces will be have the following file structure:

```shell
.
├── app
├── migrations
├── node_modules
├── programs
├── target
└── tests
```

The main program is the `lib.rs` file, which lives insides the `programs`
directory, as shown below:

```shell
.
├── app
├── migrations
├── node_modules
├── programs
    ├── src
        ├── lib.rs
├── target
└── tests
```

As the program gets more cumbersome, you'll typically want to separate the logic
into multiple files, as shown below:

```shell
├── programs
    ├── src
        ├── state.rs
        ├── instructions
            ├── instruction_1.rs
            ├── instruction_2.rs
            ├── instruction_3.rs
        ├── lib.rs
        ├── constants.rs
        ├── error.rs
        ├── mod.rs
```

For [native rust program development](/docs/programs/rust/index.md), you need to
explicitly write out the entrypoint and processor for the program, so you'll
need a few more files:

```shell
├── program.rs
│   ├── src.rs
│   │   ├──assertions.rs
│   │   ├──entrypoint.rs
│   │   ├──error.rs
│   │   ├──instruction.rs
│   │   ├──lib.rs
│   │   ├──processor.rs
│   │   ├──state.rs
│   │   ├──utils.rs
│   ├── Cargo.toml
│   ├── keypair.json
│   ├── README.md
```
