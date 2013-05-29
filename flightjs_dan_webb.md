Flight.js - Dan Webb
====================

@danwrong at Twitter

Overview about Flight, what it is and why.

Angust wrote blog post introducing flight. Flight now runs the twitter sight and tweetdeck. Really excited, 

First comments was "why not use Angular"?

It's a good question in a sense. There are a ton of client-side frameworks. We felt that what we tried to achieve was distinct from the existing frameworks.

## \#NewTwitter

At the time it was built using a home grown MVC framework. 

* we had models
* models can addEventListener
* we had controllers
* we had views

lots of relationshipts between models, views and cotrollers, and it's complicated. Twitter.com is a complex UI and so the complexity is necessary. But the problem is we made the code more complicated over time, and the engineers needed to really understand what everything was going on.

## How can we have complex ap that is easy to reason about?

Our answer: decoupling

In a sense MVC tightens the coupling and gives some structure. But we wanted the decoupling to go further, where everything is completely independent.

Cells is one way to look at it: every cell in the body isn't aware of what is outside it, but in aggregate it creates something really complicated. The way to get to that is components need to have a very simple contract with the outside world. Rather than views have know about the API of a particular model object we wanted it to be completely ignorant.

"if the poo is trapped in a box then it only smells when you open it." - @danwrong

## So how does Flight achieve this?

* Make greater use of the DOM
  - one thing nice about DOM is events
  - inherent hierarchy - objects have structure too so DOM maps to the way the app needs to work

Flight components - object has a reference to a DOM node
  
  * it can manipulate that node
  * trigger evets on that DOM node
  * listen to events

Example

    var ToggleComponent = flight.component(function(){
      this.enable = function(){
        ...
      }
      this.disable = function(){
        ...
      }
      this.toggle = function(){
        this.enabled = !this.enabled
        return this.enabled ? this.enable() : this.disable()
      }
      this.after('initialize', function(){

      })
    })

With Flight, you app becomes a collection of components. An app is just attaching a bunch of components to DOM nodes

    function app(){
      Navigation.attachTo('#topnav');
      Toggle.attachTo('button.toggle', {toggleClass: 'enable'})
    }

You only need to understand one component at a time.

## Atomic components make for great tests

Easy to test. You fire events on it and check if it does what it's supposed to.

<github.com/twitter/flight-jasmine> - some jasmine helpers

    describeComponent('toggle', function(){
      beforeEach(setupCompoent);

      it('fires an enabled event when cliiked', function90{
        var onEvent= spyOnEvent(this.node, 'enable');
        this.node.trigger('click');
        expect(onEvent).toHaveBeenTrigged();
      })
    })

How odes it work on tiwtter.com?

Separation between UI vs data components. UI's only job  is to manipulate the. Example follow button: it listens a click and fires a UI follow event, with the username. And then the data components listen to the event and contacts the server. When request from server comes back first another event. The UI component listens to that event and renders that it was succesful.

If you want to write another UI to display that event, you can just add it on there. And you can remove the old UI, and it's all fine.

We used to have a logger. But now a logger is just a separate component that listens to events and sends them to a server.

But that's just our archectture. We don't prescribe a templating engine, or where you keep state or ho you structure data.

So, it's not like Angular. It's a framework for making frameworks.

Icarus: New JS framework on top of flight.js

So it's a bring your own archecture kind of thing.

## What's next?

* could map to web components nicely
* 

## Links

* <http://twitter.github.io/flight/>
* twitter @flight
