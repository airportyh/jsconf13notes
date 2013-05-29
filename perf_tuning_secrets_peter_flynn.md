Perf Tuning Secrets - Peter Flynn
=================================

Dev tools perf tuning
console.timestamp to add new labels to the timeline
but can't automate the timeline. But there is a way to do that. There is a remote debugging api that ties to  dev tools.
telemetry testing framework is built atop the debugging API. Can simulate scrolling etc accurately.

get chrome srcs, and compi

topcoat project 
view results topcoat/topcoat-server  
run tests github.com/topcoat/topcoat/tree/master/test/perf/telemetry

PFS Meter & continous painting

show paint rectangles. and FPS

chrome://tracing - like time line but separated by thread. Closed a lot of thread we don't care about. 2 threads: compositer and renderer thread. Alt-mousewhite to zoom in to see frame-by-frame. Has keyboard shortcuts. GPU thread. This is only a complement to the timeline. Sometimes timelines has more info.

## 2012 & Earlier

Back before these tools it was really hard. What did you do to get the data? We developed a redicuous idea: used real SLR camera pointed at a screen. You can see noticiable delay using camera. Latency can be measured using this way. Also perf of app where you don't have access to the code, this is great.

## VM Guts

## Profiler panel

Memory view - memory usage over time, memory leaks and saw tooths. Individual GC events. You can quantify time taken by individual GCs. Sides of individual objects.
Memory profile view - drill down to snapshots. Can also diff multiple mem snapshots. Take one snapshot, do something, and then snapshot again. And then diff them to find mem leaks.

## Flame Chart view in canary

CPU flame chart view - this tells how hotspot vary over time. Spikes are JS activity (cpu). Buttom is zoomed in view. X-axis represents time, matches Y-axis on top. Colors are random color codes. 

console.profile('foo()') and console.profileEnd('foo()') rather than manually.

console.time('foo()') and console.timeEnd('foo()')

## V8 Logging Analysis

Provides more than what dev tools show. Setup is involved. Close all Chrome processes and run with special flag. And then find a log file, and then run a script that watches the log file, and then get a graph. You can get really really fine grain details. You can see GC activity and what is it doing? "V8 Logging: plot-timer-events". You can zoom in down to the millisecond. 

I also made a tool that makes looking at this plot more interactive using gnuplot.

## V8 tick processor

tools/mac-tick-processor

an asterisk tells you that function is optimized, lack of one means it's not optimized. 

## V8 Logging: deopttracing

Will tell you why the function was not "eligiable" for being optimized.

## Or...

Ignore all this! Because there are reasons to not focus on performance.

## Network slowness is much more slow

Resource time monitoring
    
    var loadTiming = performance.timing;

By resource

    var resources = performance.webkitGetEntriesByType('resource'); // perf grouped by resource name

W3C is producing the perf apis. Scrolling simulation api, frame rate perf api, and resource api.

## Maybe your code is fast enough already.

Identify specific bottlenecks.

## Engineering time is a finite resource

There are other things more important than perf.


## GitHub Repo for the content

<http://github.com/peterflynn/jsconf-2013>

