AI.js: Robots with Brains - Raquel Velez
========================================

Brought to you by @rockbot : Roqual Velez. I work at storify.

(Warning: there my be math)

I've been doing robots for ~10 years. Saw a robot demo in high school by a woman and turned me on to it.

My First robot was Adrian was a search and rescue robot via lego mindstorms. Won some awards internationally. At the time lego mindstorms was 34 year old male.

Second robot was bob: an actual car (atonomous vehicles in the desert). It was a chevy tahoe, because it was full of computers inside.

I built more robots. Some are top secret.

I was in the world of "traditional" robotics.

* robots come from research - slow academic process
  - robots come from research
  - have to write papers
  - need phd
  - robots "need" oop and threading (C++, Python)
* robot domination: not anytime soon

## NodeBots: a new beginning

I did some web development and hit refresh and I get immediate feedback!!! So gratifying! But then, I met Chris Willams (@vodotikigod) who wanted to start playing with hardware. And then @rwaldron wanted to play with robots. 

## Vektor

linear algerbra module for robotics by @rockbot. 

## Robotics 101: AI

You are giving something else the ability to make decisions. 

## Example: Obstacle avoidance

You can do an if statement. Okay. But what if more complex

## Serial Manipulators

Robot arm (kuka robot) - serial manipulator . It has joints (a series of them) connected by links. You have some sort of claw and a base. My arm is a serial manipulator.

## Forward Kinematics

    f(jointAngles) = positionOfEndEffector

If I put in a bunch of angles for each joint, get the claw in a certain position. 
## Inverse Kinematics

We know the position of the claw, what are the angles of the joints? This is little harder.

## Matrices are Your Friend

    [R P]
    [0 1]

Every joint has a R(rotation) and a P(position). If you change angle, position will change. 

## Vektor - make the computer do the hard stuff

## Forward Kinematics with Vektor
  
    var H0 = HOMOG(Rotate.RotX(0), new Vector([0, 0, 0]))

(demo) - she has a video somewhere. You can drag a joint or the claw itself in the UI and the robot arm follows suit.

## Robots vs. NodeBots

    Robots                            NodeBots

    Tradition( C++)                   Javascrip (Node.js)
    Multi-threaded                    Single-therads
    Well established                  Just getting started


    Research & Papers                 Open Source
    $$$$$                             Open Source
    Compile, Load, Boot, Hope, Pray   F5 / Cmd-R
    Get a PhD                         Just get started

What if we can solve the problem better than traditional robotics?

So, what? Why bother? 

## Links

* @rockbot
* <http://rckbt.me>





