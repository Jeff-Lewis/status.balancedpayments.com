# Balanced Status Dashboard

https://status.balancedpayments.com

The status page consists of several sections:

* The top portion displays the service name and an icon for its current state
* The upper middle portion displays the uptime as a percentage of non-error
  requests over the last 30 days
* The middle portion displays informational messages
* The lower portion displays issues with behavior

## Message Display Behavior

Messages are fed into the system via the @balancedstatus Twitter account. 

Messages take the format

`<SYSTEM>-<STATE>: <MESSAGE>`; e.g. 

* `DASH-UP: Everything is back to normal`
* `API-ISSUE: We are experiencing problems`
* `JS: Here's an informal message` _(non-error message)_

Where STATE is one of `UP`, `DOWN`, `ISSUE`

Messages with a state are displayed in the lower portion of the page
indefinitely, `ISSUE` or `DOWN` messages will change the icon of the
corresponding service. These messages must be followed by an `UP` state message
in order to revert the displayed icon to its natural state.

Messages without a state are displayed in the upper middle portion of the page
for 24 hours.

## System state behavior

The state of a system will be degraded as described in the above section,
additionally if the number of successful requests served in the last *5*
minutes drops below *99%* then the system will automatically go into an `ISSUE`
state, if the number of successful requests in the same period drops below
*90%* then the system will be in the `DOWN` state.
