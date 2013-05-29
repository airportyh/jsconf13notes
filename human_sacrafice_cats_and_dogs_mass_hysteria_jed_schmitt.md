Quote from Ghost Busters

Men are From Mars, WEomna are from venius.

Client-server model: hich on are you?

Mars, Venus: duh, people are from earth.

Romeo+Juliet, West Side Story

Client side store. Are we gonig to find our maria and tony.

1. let's turn servers into clients!
2. let's turn clients into servers!

## let's turn servers into clients!

browserver: presented at 10/4/2012 in reject.js Berlin. 

Basically http over websockets. 

1. browser connects to server using websockts
2. server assigns/ a hostname for that browser
3. server proxies http in
4. browser becomes the server

Why http? because why useng javascript? "you already know it"

why node.js? callbacks? callbacks are the best/worst/best thing about node.js.

Webhooks? the http version of callbacks. With browserver you can use web hooks easily.

## Top Charts

1. Callaback girl
2. don't reject my promise, girl

## let's turn servers into clients!

1. cheerio
2. jsdom
3. phantomjs

Abe Vigoda - there is a web site that tells you whether he is dead.

Web scraping. Use request. Regular Expression. "You can't parse HTML with RE". "Have you tried an HTML Parser". 

## Cheerio: jQuery core for servers.

    checkOnAbe(function(err, abesOkay){
      if (err) throw err
      if (thypeof absOkay == 'boolean') return
    })

    npm install abevigoda

## JSDOM

The biggest problem is Javascript. What is the web page is running Javascript? JSDOM can execute js. tobi.js, zombie.js are built on top of JSDOM. The problem is, it's not real browser.

## PhantomJS

It great! Better gateway drug that node? CasperJS is built on phantomjs. SpookyJS is a node integration for PhantomJS. Schoolbus is a way to drive around an iframe in the browser, doesn't need PhantomJS.

Extra APIs from PhantomJS: 'clipRect', 'canGoBack', 'offlineStoragePath'.

## rndr

I built this thing called `rndr`. #! SEO? You can inject your html and put in a `<noscript>`. :// (double meh). #! will be replaced with a query parameter for google. What `rndr` does is it lets you do SEO easily.

<http://rndr.me/> Basically, you can redirect google robot to 3rd party service to render #! urls!


