# Semantic Verse in Markdown

This repository contains a small browser-based prototype exploring a semantic `verse` block for Markdown.

Verse depends on authored line and stanza boundaries. Existing workarounds preserve some of that structure, but often represent the text as code, require invisible trailing spaces, or add a marker to every line. The project asks whether poetry, lyrics, hymns, psalms, dramatic verse, and similar forms could have a clearer block-level representation.

## Live demo

Try the [live interactive demo](https://beppepic.github.io/markdown-verse/).

To run it locally, open [`index.html`](index.html) in a browser. The demo is self-contained and has no build step or external dependencies.

The source pane is editable. It includes examples of verse inside prose, regular and free verse, short lines, intentional whitespace, long-line wrapping, optical centering, and hanging indents.

## Prototype notation

The current prototype uses a fenced info-string convention:

````markdown
```verse
First line.
Second line.

Second stanza.
```
````

Under the current CommonMark specification, this remains a fenced code block. Here, `verse` is interpreted by the prototype as an extension marker. The delimiter is not the essential part of the proposal and may change.

Other relevant approaches include Pandoc line blocks and directive-style notation such as `::: verse`. The central question is independent of the final syntax: how should Markdown represent a whole verse passage while preserving its authored lines and stanzas without treating natural-language text as code?

## Status

This is an exploratory demo, not a complete Markdown parser and not a claim of CommonMark compatibility. Rendering choices such as optical centering and hanging indentation are optional presentation experiments, not proposed syntax rules.

Discussion:

- [CommonMark forum](https://talk.commonmark.org/t/semantic-block-for-poetry-lyrics-with-optical-alignment-the-longest-line-rule/9091)
- [CommonMark specification issue #838](https://github.com/commonmark/commonmark-spec/issues/838)
- [Pandoc line blocks](https://pandoc.org/MANUAL.html#line-blocks)

See [`proposal.md`](proposal.md) for the semantic proposal and [`technical-notes.md`](technical-notes.md) for implementation details and limitations.

## License

The prototype code and original documentation are available under the [MIT License](LICENSE). Literary excerpts in the demo are identified separately in [`examples.md`](examples.md).
