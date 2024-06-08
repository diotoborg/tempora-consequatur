# @diotoborg/tempora-consequatur <sup>[![Version Badge][npm-version-svg]][package-url]</sup>

[![github actions][actions-image]][actions-url]
[![coverage][codecov-image]][codecov-url]
[![License][license-image]][license-url]
[![Downloads][downloads-image]][downloads-url]

[![npm badge][npm-badge-png]][package-url]

Define a data property on an object. Will fall back to assignment in an engine without descriptors.

The three `non*` argument can also be passed `null`, which will use the existing state if available.

The `loose` argument will mean that if you attempt to set a non-normal data property, in an environment without descriptor support, it will fall back to normal assignment.

## Usage

```javascript
var defineDataProperty = require('@diotoborg/tempora-consequatur');
var assert = require('assert');

var obj = {};
defineDataProperty(obj, 'key', 'value');
defineDataProperty(
	obj,
	'key2',
	'value',
	true, // nonEnumerable, optional
	false, // nonWritable, optional
	true, // nonConfigurable, optional
	false // loose, optional
);

assert.deepEqual(
	Object.getOwnPropertyDescriptors(obj),
	{
		key: {
			configurable: true,
			enumerable: true,
			value: 'value',
			writable: true,
		},
		key2: {
			configurable: false,
			enumerable: false,
			value: 'value',
			writable: true,
		},
	}
);
```

[package-url]: https://npmjs.org/package/@diotoborg/tempora-consequatur
[npm-version-svg]: https://versionbadg.es/ljharb/@diotoborg/tempora-consequatur.svg
[deps-svg]: https://david-dm.org/ljharb/@diotoborg/tempora-consequatur.svg
[deps-url]: https://david-dm.org/ljharb/@diotoborg/tempora-consequatur
[dev-deps-svg]: https://david-dm.org/ljharb/@diotoborg/tempora-consequatur/dev-status.svg
[dev-deps-url]: https://david-dm.org/ljharb/@diotoborg/tempora-consequatur#info=devDependencies
[npm-badge-png]: https://nodei.co/npm/@diotoborg/tempora-consequatur.png?downloads=true&stars=true
[license-image]: https://img.shields.io/npm/l/@diotoborg/tempora-consequatur.svg
[license-url]: LICENSE
[downloads-image]: https://img.shields.io/npm/dm/@diotoborg/tempora-consequatur.svg
[downloads-url]: https://npm-stat.com/charts.html?package=@diotoborg/tempora-consequatur
[codecov-image]: https://codecov.io/gh/ljharb/@diotoborg/tempora-consequatur/branch/main/graphs/badge.svg
[codecov-url]: https://app.codecov.io/gh/ljharb/@diotoborg/tempora-consequatur/
[actions-image]: https://img.shields.io/endpoint?url=https://github-actions-badge-u3jn4tfpocch.runkit.sh/ljharb/@diotoborg/tempora-consequatur
[actions-url]: https://github.com/diotoborg/tempora-consequatur/actions
