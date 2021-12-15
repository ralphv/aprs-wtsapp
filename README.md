# [APRS-WTSAPP](https://wtsapp.org) - APRS to WhatsApp Radio Gateway for Amateur Radio

* [What is it](#what-is-it)
* [Current Status](#current-status)
* [How to use it](#how-to-use-it)
* [Limitations](#limitations)
* [Error messages](#error-messages)
* [Contact](#contact)

## What is it

* WTSAPP is an APRS Gateway designed to allow Licenced Radio Amateurs around the world reach their loved ones from their radios by using [APRS messages](http://www.aprs.org/).
* This is very similar to the gateway SMSGTE, that allows communication to text messages.

## Current status

Currently this is being developed/tested and is in __[closed beta]__.
    
## How to use it

The simplest use case is to send an APRS message to the destination `WTSAPP` with a message starting with the `@` sign, followed by the phone number, then a space and followed by the message.

__Example__

```
    To: WTSAPP
    Message: @123-456-7890 this is my message.
```

The following commands are also available. Commands start with the `#` sign

* Set Alias for a phone number

```
    To: WTSAPP
    Message: #SET me @123-456-7890
```

Now sending a message can be done by using an alias instead of a phone number

```
    To: WTSAPP
    Message: @me this is my message.
```

* Remove an alias

```
    To: WTSAPP
    Message: #RM me
```

* Conversation mode

Once an initial message establish a destination by the use of @, subsequent messages don't need the destination anymore.


```
    To: WTSAPP
    Message: this is a follow up message, will send to the destination used.
```
## Limitations

* Rate limiter per callsign -> 50 messages / 10 minutes
* Rate limiter for server -> There is also a rate limit for the whole service for all the users using it.
* Rate limiter for replies -> WhatsApp users can reply with a maxium rate of 50 messages / 10 minutes

## Error messages

* `Rate Exceeded*` various messages that indicate the rate limitations
* `No conversation to follow up, missing directive.` You sent a messages from APRS without a destination using the `@` sign
* `Invalid command` You sent a message starting with `#` sign but doesn't match any of the commands known.
* `Invalid set alias command body` You tried to use the set alias command but the message was not properly formatted.
* `Invalid remove alias command body` You tried to use the remove alias command but the message was not properly formatted.
* `No active session found for incoming from` The WhatsApp user replied to WTSAPP Gateway but there was no active conversation. Conversations must be initiated by the radio user and converstations remain active for one hour to allow replies.

## Contact
Please find me at this [Facebook page](https://facebook.com/aprs.wtsapp)