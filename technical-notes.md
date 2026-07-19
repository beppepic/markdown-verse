# Technical notes

## Scope

The demo in [`index.html`](index.html) is a self-contained visual prototype. Its parser recognizes only the subset of Markdown needed to demonstrate the proposed `verse` behavior. It must not be presented as a production parser or a full CommonMark implementation.

## Prototype parsing

The prototype recognizes an exact opening line of `` ```verse `` and a closing line of `` ``` ``. Within the block:

- a blank line starts a new stanza;
- every other newline creates a verse line;
- leading and repeated internal spaces are preserved;
- minimal inline parsing supports bold, emphasis, and inline code;
- an unclosed fence is handled without indexing beyond the document.

The renderer escapes `&`, `<`, and `>` before applying its small inline subset.

## Semantic DOM

The current DOM uses:

- one `.verse` container per passage;
- one paragraph `.stanza` per stanza;
- one `.vline` span per authored line.

This representation makes line and stanza boundaries available independently of styling.

## Whitespace

Verse lines use:

```css
white-space: pre-wrap;
overflow-wrap: anywhere;
word-break: normal;
```

The renderer does not call `.trim()` on verse lines. This is essential: trimming would destroy intentional indentation.

## Optical centering

The optional optical-centering experiment measures the natural width of every verse line and chooses the longest line that fits inside the current preview width. The verse block is sized to that reference and centered; exceptional longer lines wrap inside it.

This is a presentation heuristic, not part of the semantic proposal.

## Hanging indent

The optional hanging indent applies a negative first-line indent balanced by left padding. When an authored verse line wraps visually, its continuation is indented so it cannot easily be mistaken for a new authored line.

This is also a presentation choice, not syntax.

## Responsive behavior

Optical widths are recalculated after:

- source edits;
- example changes;
- presentation-control changes;
- viewport or preview resizing;
- font loading.

The demo uses `ResizeObserver` when available and falls back to the window resize event.

## Known limitations

The prototype does not implement:

- arbitrary fence lengths or tilde fences;
- the complete CommonMark inline grammar;
- nested block contexts;
- full list, quotation, HTML, or link parsing;
- directive-style or Pandoc line-block input;
- exact width measurement for every mixture of inline styles;
- a formal abstract syntax tree or non-HTML output.

These limitations are intentional. The artifact demonstrates the use case and rendering behavior, not a finished parser architecture.
