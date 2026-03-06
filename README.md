# Multi-Sig Safe Core

A secure, flat-structure Multi-Signature wallet. This repository provides the logic for managing shared funds where no single individual has the authority to move assets.

## Core Mechanics
* **M-of-N Consensus**: Transactions require a predefined threshold of signatures to execute.
* **Proposal Lifecycle**: Owners submit a transaction, other owners "confirm" it, and once the threshold is met, any owner can execute.
* **Revocability**: Confirmations can be revoked before execution if an owner changes their mind.

## Security Features
* **Reentrancy Protection**: Guards against recursive calls during execution.
* **Owner Management**: The initial owner set is immutable in this version for maximum simplicity and security.

## How to Use
1. Deploy `MultiSigWallet.sol` with an array of owner addresses and the required number of confirmations.
2. Call `submitTransaction` to propose a spend.
3. Other owners call `confirmTransaction` using the `txIndex`.
4. Once `isConfirmed` is true, call `executeTransaction`.
