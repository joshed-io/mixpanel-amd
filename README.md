mixpanel-amd
============

An AMD module for running Mixpanel conflict-free

An AMD-compatible version of the Mixpanel Library, useful when you need to run mixpanel
on a foreign page without global conflict or where you want to run multiple mixpanels on a page.

Simple features
-------------
*   Use Mixpanel's JavaScript library as an AMD module
*   Debug flag to switch between actual tracking and just logging to console.log (when available).
*   Customizeable namespace for the JSONP callback - set to something unique or guid-y

Cavaets:
*   The Mixpanel JS file is BORG-ed (inlined in cube fashion). This was a necessary evil for now, as the Mixpanel library only knows to look for the mpq variable on global when injected via script tag for JSONP.
*   The Mixpanel JS file is modified slightly near the end (see the comments). This is to allow the customizeable JSONP callback.
*   So, if you need to take a new Mixpanel JS version in, just swap out the borg cube below and make the same modification I did. Otherwise, you may be assimilated because you didn't maintain the cube.

To the Mixpanel guys
-------------
<3, but if you could provide a version of your library that supports AMD and a
configurable JSONP callback namespace, well that'd be <3 <3.

Usage
-------------

It's easy!

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

Ideally your AMD project is using a [build optimizer](http://requirejs.org/docs/optimization.html)
which takes care of your environment's needs (and removes my 40 lines of comments).

Issues and Contributions
------------------------
Don't let me have all the fun.

License
-------
(The MIT License)

Copyright (c) 2011 [Josh Dzielak](http://joshdzielak.com)

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING
FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS
IN THE SOFTWARE.