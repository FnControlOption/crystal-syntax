# syntax

`compiler/crystal/syntax` but as a standalone module

```yaml
dependencies:
  syntax:
    github: FnControlOption/crystal-syntax
```

```crystal
require "syntax"

p Syntax::Parser.parse("2 + 2").class_desc
# "Call"

p Syntax::Parser.parse("2 + 2").location
# :1:1

p Syntax::Parser.parse("2 + 2").end_location
# :1:5
```
