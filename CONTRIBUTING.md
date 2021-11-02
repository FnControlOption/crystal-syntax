## Applying a commit from crystal-lang/crystal

1. Obtain the patch file by adding `.patch` to the end of the commit URL.
    - Example: https://github.com/crystal-lang/crystal/commit/ce7bbe1d92ec4a0b6917c4a742666c7974f0e875.patch

1. Update references to upstream issues and/or pull requests with the prefix `CR-`
    - Example: `#11365` becomes `CR-11365`
    - *Note: We purposely avoid direct links so that we don't spam the crystal-lang issue tracker.*

1. Replace `spec/compiler/` with `spec/`
    - Example: `spec/compiler/parser/parser_spec.cr` becomes `spec/parser/parser_spec.cr`

1. Replace `src/compiler/crystal/` with `src/`
    - Example: `src/compiler/crystal/syntax/parser.cr` becomes `src/syntax/parser.cr`

1. Apply the patch by running `git am --signoff < [path to patch]`
    - Example: `git am --signoff < ~/Downloads/ce7bbe1.patch`
