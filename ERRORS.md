# Errors in Burger-based software and how to handle them

## The console

All Burger-based software uses a simple logging system that outputs to TTY. Log files are not provided by default and users are expected to use pipes to redirect the logs as they wish.

A log entry looks something like this:

| DATE | HUMAN-READABLE TIME | LOGLEVEL | DESCRIPTION |
|---|---|---|---|---|
| 1969/12/31 | 11:59:59 | [INFO] | Added a new user |

## Log levels

There are 5 different log levels, with differing amounts of urgency

| INFO                                                    | WARN                                                                            | ERROR                                                                                  | CRITICAL                                        | FATAL                                                                                                                                                                     | PROMPT                                                                                         |
|---------------------------------------------------------|---------------------------------------------------------------------------------|----------------------------------------------------------------------------------------|-------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|
| Usually harmless information, like a user being created | A warning about bad practices being used, such as having an unset config option | An error that disrupts user experience and may lead to undesired client-side behaviour | An error that affects all users on the platform | An error critical enough to warrant crashing the server process, usually something like the server being unable to bind to an IP or not being able to create the database | Anything that asks the user for input, like a confirmation dialog (typically has no timestamp) |

## Error reporting

Clients will be given 500 status code and an error code if any errors were to affect them. They are told to come to this page for more information. If you are one such client, please go to the issues tab and paste the error code along with some context, so we can fix the bug.