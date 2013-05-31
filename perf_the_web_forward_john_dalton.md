Perf the Web Forward - John Dalton
==================================

/#perffwd

## Me

* <http://jsperf.com>
* <http://lodash.com>
* <http://benchmarkjs.com>
* Perf PM @Microsoft
* All-around JS Fanboy

## Themes

* optimize for teh common case
* use natives wisely
* avoid abstraction
* balance pros/cons

## Hoist call & apply

from this

    function forEach(array, callback, thisArg){
      var index, = -1,
        length = array.length;
      while (++index < length) {
        callback.call(thisArg, array[index], index, array);
      }
    }

to this

    callback = createCallback(callback, thisArg);
    while (++index < length){
      callback(array[index], index, array);
    }

    function createCallback(fun, thisArg){
      if (thisArg === undefined){
        return callback; // this is what make it fast for when thisArg is not present
      }
      return function(value, index, array){
        callback.call(thisArg, value, index, array);
      };
    }

## Avoid Binding

Grep the function source to see if its using a `this` binding to avoid binding if you can. But `Function.prototype.toString` is not exactly a standard.

    var fnToString = Function.prototype.toSTring,
      reThis = /\bthis\b/;

    function on(element, name, fn){
      var listeners = cache[name] || (cache[name] = []);
      listeners.push({
        'fn': fn,
        'ctx': reThis.test(fnToString.call(fn)) && element
      });
      return this;
    }

## Reduce Searches

Array `indexOf` is slow. So you might use an object/hash instead, but keys have to be unique strings. So, another way is to a `cachedContains` function. The function caches values using an object/hash for "large arrays". 

Another technique: have separate caches for each "typeof" value.

## Coerce with Care

A lot of times you don't have to convert `arguments` to an array. Use concat to flatten arrays. INstead of
`concat.apply([], array)` can do `concat.apply(Array.prototype, array)`. You can push more than one element with `push.apply`.

## Sugar in Moderation

Underscore chaining syntax: has a perf panelty. Can use defered eval to improve perf with chaining syntax. <http://dtao.github.io/lazy.js>.

## Links

Twitter: [@jdalton](http://twitter.com/jdalton)