# Hello World

## Script tag

This is the simplest demo and it's composed of one single file:

```
script-tag/
└── index.html
```

Explaining the code... The first piece that matters is the script tag that loads
`cldr.js`. It's the only dependency of Globalize.

```html
<script src="cldr.js"></script>
```

You need to manually download `cldr.js` yourself as an exercise of this demo.
See https://github.com/rxaviers/cldr for instructions. Then, copy the file into
`script-tag/`, so you'll get:

```
script-tag/
├── cldr.js
└── index.html
```

The next script tag loads `globalize.js`, which is already available on this
repository. If it's not, it means you're using a development branch (not a
release branch). So, you need to either use a release branch or build the
distribution files yourself. See root's [README](../../README.md) for help.

```html
<script src="../../../dist/globalize.js"></script>
```

Before using Globalize, we need to feed in I18n content (Unicode CLDR). In
order to do so, we use `Globalize.load()` and pass the content as the first
argument. In this demo, we use embedded static JSON. So, no extra step is
required.

```javascript
Globalize.load( ... );
```

Then, we set `en` as our default locale.

```javascript
Globalize.locale( "en" );
```

We run some Globalize functions.

```javascript
Globalize.formatDate( new Date(), { datetime: "medium" } );
Globalize.formatNumber( 12345 );
```

Open your JavaScript console to see the output...
