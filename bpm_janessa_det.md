BPM JS - Janessa Det
=====================

Automatic Bits-per-second detection. Working for Twitter.

## BPM: Onset Detection

When the beat happens. Fundamental to sonar, speech, ekg, movement detection. And iron man: depends on detecting onsets for signals in the body.

## Auto Transcription of music

1. instrucment iden
2. instrument isolation
3. pitch detection
4. _____

## Why in the browser

* sharable
* cross-platform
* JS is fast enough now for DSP
* It is fun
* diverse community

## How to do onset detection?

What is a beat? pitch, notes or percussive beats.

1. STFT (short time fourier transform)
2. detection function
3. peak pickings
4. bpm

## STFT

Steps:

1. window slicing
2. hamming window
3. normalizationg
4. zero padding
5. fast fourier transform

## Detection Functions

I use frequency based methods

1. high frequency content
2. spectral difference

## Peak picking

build a threshold using a median filter or use adaptive thresholding

## BPM Calculation

Peak times 0.5, 1.0 1.5, 2.0, now you can guess it's 0.5 seconds per period.

## Music Characterization

One song "So Insane" by Discovery. 10 second signals and average of 115 bpm. 

## Tools Used

* DSP.JS
* complex arithmetic
* lots of loops and math
* browserify to organize

## JS Challenges

* Float30Array
* compatibility
* complex arithmetic matrices

## Optimizations

1. web workers
2. sample just part of the song
3. about the same time as matlab in perf
4. the dream is real time

## Weaknesses

1. sensitive to tuning params
2. need a priori knowledge about the song

## Future Work

1. many detection functions
2. onset detection for different apps

## the web is changing

1. lots of packages on npm

