# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [2.0.0]

### Uncategorized

- chore(deps): Bump actions to latest versions ([#41](https://github.com/MetaMask/action-checkout-and-setup/pull/41))
- refactor!: Always include runner OS and arch in cache key ([#40](https://github.com/MetaMask/action-checkout-and-setup/pull/40))
- feat!: Include full Node version in cache key ([#38](https://github.com/MetaMask/action-checkout-and-setup/pull/38))

## [1.4.0]

### Added

- Add parameter for platform specific caching ([#34](https://github.com/MetaMask/action-checkout-and-setup/pull/34))
  - By default the cache is not platform specific, meaning the same cache is used by different operating systems.
  - The new behaviour can be enabled by setting `platform-specific-caching` to `true`.

### Changed

- Use more efficient cache key ([#33](https://github.com/MetaMask/action-checkout-and-setup/pull/33))

## [1.3.0]

### Added

- Allow to use a local stored yarn binary ([#28](https://github.com/MetaMask/action-checkout-and-setup/pull/28), [#30](https://github.com/MetaMask/action-checkout-and-setup/pull/30))

## [1.2.0]

### Added

- Add `yarn-custom-url` and `yarn-install-max-retries` options ([#24](https://github.com/MetaMask/action-checkout-and-setup/pull/24))

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

[Unreleased]: https://github.com/MetaMask/action-checkout-and-setup/compare/v2.0.0...HEAD
[2.0.0]: https://github.com/MetaMask/action-checkout-and-setup/compare/v1.4.0...v2.0.0
[1.4.0]: https://github.com/MetaMask/action-checkout-and-setup/compare/v1.3.0...v1.4.0
[1.3.0]: https://github.com/MetaMask/action-checkout-and-setup/compare/v1.2.0...v1.3.0
[1.2.0]: https://github.com/MetaMask/action-checkout-and-setup/compare/v1.1.1...v1.2.0
[1.1.1]: https://github.com/MetaMask/action-checkout-and-setup/compare/v1.1.0...v1.1.1
[1.1.0]: https://github.com/MetaMask/action-checkout-and-setup/compare/v1.0.1...v1.1.0
[1.0.1]: https://github.com/MetaMask/action-checkout-and-setup/compare/v1.0.0...v1.0.1
[1.0.0]: https://github.com/MetaMask/action-checkout-and-setup/releases/tag/v1.0.0
