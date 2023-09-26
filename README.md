[English](./README.md)
---
**Overview
Rune balances are held by UTXOs. A UTXO can contain any amount of any number of runes.

A transaction contains a protocol message if it contains an output whose script pubkey contains an OP_RETURN followed by a data push of the ASCII uppercase letter R. The protocol message is all data pushes after the first.

Runes input to a transaction with an invalid protocol message are burned. This allows for future upgrades that change how runes are assigned or created from creating situations where old clients erroneously assign rune balances.

Integers are encoded as prefix varints, where the number of leading ones in a varint determines its length in bytes.

**Transfer
The first data push in a protocol message is decoded as a sequence integers.

These integers are interpreted as a sequence of (ID, OUTPUT, AMOUNT) tuples. If the number of decoded integers is not a multiple of three, the protocol message message is invalid.

ID is the numeric ID of the run to assign
OUTPUT is the index of the output to assign it to
AMOUNT is the amount of the run to assign
ID is encoded as a delta. This allows multiple assignments of the same rune to avoid repeating the full rune ID. For example, the tuples:

```[(100, 1, 20), (0, 2 10), (20, 1, 5)]```

Make the following assignments:

ID 100, output 1, 20 runes
ID 100, output 2, 10 runes
ID 120, output 1, 5 runes
The AMOUNT 0 is shorthand for "all remaining runes".

After processing all tuple assignments, any unassigned runes are assigned to the first non-OP_RETURN output, if any.

Excess assignments are ignored.

Runes may be burned by assigning them to the OP_RETURN output containing the protocol message.

**Issuance
If the protocol message has a second data push, it is an issuance transaction. The second data push is decoded as two integers, SYMBOL, DECIMALS. If additional integers remain, the protocol message is invalid.

An issuance transaction may create any amount, up to 2^128 - 1 of the issued rune, using the ID 0 in assignment tuples.

SYMBOL is a base 26-encoded human readable symbol, similar to that used in ordinal number sat names. The only valid characters are A through Z.

DECIMALS is the number of digits after the decimal point that should be used when displaying the issued rune.

If SYMBOL has not already been assigned, it is assigned to the issued rune, and the issued rune receives the next available numeric rune ID, starting at one.

If SYMBOL has already been assigned, or is BITCOIN, BTC, or XBT, then no new rune is created. Issuance transaction assignments using the 0 rune ID are ignored, but other assignments are still processed.
