# Changelog
All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]
(nothing right now)

## [0.1.2] - 2022-04-17
### Changed
- added missing option to README.md

## [0.1.1] - 2022-04-17
### Added
- `padded-blocks` rule now can handle Objects as well using the `"includeObjects": true` option.

### Fixed
- `padded-blocks` rule detection of padding lines incorrectly detected a block to include paddings if an object inside the block contained paddings, but the block itself did not

## [0.1.0] - 2022-04-17
### Added
- ESLint plugin base code
- Two rules with customized options: `padded-blocks`, `space-in-parens`

[Unreleased]: https://github.com/BenceSzalai/eslint-plugin-sbnc-rules/compare/v0.1.2...HEAD
[0.1.2]: https://github.com/BenceSzalai/eslint-plugin-sbnc-rules/releases/tag/v0.1.2
[0.1.1]: https://github.com/BenceSzalai/eslint-plugin-sbnc-rules/releases/tag/v0.1.1
[0.1.0]: https://github.com/BenceSzalai/eslint-plugin-sbnc-rules/releases/tag/v0.1.0

