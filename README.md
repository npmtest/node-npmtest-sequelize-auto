# npmtest-sequelize-auto

#### basic test coverage for  sequelize-auto (v0.4.27)  [![npm package](https://img.shields.io/npm/v/npmtest-sequelize-auto.svg?style=flat-square)](https://www.npmjs.org/package/npmtest-sequelize-auto) [![travis-ci.org build-status](https://api.travis-ci.org/npmtest/node-npmtest-sequelize-auto.svg)](https://travis-ci.org/npmtest/node-npmtest-sequelize-auto)

#### Automatically generate bare sequelize models from your database.

[![NPM](https://nodei.co/npm/sequelize-auto.png?downloads=true&downloadRank=true&stars=true)](https://www.npmjs.com/package/sequelize-auto)

| git-branch : | [alpha](https://github.com/npmtest/node-npmtest-sequelize-auto/tree/alpha)|
|--:|:--|
| coverage : | [![istanbul-coverage](https://npmtest.github.io/node-npmtest-sequelize-auto/build/coverage.badge.svg)](https://npmtest.github.io/node-npmtest-sequelize-auto/build/coverage.html/index.html)|
| test-report : | [![test-report](https://npmtest.github.io/node-npmtest-sequelize-auto/build/test-report.badge.svg)](https://npmtest.github.io/node-npmtest-sequelize-auto/build/test-report.html)|
| build-artifacts : | [![build-artifacts](https://npmtest.github.io/node-npmtest-sequelize-auto/glyphicons_144_folder_open.png)](https://github.com/npmtest/node-npmtest-sequelize-auto/tree/gh-pages/build)|

- [https://npmtest.github.io/node-npmtest-sequelize-auto/build/coverage.html/index.html](https://npmtest.github.io/node-npmtest-sequelize-auto/build/coverage.html/index.html)

[![istanbul-coverage](https://npmtest.github.io/node-npmtest-sequelize-auto/build/screenCapture.buildCi.browser.%252Ftmp%252Fbuild%252Fcoverage.lib.html.png)](https://npmtest.github.io/node-npmtest-sequelize-auto/build/coverage.html/index.html)

- [https://npmtest.github.io/node-npmtest-sequelize-auto/build/test-report.html](https://npmtest.github.io/node-npmtest-sequelize-auto/build/test-report.html)

[![test-report](https://npmtest.github.io/node-npmtest-sequelize-auto/build/screenCapture.buildCi.browser.%252Ftmp%252Fbuild%252Ftest-report.html.png)](https://npmtest.github.io/node-npmtest-sequelize-auto/build/test-report.html)

- [https://npmdoc.github.io/node-npmdoc-sequelize-auto/build/apidoc.html](https://npmdoc.github.io/node-npmdoc-sequelize-auto/build/apidoc.html)

[![apidoc](https://npmdoc.github.io/node-npmdoc-sequelize-auto/build/screenCapture.buildCi.browser.%252Ftmp%252Fbuild%252Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-sequelize-auto/build/apidoc.html)

![npmPackageListing](https://npmtest.github.io/node-npmtest-sequelize-auto/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmtest.github.io/node-npmtest-sequelize-auto/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "name": "sequelize-auto",
    "version": "0.4.27",
    "description": "Automatically generate bare sequelize models from your database.",
    "main": "index",
    "keywords": [
        "mysql",
        "postgres",
        "sequelize",
        "sequelizejs",
        "mapper"
    ],
    "bin": {
        "sequelize-auto": "bin/sequelize-auto"
    },
    "repository": {
        "type": "git",
        "url": "https://github.com/sequelize/sequelize-auto.git"
    },
    "bugs": {
        "url": "https://github.com/sequelize/sequelize-auto/issues"
    },
    "nyc": {
        "exclude": [
            "**/test/**.js"
        ]
    },
    "scripts": {
        "test": "./node_modules/.bin/mocha --globals setImmediate,clearImmediate,__core-js_shared__ --ui tdd --check-leaks --colors -t 15000 --reporter spec \"test/**/*.test.js\"",
        "test-postgres": "./node_modules/.bin/cross-env DIALECT=postgres npm run test",
        "test-mysql": "./node_modules/.bin/cross-env DIALECT=mysql npm run test",
        "test-sqlite": "./node_modules/.bin/cross-env DIALECT=sqlite npm run test",
        "test-mssql": "./node_modules/.bin/cross-env DIALECT=mssql npm run test",
        "cover": "rm -rf coverage && COVERAGE=true ./node_modules/.bin/nyc -r lcov npm run test",
        "cover-mysql": "DIALECT=mysql npm run cover && mv coverage coverage-mysql",
        "cover-sqlite": "DIALECT=sqlite npm run cover && mv coverage coverage-sqlite",
        "cover-postgres": "DIALECT=postgres npm run cover && mv coverage coverage-postgres",
        "cover-postgres-native": "DIALECT=postgres-native npm run cover && mv coverage coverage-postgres-native",
        "cover-all": "npm run cover-mysql && npm run cover-postgres && npm run cover-postgres-native && npm run cover-sqlite && npm run merge-coverage",
        "merge-coverage": "rm -rf coverage && mkdir coverage && ./node_modules/.bin/lcov-result-merger 'coverage-*/lcov.info' 'coverage/lcov.info'",
        "codeclimate-send": "npm install -g codeclimate-test-reporter && CODECLIMATE_REPO_TOKEN=b9a25c5bf4c3875fb46ecb6d3a5f99e49f6872e6b92c074e5725d6dc2cd94f22 codeclimate-test-reporter < coverage/lcov.info",
        "codeclimate": "npm run cover-all && npm run codeclimate-send && npm run clean-coverage",
        "clean-coverage": "rm -rf coverage && rm -rf coverage-*"
    },
    "engines": {
        "node": ">=0.10"
    },
    "author": "Daniel Durante <me@danieldurante.com>",
    "license": "MIT",
    "dependencies": {
        "async": "^2.1.5",
        "graceful-fs-extra": "^2.0.0",
        "mkdirp": "^0.5.1",
        "sequelize": "^3.30.2",
        "yargs": "^6.6.0"
    },
    "devDependencies": {
        "chai": "^3.5.0",
        "cross-env": "^3.2.4",
        "istanbul": "^0.4.5",
        "lcov-result-merger": "^1.2.0",
        "mkdirp": "^0.5.1",
        "mocha": "^3.2.0",
        "mysql": "^2.13.0",
        "nyc": "^10.1.2",
        "pg": "^6.1.5",
        "pg-hstore": "^2.3.2",
        "sqlite3": "^3.1.8",
        "tedious": "^1.14.0"
    }
}
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
