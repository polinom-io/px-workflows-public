# Changelog

## [0.5.0](https://github.com/polinom-io/px-workflows-public/compare/v0.4.0...v0.5.0) (2026-11-24)


### Features

* add reusable gitignore order check ([#15](https://github.com/polinom-io/px-workflows-public/issues/15)) ([5d6d487](https://github.com/polinom-io/px-workflows-public/commit/5d6d4879370e9d67e72a7da8bbc1c47093fff1e2))

## [0.4.0](https://github.com/polinom-io/px-workflows-public/compare/v0.3.0...v0.4.0) (2026-11-24)


### Features

* add reusable pr template check workflow ([#12](https://github.com/polinom-io/px-workflows-public/issues/12)) ([4734cb4](https://github.com/polinom-io/px-workflows-public/commit/4734cb4989d706e463193a802b9a78bcf0720ced))


### Bug Fixes

* **pr-standard:** align the check with the org pr structure ([#14](https://github.com/polinom-io/px-workflows-public/issues/14)) ([60ef121](https://github.com/polinom-io/px-workflows-public/commit/60ef121ad0f4795d572616956eebbe64236cfd58))

## [0.3.0](https://github.com/polinom-io/px-workflows-public/compare/v0.2.0...v0.3.0) (2026-11-24)


### ⚠ BREAKING CHANGES

* **ci-node:** callers of ci-node.yml must grant packages: read in addition to contents: read, otherwise the run fails at startup.

### Features

* **ci-node:** install [@polinom-io](https://github.com/polinom-io) packages from GitHub Packages ([#9](https://github.com/polinom-io/px-workflows-public/issues/9)) ([c2b8030](https://github.com/polinom-io/px-workflows-public/commit/c2b8030c527a5b73566104464096427e4cf13ee7))
* **release-please:** serialize runs per ref with concurrency ([#10](https://github.com/polinom-io/px-workflows-public/issues/10)) ([f456ca2](https://github.com/polinom-io/px-workflows-public/commit/f456ca270e715b646e3ea92e97d8f0a23a2588d0))

## [0.2.0](https://github.com/polinom-io/px-workflows-public/compare/v0.1.0...v0.2.0) (2026-11-24)


### Features

* add reusable security scan workflow ([#7](https://github.com/polinom-io/px-workflows-public/issues/7)) ([603fca7](https://github.com/polinom-io/px-workflows-public/commit/603fca7aeb03f8c31217fd1a57193457d88fa0fc))


### Bug Fixes

* keep breaking changes on 0.x as minor bumps ([#5](https://github.com/polinom-io/px-workflows-public/issues/5)) ([fbf8e71](https://github.com/polinom-io/px-workflows-public/commit/fbf8e712ef6556c083e424c660d61d776bc9287c))

## 0.1.0 (2026-11-23)


### Features

* add reusable node ci and release-please workflows ([#1](https://github.com/polinom-io/px-workflows-public/issues/1)) ([b87d738](https://github.com/polinom-io/px-workflows-public/commit/b87d73819d9735c0b62e8d2bbfeb0ac4b0f6a6d7))


### Bug Fixes

* move publish to a separate reusable workflow ([#3](https://github.com/polinom-io/px-workflows-public/issues/3)) ([8f184e3](https://github.com/polinom-io/px-workflows-public/commit/8f184e32120e49fa5fcd13ece2d43d957dc376cb))
