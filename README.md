# xmlLib

A fork of [beevik/etree](https://github.com/beevik/etree) - a lightweight XML library for Go.

## Differences from Original

This fork maintains all features from the upstream etree library with the following modifications:

### 1. Bug Fix in `InsertChildAt`
- Fixed index adjustment logic when inserting a child that already belongs to the same parent
- Changed condition from `t.Index() < index` to `t.Index() > index` (line 835 in etree.go)

### 2. Simplified XML Escaping
The XML escape function does **not** escape the following characters:
- `'` (apostrophe) - Not escaped as `&apos;`
- `\t` (tab) - Not escaped as `&#x9;`
- `\n` (newline) - Not escaped as `&#xA;`

This produces more readable XML output while maintaining valid XML structure.

## Original etree

For full documentation and examples, see the [original etree repository](https://github.com/beevik/etree).

## License

Same BSD-style license as the original etree project. See LICENSE file.
