# npmdoc-sbd

#### api documentation for  [sbd (v1.0.12)](http://github.com/Tessmore/sbd)  [![npm package](https://img.shields.io/npm/v/npmdoc-sbd.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-sbd) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-sbd.svg)](https://travis-ci.org/npmdoc/node-npmdoc-sbd)

#### Split text into sentences with Sentence Boundary Detection (SBD).

[![NPM](https://nodei.co/npm/sbd.png?downloads=true&downloadRank=true&stars=true)](https://www.npmjs.com/package/sbd)

- [https://npmdoc.github.io/node-npmdoc-sbd/build/apidoc.html](https://npmdoc.github.io/node-npmdoc-sbd/build/apidoc.html)

[![apidoc](https://npmdoc.github.io/node-npmdoc-sbd/build/screenCapture.buildCi.browser.%252Ftmp%252Fbuild%252Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-sbd/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-sbd/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-sbd/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Fabiën Tesselaar"
    },
    "browser": {
        "sanitize-html": "./lib/sanitize-html-browser.js"
    },
    "bugs": {
        "url": "https://github.com/Tessmore/sbd/issues"
    },
    "dependencies": {
        "sanitize-html": "^1.11.2"
    },
    "description": "Split text into sentences with Sentence Boundary Detection (SBD).",
    "devDependencies": {
        "mocha": "3.0.x"
    },
    "directories": {},
    "dist": {
        "shasum": "cd2288f6158ead8214434cd8209630eb1d94828d",
        "tarball": "https://registry.npmjs.org/sbd/-/sbd-1.0.12.tgz"
    },
    "gitHead": "16ab804fbf51b6a8946be64ce39621005f710b5e",
    "homepage": "http://github.com/Tessmore/sbd",
    "keywords": [
        "sentence",
        "detection",
        "boundary"
    ],
    "license": "MIT",
    "main": "lib/tokenizer.js",
    "maintainers": [
        {
            "name": "tessmore"
        }
    ],
    "name": "sbd",
    "optionalDependencies": {},
    "repository": {
        "type": "git",
        "url": "git+https://github.com/Tessmore/sbd.git"
    },
    "scripts": {
        "build": "npm run build:js && npm run build:minify",
        "build:js": "browserify lib/tokenizer.js --standalone tokenizer > dist/sbd.js",
        "build:minify": "uglifyjs dist/sbd.js > dist/sbd.min.js",
        "test": "mocha -R spec"
    },
    "version": "1.0.12"
}
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
