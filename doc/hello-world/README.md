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
repository.

```html
<script src="../../../dist/globalize.js"></script>
```

To load the I18n content (Unicode CLDR) needed for this demo, we use
`Globalize.load()` and pass an embedded static JSON.


```javascript
Globalize.load( ... );
```

Then, we set the current locale to `en`.

```javascript
Globalize.locale( "en" );
```

And, run some Globalize functions... Open your JavaScript console to see the output.
