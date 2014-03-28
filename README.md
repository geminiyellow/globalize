# Globalize

[![Build Status](https://secure.travis-ci.org/jquery/globalize.png)](http://travis-ci.org/jquery/globalize)
[![devDependency Status](https://david-dm.org/jquery/globalize/dev-status.png)](https://david-dm.org/jquery/globalize#info=devDependencies)

A JavaScript library for internationalization and localization that leverage the
official [Unicode CLDR](http://cldr.unicode.org/) JSON data. The library works both for the browser and as a
Node.js module.

- [Heads up!](#heads_up)
  - [This is an alpha 1.x version](#alpha)
  - [Not accepting 0.x fixes anymore](#0.x-fixes)
- [About Globalize](#about)
  - [Why globalization?](#why)
  - [Where to use it?](#where)
  - [Where does the data come from?](#cldr)
  - [Only load and use what you need](#modules)
  - [Browser support](#where)
- [Getting started](#getting_started)
  - [Hello World](#hello_world)
  - [Usage](#usage)
  - [How to get and load CLDR JSON data](#cldr_usage)
- [API](#api)
  - [Core](#core)
    - [Globalize.load](#load)
    - [Globalize.locale](#locale)
  - [Number module](#number_module)
    - [Globalize.formatNumber](#format_number)
    - [Globalize.parseNumber](#parse_number)
  - [Date module](#date_module)
    - [Globalize.formatDate](#format_date)
    - [Globalize.parseDate](#parse_date)
  - [Translate module](#translate_module)
    - [Globalize.loadTranslation](#load_translations)
    - [Globalize.translate](#translate)
  - more to come...
- [Development](#development)
  - [File structure](#file_structure)
  - [Source files](#source_files)
  - [Build](#build)
  - [Tests](#tests)


<a name="heads_up"></a>
## Heads up!

<a name="alpha"></a>
### This is an alpha 1.x version
We're working on the migration to using the Unicode CLDR. This is an alpha
version of Globalize. In other words, this is not a software for production
environment (yet).

<a name="0.x-fixes"></a>
### Not accepting 0.x fixes anymore

Patches to the previous 0.x codebase probably can't be used. If you have a
problem, please create an issue first before trying to patch it.

Are you looking for 0.x docs? Find them [here](https://github.com/jquery/globalize/tree/79ae658b842f75f58199d6e9074e01f7ce207468).


<a name="about"></a>
## About Globalize

<a name="why"></a>
### Why globalization?

Each language, and the countries that speak that language, have different
expectations when it comes to how numbers (including currency and percentages)
and dates should appear. Obviously, each language has different names for the
days of the week and the months of the year. But they also have different
expectations for the structure of dates, such as what order the day, month and
year are in. In number formatting, not only does the character used to
delineate number groupings and the decimal portion differ, but the placement of
those characters differ as well.

A user using an application should be able to read and write dates and numbers
in the format they are accustomed to. This library makes this possible,
providing an API to convert user-entered number and date strings - in their
own format - into actual numbers and dates, and conversely, to format numbers
and dates into that string format.

<a name="where"></a>
### Where to use it?

It's designed to work both in the [browser](#browser_support), or in
[Node.js](#usage). It supports both [AMD](#usage) and [CommonJS](#usage).

<a name="cldr"></a>
### Where does the data come from?

Globalize uses the [Unicode CLDR](http://cldr.unicode.org/), the largest and
most extensive standard repository of locale data.

We do NOT embed any i18n data within our library. However, we make it really
easy to use. Read [How to get and load CLDR JSON data](#cldr_usage) for more
information on its usage.

<a name="modules"></a>
### Pick the modules you need

| File | Minified size | Summary |
|---|--:|---|
| globalize.js | 0.4KB | [Core library](#core) |
| globalize/date.js | +9.2KB | [Date module](#date_module) provides date formatting and parsing |
| globalize/number.js | +3.7KB | [Number module](#number_module) provides number formatting and parsing |
| globalize/translate.js | +0.7KB | [Translate module](#translate_module) provides message translation |
<!--- By updating this table, also update its clone in #globalize_usage -->

<a name="browser_support"></a>
### Browser Support

We officialy support http://jquery.com/browser-support/. If you find any bugs,
please just [let us know](https://github.com/jquery/globalize/issues).


<a name="getting_started"></a>
## Getting Started

<a name="hello_world"></a>
### Hello World

An example is worth a thousand words. Check out our [Hello
World](doc/hello-world/) demo. Also, note that we have the same Hello World demo
in two different flavors: [AMD + bower](doc/hello-world-amd-bower/), and
[Node.js + npm](doc/hello-world-node-npm/).

<a name="usage"></a>
### Usage

1. Get and load Globalize's dependencies.
1. Get and load the appropriate Unicode CLDR JSON content you are about to use.
1. Get and load Globalize.

<a name="dependencies"></a>
#### Globalize's dependencies

| Dependency | Summary |
|---|---|
| [cldr.js](https://github.com/rxaviers/cldr) | CLDR low level manipulation tool (analogous to what sizzle is for jQuery Core) |

The only Globalize dependency is `cldr.js` and you need to load it prior to
using Globalize. [Learn more about how to get and use it by clicking
here](doc/usage/dependencies.md).

<a name="cldr_usage"></a>
#### Unicode CLDR (the i18n content)

Globalize is the i18n software, and Unicode CLDR is the i18n content. It's
analogous to Globalize being the engine, and Unicode CLDR being the fuel.

You need to feed Globalize on the appropriate portions of CLDR prior to using
it.

*How do I figure out which CLDR portions are the appropriate ones?*

On the [API documentation](#api), each Globalize function specifies which CLDR
portions they require.

*How am I supposed to get and load CLDR content?*

Learn [how to get and load CLDR content](doc/usage/cldr.md).

<a name="globalize_usage"></a>
#### Globalize (the i18n software)

Globalize can be used for a variety of different I18n tasks (format or parse
dates, format or parse numbers, format messages, etc). Therefore, you may
NOT need Globalize in its entirety. For that reason, we made it modular, so you
can pick the pieces you need.

Globalize's consumable-files are located in the `./dist` directory. If you don't
find it, it's because you are using a development branch. You should either use
a [released branch](doc/usage/globalize.md) or [build the distrubution files
yourself](#build). The files are:

| File | Minified size | Summary |
|---|--:|---|
| globalize.js | 0.4KB | [Core library](#core) |
| globalize/date.js | +9.2KB | [Date module](#date_module) provides date formatting and parsing |
| globalize/number.js | +3.7KB | [Number module](#number_module) provides number formatting and parsing |
| globalize/translate.js | +0.7KB | [Translate module](#translate_module) provides message translation |
<!--- By updating this table, also update its clone in #modules -->

Learn more on [how to get a Globalize release, load and use
it](doc/usage/globalize.md).


<a name="api"></a>
## API

<a name="core"></a>
### Core module

<a name="load"></a>
#### `Globalize.load( cldrJSONData )`

This method allows you to load CLDR JSON locale data. `Globalize.load()` is a proxy to `Cldr.load()`. For more information, see https://github.com/rxaviers/cldr#readme.

Parameters:

- **cldrJSONData** A JSON object with CLDR data. See ["How to get and load CLDR
  JSON data" above](#cldr_usage) for more information and examples;

<a name="locale"></a>
#### `Globalize.locale( [locale] )`

Set default locale, or get it if locale argument is omitted.

Parameters:

- **locale** The locale string, eg. "en", "pt_BR", or "zh_Hant_TW".

An application that supports globalization and/or localization will need to
have a way to determine the user's preference. Attempting to automatically
determine the appropriate culture is useful, but it is good practice to always
offer the user a choice, by whatever means.

Whatever your mechanism, it is likely that you will have to correlate the
user's preferences with the list of locale data supported in the app. This
method allows you to select the best match given the locale data that you
have included and to set the Globalize locale to the one which the user
prefers.

```javascript
Globalize.locale( "pt" );
console.log( Globalize.locale().attributes );
// {
//    "languageId": "pt",
//    "maxLanguageId": "pt_Latn_BR",
//    "language": "pt",
//    "script": "Latn",
//    "territory": "BR",
//    "region": "BR"
// }
```

LanguageMatching TBD (CLDR's spec http://www.unicode.org/reports/tr35/#LanguageMatching).


<a name="number_module"></a>
### Number module

<a name="format_number"></a>
#### `Globalize.formatNumber( value [, attributes] [, locale] )`

Format a number according to the given attributes and the given locale (or the
default locale if not specified).

Parameters:

- **value** Number to be formatted, eg. `3.14`;
- **attributes** Optional
  - style: Optional String `decimal` (default), or `percent`;
  - minimumIntegerDigits: Optional non-negative integer Number value indicating
    the minimum integer digits to be used. Numbers will be padded with leading
    zeroes if necessary;
  - minimumFractionDigits and maximumFractionDigits: Optional non-negative
    integer Number values indicating the minimum and maximum fraction digits to
    be used. Numbers will be rounded or padded with trailing zeroes if
    necessary;
  - minimumSignificantDigits and maximumSignificantDigits: Optional positive
    integer Number values indicating the minimum and maximum fraction digits to
    be shown. Either none or both of these properties are present; if they are,
    they override minimum and maximum integer and fraction digits. The formatter
    uses however many integer and fraction digits are required to display the
    specified number of significant digits;
  - round: Optional String with rounding method `ceil`, `floor`, `round`
    (default), or `truncate`;
  - useGrouping: Optional boolean (default is true) value indicating whether a
    grouping separator should be used;
- **locale** Optional locale string that overrides default;

```javascript
Globalize.locale( "en" );
Globalize.formatNumber( 3.141592 );           // "3.142"
Globalize.formatNumber( 3.141592, {}, "es" ); // "3,142"
Globalize.formatNumber( 3.141592, {}, "ar" ); // "3٫142"
```

Controlling digits by specifying integer and fraction digits counts:

```
Globalize.formatNumber( 3.141592, { maximumFractionDigits: 2 } );
// "3.14"

Globalize.formatNumber( 1.5, { minimumFractionDigits: 2 } );
// "1.50"
```

Controlling digits by specifying significant digits counts:

```
Globalize.formatNumber( 3.141592, {
  minimumSignificantDigits: 1,
  maximumSignificantDigits: 3
});
// "3.14"

Globalize.formatNumber( 12345, {
  minimumSignificantDigits: 1,
  maximumSignificantDigits: 3
});
// "12,300"

equal( Globalize.formatNumber( 0.00012345, {
    minimumSignificantDigits: 1,
    maximumSignificantDigits: 3
});
// "0.000123"
```

Using different rounding functions example:

```
Globalize.formatNumber( 3.141592, { maximumFractionDigits: 2, round: "ceil" } );
// "3.15"
```

<a name="parse_number"></a>
#### `Globalize.parseNumber( value, [formats], [locale] )`

TBD


<a name="date_module"></a>
### Date module

<a name="format_date"></a>
#### `Globalize.formatDate( value, format [, locale] )`

Format a date according to the given format and locale (or the current locale if not specified).

Parameters:

- **value** Date instance to be formatted, eg. `new Date()`;
- **format**
  - String, skeleton. Eg "GyMMMd";
  - Object, accepts either one:
    - Skeleton, eg. `{ skeleton: "GyMMMd" }`. List of all skeletons [TODO];
    - Date, eg. `{ date: "full" }`. Possible values are full, long, medium, short;
    - Time, eg. `{ time: "full" }`. Possible values are full, long, medium, short;
    - Datetime, eg. `{ datetime: "full" }`. Possible values are full, long, medium, short;
    - Raw pattern, eg. `{ pattern: "dd/mm" }`. [List of all date
      patterns](http://www.unicode.org/reports/tr35/tr35-dates.html#Date_Field_Symbol_Table);
- **locale** Optional locale string that overrides default;

```javascript
Globalize.formatDate( new Date( 2010, 10, 30, 17, 55 ), { datetime: "short" } );
// "11/30/10, 5:55 PM"

Globalize.formatDate( new Date( 2010, 10, 30, 17, 55 ), { datetime: "short" }, "de" );
// "30.11.10 17:55"
```

Comparison between different locales.

| locale | `Globalize.formatDate( new Date( 2010, 10, 1, 17, 55 ), { datetime: "short" } )` |
| --- | --- |
| **en** | `"11/1/10, 5:55 PM"` |
| **en_GB** | `"01/11/2010 17:55"` |
| **de** | `"01.11.10 17:55"` |
| **zh** | `"10/11/1 下午5:55"` |
| **ar** | `"1‏/11‏/2010 5:55 م"` |
| **pt** | `"01/11/10 17:55"` |
| **es** | `"1/11/10 17:55"` |

<a name="parse_date"></a>
#### `Globalize.parseDate( value [, formats] [, locale] )`

Parse a string representing a date into a JavaScript Date object, taking into
account the given possible formats (or the given locale's set of preset
formats if not provided). As before, the current locale is used if one is not
specified.

Parameters:

- **value** String with date to be parsed, eg. `"11/1/10, 5:55 PM"`;
- **formats** Optional array of formats;
- **locale** Optional locale string that overrides default

```javascript
Globalize.locale( "en" );
Globalize.parseDate( "1/2/13" );
// Wed Jan 02 2013 00:00:00

Globalize.locale( "es" );
Globalize.parseDate( "1/2/13" );
// Fri Feb 01 2013 00:00:00
```


<a name="translate_module"></a>
### Translate module

<a name="load_translations"></a>
#### `Globalize.loadTranslation( locale, translationData )`

Load translation data per locale.

Parameters:
- **locale** Locale string;
- **translationData** A JSON object with translation mappings;

```javascript
Globalize.loadTranslation( "pt_BR", {
  greetings: {
    hello: "Olá",
    bye: "Tchau"
  }
});
```

<a name="translate"></a>
#### `Globalize.translate( path [, locale] )`

Translate item given its path.

Parameters:
- **path** Translation item path;
- **locale** Optional locale string that overrides default

```javascript
Globalize.locale( "pt_BR" );
Globalize.translate( "greetings/bye" );
// ➡ "Tchau"
```


<a name="development"></a>
## Development

<a name="file_structure"></a>
### File structure
```
├── bower.json (metadata file)
├── CONTRIBUTING.md (doc file)
├── dist/ (output of built bundles)
├── external/ (external dependencies, eg. cldr.js, QUnit, RequireJS)
├── Gruntfile.js (Grunt tasks)
├── LICENSE (license file)
├── package.json (metadata file)
├── README.md (doc file)
├── src/ (source code)
│   ├── build/ (build helpers, eg. intro, and outro)
│   ├── common/ (common function helpers across modules)
│   ├── core.js (core module)
│   ├── date/ (date source code)
│   ├── date.js (date module)
│   ├── translate.js (translate module)
│   └── util/ (basic JavaScript helpers polyfills, eg array.map)
└── test/ (unit and functional test files)
    ├── fixtures/ (CLDR fixture data)
    ├── functional/ (functional tests)
    ├── functional.html
    ├── functional.js
    ├── unit/ (unit tests)
    ├── unit.html
    └── unit.js
```

<a name="source_files"></a>
### Source files

The source files are as granular as possible. When combined to generate the
build file, all the excessive/overhead wrappers are cut off. It's following
the same build model of jQuery and Modernizr.

Core, and all modules' public APIs are located in the `src/` directory. For
example: `core.js`, `date.js`, and `translate.js`.

<a name="build"></a>
### Build

Install Grunt and external dependencies. First, install the
[grunt-cli](http://gruntjs.com/getting-started#installing-the-cli) and
[bower](http://bower.io/) packages if you haven't before. These should be installed
globally (like this: `npm install -g grunt-cli bower`). Then:

```bash
npm install && bower install
```

Build distribution files.
```bash
grunt
```

<a name="tests"></a>
### Tests

Tests can be run either in the browser or using Node.js (via Grunt).

***Unit tests***

To run the unit tests, run `grunt test:unit`, or open
`file:///.../globalize/test/unit.html` in a browser. It tests the very specific functionality
of each function (sometimes internal/private).

The goal of the unit tests is to make it easy to spot bugs, easy to debug.

***Functional tests***

To run the functional tests, create the dist files by running `grunt`. Then, run
`grunt test:functional`, or open
`file:///.../globalize/test/functional.html` in a browser. Note that `grunt` will
automatically run unit and functional tests for you to ensure the built files
are safe.

The goal of the functional tests is to ensure that everything works as expected when it is combined.
