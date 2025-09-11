# `@metamask/action-checkout-and-setup`

This TypeScript module is maintained in the style of the MetaMask team.

## Usage

This action provides automatic caching for both `node_modules` and yarn's offline mirror, enabling faster and more reliable CI runs. When yarn's offline mirror is available, the action will automatically use `--prefer-offline` mode for installations.

### Examples

#### High-risk environment

```yaml
- name: Checkout and setup high risk environment
  uses: MetaMask/action-checkout-and-setup@v1
  with:
    is-high-risk-environment: true
```

Note: In high-risk environments, all caching is disabled for security reasons.

#### Low-risk environment

```yaml
- name: Checkout and setup
  uses: MetaMask/action-checkout-and-setup@v1
  with:
    is-high-risk-environment: false
```

In low-risk environments, the action automatically:
- Caches `node_modules` for exact commit matches
- Caches yarn's offline mirror for faster, offline-capable installations
- Uses `--prefer-offline` when offline mirror cache is available

#### Custom ref and fetch depth

```yaml
- name: Checkout and setup
  uses: MetaMask/action-checkout-and-setup@v1
  with:
    ref: ${{ github.sha }}
    fetch-depth: 1
```

#### Custom Yarn URL and Install Retries

```yaml
- name: Checkout and setup with custom Yarn
  uses: MetaMask/action-checkout-and-setup@v1
  with:
    is-high-risk-environment: false
    yarn-custom-url: 'https://your-cdn.com/yarn-4.9.1/yarn.js#sha224.abc123'
    yarn-install-max-retries: 5
```

### Caching Mechanism

This action implements a two-tier caching strategy for optimal performance:

#### 1. Node Modules Cache
- **Cache Key**: Based on the exact commit hash
- **When Used**: In low-risk environments when `cache-node-modules` is enabled
- **Benefit**: Skips yarn install entirely when dependencies haven't changed

#### 2. Yarn Offline Mirror Cache
- **Cache Key**: Based on `yarn.lock` file content
- **When Used**: In low-risk environments when node_modules cache misses
- **What's Cached**:
  - `.yarn-offline-mirror/` - Package tarballs (*.tgz files)
  - `.yarn-cache/` - Yarn's local cache
  - `~/.yarn/cache/` - Global yarn cache
- **Benefits**:
  - Enables offline installations with `--prefer-offline`
  - Reduces install time from 3-5 minutes to 30-60 seconds
  - Eliminates NPM registry failures
  - Works completely offline after first cache build

#### Cache Performance

| Scenario | Install Time | Network Usage |
|----------|-------------|---------------|
| Cold cache (first run) | 3-5 minutes | Full download |
| Node modules cache hit | 0 seconds | None |
| Offline mirror cache hit | 30-60 seconds | None |
| Cache miss | 3-5 minutes | Full download |

### Options

#### `is-high-risk-environment`

If set to `true`, the action will set up the environment for a high-risk
environment. An environment is considered high-risk if (not exhaustive):

- It contains secrets that should not be exposed.
- It is a production environment, or deploys to a production environment.
- It creates a build artifact that may be distributed to someone else.

#### `fetch-depth`

The depth of commits to fetch.

Defaults to `0`.

#### `ref`

The ref to checkout.

Defaults to the current ref.

#### `cache-node-modules`

If set to `true`, the action will cache the `node_modules` directory. This
should only be enabled for a "prepare"-type job. This cannot be enabled in a
high-risk environment.

Defaults to `false`.

#### `node-version`

The version of Node.js to use.

Defaults to the version specified in the `.nvmrc` file.

#### `skip-allow-scripts`

If set to `true`, the action will skip the `yarn allow-scripts` step. This can save time if your job does not require this step.

Defaults to `false`.

#### `yarn-custom-url`

If set, provides a custom URL for a Yarn bundle to be prepared and activated by Corepack. This is useful for CI environments that need to use a self-hosted or alternative Yarn bundle (for example, to avoid rate-limiting from the public Yarn registry).

Defaults to `''` (not set).

#### `yarn-install-max-retries`

Sets the maximum number of retries for the `yarn --immutable` install command. This helps handle transient network errors more gracefully in CI environments.

Defaults to `5`.

## Contributing

### Setup

- Install the current LTS version of [Node.js](https://nodejs.org)
  - If you are using [nvm](https://github.com/creationix/nvm#installation) (recommended) running `nvm install` will install the latest version and running `nvm use` will automatically choose the right node version for you.
- Install [Yarn](https://yarnpkg.com) v4 via [Corepack](https://github.com/nodejs/corepack?tab=readme-ov-file#how-to-install)
- Run `yarn install` to install dependencies and run any required post-install scripts

### Testing and Linting

Run `yarn lint` to run the linter, or run `yarn lint:fix` to run the linter and
fix any automatically fixable issues.

### Release & Publishing

The project follows the same release process as the other libraries in the
MetaMask organization. The GitHub Actions [`action-create-release-pr`](https://github.com/MetaMask/action-create-release-pr)
and [`action-publish-release`](https://github.com/MetaMask/action-publish-release)
are used to automate the release process; see those repositories for more
information about how they work.

1. Choose a release version.

   - The release version should be chosen according to SemVer. Analyze the
     changes to see whether they include any breaking changes, new features,
     or deprecations, then choose the appropriate SemVer version. See
     [the SemVer specification](https://semver.org/) for more information.

2. If this release is backporting changes onto a previous release, then ensure
   there is a major version branch for that version (e.g. `1.x` for a `v1`
   backport release).

   - The major version branch should be set to the most recent release with that
     major version. For example, when backporting a `v1.0.2` release, you'd want
     to ensure there was a `1.x` branch that was set to the `v1.0.1` tag.

3. Trigger the [`workflow_dispatch`](https://docs.github.com/en/actions/reference/events-that-trigger-workflows#workflow_dispatch)
   event [manually](https://docs.github.com/en/actions/managing-workflow-runs/manually-running-a-workflow)
   for the `Create Release Pull Request` action to create the release PR.

   - For a backport release, the base branch should be the major version branch
     that you ensured existed in step 2. For a normal release, the base branch
     should be the main branch for that repository (which should be the default value).
   - This should trigger the [`action-create-release-pr`](https://github.com/MetaMask/action-create-release-pr)
     workflow to create the release PR.

4. Update the changelog to move each change entry into the appropriate change
   category ([See here](https://keepachangelog.com/en/1.0.0/#types) for the full
   list of change categories, and the correct ordering), and edit them to be
   more easily understood by users of the package.

   - Generally any changes that don't affect consumers of the package (e.g.,
     lockfile changes or development environment changes) are omitted.
     Exceptions may be made for changes that might be of interest despite not
     having an effect upon the published package (e.g. major test improvements,
     security improvements, improved documentation, etc.).
   - Try to explain each change in terms that users of the package would
     understand (e.g., avoid referencing internal variables/concepts).
   - Consolidate related changes into one change entry if it makes it easier to
     explain.
   - Run `yarn auto-changelog validate --prettier --rc` to check that the
     changelog is correctly formatted.

5. Review and QA the release.

   - If changes are made to the base branch, the release branch will need to be
     updated with these changes and review/QA will need to restart again. As
     such, it's probably best to avoid merging other PRs into the base branch
     while review is underway.

6. Squash & Merge the release.

   - This should trigger the [`action-publish-release`](https://github.com/MetaMask/action-publish-release)
     workflow to tag the final release commit and publish the release on GitHub.

7. Publish the release.

   - Wait for the `announce-release` GitHub Action workflow to finish. This
     should trigger a second job (`publish-release`), which will wait for a run
     approval by the [`npm publishers`](https://github.com/orgs/MetaMask/teams/npm-publishers)
     team.
   - Approve the `publish-release` job (or ask somebody on the npm publishers team
     to approve it for you).
   - Once the `publish-release` job has finished, check the tag on GitHub to
     ensure that the release was published correctly.
