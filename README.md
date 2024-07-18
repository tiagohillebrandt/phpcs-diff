# phpcs-diff

`phpcs-diff` detects violations of a defined set of coding standards based on a `git diff`.

<div aria-hidden="true">

[![Latest Stable Version](https://img.shields.io/github/v/tag/tiagohillebrandt/phpcs-diff.svg?style=flat&label=release)](https://github.com/tiagohillebrandt/phpcs-diff/tags)
![Minimum PHP Version](https://img.shields.io/packagist/php-v/tiagohillebrandt/phpcs-diff.svg?cacheSeconds=3600)
[![Software License](https://img.shields.io/badge/license-MIT-brightgreen.svg?style=flat)](LICENSE)
[![GitHub Issues](https://img.shields.io/github/issues/tiagohillebrandt/phpcs-diff.svg)](https://github.com/tiagohillebrandt/phpcs-diff/issues)

</div>

## Requirements
The latest version of `phpcs-diff` requires PHP version 7.3.0 or later.

This project also depends on `squizlabs/php_codesniffer` which is used internally to fetch the failed violations via `phpcs`.

Finally, the `league/climate` package is also installed. This is to deal with console output, but this dependency may be removed in a future release.

## Installation
### Composer
If you use Composer, you can install `phpcs-diff` system-wide with the following command:

```shell
composer global require tiagohillebrandt/phpcs-diff
```

It's also possible to install `phpcs-diff` as a development dependency in your project:

```shell
composer require tiagohillebrandt/phpcs-diff
````

Or alternatively, include a dependency for `tiagohillebrandt/phpcs-diff` in your `composer.json` file. For example:

```json
{
    "require-dev": {
        "tiagohillebrandt/phpcs-diff": "^3.0"
    }
}
```

You will then be able to run phpcs-diff from the vendor bin directory:

```shell
./vendor/bin/phpcs-diff
```

### Git Clone
You can also download the `phpcs-diff` source and create a symlink to your `/usr/bin` directory:

```shell
git clone https://github.com/tiagohillebrandt/phpcs-diff.git
cd phpcs-diff
php bin/phpcs-diff main -v
```

You could also add a symlink to your `/usr/bin` directory:

```shell
ln -s phpcs-diff/bin/phpcs-diff /usr/bin/phpcs-diff
```

## Getting Started

### Basic Usage
```shell
phpcs-diff <current-branch> <base-branch> -v
```

In this example, the current branch is compared to the `main` branch. `phpcs-diff` would execute the following diff statement behind the scenes:

```shell
git diff current-branch main
```

_Please note:_
- The `-v` flag is optional. This returns a verbose output during processing.
- The `current-branch` parameter is optional. If this is not defined, `phpcs-diff` will use the current commit hash via `git rev-parse --verify HEAD`.
- You must have a `ruleset.xml` defined in your project base directory.

After running `phpcs-diff`, the executable will return an output similar to the following:

```
########## START OF PHPCS CHECK ##########
module/Poject/src/Console/Script.php
 - Line 28 (WARNING) Line exceeds 120 characters; contains 190 characters
 - Line 317 (ERROR) Blank line found at end of control structure
########### END OF PHPCS CHECK ###########
```

Currently this is the only supported format however, I will look into adding additional formats (much like `phpcs`) in the near future.

## About
`phpcs-diff` detects violations of a defined set of coding standards based on a `git diff`. It uses `phpcs` from the [PHP_CodeSniffer](https://github.com/PHPCSStandards/PHP_CodeSniffer/) project.

This project offers the following benefits:
- Accelerates your CI/CD pipeline by validating only the modified files instead of the entire codebase.
- Facilitates the migration of legacy codebases, enabling incremental compliance with coding standards without the risk of extensive changes at once.

This executable works by checking the changed lines, compared to the base branch, against all failed violations for those files. This ensures that any new or changed code will be compliant.

Over time, this approach will help your codebase become more compliant with the coding standard, and you may eventually reach a point where you can run `phpcs` on the entire codebase.

### Fork
This project is derived from the **olivertappin/phpcs-diff** library.
It was created to ensure more frequent updates, as the original repository appears to be abandoned.
