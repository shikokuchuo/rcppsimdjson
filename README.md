## RcppSimdJson: Rcpp Bindings for the simdjson Header Library

[![Build Status](https://travis-ci.org/eddelbuettel/rcppsimdjson.svg)](https://travis-ci.org/eddelbuettel/rcppsimdjson)
[![CI](https://github.com/eddelbuettel/rcppsimdjson/workflows/ci/badge.svg)](https://github.com/eddelbuettel/rcppsimdjson/actions?query=workflow%3Aci)
[![License](https://eddelbuettel.github.io/badges/GPL2+.svg)](https://www.gnu.org/licenses/gpl-2.0.html)
[![CRAN](https://www.r-pkg.org/badges/version/RcppSimdJson)](https://cran.r-project.org/package=RcppSimdJson)
[![Dependencies](https://tinyverse.netlify.com/badge/RcppSimdJson)](https://cran.r-project.org/package=RcppSimdJson)
[![Downloads](https://cranlogs.r-pkg.org/badges/RcppSimdJson?color=brightgreen)](https://www.r-pkg.org/pkg/RcppSimdJson)
[![Code Coverage](https://codecov.io/gh/eddelbuettel/RcppSimdJson/graph/badge.svg)](https://codecov.io/gh/eddelbuettel/RcppSimdJson)
[![Last Commit](https://img.shields.io/github/last-commit/eddelbuettel/rcppsimdjson)](https://github.com/eddelbuettel/rcppsimdjson)

### Motivation

[simdjson](https://github.com/simdjson/simdjson) by [Daniel Lemire](https://lemire.me/en/) (with contributions by [Geoff
Langdale](https://branchfree.org/),  [John Keiser](https://github.com/jkeiser) and  [many others](https://github.com/simdjson/simdjson/graphs/contributors)) is an
engineering marvel.  Through very clever use of [SIMD instructions](https://en.wikipedia.org/wiki/SIMD),
it manages to parse JSON files faster than disc access. Wut? Yes you read that right: parallel
processing with so little overhead that the net throughput is limited only by disk speed.

Moreover, it is implemented in neat modern C++ and can be accessed as a header-only library. (Well,
one library in two files, really.)  Which makes R packaging easy and convenient and compelling. So
here we are.

For further introduction, see the [arXiv paper](https://arxiv.org/abs/1902.08318) by Langdale and Lemire (out/to appear in VLDB
Journal 28(6) as well) and/or the video of the [recent talk by Daniel Lemire at
QCon](https://www.youtube.com/watch?v=wlvKAT7SZIQ) (voted best talk).

### Example

```r
jsonfile <- system.file("jsonexamples", "twitter.json", package="RcppSimdJson")
library(RcppSimdJson)
validateJSON(jsonfile)                  # validate a JSON file
res <- fload(jsonfile)                  # parse a JSON file
```

### Status

As of version 0.1.0, all three major OSs are supported, and JSON can be parsed from file and string
under a variety of settings. Prefers a real C++17 compiler but can fall back to older
compiler. Still subject to change.

### Contributing

Any problems, bug reports, or features requests for the package can be submitted and handled most
conveniently as [Github issues](https://github.com/eddelbuettel/rcppsimdjson/issues) in the repository.

Before submitting pull requests, it is frequently preferable to first discuss need and scope in such
an issue ticket.  See the file
[Contributing.md](https://github.com/RcppCore/Rcpp/blob/master/Contributing.md) (in the
[Rcpp](https://github.com/RcppCore/Rcpp) repo) for a brief discussion.

### Author

For the R package, [Dirk Eddelbuettel](https://github.com/eddelbuettel) and [Brendan
Knapp](https://github.com/knapply).

For everything pertaining to simdjson, [Daniel Lemire](https://lemire.me/en/) (and [many
contributors](https://github.com/simdjson/simdjson/graphs/contributors)).
