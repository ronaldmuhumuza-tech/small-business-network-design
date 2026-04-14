## Console Access Behaviour in EVE-NG

### Overview

During initial setup, device console access in EVE-NG was provided through a web-based interface using session tokens, rather than traditional Telnet-based console ports.

This differed from expectations, where external terminal tools such as MobaXterm would typically be used to establish console sessions.

---

### Observation

Attempts to access device consoles using Telnet from MobaXterm resulted in connections being established, but without visible output from the device.

This created the impression that the connection was not functioning correctly.

---

### Root Cause

EVE-NG (in its default or newer configurations) uses a web-based console mechanism, where session access is handled via the browser using dynamically generated tokens.

As a result:

* Telnet ports are not always exposed or visible
* External terminal tools may not behave as expected
* Console sessions are intended to be accessed via the EVE-NG web interface

---

### Resolution

Device access was performed using the built-in EVE-NG console, which provided reliable and immediate interaction with all devices.

Where Telnet access was attempted:

* Additional input (e.g. pressing Enter) was sometimes required to trigger console output
* Ensuring the device was fully booted resolved cases where no output was initially displayed

---

### Outcome

Console access was successfully established using the EVE-NG web interface, allowing all configuration tasks to proceed as expected.

---

### Notes

This behaviour is specific to the EVE-NG environment and differs from traditional lab setups where direct Telnet access to console ports is common.

Remote access using SSH will be configured in later phases once management IP addressing is in place, aligning the environment more closely with real-world network operations.
