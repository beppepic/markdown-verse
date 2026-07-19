# Example corpus

The demo opens with all examples visible. Each example exercises a different aspect of the proposed verse model.

## Prose and verse

Shows a verse passage embedded between ordinary paragraphs. This is the central semantic example: the passage is neither source code nor necessarily a block quotation.

The three verse lines are from Walt Whitman's *Song of Myself* (1892 version), section 1.

## Regular verse

William Shakespeare, *Sonnet 18*. Tests regular line lengths, multiple stanzas, and a final couplet.

## Free verse

Walt Whitman, *Song of Myself* (1892 version), section 1. Tests naturally long lines and uneven stanza lengths without altering the original lineation.

## Short lines

An original synthetic poem arranged as three two-line stanzas. Tests a narrow optically centered block.

## Intentional whitespace

An original regression fixture with five leading spaces, repeated internal spaces, and an indented stanza opening.

## Dante

Dante Alighieri, *Inferno*, Canto I. Tests authentic Italian verse and stanza preservation.

## Renderer stress test

An original synthetic fixture containing:

- a very short line;
- a normal line;
- a long line that fits;
- an overlong wrapping line;
- leading spaces;
- repeated internal spaces;
- an unbreakable token;
- a final normal line.

## Rights note

Shakespeare, Whitman, and Dante are in the public domain. The remaining fixtures were written specifically for this prototype. No complete twentieth-century poem is included in the public demo.
