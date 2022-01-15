## Applying a commit from crystal-lang/crystal

Upstream commits that touch [`src/compiler/crystal/syntax`](https://github.com/crystal-lang/crystal/commits/master/src/compiler/crystal/syntax), [`spec/compiler/lexer`](https://github.com/crystal-lang/crystal/commits/master/spec/compiler/lexer) [`spec/compiler/parser`](https://github.com/crystal-lang/crystal/commits/master/spec/compiler/parser), and/or [`spec/support/syntax.cr`](https://github.com/crystal-lang/crystal/blob/master/spec/support/syntax.cr) should be applied to crystal-syntax.

(Crystal's `spec/support/syntax.cr` maps to our `spec/spec_helper.cr`)

1. Obtain the list of missing commits by running this command in a local clone of [crystal-lang/crystal](https://github.com/crystal-lang/crystal):

   `git log --reverse --oneline ae403d319..HEAD -- src/compiler/crystal/syntax spec/compiler/lexer spec/compiler/parser spec/support/syntax.cr`

   Replace `ae403d319` with the last crystal-lang/crystal commit that had been applied to crystal-syntax. (You will need to search for the commit that has the same commit message.)

1. Obtain the patch file of a commit by adding `.patch` to the end of the commit URL.

   `curl -L -o /tmp/crystal.patch https://github.com/crystal-lang/crystal/commit/9e52bc97c.patch`

   Replace `9e52bc97c` with the commit to be applied.

1. Update references (in the commit message only) to upstream issues and/or pull requests with the prefix `CR-`

   `#11365` becomes `CR-11365` *(We purposely avoid direct links so that we don't spam the crystal-lang issue tracker.)*

1. Delete diffs that don't modify the directories mentioned above.

1. Replace `spec/compiler/` with `spec/` and `src/compiler/crystal/` with `src/`

   The regex for this is `/compiler/(crystal/)?` replaced by `/`

1. Apply the patch by running `git am --signoff < [path to patch]`

   `git am --signoff < /tmp/crystal.patch`
