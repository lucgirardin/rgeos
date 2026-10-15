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

or from a cloned copy of this repository:
```bash
OS="$(uname -s)"
ARCH="$(uname -m)"

# Select the appropriate R library path
if [ "$OS" = "Darwin" ]; then
    # macOS paths based on architecture
    if [ "$ARCH" = "arm64" ]; then
        R_LIB_PATH="/Library/Frameworks/R.framework/Versions/4.6-arm64/Resources/library/"
    else
        R_LIB_PATH="/Library/Frameworks/R.framework/Versions/4.6-x86_64/Resources/library/"
    fi
elif [ "$OS" = "Linux" ]; then
    # Linux path
    R_LIB_PATH="/usr/lib/R/site-library/sp/"
else
    echo "Unsupported operating system: $OS"
    exit 1
fi
mkdir $R_LIB_PATH/sp/include
cp -r sp/include/* $R_LIB_PATH/sp/include/
Rscript -e 'install.packages(here::here(""), repos = NULL, type="source")'
```

It is then possible to install RGDAL as well:
```R
devtools::install_version("rgdal", version = "1.6-7", repos = "http://cran.us.r-project.org")
```

Disclaimer
This fork is provided as-is. Use at your own risk! No guarantees are made regarding stability, performance, or full compatibility with all use cases. Test thoroughly before deploying in production environments.
