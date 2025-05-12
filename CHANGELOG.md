# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [3.0.1] - 2025-05-12
### Fixed
- Fixed an issue where PHPCS deprecation notices would break JSON output decoding. https://github.com/tiagohillebrandt/phpcs-diff/pull/10

## [3.0.0] - 2024-07-18
### Added
- Added support for custom standards and custom ruleset files. https://github.com/tiagohillebrandt/phpcs-diff/pull/4

### Fixed
- Fixed a bug where `phpcs-diff` would fail to load in directories containing spaces. https://github.com/tiagohillebrandt/phpcs-diff/pull/5

### Forked
- Repository forked from `olivertappin/phpcs-diff`.
