## Applying a commit from crystal-lang/crystal

Upstream commits that touch [`src/compiler/crystal/syntax`](https://github.com/crystal-lang/crystal/commits/master/src/compiler/crystal/syntax), [`spec/compiler/lexer`](https://github.com/crystal-lang/crystal/commits/master/spec/compiler/lexer), and/or [`spec/compiler/parser`](https://github.com/crystal-lang/crystal/commits/master/spec/compiler/parser) should be applied to crystal-syntax.

1. Obtain the list of missing commits by running this command in a local clone of [crystal-lang/crystal](https://github.com/crystal-lang/crystal):

   `git log --reverse --oneline ae403d319..HEAD -- src/compiler/crystal/syntax spec/compiler/lexer spec/compiler/parser`

1. Obtain the patch file of a commit by adding `.patch` to the end of the commit URL.

   `curl -L -o /tmp/crystal.patch https://github.com/crystal-lang/crystal/commit/9e52bc97c.patch`

1. Update references (in the commit message only) to upstream issues and/or pull requests with the prefix `CR-`

   `#11365` becomes `CR-11365` *(We purposely avoid direct links so that we don't spam the crystal-lang issue tracker.)*

1. Replace `spec/compiler/` with `spec/`

   `spec/compiler/parser/parser_spec.cr` becomes `spec/parser/parser_spec.cr`

1. Replace `src/compiler/crystal/` with `src/`

   `src/compiler/crystal/syntax/parser.cr` becomes `src/syntax/parser.cr`

1. Apply the patch by running `git am --signoff < [path to patch]`

   `git am --signoff < /tmp/crystal.patch`
