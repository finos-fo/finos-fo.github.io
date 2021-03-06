# Publishing Docusaurus website

The [docusaurus-build workflow](.github/workflows/docusaurus-build.yml) is a GitHub Action that automatically builds the Docusaurus website after any commit.

If a `Push` event occurs on the a Docusaurus file (`website/**`, `docs/**` or `docusaurus-build.yml`) on a FINOS master branch, the action will simply invoke the `docusaurus-build` command and push the (HTML) result into the `gh-pages` branch.

If the `Push` event occurs on a fork of a repo with this action, the same workflow will follow, and the Docusaurus configuration (`siteConfig.js`) will be patched prior to the build, in order to serve the pages using the personal GitHub account that forked the repo.

If a `Pull Request` is submitted (related to Docusaurus files) against a FINOS repository with this action, beyond following the process described above, the action also adds a comment to the PR with the link to the preview website, containing the changes to the PR.

No configuration is needed, this should work out of the box; you can track builds on https://github.com/maoo/finos-fo/actions .

TODOs
1. Test comment on PR
2. Test fork VS upstream builds