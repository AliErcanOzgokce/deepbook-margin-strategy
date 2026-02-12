# Strategy Wrapper — DeepBook Composability POC

## Overview

This repository contains a focused Proof-of-Concept demonstrating composability between Suilend obligations and DeepBook margin pools.

The objective is to validate architectural feasibility of deploying borrowed liquidity from a Suilend obligation into DeepBook while preserving protocol isolation.

Importantly:

- The core Suilend protocol logic is untouched.
- No modifications were made to core accounting, health checks, or reserve logic.
- Integration is implemented strictly as a wrapper layer.

---

## Architectural Goals

This POC explores:

- Capability-based obligation ownership wrapping
- Relayer-restricted “hot potato” borrow/return pattern
- Controlled external capital deployment
- Minimal attack surface extension
- Clean composability boundaries

The DeepBook integration acts as an execution layer extension rather than a new strategy primitive.

---

## What This Demonstrates

- Borrowing from Suilend via wrapped obligation cap
- Supplying borrowed liquidity into DeepBook margin pool
- Withdrawing from DeepBook and repaying Suilend
- Maintaining version control and ownership safety
- No direct mutation of protocol-level invariants

---

## Deliberate Design Constraints

This POC intentionally:

- Does **not** introduce a new strategy type
- Does **not** modify health factor logic
- Does **not** add liquidation guards
- Does **not** implement production-grade risk management

These omissions are intentional to keep scope minimal and focused on composability validation.

---

## Production Considerations (Out of Scope)

A production implementation would require:

- Health factor-aware deployment guards
- Liquidation-aware DeepBook exposure tracking
- Borrow ceiling constraints
- Automated unwind mechanisms
- Oracle-aware margin exposure limits

These are explicitly excluded from this POC.

---

## Purpose

The purpose of this repository is to demonstrate:

- Protocol-level composability thinking
- Capability security modeling
- Safe extension design without invasive core modifications

This is a design validation artifact, not a protocol upgrade proposal.
