# Rust Ethereum Virtual Machine (revm)

The `crate` is focused on the implementation of Ethereum Virtual Machine (EVM) including call loop and host implementation, database handling, state journaling and powerful logic handlers that can be overwritten. This crate pulls Primitives, Interpreter and Precompiles together to deliver the rust evm.

Starting point of the documentation should be a [`Evm`](./revm/evm.md) that is main structure of EVM. Then i would recommend reading about the `EvmBuilder` that is used to create the `Evm` and modify. After that you can read about the `Handler` that is used to modify the logic of the Evm and it will tie with how introspection of Evm can be done. And lastly you can read about the `Inspector` that is legacy interface for inspecting execution that is repurposed as one of example of handler registers.

Modules:
- `evm`: This is main module that executed EVM calls.
- `builder`: This modules build the Evm, sets database, handlers and other parameters. Here is where we set handlers for specific fork or external state for inspection.
- `db`: This module includes structures and functions for database interaction. It is a glue between EVM and database. It transforms or aggregates the EVM changes.
- `inspector`: This module introduces the `Inspector` trait and its implementations for observing the EVM execution. This was main way to inspect EVM execution before the Builder and Handlers were introduced. It is still enabled through the Builder.
- `journaled_state`: This module manages the state of the EVM and implements a journaling system to handle changes and reverts.

Re-exported Crates:

- `revm_precompile`: This crate is re-exported, providing the precompiled contracts used in the EVM implementation.
- `revm_interpreter`: This crate is re-exported, providing the execution engine for EVM opcodes.
- `revm_interpreter`::primitives: This module from the `revm_interpreter` crate is re-exported, providing primitive types or functionality used in the EVM implementation.

Re-exported Types:

- `Database`, `DatabaseCommit`, `InMemoryDB`: These types from the `db` module are re-exported for handling the database operations.
- `EVM`: The `EVM` struct from the `evm` module is re-exported, serving as the main interface to the EVM implementation.
- `EvmContext`: The `EvmContext` struct from the `evm_impl` module is re-exported, likely providing data structures to encapsulate EVM execution data.
- `JournalEntry`, `JournaledState`: These types from the `journaled_state` module are re-exported, providing the journaling system for the EVM state.
- `inspectors`, `Inspector`: The `Inspector` trait and its implementations from the `inspector` module are re-exported for observing the EVM execution.
