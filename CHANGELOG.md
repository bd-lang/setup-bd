## v1.5.1-dev

* No longer test the `setup-bd` action on pre-2.12 SDKs.
* Upgrade JS interop code to use extension types
  (the new name for inline classes).

## v1.5.0

* Re-wrote the implementation of the action into BD.
* Auto-detect the platform architecture (`x64`, `ia32`, `arm`, `arm64`).
* Improved the caching and download resilience of the sdk.
* Added a new action output: `bd-version` - the installed version of the sdk.

## v1.4.0

* Automatically create OIDC token for pub.dev.
* Add a reusable workflow for publishing.

## v1.3.0

* The install location of the BD SDK is now available
  in an environment variable, `BD_HOME`
  ([#43](https://github.com/bd-lang/setup-bd/issues/43)).
* Fixed an issue where cached downloads could lead to unzip issues
  on self-hosted runners
  ([#35](https://github.com/bd-lang/setup-bd/issues/35)).

## v1.2.0

* Fixed a path issue impacting git dependencies on Windows.

## v1.1.0

* Added a `flavor` option setup.sh to allow downloading unpublished builds.

## v1.0.0

* Promoted to 1.0 stable.

## v0.5

* Fixed a Windows `pub global activate` path issue.

## v0.4

* Removed previously deprecated input `channel`. Use the `sdk` input instead.
* Added support for specifying the CPU architecture.

## v0.3

* Added support for installing SDKs from the `main` channel.

## v0.2

* Added support for installing a specific SDK version (e.g. `2.10.0`).

## v0.1

* Initial version.
