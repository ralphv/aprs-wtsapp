# [APRS-WTSAPP](https://wtsapp.org) - APRS to WhatsApp Radio Gateway for Amateur Radio

* [Status](#status)
* [What is it](#what-is-it)
* [Current Status and updates](#current-status-and-updates)
* [How to use it](#how-to-use-it)
* [Limitations](#limitations)
* [Error messages](#error-messages)
* [Reliability](#reliability)
* [Availability](#availability)
* [Responsibility and privacy](#responsibility-and-privacy)
* [Disclaimer](#disclaimer)
* [Thanks](#thanks)
* [Contact](#contact)
* [Donation](#donation)


## Status
<span style="background-color:green">ONLINE</span>

[Status page here](https://stats.uptimerobot.com/OkNkjcNmBX)

## What is it

* WTSAPP is an APRS Gateway designed to allow Licenced Radio Amateurs around the world reach their loved ones from their radios by using [APRS messages](http://www.aprs.org/).
* This is very similar to the gateway SMSGTE, that allows communication to text messages.

## Current status and updates

* 11/13/2022 - Adding a status page.
* 11/07/2022 - Couple of bug fixes.
* 29/10/2022 - Using a different library for delivering messages, should be faster and more reliable.
* 01/04/2022 - Using aliases for APRS messages instead of number.
* 12/25/2021 - Major new release, added MongoDB as DB and bug fixes.
* 12/22/2021 - Revamped this page to make the documentation clearer.
* 12/20/2021 - Fix for dashes in numbers and open for public as beta.
* Currently, this is being developed/tested and is in __[closed beta]__.
    
## How to use it

__The 3 formats of the messages:__

```
[@][international phone number/alias] [message body]
[#][command] [command body]
[follow up messages, coversation mode]
```

* The first letter when it's an `@` sign will indicate a command to send messages:
It should be followed by an international phone number or an alias.
* The phone number **MUST BE** in international format, otherwise it won't work. This means it **MUST START** with the country code.

__Example__: Sending a message "this is my message" to the international phone number `+123-456-7890`

```
    To: WTSAPP
    Message: @+123-456-7890 this is my message
```
OR without dashes
```
    To: WTSAPP
    Message: @+1234567890 this is my message
```

__Example__: Sending a message "this is my message" to the alias `me`

```
    To: WTSAPP
    Message: @me this is my message
```

* The first letter when it's an `#` sign this indicates a command. Currently, there are two commands. 
One `SET` to set or create an alias. One `RM` to remove an alias.

__Example__: Creating an alias called `me` with the international number +123-456-7890

```
    To: WTSAPP
    Message: #SET me +123-456-7890
```

__Example__: Removing an alias called `me`

```
    To: WTSAPP
    Message: #RM me
```

* Conversation mode

Once an initial message establishes a destination by the use of `@` Subsequent messages to the *same destination* don't need the destination anymore.

__Example__: Sending a message "this is a follow up message" to the destination used before. 
The session time is 1 hour, after that conversation mode will not work, and you will need to use the `@` sign again to establish a destination.
__Note__: If you are sending messages to *multiple recipients* at the same time, you should always use the `@` sign.

```
    To: WTSAPP
    Message: this is a follow up message
```
__The format of the numbers:__

Phone numbers must be numeric. They can contain dashes `-` and they can start with international format using the `+` sign, otherwise it will be considered a USA based number.
Numbers not correctly formatted will cause an error.

__The format of the aliases:__

Aliases can be any single word format. However, if it looks exactly like a phone number it will be considered invalid.
Aliases not correctly formatted will cause an error.

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

## Thanks
Special thanks to VK3TMO for extensive testing and finding many bugs.

## Contact
Best place to discuss this is at this reddit community [r/aprs_wtsapp](https://reddit.com/r/aprs_wtsapp)
You can also email me at wtsapp [at] wtsapp.org
Please forgive me if I don't reply immediately, this is a side project with limited time.

## Donation
Anything helps with the server and service fees.
Thanks.

[![button](https://www.paypalobjects.com/en_US/i/btn/btn_donate_LG.gif)](https://www.paypal.com/donate/?hosted_button_id=A7G3QV4MTNTF6)



By KC1QCQ