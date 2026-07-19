# Proposal: a semantic verse block for Markdown

## Problem

Markdown has no dedicated block-level representation for verse: poetry, song lyrics, hymns, psalms, dramatic verse, and related line-structured forms.

Common workarounds have drawbacks:

- block quotations have quotation semantics;
- hard line breaks made with trailing spaces are invisible and fragile;
- fenced code blocks preserve layout but identify the content as code or code-like text;
- raw HTML is verbose and reduces portability;
- Pandoc line blocks require a `|` marker on every authored line.

Verse can also occur inside ordinary prose, including novels, essays, criticism, biographies, manuals, and educational material. It needs a way to remain structurally distinct without being represented as source code.

## Semantic requirements

A verse block should:

1. identify one complete verse passage;
2. preserve every authored line boundary;
3. treat a blank line as a stanza boundary;
4. preserve intentional leading and repeated internal spaces;
5. allow ordinary inline emphasis where supported;
6. remain independent of any required visual presentation.

## Prototype notation

The demo currently uses:

````markdown
```verse
This is the first line.
This is the second line.

This is another stanza.
```
````

This deliberately reuses fenced code-block notation as an immediately implementable extension convention. Under CommonMark it is still a code block, so this notation should not be understood as settled or normative.

## Illustrative HTML

One possible representation is:

```html
<div class="verse">
  <p class="stanza">
    <span class="vline">This is the first line.</span>
    <span class="vline">This is the second line.</span>
  </p>
  <p class="stanza">
    <span class="vline">This is another stanza.</span>
  </p>
</div>
```

The exact HTML is open to discussion. What matters is that the document model retains passage, stanza, and line structure.

## Related approaches

### Pandoc line blocks

Pandoc preserves line boundaries, leading spaces, and inline formatting with a `|` marker on every line. This is established prior art and solves much of the structural problem. The remaining authoring concern is the repeated per-line marker, especially in long poems and lyrics.

### Directive-style blocks

A possible alternative is a named block such as:

```markdown
::: verse
First line.
Second line.
:::
```

This visually separates semantic containers from code fences, but directives are not currently part of CommonMark and a verse directive would still need explicit rules for line breaks, indentation, and inline parsing.

## Non-goals

The proposal does not require:

- optical centering;
- a particular font or alignment;
- hanging indentation;
- a single HTML vocabulary;
- the prototype delimiter to become standard syntax.

These are renderer and stylesheet decisions. The proposal concerns the preservation and identification of verse structure.

## Open question

What block notation best fits the Markdown ecosystem while remaining comfortable for writers and preserving authored line and stanza boundaries without code semantics?
