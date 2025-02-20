
<!-- README.md is generated from README.Rmd. Please edit that file -->

# gitignore

<!-- badges: start -->

[![CRAN
status](https://www.r-pkg.org/badges/version/gitignore)](https://cran.r-project.org/package=gitignore)
[![License: GPL
v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)
[![AppVeyor Build
Status](https://ci.appveyor.com/api/projects/status/github/ropensci/gitignore?branch=master&svg=true)](https://ci.appveyor.com/project/pmassicotte/gitignore)
[![Build
Status](https://travis-ci.org/ropensci/gitignore.svg?branch=master)](https://travis-ci.org/ropensci/gitignore)
[![Codecov test
coverage](https://codecov.io/gh/PMassicotte/gitignore/branch/master/graph/badge.svg)](https://codecov.io/gh/PMassicotte/gitignore?branch=master)

[![DOI](https://zenodo.org/badge/184759416.svg)](https://zenodo.org/badge/latestdoi/184759416)

<!-- badges: end -->

Based on the definition proposed by
[freecodecamp](https://guide.freecodecamp.org/git/gitignore/):

> The .gitignore file is a text file that tells Git which files or
> folders to ignore in a project. A local .gitignore file is usually
> placed in the root directory of a project. You can also create a
> global .gitignore file and any entries in that file will be ignored in
> all of your Git repositories.

For any project, it is therefore important to have a `.gitignore` file
that is complete and accurate. The package `gitignore` provides a simple
R interface to the [gitignore.io](https://gitignore.io/) API. It can be
used to fetch gitignore templates that can be included into the
`.gitignore` file of you git repository. The `gitignore` R package can
be used with R package, R Studio project or with any `.gitignore` file.
Note that be default, the `usethis` package populates the `.gitignore`
for the R language when you create a R project. However, it is common to
use many different programming languages in a project such as `LaTeX`,
`python`, `matlab`, `julia` and so one. This is where the `gitignore`
package shines as it can be used to programmatically modify the
`.gitignore` file of your project.

## Installation

`gitignore` can be installed from GitHub:

``` r
install.packages("devtools")
devtools::install_github("ropensci/gitignore")
```

## Examples

There are currently two useful functions in the package:

  - `gi_available_templates()` to fetch all supported gitignore
    templates.
  - `gi_fetch_templates()` to fetch one or many gitignore templates.

Show the first 25 templates returned by `gi_available_templates()`.

``` r
library(gitignore)

head(gi_available_templates(), 25)
#>  [1] "1c"                   "1c-bitrix"            "actionscript"        
#>  [4] "ada"                  "adobe"                "advancedinstaller"   
#>  [7] "a-frame"              "agda"                 "al"                  
#> [10] "alteraquartusii"      "altium"               "android"             
#> [13] "androidstudio"        "angular"              "anjuta"              
#> [16] "ansible"              "apachecordova"        "apachehadoop"        
#> [19] "appbuilder"           "appceleratortitanium" "appcode"             
#> [22] "appcode+all"          "appcode+iml"          "appengine"           
#> [25] "aptanastudio"
```

Templates can be fetched using the `gi_fetch_templates()` function.

``` r
gi_fetch_templates("R")
● Copied to the clipboard. You can now paste it in your .gitignore file.
```

Multiple templates can be fetched by specifying multiple values:

``` r
gi_fetch_templates(c("java", "c++"))
● Copied to the clipboard. You can now paste it in your .gitignore file.
```

By default, templates are copied into the clipboard. It is also possible
to modify a `.gitignore` file using the `gi_write_gitignore()` function.

``` r
f <- paste0(tempdir(), "/.gitignore")
new_lines <- gi_fetch_templates("r")
gi_write_gitignore(fetched_template = new_lines, gitignore_file = f)
```

If `gitignore_file` is not specified, `gitignore` will try to find the
`.gitignore` file of your current project or package.

More examples are provided in the vignette.

``` r
browseVignettes("gitignore")
```

You can also visit the [gitignore
website](https://docs.ropensci.org/gitignore/).

## Code of conduct

Please note that the ‘gitignore’ project is released with a [Contributor
Code of
Conduct](https://docs.ropensci.org/gitignore/CODE_OF_CONDUCT.html). By
[contributing to this
project](https://docs.ropensci.org/gitignore/CONTRIBUTING.html), you
agree to abide by its
terms.

[![ropensci\_footer](https://ropensci.org/public_images/ropensci_footer.png)](https://ropensci.org)
