---
title: Markdown Syntax Reference
tags: [ Markdown ]
---

## Markdown Syntax Reference

### Formating Text

Bold or italic text can be indicated using either asterisks or underscores (single for italic, doubled for bold). Strikethrough uses two tildes. The effects can be combined or nested within one paragraph.

|Markdown|Displayed Text|
|---|---|
|`*This text will be italic*`|*This text will be italic*
|`_This will also be italic_`|_This will also be italic_
|`**This text will be bold**`|**This text will be bold**
|`__This will also be bold__`|__This will also be bold__
|`*You ~~cannot~~ **can** combine them*`|*You ~~cannot~~ **can** combine them*



### Headers
Using a hash/pound symbol `#` at the start of a line defines a header. To create sub-headers, use multiple hash marks, `##`, then `###`, and so on...
> Example of header display styles:
> # Heading 1 (#)
> ## Heading 2 (##)
> ### Heading 3 (###)
> #### Heading 4 (####)
> ##### Heading 5 (#####)
> ###### Heading 6 (######)


### Highlighting Code

Inline highlighting of code can used for example to emphasise `keywords` in paragraphs or highlight small code blocks such as `my @args = @ARGV;`. To achive this use single backticks <code>`</code> to wrap a charector, word or string.

The SGML style `<code>` and `</code>` tags can also be used to highlight inline code. This can be convenient when needing to escape certain characters.

You can use three backticks <code>```</code> to mark the beginning and the end of a code block. For Example:

```
#include <stdio.h>

int main() {
  printf("Hello, World!");
  return 0;
}
```

Indenting the code block by four spaces will have the same effect.

Automatic syntax highlighting can be achieved by specifing the langugue after the three backticks:

```perl
# Perl Syntax
open(DATA, "<file.txt") or die "Couldn't open file file.txt, $!";

while(<DATA>) {
   print "$_";
}
```
```tcl
# TCL syntax
set fp [open "input.txt" w+]
puts $fp "test\ntest"
close $fp
set fp [open "input.txt" r]

while { [gets $fp data] >= 0 } {
   puts $data
}
close $fp
```

```python
# Python syntax
reader = open('myfile.txt', 'r')
data = reader.read()
reader.close()
print('file contains', len(data), 'bytes')
```

### Quoted Text
A single greater-than symbol `>` at the start of any paragraph will create a quote block.  

> "An unattributed quote is not a citation."

There is no standard way to include attribution in a quote block but the follow style:

```
>"some text....."
>
> \<div style="text-align: right">*Author*</div>;
```

...will produce a good starting point:

>A hundred times every day I remind myself that my inner and outer life depend on the labors of other men, living and dead, and that I must exert myself in order to give in the same measure as I have received and am still receiving.
>
><div style="text-align: right">*Albert Einstein, (1879 - 1955)*</div>


You can nest quotes (should you feel the need):

>When you pay off the first baseman every month, who gets the money?
>
>>Every dollar of it. And why not, the man's entitled to it.
>
>Who is?
>
>>Yes.

### Lists

Use asterisks or hyphons to define an unordered list. Indentation indicates a nested sublist.

```
* Item 1
* Item 2
 * Item 2a
 * Item 2b
```
* Item 1
* Item 2
 * Item 2a
 * Item 2b

Use numbers for ordered lists. The styles can be matched

```
1. Item 1
2. Item 2
 * Item 2a
 * Item 2b
 * Item 2c
3. Item 3
 * Item 3a
 * Item 3b
```

1. Item 1
2. Item 2
 * Item 2a
 * Item 2b
 * Item 2c
3. Item 3
 * Item 3a
 * Item 3b

### Hyperlinks

Just typing the full hyterlink text will work, for example: http://github.com

To specify the link text use `[GitHub](http://github.com)`, yielding [GitHub](http://github.com).



### Other Markdown Elements

Not cover here, but availibe in markdown:
- Image Links
- Tables
- Emojis

## Other resources
- https://guides.github.com/pdfs/markdown-cheatsheet-online.pdf
