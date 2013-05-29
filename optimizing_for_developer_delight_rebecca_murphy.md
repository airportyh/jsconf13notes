Optimizing For Developer Delight - Rebecca Murphy
=================================================

Working at bazaarvoice and working on a new version of the software and the new framework.

Customers don't want to switch to the new version until all the old features are there.

Bottomline: the easier I can make it to add new features, the more money we make.

## the problem

* large and growing codebase
* mission-critical app
* consantly expanding team
* mix of junior and senior devs - some from java, some from python
* mandate for rapid feature development - under the pressure of deadlines

Lots of smart people working together can still end up with working towards interest of in narrow case but cause problems in the future.

## "Developer Delight"

* a clear path for getting up to speed
* points of entry for junior & senior devs - you probably don't need all senior devs working on features - because they are in short demand
* as few surprises as possible: it just works
* isolated complexity
* easy development and debugging
* nothing more difficult than it "should" be

## The truth is out there - Assert all the things

Catch errors early.

## Log the lifecycle

Put in `console.log` and then taking them out is wasteful. Next person trying to debug it is probably going to have to do the same thing again. So we have logging system with grouped log messages. The UI prints a tree structure: this is a part of the console.log api. Can set different log levels. Great for new devs because they can see what is happening. And great for debugging too.

## Eliminate Temptation

Want to eliminate temptation to make bad decisions. Example: globals. We had a global ENV, which was a dependency in every single file, it's basically a glorified global. The next thing you know the global becomes the solution for everything. It was a global event bus, error aggregator, etc. It was the magical third argument to different methods. Now reduce modules that require ENV and only a small number of modules actually use ENV, and other modules depend of these more specific modules.

## Code for Every Concept

If there is a concept that you talk about to describe to another developer how it works. There ought to be code that describes the concept. The code talked about a component, but there wasn't an actual component object, so I made a component "class". 

## Automate Everything

Especially with a lot of devs with different skills. We have an internal tool that admins use to do specific things. Use grunt to automate this on command line too. Automate tests. Listening to devs around you and what is hard for them, and automating things (either get them to do it or do it yourself) to make it easier.

## document

Good code is good doc. But there are things that code can't tell you. Example: what is the rational for the framework? How to get started. How to find things? What conventions you use? Git workflow? Have a change log. 

## Measrue Progress (and side effects)

It's hard to measure progress. 

1. make sure the features you are adding are making the code worse: cyclomatic complexity
2. check for performance regressions
3. but the best is listening to what the devs are saying

## Are We There Yet?

Requires constant monitoring and you are never done. Code reviews, listening to conversations.

## Links

* <rmurphey.com>
* Twitter @rmurphey
* <http://bazaarvoice.com>


