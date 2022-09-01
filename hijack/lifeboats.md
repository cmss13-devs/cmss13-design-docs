## Abstract

Lifeboats are a round-end system used during evacuation on hijack. 'Lifeboats' refer to the two large escape pods located on the aft upper deck of the Almayer.

During the hijack sequence, as soon as the hijacked dropship crashes into the Almayer, a 10-minute countdown is automatically started and lifeboats begin the countdown process.

Once the 10 minutes are up, lifeboats try to launch. If xenos are onboard either lifeboat when the launch begins, the lifeboats fail to launch.

## Goals

1. Lifeboats start the evacuation process immediately upon the dropship crashing
2. Automate self-destruct and distress beacon sequences
3. Distress beacon should be launched 2 minutes after crash
4. Lifeboats should launch automatically once 12 minutes have passed
5. BOTH lifeboats should fail if a xeno or facehugger is present on EITHER lifeboat at launch time
6. Make them just fail to launch, don’t blow them up that’s silly
7. Implement cascading emergency floor lighting directing people towards the lifeboats area
8. Port over the fancy screens and timer from the original lifeboat PR
9. Add self-destruct room to lower engineering. SD rods will self-insert themselves automatically
10. SD rods need to become their own dedicated structure rather than being a wacky overlay
11. The non-hijacked dropship (the one sitting pretty on the pad) should launch to perpetual flyby as its own escape pod
12. Remove larva surge! It was meant to be a stopgap until lifeboats anyway.

## Non-Goals

1. Do not use tgshuttles for escape pods (yet). That's another rabbithole for another PR to handle.
2. Do not overcomplicate this PR. It should do what is outlined above and avoid adding unnecessary complexity.

## Content

Everything in the hijack sequence on the Almayer's end should be automatic for both realism and gameplay flow. Sure, it's a dilapidated ship, but even a dilapidated ship would still be able to evacuate its crew to the best of its abilities.

### Timeline

* T+00:00 - Dropship crashes into the Almayer. ARES, communications, and power all shut down or run on emergency.
* T+00:05 - Lifeboat countdown and evacuation begins automatically.
* T+01:00 - Individual escape pods are primed for evacuation. May be launched at any time.
* T+02:00 - Randomized distress beacon automatically called. May be disabled by command(?)
* T+03:00 - Self-destruct initiates. May be deactivated until T+08:00 by anyone; however this does not prevent the lifeboats from launching. See 'Self-Destruct' section below.
* T+08:00 - Boarding begins. Lifeboat doors open for Marines (and maybe Xenos) to flood in.
* T+10:00 - Lifeboat doors seal and try to launch automatically regardless of survivors. Xenos disable this as a failsafe. Grace period begins.
* T+11:00 - Grace period ends with round-end. If the SD remains primed, it triggers now, incinerating everyone on the ship, remaining humans included.

### Round-end

* Xenos will *always* win once the dropship is hijacked.
* Activation of the lifeboats (and subsequently SD) results in a xeno minor victory. 
* Failure of the lifeboats (due to xenos taking over) results in a xeno major.
* Activation of the lifeboats, but manual deactivation of the SD, still results in a xeno minor, except everyone on the ship isn't killed in a nuclear explosion.

### Self-Destruct

Self-destruct (SD) will be automatically primed at T+03:00 and will gradually arm itself until locking at T+08:00. SD consists of six control rods and a central console; these rods will gradually rotate themselves as the timer progresses before self-detonating at T+11:00.

Anyone can attempt to override the self-destruct and disable it, but this takes time, sped up by engineering skill. The Commanders (CO or XO) should be able to individually instantly disarm the SD system via biometrics (i.e. not their ID card).

SD will be locked in at T+08:00 and cannot be deactivated if it wasn't before then.

## Alternatives

Or maybe it'd be better to just bring old SD itself back with the timer system. Who knows.

## Potential Changes

* For the lifeboats sequence, the individual escape pods could just be axed entirely depending on how much sense they make.
* Times are subject to change. Dev consensus + numerous test-runs of the lifeboat hold itself show that 10 minutes is a sweet spot for Marines to hold.
* Larva surge removal and 10-minute hold combined could end up making the timer too short, too. Find out in testmerge.
* Could also just make SD unable to be overridden by anyone *except* the CO or XO, to prevent abuse.
