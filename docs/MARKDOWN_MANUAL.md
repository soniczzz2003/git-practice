# Markdown Manual

Markdown is a lightweight markup language for formatting plain text. It's used in READMEs, documentation, issues, and comments across GitHub, GitLab, and many static site generators. This manual covers core Markdown plus common GitHub Flavored Markdown (GFM) extensions.

## Headings

Use one to six `#` characters at the start of a line for headings level 1 through 6.

```
# Heading 1
## Heading 2
### Heading 3
#### Heading 4
##### Heading 5
###### Heading 6
```

## Paragraphs

Separate paragraphs with one blank line. No special markers are needed.

```
This is the first paragraph.

This is the second paragraph.
```

## Line Breaks

End a line with two or more spaces to insert a single line break (`<br>`). Otherwise, lines within a paragraph wrap together.

```
This line ends with two spaces.  
This text appears on the next line but in the same paragraph.
```

## Emphasis

**Bold** with `**` or `__`, *italic* with `*` or `_`, **_bold + italic_** by combining, and ~~strikethrough~~ with `~~` (GFM).

```
**bold text**
__bold text__
*italic text_
_italic text_
**_bold and italic_**
*__bold and italic__*
~~strikethrough text~~
```

## Links

Inline links use link text in brackets followed by the URL in parentheses. Reference-style links define the URL elsewhere. Autolinks wrap a URL in angle brackets. Email links use `mailto:`.

```
[inline link](https://example.com)

[reference link][example-ref]

<https://example.com>

<mailto:user@example.com>

[example-ref]: https://example.com "Optional title"
```

## Images

Images use the same syntax as links but start with `!`. The alt text goes in brackets and the image URL in parentheses.

```
![Alt text](https://example.com/image.png)

![Alt text](https://example.com/image.png "Optional title")

![Alt text][image-ref]

[image-ref]: https://example.com/image.png
```

## Code

Inline code uses backticks. Fenced code blocks use triple backticks with an optional language for syntax highlighting. Indented code blocks use four spaces or one tab per line.

```
`inline code here`

```javascript
const greeting = "Hello, world!";
console.log(greeting);
```

    indented code block
    with four spaces
```

## Lists

### Unordered

Use `-`, `*`, or `+` as list markers.

```
- Item one
- Item two
- Item three
```

### Ordered

Use numbers followed by a period.

```
1. First item
2. Second item
3. Third item
```

### Task lists

Add `[ ]` or `[x]` after the list marker for checkable items (GFM).

```
- [ ] Unchecked task
- [x] Checked task
- [ ] Another unchecked task
```

### Nested lists

Indent child items by two spaces under a parent item.

```
- Parent item
  - Child item one
  - Child item two
- Another parent
```

## Blockquotes

Prefix lines with `>` for blockquotes. Nest with multiple `>` characters.

```
> This is a blockquote.

> Nested blockquote
> > Nested deeper
```

## Horizontal Rules

Use `---`, `***`, or `___` on a line by itself.

```
---

***

___
```

## Tables

Tables use pipes `|` to separate columns and a separator row with dashes. Align columns with colons in the separator row.

```
| Column 1 | Column 2 | Column 3 |
|----------|----------|----------|
| Value 1  | Value 2  | Value 3  |
| Value 4  | Value 5  | Value 6  |

| Left     | Center   | Right    |
|:---------|:--------:|---------:|
| text     | text     | text     |
| more     | more     | more     |
```

## YAML Frontmatter

YAML frontmatter is a metadata block at the very top of a file, wrapped in `---` delimiters. Repo notes use it for title, tags, and dates. This manual itself does not use frontmatter.

```
---
title: My Document
tags: [markdown, guide]
date: 2026-10-28
---

Content starts here.
```

## Alert Blocks

GFM alert blocks use `>` followed by an alert type in brackets. Supported types include `NOTE`, `TIP`, `IMPORTANT`, `WARNING`, and `CAUTION`.

```
> [!NOTE]
> Useful supplementary information.

> [!TIP]
> Helpful advice for getting things done.

> [!IMPORTANT]
> Key information users should know.

> [!WARNING]
> Critical info requiring immediate attention.

> [!CAUTION]
> Negative potential consequences of an action.
```

## Quick Reference

| Element | Syntax | Example |
|---------|--------|---------|
| Heading 1 | `# text` | `# Title` |
| Bold | `**text**` | `**bold**` |
| Italic | `*text*` | `*italic*` |
| Strikethrough | `~~text~~` | `~~deleted~~` |
| Inline link | `[text](url)` | `[example](https://example.com)` |
| Autolink | `<url>` | `<https://example.com>` |
| Image | `![alt](url)` | `![img](pic.png)` |
| Inline code | `` `code` `` | `` `code` `` |
| Fenced code | ` ```lang ` | ` ```js ` |
| Unordered list | `- item` | `- apples` |
| Ordered list | `1. item` | `1. first` |
| Task list | `- [ ] item` | `- [ ] todo` |
| Blockquote | `> text` | `> quote` |
| Horizontal rule | `---` | `---` |
| Table | `\| col \| col \|` | `\| a \| b \|` |
| Frontmatter | `---\nyaml\n---` | `---\ntitle: x\n---` |
| Alert | `> [!TYPE]` | `> [!NOTE]` |
