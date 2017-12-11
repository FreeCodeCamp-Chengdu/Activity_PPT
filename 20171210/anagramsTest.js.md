##  anagramsTest.js

```javascript
'use strict';

const answer  = require('./hiker.js');
const assert = require('assert');

assert.equal(answer.permutations("ab") instanceof Array, true);
assert.equal(answer.permutations("ab").toString(), ["ab","ba"].toString());
assert.equal(answer.permutations("a").toString(), "a");
assert.equal(answer.permutations("abc").toString(), ["abc","bac","bca","acb","cab","cba"].toString());
assert.equal(answer.permutations("aabbcc").length, 90);
assert.equal(answer.permutations("abcd").length, 24);
assert.equal(answer.permutations("abcd").length, answer.getAnaNum("abcd"));
assert.equal(answer.getAnaNum("biro"), 24);
assert.equal(answer.getAnaNum("abcde"), 120);
assert.equal(answer.getAnaNum("cass"), 12);
assert.equal(answer.getAnaNum("haaa"), 4);


// Do not remove this line.
// It is the green-traffic-llight pattern.
console.log('All tests passed');
```

## anagrams.js

```javascript
'use strict';


function factorial (num) { 
  if (num < 0) { 
    return -1; 
  } 
  else if (num === 0 || num === 1) { 
    return 1; 
  } else { 
    return (num * factorial(num - 1)); 
  } 
}


function getAnaNum(str) { //计算排列后的个数
  var length  = str.length;
  var result = factorial(length);
  var strObj = {};
  for (var i = 0; i < str.length; i++) {
    if (!strObj[str[i]]){
      strObj[str[i]] = 0;
    }
    strObj[str[i]]++;
  }
  
  for (var value in strObj) {
    result = result / factorial(strObj[value]);
  }  
  return result;
}

function permutations(string) {
   var result=[];
    if(string.length === 1){
        return [string];
    }else{
        var preResult=permutations(string.slice(1));
        for (var j = 0; j < preResult.length; j++) {
            for (var k = 0; k < preResult[j].length+1; k++) {
                 var temp = preResult[j].slice(0,k)+string[0]+preResult[j].slice(k);
                    result.push(temp);         
                }
            }
        return unique(result);
    }  
}


function unique(arr) {
  var ret = [];

  for (var i = 0; i < arr.length; i++) {
    var item = arr[i];
    if (ret.indexOf(item) === -1) {
      ret.push(item);
    }
  }
  return ret;
}

module.exports.getAnaNum = getAnaNum;
module.exports.permutations = permutations;

```

