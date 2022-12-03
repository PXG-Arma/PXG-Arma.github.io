# Phoenix Group Bootcamp

This repository contains web site source files for the PXG Bootcamp training materials. The repository is served by GitHub Pages.

The web site is accessible at [pxg-arma.github.io](https://pxg-arma.github.io/).

## Building

The primary web page sources are located in the `php-sources` directory. The PHP source files are compiled to HTML, and then placed in the repository root to be served by GitHub Pages.

The build process is automated with a makefile. It requires GNU Make, PHP (version 8 or greater) and rsync. PHP files can be compiled to HTML using the following command (when in `php-sources` directory):
```console
make html
```

Compiled HTML files are placed in the directory `php-sources/build`. To sync them to the repository root with rsync, use:
```console
make sync
```
