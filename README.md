<h1 align="center">
    <img
        width="300"
        alt="hdoc logo"
        src="assets/icon.png">
</h1>

<h3 align="center">
    hdoc: the modern documentation tool for C++
</h3>

See [hdoc.io](https://hdoc.io/) for more details.
Usage documentation is hosted at [hdoc.io/docs](https://hdoc.io/docs).

## An important notice about this repository

The contents of this repository are a subset of a private repository where hdoc's development takes place.

## Overview and features

* **Autogenerated API documentation.** hdoc generated API documentation for every function, record, enum, and namespace in your codebase.
* **Integrated Markdown pages.** hdoc converts your Markdown pages into a website and puts it next to your API docs. All of your documentation is in one place.
* **Instant codebase search.** Instant search-as-you-type lookup of symbols throughout your entire codebase.
* **Easy CI integration.** Your documentation is never out of date if you build it with your code. All you need to do is add hdoc to your build job.
* **Advanced C++ parser.** hdoc understands the newest C++ features with its advanced LLVM/Clang-based parser.
* **Clean, fast output.** hdoc outputs fully static HTML with no required Javascript, ensuring your users never have to wait.

## Quick start

hdoc depends on LLVM/Clang and OpenSSL, and all other dependencies are vendored in `subprojects/`.
hdoc also comes with a Nix Flake which sets up a development environment for you with all of the needed dependencies, and should work on all Linux distributions.
Follow the instructions below to build hdoc.

```sh
# Build hdoc
meson build             # Configure the build directory
ninja -C build          # Compile hdoc binaries and tests
./build/hdoc --verbose  # Run hdoc over itself, saving the HTML documentation to ./hdoc-output/
```

More instructions for using hdoc can be found at [hdoc.io/docs](https://hdoc.io/docs).

## Running tests

hdoc has a suite of unit and integration tests, which can be run using the instructions below.

```sh
# Assumes you've already built hdoc
cd build

# Running indexing tests and unit tests
./index-tests
./unit-tests

# Running integration tests
cd ../tests
./clone_test_repos.sh  # Pull testing repos from GitHub
./test.sh              # Run hdoc over testing repos
```

## Repository structure

```
hdoc
├── assets       # Static HTML/CSS/Favicons used in the generated HTML docs
├── index-tests  # Unit tests of hdoc's indexing functionality
├── site         # Source code for hdoc.io and hdoc's documentation
├── src          # C++ source code
│   ├── frontend   # Parses configuration file and CLI arguments
│   ├── indexer    # Parses a codebase and extracts documentation from it into an index
│   ├── serde      # Serialization/Deserialization of hdoc's index into HTML and other formats
│   ├── support    # Ancillary code used to parallelize indexing
│   └── types      # Types used by hdoc
├── subprojects  # Vendored dependencies
├── tests        # Integration testing scripts
└── unit-tests   # Unit tests for a small portion of hdoc's codebase
```

## Attribution

hdoc relies on several open source software projects.
We thank all of the contributors to these projects for their work.
These are listed below in alphabetical order:
- [argparse](https://github.com/p-ranav/argparse)
- [cereal](https://uscilab.github.io/cereal/)
- [Clang](https://clang.llvm.org/)
- [cmark](https://github.com/commonmark/cmark)
- [cpp-httplib](https://github.com/yhirose/cpp-httplib)
- [CTML](https://github.com/tinfoilboy/CTML)
- [doctest](https://github.com/onqtam/doctest)
- [LLVM](https://llvm.org/)
- [spdlog](https://github.com/gabime/spdlog)
- [tiny-process-library](https://gitlab.com/eidheim/tiny-process-library)
- [toml++](https://marzer.github.io/tomlplusplus/)

More information, including licenses, can be found at [hdoc.io/oss](https://hdoc.io/oss/).

## License

hdoc is available under the AGPLv3 license, or a custom commercial license.
For more information about commercial licensing, reach out to [contact@hdoc.io](mailto:contact@hdoc.io).
