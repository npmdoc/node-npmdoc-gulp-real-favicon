# api documentation for  [gulp-real-favicon (v0.2.2)](https://github.com/RealFaviconGenerator/gulp-real-favicon#readme)  [![npm package](https://img.shields.io/npm/v/npmdoc-gulp-real-favicon.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-gulp-real-favicon) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-gulp-real-favicon.svg)](https://travis-ci.org/npmdoc/node-npmdoc-gulp-real-favicon)
#### Generate a multiplatform favicon with RealFaviconGenerator

[![NPM](https://nodei.co/npm/gulp-real-favicon.png?downloads=true)](https://www.npmjs.com/package/gulp-real-favicon)

[![apidoc](https://npmdoc.github.io/node-npmdoc-gulp-real-favicon/build/screenCapture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-gulp-real-favicon_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-gulp-real-favicon/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-gulp-real-favicon/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-gulp-real-favicon/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Philippe Bernard",
        "email": "philippe@realfavicongenerator.net",
        "url": "https://realfavicongenerator.net/"
    },
    "bugs": {
        "url": "https://github.com/RealFaviconGenerator/gulp-real-favicon/issues"
    },
    "dependencies": {
        "gulp-util": "^3.0.7",
        "rfg-api": "^0.3.0",
        "through2": "^2.0.0"
    },
    "description": "Generate a multiplatform favicon with RealFaviconGenerator",
    "devDependencies": {
        "assert": "^1.3.0",
        "mocha": "^2.3.3",
        "rimraf": "^2.4.3",
        "vinyl": "^1.1.0"
    },
    "directories": {},
    "dist": {
        "shasum": "050c9f68e55ef48a51e3e18eb86299a364391195",
        "tarball": "https://registry.npmjs.org/gulp-real-favicon/-/gulp-real-favicon-0.2.2.tgz"
    },
    "gitHead": "7b111821049c42fbc5a516433695b62105b4bc4c",
    "homepage": "https://github.com/RealFaviconGenerator/gulp-real-favicon#readme",
    "keywords": [
        "gulpplugin",
        "favicon",
        "realfavicongenerator"
    ],
    "license": "MIT",
    "main": "index.js",
    "maintainers": [
        {
            "name": "pbernard_rfg",
            "email": "philippe@realfavicongenerator.net"
        }
    ],
    "name": "gulp-real-favicon",
    "optionalDependencies": {},
    "readme": "ERROR: No README data found!",
    "repository": {
        "type": "git",
        "url": "git+https://github.com/RealFaviconGenerator/gulp-real-favicon.git"
    },
    "scripts": {
        "test": "mocha"
    },
    "version": "0.2.2"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module gulp-real-favicon](#apidoc.module.gulp-real-favicon)
1.  [function <span class="apidocSignatureSpan">gulp-real-favicon.</span>checkForUpdates (currentVersion, callback)](#apidoc.element.gulp-real-favicon.checkForUpdates)
1.  [function <span class="apidocSignatureSpan">gulp-real-favicon.</span>escapeJSONSpecialChars (json)](#apidoc.element.gulp-real-favicon.escapeJSONSpecialChars)
1.  [function <span class="apidocSignatureSpan">gulp-real-favicon.</span>generateFavicon (params, callback)](#apidoc.element.gulp-real-favicon.generateFavicon)
1.  [function <span class="apidocSignatureSpan">gulp-real-favicon.</span>injectFaviconMarkups (htmlMarkups, options)](#apidoc.element.gulp-real-favicon.injectFaviconMarkups)



# <a name="apidoc.module.gulp-real-favicon"></a>[module gulp-real-favicon](#apidoc.module.gulp-real-favicon)

#### <a name="apidoc.element.gulp-real-favicon.checkForUpdates"></a>[function <span class="apidocSignatureSpan">gulp-real-favicon.</span>checkForUpdates (currentVersion, callback)](#apidoc.element.gulp-real-favicon.checkForUpdates)
- description and source-code
```javascript
checkForUpdates = function (currentVersion, callback) {
  rfg.changeLog(currentVersion, function(err, versions) {
    if ((err !== undefined) && (callback !== undefined)) {
      callback(err, versions);
      return;
    }

    if (versions.length > 0) {
      var url = 'https://realfavicongenerator.net/change_log?since=' + currentVersion;
      // Yep, override err so callback receives it as an error
      err = "A new version is available for your favicon. Visit " + url + " for more information.";

      gutil.log(gutil.colors.red(err));
    }
    else {
      gutil.log(gutil.colors.green("Your favicon is up-to-date. Hurray!"));
    }

    if (callback !== undefined) {
      callback(err, versions);
    }
  });
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.gulp-real-favicon.escapeJSONSpecialChars"></a>[function <span class="apidocSignatureSpan">gulp-real-favicon.</span>escapeJSONSpecialChars (json)](#apidoc.element.gulp-real-favicon.escapeJSONSpecialChars)
- description and source-code
```javascript
escapeJSONSpecialChars = function (json) {
  return rfg.escapeJSONSpecialChars(json);
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.gulp-real-favicon.generateFavicon"></a>[function <span class="apidocSignatureSpan">gulp-real-favicon.</span>generateFavicon (params, callback)](#apidoc.element.gulp-real-favicon.generateFavicon)
- description and source-code
```javascript
generateFavicon = function (params, callback) {
  var request = rfg.createRequest({
    apiKey: API_KEY,
    masterPicture: params.masterPicture,
    iconsPath: params.iconsPath,
    design: params.design,
    settings: params.settings,
    versioning: params.versioning
  });

  rfg.generateFavicon(request, params.dest, function(err, data) {
    if (err) {
      throw new gutil.PluginError({
        plugin: PLUGIN_NAME,
        message: err
      });
    }

    fs.writeFileSync(params.markupFile, JSON.stringify(data));

    if (callback !== undefined) {
      callback(err);
    }
  });
}
```
- example usage
```shell
...
  masterPicture: params.masterPicture,
  iconsPath: params.iconsPath,
  design: params.design,
  settings: params.settings,
  versioning: params.versioning
});

rfg.generateFavicon(request, params.dest, function(err, data) {
  if (err) {
    throw new gutil.PluginError({
      plugin: PLUGIN_NAME,
      message: err
    });
  }
...
```

#### <a name="apidoc.element.gulp-real-favicon.injectFaviconMarkups"></a>[function <span class="apidocSignatureSpan">gulp-real-favicon.</span>injectFaviconMarkups (htmlMarkups, options)](#apidoc.element.gulp-real-favicon.injectFaviconMarkups)
- description and source-code
```javascript
injectFaviconMarkups = function (htmlMarkups, options) {
  var stream = through.obj(function(file, enc, cb) {
    if (file.isBuffer()) {
      rfg.injectFaviconMarkups(file.contents, htmlMarkups,
        (typeof options !== undefined) ? options : {}, function(err, html) {
        file.contents = new Buffer(html);
        stream.push(file);
        cb();
      });
    }

    if (file.isStream()) {
      this.emit('error', new gutil.PluginError(PLUGIN_NAME, 'Stream not supported'));
    }
  });

  // returning the file stream
  return stream;
}
```
- example usage
```shell
...
    }
  });
},

injectFaviconMarkups: function(htmlMarkups, options) {
  var stream = through.obj(function(file, enc, cb) {
    if (file.isBuffer()) {
      rfg.injectFaviconMarkups(file.contents, htmlMarkups,
        (typeof options !== undefined) ? options : {}, function(err, html) {
        file.contents = new Buffer(html);
        stream.push(file);
        cb();
      });
    }
...
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
