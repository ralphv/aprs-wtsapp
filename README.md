# [APRS-WTSAPP](https://wtsapp.org) - APRS to WhatsApp Radio Gateway for Amateur Radio

* [What is it](#what-is-it)
* [Current Status and updates](#current-status-and-updates)
* [How to use it](#how-to-use-it)
* [Limitations](#limitations)
* [Error messages](#error-messages)
* [Reliability](#reliability)
* [Availability](#availability)
* [Responsibility and privacy](#responsibility-and-privacy)
* [Disclaimer](#disclaimer)
* [Contact](#contact)


## What is it

* WTSAPP is an APRS Gateway designed to allow Licenced Radio Amateurs around the world reach their loved ones from their radios by using [APRS messages](http://www.aprs.org/).
* This is very similar to the gateway SMSGTE, that allows communication to text messages.

## Current status and updates

* 12/20/2021 - Fix for dashes in numbers and open for public as beta.
* Currently, this is being developed/tested and is in __[closed beta]__.
    
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

* Rate limiter per call sign -> 50 messages / 10 minutes
* Rate limiter for server -> There is also a rate limit for the whole service for all the users using it.
* Rate limiter for replies -> WhatsApp users can reply with a maximum rate of 50 messages / 10 minutes

## Error messages

* `Rate Exceeded*` various messages that indicate the rate limitations
* `No conversation to follow up, missing directive.` You sent a messages from APRS without a destination using the `@` sign
* `Invalid command` You sent a message starting with `#` sign but doesn't match any of the commands known.
* `Invalid set alias command body` You tried to use the set alias command but the message was not properly formatted.
* `Invalid remove alias command body` You tried to use the remove alias command but the message was not properly formatted.
* `No active session found for incoming from` The WhatsApp user replied to WTSAPP Gateway but there was no active conversation. Conversations must be initiated by the radio user and conversations remain active for one hour to allow replies.

## Availability
* This is a personal project with a personal small budget set aside. I could not secure a WhatsApp business account because it needs a registered company that can be verified by Facebook. If the number I am using starts getting a lot of traffic, WhatsApp may ban it. 
* Recipients should add the number as a contact to help against banning this service.

## Reliability
* Radio communication may be affected by weather conditions.
* APRS is not always within reach, there are areas without coverage. The gateway responds with `status` messages on both ends. Watch for them.
* My software may contain bugs and probably does.
* My software may lose Internet connectivity, or the services to send WhatsApp via API may be down, or the APRS-IS network may be down.
* Try not to send too many messages, this service is intended to `stay in touch` or `check in` during limited connectivity, it is not intended to create a full day-to-day conversations. Please use it sparingly.
* Send one message at a time and wait for delivery confirmations, both APRS -> WhatsApp and WhatsApp -> APRS.
* **DO NOT Rely** on this service for emergency use or as a reliable means of contact when you are out of reach. At best, it should be a redundant mean. Other means like a satellite phone, Garmin inReach, PLB and the likes are to be used if you are far from civilization. 

## Responsibility and privacy
* When you use this service as a Licensed Ham, you are 100% responsible for abiding by the FCC Rules or the equivalent Rules of your country. You are 100% responsible for the contents of your messages and their destination.
* When using APRS and radio, you have zero privacy when it comes to your messages and their contents. Furthermore, some websites keep a history or database of all the APRS messages sent worldwide.
* Since this is a radio amateur service, you can not use this service for any commercial or business related purposes. This should only be used for non-profit and purely for personal usage, as is the case with everything Amateur Radio related.

## Disclaimer

THE SERVICES ARE PROVIDED “AS IS” AND “AS AVAILABLE” WITHOUT REPRESENTATIONS, WARRANTIES, OR CONDITIONS OF ANY KIND, WHETHER EXPRESS, IMPLIED, LEGAL, OR STATUTORY, INCLUDING, BUT NOT LIMITED TO, IMPLIED WARRANTIES OF MERCHANTABILITY, TITLE, FITNESS FOR A PARTICULAR PURPOSE, AND NON-INFRINGEMENT. I DO NOT WARRANT THAT THE SERVICES ARE ACCURATE, COMPLETE, RELIABLE, CURRENT, OR ERROR FREE. I DO NOT CONTROL, ENDORSE, OR TAKE RESPONSIBILITY FOR ANY CONTENT AVAILABLE ON OR LINKED TO THE SERVICES OR THE ACTIONS OF ANY THIRD PARTY OR USER, INCLUDING LICENSED RADIO AMATEURS.

IN NO EVENT WILL I BE LIABLE TO YOU FOR ANY INDIRECT, CONSEQUENTIAL, EXEMPLARY, INCIDENTAL, SPECIAL, OR PUNITIVE DAMAGES, OR LOST PROFITS ARISING FROM OR RELATING TO THESE TERMS OR THE SERVICES, INCLUDING THOSE ARISING FROM OR RELATING TO CONTENT MADE AVAILABLE ON THE SERVICES THAT IS ALLEGED TO BE DEFAMATORY, OFFENSIVE, OR ILLEGAL. ACCESS TO, AND USE OF, THE SERVICES IS AT YOUR OWN DISCRETION AND RISK, AND YOU WILL BE SOLELY RESPONSIBLE FOR ANY DAMAGE TO YOUR DEVICE OR COMPUTER SYSTEM, OR RESULTING LOSS OF DATA.

## Contact
Best place to discuss this is at this reddit community [r/aprs_wtsapp](https://reddit.com/r/aprs_wtsapp)
You can also email me at wtsapp [at] wtsapp.org
Please forgive me if I don't reply immediately, this is a side project with limited time.

By KC1QCQ