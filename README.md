## Goals
In building this API template I had several goals in mind:

1.  Use only standard Mule components.  No JSON Logger, Error Handling, or other third party components.  Non-standard components are not updated by MuleSoft and can introduce security issues or become deprecated due to updates by MuleSoft.
2.  Be generic enough for various deployment targets like CloudHub, RTF, on-prem, etc.  And do this using a standard pom that can be used with the MuleSoft Maven plugin (MMP).
3.  Include bare minimal error handling and logging including a catch-all global error handler.
4.  Base property files for the usual environments (dev,qa, and prod) along with local and common (the later is shared regardless of environment).

## Logging
To facilitate logging there is an included log flow in the template.  This has several subflows for various log levels (error, info, debug) which use the standard Mule log component.  The output of the log message will be in JSON format.  The reason for this is many logging systems prefer this over any other format to allow them to easily parse the content of messages.

Along with the flow there are per environment logging settings.  This allows for per enviornment toggling if payloads are included in messages and attribute filtering.

To set a custom message for a log subflow just set the variable "logMessage" before calling one.

Customize this based on customer needs.  It is also possible to externalize the log flow in to its own dependent asset if needed.  This has its own pros and cons with keeping projects up to date.
