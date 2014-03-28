# Hello World


## Script tag

This is the simplest demo and it's composed of one single file:

```
script-tag/
└── index.html
```

### Running the demo

1. Download `cldr.js`. See https://github.com/rxaviers/cldr for instructions. Then, copy the file into `script-tag/`, so you'll get:

```
script-tag/
├── cldr.js
└── index.html
```

2. Point your browser to `./script-tag/index.html`.

### Understanding the demo

The first piece that matters is the script tag that loads `cldr.js`. It's the
only dependency of Globalize.

```html
<script src="cldr.js"></script>
```

You need to manually download `cldr.js` yourself as an exercise of this demo as
told above.

The next script tag loads `globalize.js`, which is already available on this
repository. If it's not, it means you're using a development branch (not a
release branch). So, you need to either use a release branch or build the
distribution files yourself. See root's [README](../../README.md) for help.

```html
<script src="../../../dist/globalize.js"></script>
```

Before using Globalize, we always need to feed it on the I18n content (Unicode
CLDR) we are about to use. In order to do so, we use `Globalize.load()` and pass
the content. On this demo, we tried to make things a little easier for you.
So, we are using embedded static JSON, and we don't need to fetch this content
elsewhere.

```javascript
Globalize.load( ... );
```

Then, we set `en` as our default locale.

```javascript
Globalize.locale( "en" );
```

And, we run some Globalize functions.

```javascript
Globalize.formatDate( new Date(), { datetime: "medium" } );
Globalize.formatNumber( 12345 );
```

Remember, when you point your browser at `./script-tag/index.html`, don't forget
to open your JavaScript console to see the demo output...


## AMD

This demo assumes you know what AMD is. It's composed of one single file:

```
amd/
├── index.html
└── main.js
```

### Running the demo

1. Fetch `cldr.js` by using the instructions from Script Tag demo, or by using
`bower install cldr.js`. If you used bower, you'll get:

```
amd/
├── bower_components/
│   └── cldr.js/ 
│       └── dist/
│           ├── cldr
│           │   └── supplemental.js
│           └── cldr.js
├── index.html
└── main.js
```

2. Fetch Unicode CLDR JSON by running `wget http://www.unicode.org/Public/cldr/latest/json.zip && unzip json.zip -d cldr`.
For more information, see root's [README](../../README.md#how-to-get-and-load-cldr-json-data). You'll get:

```
amd/
├── bower_components/
│   └── cldr.js/ 
│       └── dist/
│           ├── cldr
│           │   └── supplemental.js
│           └── cldr.js
├── cldr/
│   ├── main/
│   │   └── ...
│   └── supplemental/
│       └── ...
├── index.html
└── main.js
```

3. Point your browser to `./amd/index.html`.

### Understanding the demo

