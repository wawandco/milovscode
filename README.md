# Milo

Integrates the [Milo](https://github.com/wawandco/milo) HTML linter tool into vs code.

![hero](images/hero.png)

Milo is a linter tool that will check for both syntax correctness and style recommendations in HTML files. Milo differences from other HTML linters because is friendly with ERB and Plush tags defined inside HTML files. The end goal is to have a single binary that could be used in the context of a CI server which could check the codebase HTML before PR's get merged.

This visual code extension allows developers to perform milo when writing and editing HTML files.

## Usage
The Milo vs code extension will run Milo on your open HTML files and report the number of rules that don't accomplish in the html file as warnings on the *Status Bar* and details in the *Problems* panel.

![hero](images/problems.png)

Milo expands details about the rule being warned with hover actions in the active editor.

![hero](images/detail.png)


## Important Considerations

- Milo will check the HTML syntax of HTML only. ([see this](https://html.spec.whatwg.org/multipage/syntax.html))
- Milo will also check some style best practices and point those as issues to fix.
- Rules can be enabled/disabled. (See configuration)
- Milo considers html partials and validates the rules that apply to these.
- Milo considers erb and [plush](https://github.com/gobuffalo/plush) as part of the HTML.

You can also download Milo binaries from our releases folder.

### Configuration

By default Milo will run all the linters it has. However, some teams will want to disable some of the linters in the list, if this is your case you can add a `.milo.yml` file in the root of your codebase.
Once you have installed Milo it can generate that file by running:
```
milo init
```

That `.milo.yml` will look like the following example:

```
output: text # could be `text`, `github` or `silent`
reviewers:
  - doctype/present 
  - ...
```

This file will be used by the Milo binary to determine which reviewers to run our files against.

## Reviewers

Milo uses the following reviewers:

### Head

- [0001] Doctype must be declared.
- [0002] Doctype must be valid.
- [0004] `<title>` must be present inside `<head>` tag.
- [0005] `<style>` must not be used.

### Tags

- [0006] All HTML element names must be in lowercase.
- [0007] `src`, `href` and `data` attributes of must have a value.
- [0008] `ol` and `ul` must only have `li` direct child tags.
- [0015] tag-pair: Tag must be paired.

### Attributes

- [0013] attr-lowercase: All attribute names must be in lowercase.
- [0010] attr-no-duplication: Elements cannot have duplicate attributes.
- [0019] attr-no-unnecessary-whitespace: No spaces between attribute names and values.
- [0016] attr-unsafe-chars: Attribute values cannot contain unsafe chars.
- [0018] attr-value-double-quotes: Attribute values must be in double quotes.
- [0011] attr-value-not-empty: All attributes must have values.
- [0012] alt-require: The alt attribute of an element must be present and alt attribute of area[href] and input[type=image] must have a value.
- [0014] id-unique: The value of id attributes must be unique.

### Inline

- [0003] Inline css is not allowed p.e: style="background-color: red;".
- [0009] inline-style-disabled: Inline style cannot be used.
- [0017] inline-script-disabled: Inline script cannot be used.

## Copyright

Milo is Copyright © 2020 Wawandco SAS. It is free software, and may be redistributed under the terms specified in the LICENSE file.

