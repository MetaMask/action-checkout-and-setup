# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [3.4.1]

### Changed

- bump: update everything to the latest versions (#76)
- ci: cache only the root node_modules (#78)

## [3.4.0]

### Added

- Add `skip-install` input (#74)
  - This option can be used to skip installing Yarn dependencies, useful for when Node.js setup is needed, but dependencies are not.

## [3.3.1]

### Fixed

- Use raw GitHub URL for public repositories (#72)
  - This solves an issue with rate limit errors caused by using the GitHub API in high-activity public repositories.

## [3.3.0]

### Added

- Add `persist-credentials` input (#69)
  - This is forwarded to `actions/checkout`, and defaults to `false`.

### Fixed

- Restore support for private repositories (#68)
- Include Yarn install state when restoring cache (#66)

## [3.2.0]

### Added

- Allow high-risk the option to save cache without reading cache (#64)

## [3.1.0]

### Added

- Add `force-setup` option to always perform checkout and setup (#61)

## [3.0.1]

### Fixed

- Fix Windows runner compatibility by using `curl` instead of `wget` (#59)

## [3.0.0]

### Changed

- **BREAKING**: Security fix, removes the inputs yarn-custom-url, use-yarn-hydrate, and yarn-hydrate-command -- replaced with yarn-tarball (#57)
- **BREAKING**: Made things faster when there's a cache hit, but now _requires_ either .nvmrc or inputs.node-version (#54)

## [2.0.1]

### Fixed

- Use environment variables for script inputs (#44)

## [2.0.0]

### Changed

- **BREAKING**: Bump `GitHub/actions/*` actions to latest versions (#41)
- **BREAKING**: Always include runner OS and arch in cache key (#40)
- **BREAKING**: Include full Node version in cache key (#38)

## [1.4.0]

### Added

- Add parameter for platform specific caching (#34)
  - By default the cache is not platform specific, meaning the same cache is used by different operating systems.
  - The new behaviour can be enabled by setting `platform-specific-caching` to `true`.

### Changed

- Use more efficient cache key (#33)

## [1.3.0]

### Added

- Allow to use a local stored yarn binary (#28, #30)

## [1.2.0]

### Added

- Add `yarn-custom-url` and `yarn-install-max-retries` options (#24)

## [1.1.1]

### Fixed

- Cache nested `node_modules` directories (#20)

## [1.1.0]

### Added

- Add `skip-allow-scripts` option (#14)
  - This can speed up the action by skipping the `allow-scripts` step, if it's not required.

### Changed

- Use `MetaMask/action-retry-command` for possible flaky steps (#16)

### Fixed

- Use current commit hash for cache key instead of `github.sha` (#15)

## [1.0.1]

### Fixed

- Run `allow-scripts` when restoring from cache (#11)

## [1.0.0]

### Added

- Initial release of `MetaMask/action-checkout-and-setup` (#9)

[Unreleased]: https://github.com/MetaMask/action-checkout-and-setup/compare/v3.4.1...HEAD
[3.4.1]: https://github.com/MetaMask/action-checkout-and-setup/compare/v3.4.0...v3.4.1
[3.4.0]: https://github.com/MetaMask/action-checkout-and-setup/compare/v3.3.1...v3.4.0
[3.3.1]: https://github.com/MetaMask/action-checkout-and-setup/compare/v3.3.0...v3.3.1
[3.3.0]: https://github.com/MetaMask/action-checkout-and-setup/compare/v3.2.0...v3.3.0
[3.2.0]: https://github.com/MetaMask/action-checkout-and-setup/compare/v3.1.0...v3.2.0
[3.1.0]: https://github.com/MetaMask/action-checkout-and-setup/compare/v3.0.1...v3.1.0
[3.0.1]: https://github.com/MetaMask/action-checkout-and-setup/compare/v3.0.0...v3.0.1
[3.0.0]: https://github.com/MetaMask/action-checkout-and-setup/compare/v2.0.1...v3.0.0
[2.0.1]: https://github.com/MetaMask/action-checkout-and-setup/compare/v2.0.0...v2.0.1
[2.0.0]: https://github.com/MetaMask/action-checkout-and-setup/compare/v1.4.0...v2.0.0
[1.4.0]: https://github.com/MetaMask/action-checkout-and-setup/compare/v1.3.0...v1.4.0
[1.3.0]: https://github.com/MetaMask/action-checkout-and-setup/compare/v1.2.0...v1.3.0
[1.2.0]: https://github.com/MetaMask/action-checkout-and-setup/compare/v1.1.1...v1.2.0
[1.1.1]: https://github.com/MetaMask/action-checkout-and-setup/compare/v1.1.0...v1.1.1
[1.1.0]: https://github.com/MetaMask/action-checkout-and-setup/compare/v1.0.1...v1.1.0
[1.0.1]: https://github.com/MetaMask/action-checkout-and-setup/compare/v1.0.0...v1.0.1
[1.0.0]: https://github.com/MetaMask/action-checkout-and-setup/releases/tag/v1.0.0
