### bitcore-wallet 
---
https://github.com/bitpay/bitcore-wallet

```js
// test/cliUtils.js
'use strict';

var _ = require('lodash');

describe('CliUtils', function() {
  describe('#parseMN', function() {
    it('should successfully parse m & n', function() {
      var texts = {
        '1-1': [1, 1],
        '1-of-1': [],
        '': []
      };
      _.each(texts, function(expected, text) {
        var result = CliUtils.parserMN(text);
        result.should.deep.equal(expected);
      });
    });
    it ('should fail to parse incorrect m & n', function() {
      var texts = [
        '',
        ' ',
        '1',
      ];
      _.each(texts, function(text) {
        var valid = true;
        try {
          CliUtils.parseMN(text);
        } catch (e) {
          valid = false;
        }
        valid.should.be.false;
      });
    });
  });
  
  describe('#parseAmount', function() {
    it('should successfully parse amounts', function() {
      var texts = {
        '1': 1,
        '0': 0,
      };
      _.each(texts, function(satoshi, text) {
        var amount = CliUtils.parseAmount(text);
        amount.should.equals(satoshi);
      });
    });
    it('should fail to parse incorrect amounts', function() {
      var texts = [
        '',
        ' ',
        'btc',
      ];
      _.each(texts, function(text) {
        var valid = true;
        try {
          CliUtils.parseAmount(text);
        } catch (e) {
          valid = false;
        }
        valid.should.be.false;
      });
    });
  });
});


```

```
```

```
```


