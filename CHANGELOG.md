# Releases

## Next

## v2.0.0
* DOCS: Major documentation overhaul (https://github.com/TypeStrong/grunt-ts/pull/185)
* DOCS: More sample config for gruntfile (https://github.com/TypeStrong/grunt-ts/pull/166)
* DOCS: changelog is now *newest on top*
* FEAT: support for `files` in gruntfile (https://github.com/TypeStrong/grunt-ts/pull/171)
* FEAT: support watching multiple DIRS. (https://github.com/grunt-ts/grunt-ts/pull/155)
* CHORE: Use lodash instead of underscore (https://github.com/TypeStrong/grunt-ts/pull/161)
* FIX: missing tsc.js will now fail the build step (#177)

## v1.12.0
* ENANCEMENT: Transforms are run even when the compile option is false

## v1.11.13
* FIX: transforms will now pick up a generated references.ts (#148)

## v1.11.12
* FIX: transforms should now work for files with BOM (#146)

## v1.11.11
* import/export transforms can provide an alternate variable name to use instead of the file name (#143)
* Error displayed when `/// ts:???` is detected but no transform exists for `???`

## v1.11.10
* FIX: `///ts:import` and `///ts:ref` will now work with `d.ts` files as well. 

## v1.11.9
* DOCS: recommend `fast:always` with `grunt-contrib-watch` because `spawn:false` breaks under stress (i.e. `interrupt:true`)
* FIX: use `stdout` if not empty. Otherwise fall back to `stderr` (a change introduced in the latest version of the compiler for consistency with other Microsoft compilers) See https://github.com/grunt-ts/grunt-ts/issues/140

## v1.11.8
* Update bundled TypeScript compiler to v1.0.1

## v1.11.7
* Fix: Make `///  ts:import` etc. work same as `///ts:import` i.e. whitespace independent.(#135)

## v1.11.6
* FEAT: Add a `compiler` task option to specify a custom compiler bin path : https://github.com/grunt-ts/grunt-ts/issues/126
* DOCS: Add documentation for transforms (https://github.com/grunt-ts/grunt-ts/issues/85) + `ts:ref`
* DOCS: I don't like `amdLoader` anymore now that we have transforms. So **deprecating** it and moving its docs to its own file.
* DOCS: Moved docs for customizing `html2ts` output into their own file as I want readme to be quick and effective (focused on why).
* DOCS: Add documentation for fast compile
	* All tasks like `grunt-contrib-watch` are supported
	* will not work with `--out`
	* the granularity https://github.com/grunt-ts/grunt-ts/issues/96#issuecomment-38987023

## v1.11.5
* No need to warn when default values are usable. Ref: https://github.com/grunt-ts/grunt-ts/issues/115
* Fix path.join error because of `grunt.task.current.target` : https://github.com/grunt-ts/grunt-ts/issues/118
* Update LKG with self

## v1.11.4
* Add additional error summary for type error vs. code emit preventing error : https://github.com/grunt-ts/grunt-ts/pull/120

## v1.11.3
* Add `failOnTypeErrors` task option. If `false` build succeeds (exit code 0) if JS can be emitted successfully. More : https://github.com/grunt-ts/grunt-ts/pull/103

## v1.11.2
* Add `///ts:ref` transform for reference tags
* change `'./../path/to/file'` to be `'../path/to/file'` when doing transforms

## v1.11.1
* Do not update templateCache if previous file is same as the new calculated one

## v1.11.0
* Fix LKG https://github.com/grunt-ts/grunt-ts/issues/97 i.e. `grunt upgrade`
* Cleanup `.npmignore`
* **Breaking Change**: Update the bundled TSC to v1.0.0
* **Breaking Change**: Remove `index` option (https://github.com/grunt-ts/grunt-ts/issues/68). This has been replaced by transformers. Plus the blindly created index is unreliable for when we have any file that doesn't `export` anything.

## v1.10.0
* **Breaking Change**: updated `fast` task option to have three levels: https://github.com/grunt-ts/grunt-ts/issues/96#issuecomment-38987023 `watch` (default) | `always` | `never`. If you never specified it than you don't need to do anything as the new default `'watch'` is same as old default `true`
* use grunt-ts to smoothe grunt-ts development workflow
* Update LKG is automatic at the moment because of https://github.com/grunt-ts/grunt-ts/issues/97

## v1.9.3
* Update cache hashed filename to be more intuitive : https://github.com/grunt-ts/grunt-ts/issues/96#issuecomment-38985020
* Change `baseDir` temporary file to be less intrusive : https://github.com/grunt-ts/grunt-ts/issues/77#issuecomment-38983764

## v1.9.2
* Fix: if fast compiling and user specified an `outDir` but `baseDir` isn't specified, figure one out based on the target src glob. (https://github.com/grunt-ts/grunt-ts/issues/77#issuecomment-37714430)
* Chore: updated chokidar https://github.com/grunt-ts/grunt-ts/pull/94

## v1.9.1
* Fix: Automatically clear the `.tscache` on loading `grunt-ts` task. https://github.com/grunt-ts/grunt-ts/issues/81

## v1.9.0
* **Breaking change**: `reference.ts` generation now does EOL based on the current OS. This is the only rational reasonable way to handle EOLs.
* **Breaking change**: `fast:true` is now the default. This means that your project might not be build ready just because the last `ts:compile` succeeded. You should add a task to clean `.tscache` and recompile everything for that safety before you push to the build server.
