# api documentation for  [sbd (v1.0.12)](http://github.com/Tessmore/sbd)  [![npm package](https://img.shields.io/npm/v/npmdoc-sbd.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-sbd) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-sbd.svg)](https://travis-ci.org/npmdoc/node-npmdoc-sbd)
#### Split text into sentences with Sentence Boundary Detection (SBD).

[![NPM](https://nodei.co/npm/sbd.png?downloads=true)](https://www.npmjs.com/package/sbd)

[![apidoc](https://npmdoc.github.io/node-npmdoc-sbd/build/screenCapture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-sbd_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-sbd/build/apidoc.html)

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
            "name": "tessmore",
            "email": "fabientesselaar@gmail.com"
        }
    ],
    "name": "sbd",
    "optionalDependencies": {},
    "readme": "ERROR: No README data found!",
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



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module sbd](#apidoc.module.sbd)
1.  [function <span class="apidocSignatureSpan">sbd.</span>sentences (text, user_options)](#apidoc.element.sbd.sentences)
1.  object <span class="apidocSignatureSpan">sbd.</span>Match
1.  object <span class="apidocSignatureSpan">sbd.</span>String

#### [module sbd.Match](#apidoc.module.sbd.Match)
1.  [function <span class="apidocSignatureSpan">sbd.Match.</span>isBoundaryChar (word)](#apidoc.element.sbd.Match.isBoundaryChar)
1.  [function <span class="apidocSignatureSpan">sbd.Match.</span>isCapitalized (str)](#apidoc.element.sbd.Match.isCapitalized)
1.  [function <span class="apidocSignatureSpan">sbd.Match.</span>isCommonAbbreviation (str)](#apidoc.element.sbd.Match.isCommonAbbreviation)
1.  [function <span class="apidocSignatureSpan">sbd.Match.</span>isConcatenated (word)](#apidoc.element.sbd.Match.isConcatenated)
1.  [function <span class="apidocSignatureSpan">sbd.Match.</span>isCustomAbbreviation (str)](#apidoc.element.sbd.Match.isCustomAbbreviation)
1.  [function <span class="apidocSignatureSpan">sbd.Match.</span>isDottedAbbreviation (word)](#apidoc.element.sbd.Match.isDottedAbbreviation)
1.  [function <span class="apidocSignatureSpan">sbd.Match.</span>isNameAbbreviation (wordCount, words)](#apidoc.element.sbd.Match.isNameAbbreviation)
1.  [function <span class="apidocSignatureSpan">sbd.Match.</span>isNumber (str, dotPos)](#apidoc.element.sbd.Match.isNumber)
1.  [function <span class="apidocSignatureSpan">sbd.Match.</span>isPhoneNr (str)](#apidoc.element.sbd.Match.isPhoneNr)
1.  [function <span class="apidocSignatureSpan">sbd.Match.</span>isSentenceStarter (str)](#apidoc.element.sbd.Match.isSentenceStarter)
1.  [function <span class="apidocSignatureSpan">sbd.Match.</span>isTimeAbbreviation (word, next)](#apidoc.element.sbd.Match.isTimeAbbreviation)
1.  [function <span class="apidocSignatureSpan">sbd.Match.</span>isURL (str)](#apidoc.element.sbd.Match.isURL)
1.  [function <span class="apidocSignatureSpan">sbd.Match.</span>setAbbreviations (abbr)](#apidoc.element.sbd.Match.setAbbreviations)

#### [module sbd.String](#apidoc.module.sbd.String)
1.  [function <span class="apidocSignatureSpan">sbd.String.</span>endsWith (word, end)](#apidoc.element.sbd.String.endsWith)
1.  [function <span class="apidocSignatureSpan">sbd.String.</span>endsWithChar (word, c)](#apidoc.element.sbd.String.endsWithChar)



# <a name="apidoc.module.sbd"></a>[module sbd](#apidoc.module.sbd)

#### <a name="apidoc.element.sbd.sentences"></a>[function <span class="apidocSignatureSpan">sbd.</span>sentences (text, user_options)](#apidoc.element.sbd.sentences)
- description and source-code
```javascript
sentences = function (text, user_options) {
    if (!text || typeof text !== "string" || !text.length) {
        return [];
    }

    var options = {
        "newline_boundaries"  : false,
        "html_boundaries"     : false,
        "html_boundaries_tags": ["p","div","ul","ol"],
        "sanitize"            : false,
        "allowed_tags"        : false,
        "abbreviations"       : null
    };

    if (typeof user_options === "boolean") {
        // Deprecated quick option
        options.newline_boundaries = true;
    }
    else {
        // Extend options
        for (var k in user_options) {
            options[k] = user_options[k];
        }
    }

    Match.setAbbreviations(options.abbreviations);

    if (options.newline_boundaries) {
        text = text.replace(/\n+|[-#=_+*]{4,}/g, newline_placeholder);
    }

    if (options.html_boundaries) {
        var html_boundaries_regexp = "(<br\\s*\\/?>|<\\/(" + options.html_boundaries_tags.join("|") + ")>)";
        var re = new RegExp(html_boundaries_regexp, "g");
        text = text.replace(re, "$1" + newline_placeholder);
    }

    if (options.sanitize || options.allowed_tags) {
        if (! options.allowed_tags) {
            options.allowed_tags = [""];
        }

        text = sanitizeHtml(text, { "allowedTags" : options.allowed_tags });
    }

    // Split the text into words
    // - see http://blog.tompawlak.org/split-string-into-tokens-javascript
    var words = text.trim().match(/\S+|\n/g);

    var wordCount = 0;
    var index = 0;
    var temp  = [];
    var sentences = [];
    var current   = [];

    // If given text is only whitespace (or nothing of \S+)
    if (!words || !words.length) {
        return [];
    }

    for (var i=0, L=words.length; i < L; i++) {
        wordCount++;

        // Add the word to current sentence
        current.push(words[i]);

        // Sub-sentences, reset counter
        if (~words[i].indexOf(',')) {
            wordCount = 0;
        }

        if (Match.isBoundaryChar(words[i])      ||
            String.endsWithChar(words[i], "?!") ||
            words[i] === newline_placeholder_t)
        {
            if ((options.newline_boundaries || options.html_boundaries) && words[i] === newline_placeholder_t) {
                current.pop();
            }

            sentences.push(current);

            wordCount = 0;
            current   = [];

            continue;
        }


        if (String.endsWithChar(words[i], "\"") || String.endsWithChar(words[i], "”")) {
            // endQuote = words[i].slice(-1);
            words[i] = words[i].slice(0, -1);
        }

        // A dot might indicate the end sentences
        // Exception: The next sentence starts with a word (non abbreviation)
        //            that has a capital letter.
        if (String.endsWithChar(words[i], '.')) {
            // Check if there is a next word
            // This probably needs to be improved with machine learning
            if (i+1 < L) {
                // Single character abbr.
                if (words[i].length === 2 && isNaN(words[i].charAt(0))) {
                    continue;
                }

                // Common abbr. that often do not end sentences
                if (Match.isCommonAbbreviation(words[i])) {
                    continue;
                }

                // Next word starts with capital word, but current sentence is
                // quite short
                if (Match.isSentenceStarter(words[i+1])) {
                    if (Match.isTimeAbbreviation(words[i], words[i+1])) {
                        continue;
                    }

                    // Dealing with names at the start of sentences
                    if (Match.isNameAbbreviation(wordCount, words.slice(i, 6))) {
                        continue;
                    }

                    if (Match.isNumber(words[i+1])) {
                        if (Match.isCustomAbbreviation(words[i])) { ...
```
- example usage
```shell
...

## How to

'''javascript
var tokenizer = require('sbd');

var text = "On Jan. 20, former Sen. Barack Obama became the 44th President of the U.S. Millions attended the Inauguration.";
var sentences = tokenizer.sentences(text, optional_options);

// [
//  'On Jan. 20, former Sen. Barack Obama became the 44th President of the U.S.',
//  'Millions attended the Inauguration.',
// ]
'''
...
```



# <a name="apidoc.module.sbd.Match"></a>[module sbd.Match](#apidoc.module.sbd.Match)

#### <a name="apidoc.element.sbd.Match.isBoundaryChar"></a>[function <span class="apidocSignatureSpan">sbd.Match.</span>isBoundaryChar (word)](#apidoc.element.sbd.Match.isBoundaryChar)
- description and source-code
```javascript
isBoundaryChar = function (word) {
    return word === "." ||
           word === "!" ||
           word === "?";
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.sbd.Match.isCapitalized"></a>[function <span class="apidocSignatureSpan">sbd.Match.</span>isCapitalized (str)](#apidoc.element.sbd.Match.isCapitalized)
- description and source-code
```javascript
isCapitalized = function (str) {
    return /^[A-Z][a-z].*/.test(str) || this.isNumber(str);
}
```
- example usage
```shell
...

exports.isCapitalized = function(str) {
    return /^[A-Z][a-z].*/.test(str) || this.isNumber(str);
}

// Start with opening quotes or capitalized letter
exports.isSentenceStarter = function(str) {
    return this.isCapitalized(str) || /''|"|'/.test(str.substring(0,2));
}

exports.isCommonAbbreviation = function(str) {
    return ~abbreviations.indexOf(str.replace(/\W+/g, ''));
}

// This is going towards too much rule based
...
```

#### <a name="apidoc.element.sbd.Match.isCommonAbbreviation"></a>[function <span class="apidocSignatureSpan">sbd.Match.</span>isCommonAbbreviation (str)](#apidoc.element.sbd.Match.isCommonAbbreviation)
- description and source-code
```javascript
isCommonAbbreviation = function (str) {
    return ~abbreviations.indexOf(str.replace(/\W+/g, ''));
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.sbd.Match.isConcatenated"></a>[function <span class="apidocSignatureSpan">sbd.Match.</span>isConcatenated (word)](#apidoc.element.sbd.Match.isConcatenated)
- description and source-code
```javascript
isConcatenated = function (word) {
    var i = 0;

    if ((i = word.indexOf(".")) > -1 ||
        (i = word.indexOf("!")) > -1 ||
        (i = word.indexOf("?")) > -1)
    {
        var c = word.charAt(i + 1);

        // Check if the next word starts with a letter
        if (c.match(/[a-zA-Z].*/)) {
            return [word.slice(0, i), word.slice(i+1)];
        }
    }

    return false;
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.sbd.Match.isCustomAbbreviation"></a>[function <span class="apidocSignatureSpan">sbd.Match.</span>isCustomAbbreviation (str)](#apidoc.element.sbd.Match.isCustomAbbreviation)
- description and source-code
```javascript
isCustomAbbreviation = function (str) {
    if (str.length <= 3) {
        return true;
    }

    return this.isCapitalized(str);
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.sbd.Match.isDottedAbbreviation"></a>[function <span class="apidocSignatureSpan">sbd.Match.</span>isDottedAbbreviation (word)](#apidoc.element.sbd.Match.isDottedAbbreviation)
- description and source-code
```javascript
isDottedAbbreviation = function (word) {
    var matches = word.replace(/[\(\)\[\]\{\}]/g, '').match(/(.\.)*/);
    return matches && matches[0].length > 0;
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.sbd.Match.isNameAbbreviation"></a>[function <span class="apidocSignatureSpan">sbd.Match.</span>isNameAbbreviation (wordCount, words)](#apidoc.element.sbd.Match.isNameAbbreviation)
- description and source-code
```javascript
isNameAbbreviation = function (wordCount, words) {
    if (words.length > 0) {
        if (wordCount < 5 && words[0].length < 6 && this.isCapitalized(words[0])) {
            return true;
        }

        var capitalized = words.filter(function(str) {
            return /[A-Z]/.test(str.charAt(0));
        });

        return capitalized.length >= 3;
    }

    return false;
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.sbd.Match.isNumber"></a>[function <span class="apidocSignatureSpan">sbd.Match.</span>isNumber (str, dotPos)](#apidoc.element.sbd.Match.isNumber)
- description and source-code
```javascript
isNumber = function (str, dotPos) {
    if (dotPos) {
        str = str.slice(dotPos-1, dotPos+2);
    }

    return !isNaN(str);
}
```
- example usage
```shell
...
        abbreviations = abbr;
    } else {
        abbreviations = englishAbbreviations;
    }
}

exports.isCapitalized = function(str) {
    return /^[A-Z][a-z].*/.test(str) || this.isNumber(str);
}

// Start with opening quotes or capitalized letter
exports.isSentenceStarter = function(str) {
    return this.isCapitalized(str) || /''|"|'/.test(str.substring(0,2));
}
...
```

#### <a name="apidoc.element.sbd.Match.isPhoneNr"></a>[function <span class="apidocSignatureSpan">sbd.Match.</span>isPhoneNr (str)](#apidoc.element.sbd.Match.isPhoneNr)
- description and source-code
```javascript
isPhoneNr = function (str) {
    return str.match(/^(?:(?:\+?1\s*(?:[.-]\s*)?)?(?:\(\s*([2-9]1[02-9]|[2-9][02-8]1|[2-9][02-8][02-9])\s*\)|([2-9]1[02-9]|[2-9][
02-8]1|[2-9][02-8][02-9]))\s*(?:[.-]\s*)?)?([2-9]1[02-9]|[2-9][02-9]1|[2-9][02-9]{2})\s*(?:[.-]\s*)?([0-9]{4})(?:\s*(?:#|x\.?|ext\.?|extension)\s*(\d+))?$/);
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.sbd.Match.isSentenceStarter"></a>[function <span class="apidocSignatureSpan">sbd.Match.</span>isSentenceStarter (str)](#apidoc.element.sbd.Match.isSentenceStarter)
- description and source-code
```javascript
isSentenceStarter = function (str) {
    return this.isCapitalized(str) || /''|"|'/.test(str.substring(0,2));
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.sbd.Match.isTimeAbbreviation"></a>[function <span class="apidocSignatureSpan">sbd.Match.</span>isTimeAbbreviation (word, next)](#apidoc.element.sbd.Match.isTimeAbbreviation)
- description and source-code
```javascript
isTimeAbbreviation = function (word, next) {
    if (word === "a.m." || word === "p.m.") {
        var tmp = next.replace(/\W+/g, '').slice(-3).toLowerCase();

        if (tmp === "day") {
            return true;
        }
    }

    return false;
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.sbd.Match.isURL"></a>[function <span class="apidocSignatureSpan">sbd.Match.</span>isURL (str)](#apidoc.element.sbd.Match.isURL)
- description and source-code
```javascript
isURL = function (str) {
    return str.match(/[-a-zA-Z0-9@:%._\+~#=]{2,256}\.[a-z]{2,6}\b([-a-zA-Z0-9@:%_\+.~#?&//=]*)/);
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.sbd.Match.setAbbreviations"></a>[function <span class="apidocSignatureSpan">sbd.Match.</span>setAbbreviations (abbr)](#apidoc.element.sbd.Match.setAbbreviations)
- description and source-code
```javascript
setAbbreviations = function (abbr) {
    if(abbr){
        abbreviations = abbr;
    } else {
        abbreviations = englishAbbreviations;
    }
}
```
- example usage
```shell
n/a
```



# <a name="apidoc.module.sbd.String"></a>[module sbd.String](#apidoc.module.sbd.String)

#### <a name="apidoc.element.sbd.String.endsWith"></a>[function <span class="apidocSignatureSpan">sbd.String.</span>endsWith (word, end)](#apidoc.element.sbd.String.endsWith)
- description and source-code
```javascript
function ends_with(word, end) {
    return word.slice(word.length - end.length) === end;
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.sbd.String.endsWithChar"></a>[function <span class="apidocSignatureSpan">sbd.String.</span>endsWithChar (word, c)](#apidoc.element.sbd.String.endsWithChar)
- description and source-code
```javascript
function ends_with_char(word, c) {
    if (c.length > 1) {
        return c.indexOf(word.slice(-1)) > -1;
    }

    return word.slice(-1) === c;
}
```
- example usage
```shell
n/a
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
