# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [1.1.0]

### Uncategorized

- fix: if we want to allow pre-existing git checkout state, we must read its commit hash ([#15](https://github.com/MetaMask/action-checkout-and-setup/pull/15))
- Use `MetaMask/action-retry-command` for possible flaky steps ([#16](https://github.com/MetaMask/action-checkout-and-setup/pull/16))
- Add skip-allow-scripts ([#14](https://github.com/MetaMask/action-checkout-and-setup/pull/14))
- Ensure tags are fetched in release workflow ([#13](https://github.com/MetaMask/action-checkout-and-setup/pull/13))

## [1.0.1]

### Fixed

- Run `allow-scripts` when restoring from cache ([#11](https://github.com/MetaMask/action-checkout-and-setup/pull/11))

## [1.0.0]

### Added

- Initial release of `MetaMask/action-checkout-and-setup` ([#9](https://github.com/MetaMask/action-checkout-and-setup/pull/9))

[Unreleased]: https://github.com/MetaMask/action-checkout-and-setup/compare/v1.1.0...HEAD
[1.1.0]: https://github.com/MetaMask/action-checkout-and-setup/compare/v1.0.1...v1.1.0
[1.0.1]: https://github.com/MetaMask/action-checkout-and-setup/compare/v1.0.0...v1.0.1
[1.0.0]: https://github.com/MetaMask/action-checkout-and-setup/releases/tag/v1.0.0
