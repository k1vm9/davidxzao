---
name: Missing includes
description: 11 stub/shim files that were missing from includes/ causing runtime crashes in 15 commands
---

## Rule
Any command that uses a `require("../../includes/X")` must have that file in `includes/`. These were all missing and needed to be created.

## Files Created
- `includes/motorSafeSend.js` — scheduleMotorLoop, stopMotorLoop, isActiveLoop, getLoopStats (used by engine.js, motor2.js, cp.js, ai.js, زاوفان.js)
- `includes/humanTyping.js` — calcDelay(text), simulateTyping(api, tid, ms) (used by angel.js)
- `includes/outgoingThrottle.js` — check(tid), wrapSendMessage(api) (used by angel.js)
- `includes/HumanActivitySimulator.js` — start/stop/setMood/getStatus (used by sim.js, mood.js)
- `includes/keepAlive.js` — doSaveCookies(api) bridge (used by كوكيز.js)
- `includes/liveStats.js` — trackMessage/Command/Error, getStats() (used by احصائيات.js)
- `includes/OnlinePresenceEngine.js` — start/stop/getStatus/setSchedule (used by presence.js, mood.js)
- `includes/stealthEngineV2.js` — isRunning(), getStatus() bridging to src/protection/stealth (used by ping.js, احصائيات.js)
- `includes/labyrinth/DoubleRatchet.js` — stub class (used by e2ee.js via global._labyrinth)
- `includes/labyrinth/X3DH.js` — stub class (used by e2ee.js)
- `includes/utils/platformDetect.js` — detect(), label (used by احصائيات.js)

**Why:** Commands use lazy requires (inside function bodies), so they don't crash at load time but crash when the command path runs. Stubs prevent crashes and provide meaningful fallback behavior.
