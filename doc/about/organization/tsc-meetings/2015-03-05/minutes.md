# Minutes for the Node.js core team meeting on 03/05/2015

## Present
-----
- Alexis Campailla
- James Snell
- Michael Dawson
- Julien Gilli
- Trevor Norris
- Steven Loomis

## Discussion

### General

### Leap second

There will be a leap second between July 30th and June 1st. There was
discussion with respect to how this might affect Node. From the consumer
perspective this may seen as clock drift which is quite common. In 0.12 Node
uses absolute times, not dates. 0.10.X used to use dates. Most time dependant
functions are handled by either libuv or v8. We should likely ask these
communities what they expect the effect of the leap second to be. Michael to
open a libuv issue to ask this question and also to see if we can  find who is
the right person to ask in respect to V8. Steven volunteered to write up a FAQ
covering the issue.

### Better way to manage dependencies

Alexis initiated the discussion on a better way to manage dependencies and
will write up a proposal. It would be nice if tests for Node ran in the test
suites executed by the dependency teams. Failing that we should look at
pulling in the dependencies more frequently in our CI, run the Node tests and
provide feedback to the external teams.

### Next releases

#### 0.10.37

* Upgrade to libuv 0.10.36 in progress, code review planned for today, should
land soon.

* 0.10.37 will possibly go out next week.

* Priority issues for 0.10.37 - issue #9092 and reverting change to url that
caused a regression.

#### 0.12.1 release

Key priority issues:

* libuv upgrade to 1.4.0, down to 1 test failing on OSX, ok on windows side now,
Julien working on this.

* V8 lateral upgrade, Trevor still working on identifying goood V8 level (issue
9185).

* Issue #8540, #9204 discussing whether to pull fix from io.js or one developed in
Node.js based on which is better.

* Issue #9245, Trevor working on this, 2 ways to make callback and depending on
which one is called can lead to subtle bugs.

* Issue #9339 - to be reviewed and committed

* Issue #9317 - fix available in io.js other core team members to review to see
if it can be pulled in.

* Issue #9235 - ensuring NODELAY is on for all platforms.  Michael would like it
on for AIX Julien/Alexis to review in context of Windows and other platforms.

* Issue #9334 - tests fail when run in deep directory paths.  Julien and other
core team members to review and comment.

