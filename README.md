# xml

A fork of [beevik/etree](https://github.com/beevik/etree) - a lightweight XML library for Go.

## Installation

```bash
go get github.com/scorredoira/xml
```

## Usage

```go
import "github.com/scorredoira/xml"

doc := xml.NewDocument()
doc.CreateProcInst("xml", `version="1.0" encoding="UTF-8"`)

root := doc.CreateElement("root")
root.CreateAttr("version", "1.0")

child := root.CreateElement("child")
child.SetText("Hello World")

doc.Indent(2)
doc.WriteTo(os.Stdout)
```

## Differences from Original

This fork maintains all features from the upstream etree library with the following modifications:

### 1. Package Name
- Changed from `package etree` to `package xml`
- Import as: `import "github.com/scorredoira/xml"`

### 2. Bug Fix in `InsertChildAt`
- Fixed index adjustment logic when inserting a child that already belongs to the same parent
- Changed condition from `t.Index() < index` to `t.Index() > index` (line 835 in etree.go)

### 3. Simplified XML Escaping
The XML escape function does **not** escape the following characters:
- `'` (apostrophe) - Not escaped as `&apos;`
- `\t` (tab) - Not escaped as `&#x9;`
- `\n` (newline) - Not escaped as `&#xA;`

This produces more readable XML output while maintaining valid XML structure.

## Original etree

For full documentation and examples, see the [original etree repository](https://github.com/beevik/etree).

## License

Same BSD-style license as the original etree project. See LICENSE file.
