# Quarto docs template

Set up a new GitHub repository to be documented using [Quarto]. 
Write your documentation as a Quarto static website in the `docs/` folder. Changes to the documentation are rendered in a separate branch (`gh-pages`) published with GitHub pages.

## Background 

An empty repository with Quarto documentation published
as a GitHub Pages websites. Use this template to start
a new project that you want to document using Quarto.

Quarto is a multiformat document generator based on 
Pandoc. It can be used as a static website generators
and accepts multiple input formats. You may want to
document your project using Quarto if:

- you want to render your documentation in other formats, 
  e.g. PDF.
- you need more features than GitHub's wikis or Jekyll,
  but not advanced documentation-oriented features of 
  generators like Sphinx or Docusaurus.
- you're used to write with Quarto. 

## Installation

### With "Use this template" on the GitHub website

Click "use this template". Select the option *copy all branches*. 

This should work out of the box. If not, try running
`quarto publish gh-pages` within `docs`. (Requires a
local installation of [Quarto].)

### With a pre-existing GitHub repository

Copy from this repository:

- the `docs/` folder, except `_output/` and `.quarto/`. Make sure you include the hidden `.nojekyll` file.
- `.github/workflows/publish_docs.yml`

Add the following lines to a `.gitignore` file at the root
of your repository:

```
# Quarto Documentation artefacts
/docs/_output
/docs/.quarto
```

Run `quarto publish gh-pages` from `docs` in your 
repository. This requires a local installation
of Quarto. 

## Usage

Write documentation by amending the Quarto website in `docs/`. 
Changes to this folder that are pushed to the GitHub
repository trigger a new rendering of the documentation.
The output is visible at the URL
`https//<github-owner-name>.github.io/<template-name>`.
Add this URL to your repository's "About" information
on your repository's Github page. 

To preview your documentation before pushing it to 
GitHub, run `quarto render` in the `docs` website.
Open `docs/_output/index.html` in a browser to
see the result. (This requires a local installation
of [Quarto].)

See [Quarto guide] on how to write using Quarto.

## Advanced usage

### How this works

The GitHub Action that renders and publish your 
documentation is configured in 
`.github/workflows/publish_docs.yml`. It controls
when the action is triggered and the source 
and destination of Quarto rendering. The default
trigger is any pushed change in `docs`, the default
source is `/docs/` on the main branch, the default
destination is the `gh-pages` branch. 

Quarto rendering is configured by `docs/_quarto.yml`.
This controls where the output is rendered, which
source files to include in the documentation, 
styling the output,
whether to add extra outputs formats such as PDF.

If you change the output folder (`output-dir`), 
you need to amend `.gitignore` and the GitHub
Action paramters (`.github/workflows/publish_docs.yml`).

### Make your documentation a Quarto book

If you want to output your documentation as a Quarto
book instead of a Quarto website, you only need
to change the `_quarto.yml` file. Here's an example:

``` yaml
project:
  type: book
  output-dir: _output

book:
  title: "Sample Quarto documentation"
  chapters:
  - index.qmd
  - about.qmd

format:
  html:
    theme: cosmo
    toc: true
  pdf:
    number-sections: true
```

## Resources

* [Quarto documentation on publishing with GitHub Actions](https://quarto.org/docs/publishing/github-pages.html#github-action).
* [Quarto GitHub Actions](https://github.com/quarto-dev/quarto-actions) with documentation and examples.
* [GitHub Pages].

[Quarto]: https://quarto.org "Quarto website"
[Quarto guide]: https://quarto.org/docs/guide/ "Quarto guide"
[GitHub Pages]: https://docs.github.com/en/pages "GitHub pages documentation"
[Quarto GitHub Actions]: "https://github.com/quarto-dev/quarto-actions "Quarto's team GitHub actions"
