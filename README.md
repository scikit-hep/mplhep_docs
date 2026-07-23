# mplhep_docs

Build output for the [mplhep](https://github.com/scikit-hep/mplhep) documentation site.

The rendered site lives on the **`gh-pages`** branch, managed by
[mike](https://github.com/jimporter/mike). There is nothing to develop here.

## Why this is a separate repository

`gh-pages` holds the built HTML for every released version, images included. Kept in the
main repository it was ~45 MB of a ~71 MB clone and grew with every release, so every
contributor downloaded the published docs site just to work on the library. Splitting it out
keeps `scikit-hep/mplhep` at ~26 MB. This mirrors what matplotlib does with
`matplotlib/matplotlib.github.com`.

## How it is updated

Nobody pushes here by hand. `.github/workflows/ci-pages.yml` in `scikit-hep/mplhep` runs
`mike deploy` against this repository using a deploy key, then uploads the result as the
GitHub Pages artifact for `scikit-hep/mplhep`.

The site is served from **https://scikit-hep.org/mplhep/**, which is Pages on
`scikit-hep/mplhep`, not on this repository. Pages there is configured as `build_type:
workflow`, so it serves an uploaded artifact rather than a branch — which is what makes this
split possible without changing any URL.

## Doc sources

Sources are in `scikit-hep/mplhep` under `new_docs/`. Edit them there.
