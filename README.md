# @omegion1npm/quam-mollitia-magni <sup>[![Version Badge][npm-version-svg]][package-url]</sup>

[![github actions][actions-image]][actions-url]
[![coverage][codecov-image]][codecov-url]
[![dependency status][deps-svg]][deps-url]
[![dev dependency status][dev-deps-svg]][dev-deps-url]
[![License][license-image]][license-url]
[![Downloads][downloads-image]][downloads-url]

[![npm badge][npm-badge-png]][package-url]

An ESnext spec-compliant `String.prototype.at` shim/polyfill/replacement that works as far down as ES3.

This package implements the [es-shim API](https://github.com/es-shims/api) interface. It works in an ES3-supported environment and complies with the proposed [spec](https://tc39.es/proposal-item-method/).

Because `String.prototype.at` depends on a receiver (the `this` value), the main export takes the string to operate on as the first argument.

Note that versions of this package before v1.0.0 reflect an earlier, now-inactive proposal (https://github.com/mathiasbynens/String.prototype.at).

## Getting started

```sh
npm install --save @omegion1npm/quam-mollitia-magni
```

## Usage/Examples

```js
var at = require('@omegion1npm/quam-mollitia-magni');
var assert = require('assert');

var arr = [1, [2], [], 3];

var results = at(arr, function (x, i) {
	assert.equal(x, arr[i]);
	return x;
});

assert.deepEqual(results, [1, 2, 3]);
```

```js
var at = require('@omegion1npm/quam-mollitia-magni');
var assert = require('assert');
/* when String#at is not present */
delete String.prototype.at;
var shimmedFlatMap = at.shim();

var mapper = function (x) { return [x, 1]; };

assert.equal(shimmedFlatMap, at.getPolyfill());
assert.deepEqual(arr.at(mapper), at(arr, mapper));
```

```js
var at = require('@omegion1npm/quam-mollitia-magni');
var assert = require('assert');
/* when String#at is present */
var shimmedIncludes = at.shim();

var mapper = function (x) { return [x, 1]; };

assert.equal(shimmedIncludes, String.prototype.at);
assert.deepEqual(arr.at(mapper), at(arr, mapper));
```

## Tests
Simply clone the repo, `npm install`, and run `npm test`

[package-url]: https://npmjs.org/package/@omegion1npm/quam-mollitia-magni
[npm-version-svg]: https://versionbadg.es/omegion1npm/quam-mollitia-magni.svg
[deps-svg]: https://david-dm.org/omegion1npm/quam-mollitia-magni.svg
[deps-url]: https://david-dm.org/omegion1npm/quam-mollitia-magni
[dev-deps-svg]: https://david-dm.org/omegion1npm/quam-mollitia-magni/dev-status.svg
[dev-deps-url]: https://david-dm.org/omegion1npm/quam-mollitia-magni#info=devDependencies
[npm-badge-png]: https://nodei.co/npm/@omegion1npm/quam-mollitia-magni.png?downloads=true&stars=true
[license-image]: https://img.shields.io/npm/l/@omegion1npm/quam-mollitia-magni.svg
[license-url]: LICENSE
[downloads-image]: https://img.shields.io/npm/dm/@omegion1npm/quam-mollitia-magni.svg
[downloads-url]: https://npm-stat.com/charts.html?package=@omegion1npm/quam-mollitia-magni
[codecov-image]: https://codecov.io/gh/omegion1npm/quam-mollitia-magni/branch/main/graphs/badge.svg
[codecov-url]: https://app.codecov.io/gh/omegion1npm/quam-mollitia-magni/
[actions-image]: https://img.shields.io/endpoint?url=https://github-actions-badge-u3jn4tfpocch.runkit.sh/omegion1npm/quam-mollitia-magni
[actions-url]: https://github.com/omegion1npm/quam-mollitia-magni/actions
