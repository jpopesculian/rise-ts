[![npm](https://img.shields.io/npm/v/dpos-api-wrapper.svg)](https://npmjs.org/package/dpos-api-wrapper) [![Build Status](https://travis-ci.org/vekexasia/dpos-api-wrapper.svg?branch=master)](https://travis-ci.org/vekexasia/dpos-api-wrapper)  [![Coverage Status](https://coveralls.io/repos/github/vekexasia/dpos-api-wrapper/badge.svg?branch=master)](https://coveralls.io/github/vekexasia/dpos-api-wrapper?branch=master) 

# Dpos Javascript Library

Through this sdk you can interact with a dposAPI node in an easy way. The library works both in the browser and Node.js.

## Documentation

All available methods are available [in the jsdoc](https://vekexasia.github.io/dpos-api-wrapper/interfaces/dposapi.html)

## Quick Start

### Include the library in your browser.

Either download `dist/browser/index.js` or use gitcdn as follows:

```html
<script type="text/javascript" src="https://unpkg.com/dpos-api-wrapper/dist/browser/index.js"></script>
<script>
  dposAPI.nodeAddress = 'http://example.com:5566'; // Set your node url here. (no leading slash)
  
  // ...
</script>

```

### Include it with npm (Suitable also for webpack/browserify)

```bash
npm i dpos-api-wrapper -D
```

```javascript
var dposAPI = require('dpos-api-wrapper').dposAPI;
dposAPI.nodeAddress= 'http://example.com:5566'; // Set your node url here. (no leading slash) 

```


## Compatibility

### Browser Support

![Chrome](https://raw.github.com/alrra/browser-logos/master/src/chrome/chrome_48x48.png) | ![Firefox](https://raw.github.com/alrra/browser-logos/master/src/firefox/firefox_48x48.png) | ![Safari](https://raw.github.com/alrra/browser-logos/master/src/safari/safari_48x48.png) | ![Opera](https://raw.github.com/alrra/browser-logos/master/src/opera/opera_48x48.png) | ![Edge](https://raw.github.com/alrra/browser-logos/master/src/edge/edge_48x48.png) | ![IE](https://raw.github.com/alrra/browser-logos/master/src/archive/internet-explorer_9-11/internet-explorer_9-11_48x48.png) |
--- | --- | --- | --- | --- | --- |
Latest ✔ | Latest ✔ | Latest ✔ | Latest ✔ | Latest ✔ | 8+ ✔ |

[![Browser Matrix](https://saucelabs.com/open_sauce/build_matrix/axios.svg)](https://saucelabs.com/u/axios)

### Node support

Node >= 4.x is fully supported :)

## Examples

All the APIs are designed to be easy to use. You can use both Callbacks or Promises; you decide.

For example you can open a new account by doing. Be aware that all the methods sending a secret over the network are
going to be deprecated:

```javascript
dposAPI.accounts.open('secret', function(error, account) {
  if (!error) {
    // yay!
    console.log(account);
  } else {
    console.log('error: ', error);
  }
  // ...
});
```

or

```javascript
dposAPI.accounts.open('secret')
    .then(function (account) {
      console.log(account);
    })
    .catch(function (error) {
      console.log('error: ', error);
    });
```

which can be even shorter if you write your code in TypeScript or ES6

```javascript
dposAPI.accounts.open('secret')
    .then(console.log)
    .catch(error => console.log('error: ', error));
```


## Advanced Usage

In some cases you need to connect to multiple nodes.

To do so, just use the [newWrapper](https://vekexasia.github.io/dpos-api-wrapper/interfaces/dposapi.html#newwrapper) method:

```javascript
var node1 = dposAPI.newWrapper('http://node1:1234');
var node2 = dposAPI.newWrapper('http://node2:1234');

// interact with node1 & node2 using the same APIs available within 'dposAPI' variable.
```

