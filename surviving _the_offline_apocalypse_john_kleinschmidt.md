Surving The Offline Apocalypse - John Kleinschmidt
==================================================

* work for CURE international - non-profit
* I did serverside JS in 97

## Why Does Offline Matter?

* connection is not always good, power failure and slow
* servers may not always available

## Why Offline Matters to Me?

* helping children cure diseases
* problem: how to keep track of info for quality assurance and research data

## The Solution

* "Offline First App"
* Always assume you are offline

## Rules for Survival

* Live off the grid in a fortified shelter
* store your supplies
* have adequate weaponry
* use your escape plan

## Live off the grid: application cache

* maybe you've heard of app cache and that it's kind of a jerk
* but for spa it works pretty well
* (code for the app cache manifest) - which has a list of files needed
* use a php file to auto generate the manifest
* browser support for app cache: IE 10+, no opera mini
* link: app cache is a douchbag

## Supplies: IndexedDB

* ASYNC ALL THE THINGS!
* (code example - *looks involved*)
* onupgradeneeded?
* knows the id attribute is the primary - implied?
* indices! 2 ways to do it
  1. key ranges - upperbound and lower bound (ex: all cats name starts from c-h)
  2. not unique - get all cat pictures that have a beard
* chrome dev tools indexDB integration is nice
* browser support: iOS and Safari do not support it, but there is a polyfill that uses the websql api

## Adequate Weaponry: FileSystem API

* (picture of a retro nerf gun)
* let's you store sandboxed files - we are using it to store patient photos
* you can get a local URL to that image: just `<img src="that location">`
* (code example) for file api
* you have persistent files or temporary files
* also async api
* browser support: only in chrome, but there is a polyfill that works on top of indexDB - our case was using google chromebooks

## An Escape Plan

* really useful to store it back online
* have an attribute that says this needs to sync back up
* have to know when we are online
* navigator.onLine "returns true if the user agent might be online", WTF?
* window `online` event too (code example)

    var onlineStatus = navigator.onLine; // true or false

    $(window).on('online', function(evt){
      //
    })

## We helped people survive the offline apocalypse

Yea!

## Contact

* Twitter: @jkleinsc
* <http://resplendentdev.com>
* <http://cure.org>
* <http://jkleinsc.github.io/jsconf13>

