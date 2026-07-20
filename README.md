# Custom Lexical Analyzer (DFA)

This project implements a finite automaton designed to read text strings and classify them lexically. The program evaluates each input string (assuming it is followed by a whitespace) and determines whether it corresponds to a valid token, an identifier, a numeric constant, or if it contains a lexical error.

## Alphabet

The automaton operates strictly on the following set of characters (S):

`S = {a, f, i, n, p, t, u, z, 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, ., ;, *, +, <, &, =, (, ), {, }, ñ, _}`

## Transition Matrix

This repository also includes the **transition matrix** (state table) used with details of the state transitions and the core logic the DFA follows.

## Classification Rules

The program processes and classifies the input based on the following rules:

*   **Tokens (Keywords and Symbols):** Recognizes specific language structures and operators.
    *   *Keywords:* `int`, `input`, `if`
    *   *Operators and symbols:* `*`, `+`, `<`, `>`, `&&`, `(`, `)`, `{`, `}`, `]`, `;`
*   **Identifiers:** Valid sequences of letters from the alphabet (e.g., `paz`, `infuz`).
*   **Numeric Constants:** 
    *   Valid integers (e.g., `9456`).
    *   Well-formed decimals with a single decimal point (e.g., `94.45`).
*   **Invalid Strings (Errors):** Inputs that break formation rules or use illegal combinations, such as:
    *   Use of characters in non-permitted contexts (e.g., `infuñi`, `&_`).
    *   Numbers incorrectly combined with letters (e.g., `123abc`).
    *   Multiple decimal points (e.g., `94.15.12`).

## Test Cases

Examples of the expected behavior of the automaton with various inputs:

| Input String | Evaluation Result |
| :--- | :--- |
| `int` | Token |
| `input` | Token |
| `if` | Token |
| `paz` | Identifier |
| `infuz` | Identifier |
| `infuñi` | Invalid string |
| `123abc` | Invalid numeric string |
| `9456` | Numeric constant |
| `94.45` | Numeric constant |
| `94.15.12` | Invalid numeric string |
| `&&` | Token (Operator) |
| `&_` | Invalid string |
