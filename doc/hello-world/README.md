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

To load the I18n content (Unicode CLDR) needed for this demo, we use
`Globalize.load()` and pass as first argument the content, which is an embedded
static JSON in this case.


```javascript
Globalize.load( ... );
```

Then, we set our default locale to `en`.

```javascript
Globalize.locale( "en" );
```

And, run some Globalize functions... Open your JavaScript console to see the output.
