# Hello World (AMD + bower)

We assume you know what AMD and bower is. This demo is composed of the following
file structure.

```
./
├── index.html
└── main.js
```

## Running the demo

1) Get Globalize's dependencies. By using bower, you'll get:

```
./
├── bower_components/
│   └── cldr.js/ 
│       └── dist/
│           ├── cldr
│           │   └── supplemental.js
│           └── cldr.js
├── index.html
└── main.js
```

2) Get Unicode CLDR JSON content. By downloading the
[latest/json.zip](http://www.unicode.org/Public/cldr/latest/json.zip) and
unzipping it into `cldr/`, you'll get:

```
./
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

3) Point your browser to `./index.html`.

## Understanding the demo


