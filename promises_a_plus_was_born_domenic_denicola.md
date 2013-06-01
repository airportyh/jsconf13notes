Boom! Promises/A+ Was Born - Domenic Denicola
=============================================

Twitter @domenic

## JS community's greatest strength

> We turn tiny primitives into powerful patterns.

One example of ES6 modules, turning hacks into language feature. Streams, event emitter, chainable. 

## It's also our Greatest Weakness

We get stuck with these patterns and refuse to learn other patterns.

* Promises/A+ Story is about how we overcame this
* Let's talk about async, JS made it popular, but it's been there before. 
* continuation passing style: with node example. Node just stuck with what the DOM is doing. The moar functions trap.
* CPS is easy, but not simple - traps you in turing tarpit - it's all turing complete anyway, I'll just make it all work by reinventing a lot of things.
* Thus Promises. History:
  - Joule and E
  - Java: Future
  - Python, F#, .Net, C++, Dart
  - and now Javascript

When that many different languages are using the same pattern it means it's really good and that people have agreed it's a good solution.

* Point of Promises: give you back async versions of return and throw

## Generators

Generators are here in Chrome Canary!

    function * someNumbers(){
      yield 1;
      yield 2;
    }

    var iter = someNumbers();
    console.log(iter.next()); // {value: 1, done: false}
    console.log(iter.next()); // {value: 2, done: true}

Now a Q example

    Q.async(function* (){
      $('#loading').text("Loading...").findeIn();

      try{
        var repoEvents = yield getRepoEvents("kriskowal", "q"0;
        updateUI(repoEvents);
      }catch(e){
        console.log('error occured')
      }
    })();

## Time Travel

Promises represent objects from a different time. 

    expect(promise).to.eventually.deep.equal(['zomg', 'jsconf']);

## Space Travel

Q-connection by kriskowal promise can represent an remote objecr

## Promises in JS (history)

Promises A, learned from dojo.
It had some problems, missing key features and easy to misinterpret.

$.deferred didn't work as in spec and didn't want to change. Ember got a promise pr and was wrong as well. "You are missing the point of promises". i made a promises A trst suite. yehuda katz wrote rsvp.js.

Promises a+: a gist promisesaplus.com. Has a spec. over 30 implentations of promises a+ even in other languages. They all have a good then method that make it interopable. 

Dom futures. Es7 concurrency theme. based on promises a+. 

## Open specification Development

* The cause: sane asyne in js
* The people: strong and cooperative community
* The code: existing convergent and widely-loved solutions
* The contract: small core for interop via standardization
* The setting: github. Markdown diffs are easy to read.

## Links

* <http://promisesaplus.com>
* Twitter: [@Promisesaplus](http://twitter.com/promisesaplus)
