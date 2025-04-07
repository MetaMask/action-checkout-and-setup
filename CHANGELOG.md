# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [1.1.1]

### Fixed

- Cache nested `node_modules` directories ([#20](https://github.com/MetaMask/action-checkout-and-setup/pull/20))

## [1.1.0]

### Added

- Add `skip-allow-scripts` option ([#14](https://github.com/MetaMask/action-checkout-and-setup/pull/14))
  - This can speed up the action by skipping the `allow-scripts` step, if it's not required.

### Changed

- Use `MetaMask/action-retry-command` for possible flaky steps ([#16](https://github.com/MetaMask/action-checkout-and-setup/pull/16))

### Fixed

- Use current commit hash for cache key instead of `github.sha` ([#15](https://github.com/MetaMask/action-checkout-and-setup/pull/15))

## [1.0.1]

### Fixed

- Run `allow-scripts` when restoring from cache ([#11](https://github.com/MetaMask/action-checkout-and-setup/pull/11))

## [1.0.0]

### Added

- Initial release of `MetaMask/action-checkout-and-setup` ([#9](https://github.com/MetaMask/action-checkout-and-setup/pull/9))

[Unreleased]: https://github.com/MetaMask/action-checkout-and-setup/compare/v1.1.1...HEAD
[1.1.1]: https://github.com/MetaMask/action-checkout-and-setup/compare/v1.1.0...v1.1.1
[1.1.0]: https://github.com/MetaMask/action-checkout-and-setup/compare/v1.0.1...v1.1.0
[1.0.1]: https://github.com/MetaMask/action-checkout-and-setup/compare/v1.0.0...v1.0.1
[1.0.0]: https://github.com/MetaMask/action-checkout-and-setup/releases/tag/v1.0.0
