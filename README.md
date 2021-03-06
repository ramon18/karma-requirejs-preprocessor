# karma-requirejs-preprocessor [![NPM version](https://badge.fury.io/js/karma-requirejs-preprocessor.svg)](http://badge.fury.io/js/karma-requirejs-preprocessor)

> Karma preprocessor to create special requirejs config for tests

## Install with [npm](npmjs.org)

```sh
npm install karma-requirejs-preprocessor
```

## Usage

```js
//Karma config
module.exports = function(config) {
  config.set({
  
      files: [
          ...
          
          //load original RequireJs config
          'src/requirejsconfig.js'
      ],

  
      preprocessors: {
          'src/requirejsconfig.js': 'requirejs' //original RequireJs config
      },
    
      requirejsPreprocessor: {
          config: { //test RequireJs config
              baseUrl: '/base/src/', //replace baseUrl of original config
              paths: { //extend paths of original config
                  angularMocks: 'vendor/angular-mocks/angular-mocks'
              },
              shim:  { //extend shim of original config
                  angularMocks: ['angular']
              },
              deps:  [ //replace deps of original config
                  'angularMocks'
              ]
          },
          testRegexp: '(spec|test)\.js$' //Should be a valid regular expression
      },
  });
};
```


## API
### requirejsPreprocessor

##### config
Type: `Object`

RequireJS config for test environment

##### testRegexp
Type: `String`

Custom regular expression for test files searching. Used in instantiating a new RegExp object. Default `spec\.js$`



## License

© Oleg Istomin 2015.
Released under the MIT license

***
