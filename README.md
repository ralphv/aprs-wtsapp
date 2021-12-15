# [APRS-WTSAPP](https://wtsapp.org) - APRS to WhatsApp Radio Gateway for Amateur Radio

* [What is it](#what-is-it)
* [Current Status](#current-status)
* [How to use it](#how-to-use-it)
* [Limitations](#limitations)
* [Error messages](#error-messages)
* [Reliability](#reliability)
* [Responsibility and privacy](#responsibility-and-privacy)
* [Disclaimer](#disclaimer)
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

## Reliability
* APRS is not always within reach, there are areas without coverage. The gateway responds with `status` messages on both ends. Watch for them. 
* Try not to send too many messages, this service is intended to `stay in touch` or `check in` during limited connectivity, it is not intended to create a full day to day conversations. Please use it sparingly.
* Send one message at a time and wait for delivery confirmations, both APRS -> WhatsApp and WhatsApp -> APRS.

## Responsibility and privacy
* When you use this service as a Licensed Ham, you are 100% responsible for abiding by the FCC Rules or the equivalent Rules of your country. You are 100% responsible for the contents of your messages and the their destination.
* When using APRS and radio, you have zero privacy when it comes to your messages and their contents. Furthermore some websites keep a history or database of all the APRS messages sent worldwide.
* Since this is a radio amateur service, you can not use this service for any commercial or business related purposes. This should only be used for non-profit and purely for personal usage, as is the case with everything Amateur Radio related.

## Disclaimer

THE SERVICES ARE PROVIDED “AS IS” AND “AS AVAILABLE” WITHOUT REPRESENTATIONS, WARRANTIES, OR CONDITIONS OF ANY KIND, WHETHER EXPRESS, IMPLIED, LEGAL, OR STATUTORY, INCLUDING, BUT NOT LIMITED TO, IMPLIED WARRANTIES OF MERCHANTABILITY, TITLE, FITNESS FOR A PARTICULAR PURPOSE, AND NON-INFRINGEMENT. I DO NOT WARRANT THAT THE SERVICES ARE ACCURATE, COMPLETE, RELIABLE, CURRENT, OR ERROR FREE. I DO NOT CONTROL, ENDORSE, OR TAKE RESPONSIBILITY FOR ANY CONTENT AVAILABLE ON OR LINKED TO THE SERVICES OR THE ACTIONS OF ANY THIRD PARTY OR USER, INCLUDING LICENSED RADIO AMATEURS.

IN NO EVENT WILL I BE LIABLE TO YOU FOR ANY INDIRECT, CONSEQUENTIAL, EXEMPLARY, INCIDENTAL, SPECIAL, OR PUNITIVE DAMAGES, OR LOST PROFITS ARISING FROM OR RELATING TO THESE TERMS OR THE SERVICES, INCLUDING THOSE ARISING FROM OR RELATING TO CONTENT MADE AVAILABLE ON THE SERVICES THAT IS ALLEGED TO BE DEFAMATORY, OFFENSIVE, OR ILLEGAL. ACCESS TO, AND USE OF, THE SERVICES IS AT YOUR OWN DISCRETION AND RISK, AND YOU WILL BE SOLELY RESPONSIBLE FOR ANY DAMAGE TO YOUR DEVICE OR COMPUTER SYSTEM, OR RESULTING LOSS OF DATA.

## Contact
Please find me at this [Facebook page](https://facebook.com/aprs.wtsapp)

By KC1QCQ