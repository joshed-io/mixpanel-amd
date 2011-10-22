mixpanel-amd
============

An AMD module for running Mixpanel conflict-free

An AMD-compatible version of the Mixpanel Library, useful when you need to run mixpanel
on a foreign page without global conflict or where you want to run multiple mixpanels on a page.

Simple features:
  - Use Mixpanel's JavaScript library as an AMD module
  - Debug flag to switch between actual tracking and just logging to console.log (when available).
  - Customizeable namespace for the JSONP callback - set to something unique or guid-y

Cavaets

  - The Mixpanel JS file is BORG-ed (inlined in cube fashion). This was a necessary evil for now, as the Mixpanel library only knows to look for the mpq variable on global when injected via script tag for JSONP.
  - The Mixpanel JS file is modified slightly near the end (see the comments). This is to allow the customizeable JSONP callback.
  - So, if you need to take a new Mixpanel JS version in, just swap out the borg cube below and make the same modification I did. Otherwise, you may be assimilated because you didn't maintain the cube.

To the Mixpanel guys:

<3, but if you could provide a version of your library that supports AMD and a
configurable JSONP callback namespace, well that'd be <3 <3.

Usage:

    require(["mixpanel"], function(mpq) {
      mpq.track("signed_up");
    });

Note: the environment file referenced can look something like this, or you
can inline it all into mixpanel.js if you just have one environment, etc

    define({
      debug: false,
      mixpanel_token: "abcd123456efghij098876321",
      mixpanel_namespace: "your_apps_mixpanel"
    });

Ideally your AMD project is using a [http://requirejs.org/docs/optimization.html](build optimizer)
which takes care of your environment's needs (and removes my 40 lines of comments).

Copyright Josh Dzielak, 2011
MIT License