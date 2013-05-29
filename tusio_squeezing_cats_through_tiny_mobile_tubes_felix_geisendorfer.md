<http://tus.io> - Squeezing Cats Through Tiny Mobile Tubes
==========================================================

## 1995 : RFC1867 Forma-based file upload in HTML 

(Demo) - file upload

made an html with a form. 

    <form action="/" method="post" enctype="multipart/form-data">
      <input type="file" name="myupload">
      <input type="submit" name="Submit">
    </form>

The RFC defined `enctype`. Now we have a file uploaded. Choose a file, and submit, but now we need a backend. Let's use php

    <form action="/form.php" method="post" enctype="multipart/form-data">
      <input type="file" name="myupload">
      <input type="submit" name="Submit">
    </form>
    <?php
    print_r($_FILES);

This is the appropriate amount of complexitiy to do file uploading. But the features are lactking

1. can use Javascript
2. no progress indicator

## The Dark Ages

People turned to flash. This was a step back, flash uploaders were a PITA.

## 2008: XmlHTTPRequest Level 2

* flieluploads
* progress events
* cross site requests
* form data interface
* merged into main spec 2011

browser support: (IE version 10 has it)

## 2009: File API

* FileList interface
* File interface
* Blob interface
* File Reader interface
* URI Scheme to reference files / blobs

browser support: (IE version 10 has it)

## 2013

We took a step backwards in terms of simplicity. "Connection lost, please upload again", no restart.
more HD cameras

## Slow Uplinks

* Wifi: 2.5 min
* LTE: 10min
* 3G: 40min
* Edge: 66min

This is important.

## How to resume HTTP upload?

RFC 2626 - HTTP 1.1. It's like the bible, people think they know it, but just pick the parts they like. 

## Range Requests

Range header tells the server where to resume. YouTube API v2.0 uses. But they 

* invensted a new http code 308 resume incomplete - in violation of upcoming specs. 
* It uses "Content-Range", "Range" headers - also in violation of upcoming specs :(
* Uses PUT to "query" upload status !?
* Similar protocol used for Google Drive - but sligt incompatible

So Google haven't figured out how to do it well.

## Amazon s3

* Multipart API 
* allows sending a file in chunks
* it's okay
* 5mb min chunk size. if last 5m failed have to restart the last 5mb
* proprietary - not suitable for an open web

## resumable.js

* Uses multipart/form-data
* files are split into fixed size chunks
* best open source solution right now
* Not defined as a standard :/

## The Vision

"Adding resumable file uploads should take 5 minutes instead of 5 hours"


    <form resumable
      method="POST"
      action="/form.php"
      enctype="multipart/form-data">
      ...

## <http://tus.io>

* informal working group to defined resumable file uploads over http
* collection of open sources projects that implement this spec. HTML, iOS, Android
* Goal: publish as IETF Standard (RFC)

## Protocol

Headers: Content-Length, and new header Final-Length: 100. This just asks server to create empty resource for the upload. Separate PATCH request to actually do the upload. If works, returns 200, if not 200. Client ask how much data again with HEAD request.

* tusd - reference server in Go
* brewtus - node.js server
* tus-jquery-client
* tus-ion_client - C library

## Alternative Protocol Idea

* form centric approach
* based on multipart/form-data, compatiblity with old-school upload forms
* more complex, but maybe more powerful

## Upload Acceleration

* TCP perf over mobile networks not always ideal
* depends on congestion window, package loss, link layer, latency
* pontential benefits by using parallel requests / connections per upload (so needs to add more to the protocol)
* needs to be studied under real world conditions

## Demo

<http://www.tus.io/demo.html> - upload a file, see the progress bar go, killed the browser window to kill the upload, and then tried again, it resumes!

* files are ided by file.name + file.size + file.lastModified
* file id is mapped to upload url in local storage
* not perfect but simple

## Links

* <http://www.tus.io/>
* <https://github.com/tus/tus-resumable-upload-protocol>