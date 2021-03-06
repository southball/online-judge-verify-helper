# Online Judge Verify Helper

[![Actions Status](https://github.com/kmyk/online-judge-verify-helper/workflows/verify/badge.svg)](https://github.com/kmyk/online-judge-verify-helper/actions)
[![GitHub Pages](https://img.shields.io/static/v1?label=GitHub+Pages&message=+&color=brightgreen&logo=github)](https://kmyk.github.io/online-judge-verify-helper/)
[![PyPI](https://img.shields.io/pypi/v/online-judge-verify-helper)](https://pypi.org/project/online-judge-verify-helper/)
[![LICENSE](https://img.shields.io/pypi/l/online-judge-verify-helper.svg)](https://github.com/kmyk/online-judge-verify-helper/blob/master/LICENSE)

[README 日本語バージョン](README.ja.md)

## What is this?

This is a tool to easily automate the verify process of your code library for competitive programming.

## How to use

### Set up the repository for the library

Please read this: <https://kmyk.github.io/online-judge-verify-helper/installer.en.html>

### Running the program

#### Installation

``` console
$ pip3 install online-judge-verify-helper
```

#### Automating the verification

First, add the problem URL to be used to verify the library in the file ending with `.test.cpp` as follows (`#define PROBLEM "https://judge.yosupo.jp/problem/unionfind"`). Then, run the following command to check if the verification can be performed.

``` console
$ oj-verify run
```

Currently, problems on [Library Checker](https://judge.yosupo.jp/) and [Aizu Online Judge](https://onlinejudge.u-aizu.ac.jp/home) are supported. It is probable that problems on [HackerRank](https://www.hackerrank.com/) can also be used, but it is not guaranteed at the moment.

Other judging platforms do not currently publish the test cases in usable forms, and so are not currently supported.

#### Autoexpansion of `#include`s

The `include` statements in your files in the form of `#include "foo.hpp"` can be expanded,
similar to the functionality provided by [webpack](https://webpack.js.org) for JavaScript. This is to solve the problems that most online judges do not support submitting multiple files.
The function can be used by running the following command:

``` console
$ oj-verify bundle main.cpp
```

If your competitive programming library resides outside the current directory, please specify the flag in the form of `-I path/to/your/library`.

[Include guards](https://ja.wikibooks.org/wiki/More_C%2B%2B_Idioms/%E3%82%A4%E3%83%B3%E3%82%AF%E3%83%AB%E3%83%BC%E3%83%89%E3%82%AC%E3%83%BC%E3%83%89%E3%83%9E%E3%82%AF%E3%83%AD%28Include_Guard_Macro%29) like `#pragma once` are partially supported. If you have files that will be included multiple times but you only want them to appear once in the generated code, add `#pragma once` to the first line of the files.

#### Generating Documentation

Run the following command to generate documentation in `.verify-helper/markdown/`. Example: [https://kmyk.github.io/online-judge-verify-helper/ ![GitHub Pages](https://img.shields.io/static/v1?label=GitHub+Pages&message=+&color=brightgreen&logo=github)](https://kmyk.github.io/online-judge-verify-helper/)

``` console
$ oj-verify docs
```

If documentation generators like [Doxygen](http://www.doxygen.jp) are found when generating documentation, they will be automatically used.
TeX expressions like `$(N \sum_i A_i)$` are also supported by the [MathJax](https://www.mathjax.org/) library.
(TODO: document what commands are recognized)

## Tips

-   If you cannot find problems to verify your library, you can refer to other users' libraries. You can find all users of `online-judge-verify-helper` at <https://github.com/search?q=online-judge-verify-helper+path%3A.github>.
-   If you cannot find problems to verify your library anywhere, we suggest that you add a problem to [Library Checker](https://judge.yosupo.jp/).
-   If you want to accelerate the verify process, you can accelerate by about 100 times: <https://kmyk.github.io/online-judge-verify-helper/speedup.html> (Japanese)
-   You do not need to display the MIT License if you call `online-judge-verify-helper` from GitHub Actions ([Details, in Japanese](https://github.com/kmyk/online-judge-verify-helper/issues/34)).
-   This is tool to efficiently verify your library, not to check or prettify your code. If you need such functions, you can try formatters like [clang-format](https://clang.llvm.org/docs/ClangFormat.html) or linters like [cppcheck](http://cppcheck.sourceforge.net/).
-   Languages other than C++ are also supported (Example: [examples/circle.test.awk](https://github.com/kmyk/online-judge-verify-helper/tree/master/examples/circle.test.awk)). You need a file like `.verify-helper/config.toml` that specifies the commands for compiling and running the program (Example: [.verify-helper/config.toml](https://github.com/kmyk/online-judge-verify-helper/blob/master/.verify-helper/config.toml)).

## Authors

-   committer: [@kmyk](https://github.com/kmyk) (AtCoder: [kimiyuki](https://atcoder.jp/users/kimiyuki)): distribution on `pip` and miscellaneous tasks on [online-judge-tools](https://github.com/kmyk/online-judge-tools)
-   committer: [@beet-aizu](https://github.com/beet-aizu) (AtCoder: [beet](https://atcoder.jp/users/beet)): verify function
-   committer: [@tsutaj](https://github.com/tsutaj) (AtCoder: [Tsuta_J](https://atcoder.jp/users/Tsuta_J)): documents generation
