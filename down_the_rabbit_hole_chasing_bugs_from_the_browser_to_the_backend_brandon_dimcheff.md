Down the rabbit hole: Chasing bugs from the browser to the backend - Brandon - Dim
==================================================================================

(missed first 7 minutes)

moar UNIX! Used unix tools to grep the logs

## Lesson: Log all the things!
## Lesson: Know your tools

Use unix to grep though the logs

## Act III: Repro(duce)

Devs didn't see it. Flaky internet? how can we simulate? 

iptables: 30 minuse later: screw it. Unplug the ethernet cable, and then plug back in and reproduce the issue.

mabe also learn the tools later. but fast

## Act IV: figure it out

new work tab -> websockets in chrome dev tools. Then click on frames, you can get very detailed in websockts. but no close message, it just stopped.

Bringout out the big guns: Wireshark!

Wireshark dump: websocket was forceably closed found. So client side was closing the connection!

Shotgun Debugging: stick breakpoints everywhere that said close! And it worked!!! But it took a long time to turn all of them back off. Issue was old wesocket is swapped out for new ones but old one dosen't get cleaned up.

## Act V: the fix

(code example for a simple fix) - and graph for reconnection is now very low, yea!

## Lessons

1. graph all the things!
2. Do the supidest, easiest thing that works
3. but also learn your tools
4. listen to your users

## Hiring

* <olark.com/jobs>