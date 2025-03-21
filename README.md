# rgeos (Fork)

This is a fork of the `rgeos` package, updated to ensure compatibility with the latest version of the `sp` package. Modifications have been made to resolve compilation issues and maintain functionality with modern dependencies. This effort serves as a pushback to the forced obsolescence of the `rgeos` and `rgdal` packages.

## Installation

To install this forked version, use the following command in R:

```R
install.packages("sp")
```

then in your shell do:
```bash
wget -qO- https://api.github.com/repos/lucgirardin/rgeos/tarball/master | tar -xz --strip-components=2 -C /usr/local/lib/R/site-library/sp/ lucgirardin-rgeos-ad5027c/sp/include
```

and then back to R:
```R
remotes::install_github("lucgirardin/rgeos")
devtools::install_version("rgdal", version = "1.6-7", repos = "http://cran.us.r-project.org")
```

Disclaimer
This fork is provided as-is. Use at your own risk! No guarantees are made regarding stability, performance, or full compatibility with all use cases. Test thoroughly before deploying in production environments.
