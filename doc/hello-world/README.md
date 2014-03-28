# Hello World

This is the simplest demo and it's composed of one single file:

```
./
└── index.html
```

## Running the demo

1) Get Globalize's dependencies. If you download `cldr.js` and copy its `dist/` files into this directory (`hello-world/`), you'll get:

```
./
├── cldr
│   └── supplemental.js
├── cldr.js
└── index.html
```

2) Point your browser to `./index.html`.

## Understanding the demo

First, we load Globalize's dependencies (`cldr.js` and its supplemental module).
Note you are supposed to manually download `cldr.js` yourself as an exercise of
this demo.

```html
<script src="cldr.js"></script>
<script src="cldr/supplemental.js"></script>
```

Next, we load Globalize and its modules. Note they are already available on
this repository. If it's not, it means you're using a development branch (not a
release branch). So, you need to either use a release branch or [build the
distribution files yourself](../../README.md).

```html
<script src="../../../dist/globalize.js"></script>
<script src="../../../dist/globalize/date.js"></script>
<script src="../../../dist/globalize/number.js"></script>
```

At this point, we have Globalize loaded. But, before we can use it, we need to feed it on the appropriate I18n content (Unicode CLDR). In order to do so, we use
`Globalize.load()` and pass the content. On this demo, we made the things a
little easier for you: we've embedded static JSON into the demo. So, you don't
need to actually fetch it elsewhere.

```javascript
Globalize.load( ... );
```

Then, we set `en` as our default locale.

```javascript
Globalize.locale( "en" );
```

Then, we can enjoy Globalize.

```javascript
Globalize.formatDate( new Date(), { datetime: "medium" } );
Globalize.formatNumber( 12345 );
```

Remember, when you point your browser at `./index.html`, don't forget to open
your JavaScript console to see the demo output...
