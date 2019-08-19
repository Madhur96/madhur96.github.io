---
layout: page
title: Google Summer of Code 2019
subtitle: Infinite scrolling using MAM and General Improvement.
use-site-title: true
---

#### *About Project*

This project intends to improve the overall functionality of Poezio by implementing “Infinite scrolling using Message Archive Management (MAM)” and adding important features linked with it for general improvement.
Some of the features planned for this project along with infinite scrolling of messages are:
- Implementation of scrollback command
- Work on lastlog plugin
- A tab to display important messages
- Attaching a message with a past linked message, etc

My proposal can be viewed [here](https://docs.google.com/document/d/1jqBL_IHtQ3HnBJTF2EDyugrxHQRRzJr-FE5lz-eNp28/edit?usp=sharing)

#### *Bonding period* 

Apart from bonding with the community, I worked on the display of MUC name along with JID in the status bar.

Related issue: [#3448](https://lab.louiz.org/poezio/poezio/issues/3448).

Related merge request: [!30](https://lab.louiz.org/poezio/poezio/merge_requests/30).

#### *Coding period*  

### *Phase 1* 

* ##### *1st week*  

I have implemented the scrollback feature in my first week of GSoC.
Scrollback basically scrolls back to messages in the buffer.

I tried to implement it the way Irssi uses it, so most of its usage is the same as that explained by [Irssi](https://irssi.org/documentation/help/scrollback).

This command would be helpful when someone wants to go a particular part of the conversation and roughly remember when the conversation took place (days-ago, date, time of the conversation). 
The user can use "/sb" command with "goto" argument along with "linenumber" or "timestamp" or "+|-linecount", to go to that part of the conversation in the tab.

The exact usage of the "/scrollback" command is explained in the issue: [#3481](https://lab.louiz.org/poezio/poezio/issues/3481).

Related merge request: [!31](https://lab.louiz.org/poezio/poezio/merge_requests/31).

* ##### *2nd week*  

I worked on the lastlog plugin in my 2nd week of GSoC.
Lastlog searches the current tab for messages with the searched "keyword" in them and displays them all in the current tab.

There was already some work done on this plugin by Maxime "pep." Buquet. So, I continued my implementation on the same work.

This plugin can be helpful when someone remembers some part of a past message but doesn't remember when the message happened or there are too many messages in the buffer to scroll back.
Using "/lastlog" with the "searched keyword" as an argument, messages with that word in them can be found.

The issue on which I worked: [#2950](https://lab.louiz.org/poezio/poezio/issues/2950).

Related merge request: [!35](https://lab.louiz.org/poezio/poezio/merge_requests/35).

* ##### *3rd week*  

I planned to start working on the implementation of message fetching using XEP-0313: Message Archive Management in my 3rd week of GSoC.
But, there were few things I was stuck at and was not able to understand why I wasn't getting the complete archive.
I tried querying for messages using "/rawxml", then found that I wasn't using XEP-0059: Result Set Management correctly because of which I was getting a limited number of messages. On changing that limit I was then able to get a complete archive of messages for all types of chats.

I am currently working on [#3053](https://lab.louiz.org/poezio/poezio/issues/3053).
The issue is about getting the current MAM preferences, changing the preferences for a particular JID and getting a complete archive of messages on a particular JID.

Once it is done, then implementing scrollback using MAM [#3052](https://lab.louiz.org/poezio/poezio/issues/3052) should be really easy.

* ##### *4th week*  

This week, I worked on implementing mam_tab.
The tab is basically to query for past messages, get MAM preferences and change the preferences for a particular JID.

In the mam_tab, user can use /mam command along with the JID of the MUC and with the range of timestamp for which query of messages has to be made.

Implementation of /prefs command is yet to be done, it would allow the user to view and set archive preferences for a particular JID. It's values can be: Default, Roster, Always.

### *Phase 2* 

* ##### *1st week*  

I have implemented an initial version of infinite scroll in the first week of second phase.

What it currently does is that whenever user is at the top of the conversation and presses Page Up key, then it sends a query to get an archive of messages using MAM.

Messages are then added at the top of the conversation.
It's default limit is set to query 10 messages per request.

There are few issues with it right now, I have planned to complete this work by the end of 2nd week.

* ##### *2nd week*

This week I completed work on the infinite scroll, it is currently under testing and I am fixing whatever issues are coming in between.

Related merge request: [!36](https://lab.louiz.org/poezio/poezio/merge_requests/36).

I have also implemented /mam_prefs command in the mam_tab, the command shows the current MAM preferences in the mam_tab.

Related merge requests: [!19](https://lab.louiz.org/poezio/slixmpp/merge_requests/19), [!37](https://lab.louiz.org/poezio/poezio/merge_requests/37)


* ##### *3rd week*

This week I fixed some issues related to infinite scroll and currently working on adding a command to set preferences in the mam_tab.

### *Phase 3* 

* ##### *1st week*

Implementing Message Archive Management (MAM) was not that easy as I was thinking about it earlier. The closer I get to its completion, more issues start appearing with it.

It is taking a bit more time than expected, but as per my proposal, the major part of my work is related to MAM and I want that to work really well.

This week my work was mostly on the infinite scroll and mam tab, for that I made a few changes in Slixmpp also.

Merge request related to Slixmpp: [!20](https://lab.louiz.org/poezio/slixmpp/merge_requests/20).

For the infinite scroll, there is a single merge request I am working on since last month: [!36](https://lab.louiz.org/poezio/poezio/merge_requests/36).

My this week's work for the infinite scroll can be seen with the commit messages: [e8332f51](e8332f51963efadada0136b12f4ca41cca9ea601), [e1461b4e](e1461b4e1559dbd137b6269a89a2d46646d097bd)

The first one is a check for IqError and IqTimeout exceptions while doing mam and disco query, the second one is to stop querying messages again and again if no more messages are left in the archive ( Info message is also added for that ), it also aligns the timestamp of the MAM start/end info messages with the archived messages.

Same is for the mam tab, there is another merge request I am working on for that: [!37](https://lab.louiz.org/poezio/poezio/merge_requests/37).

My this week's work for the mam tab can be seen with the commit message: [331af1f5](331af1f50c415e86b12a2d47928383e0863641ae)

It is the final version of getting and setting MAM preferences in that tab.

* ##### *2nd week*

This week I worked on changing the way I was querying for messages using MAM.

Earlier, it was based on the start and end timestamps.
The problem I realized with it is that when there are multiple messages with the same timestamp, then querying based on the timestamp might lead to loss of messages.

Since there's a unique stanza-id for each message, so I changed the query to stanza-id based.


Merge request related to Slixmpp: [!23](https://lab.louiz.org/poezio/slixmpp/merge_requests/23).

My this week's work for the infinite scroll can be seen with the commit message: [5079efd9](https://lab.louiz.org/poezio/poezio/merge_requests/36/diffs?commit_id=5079efd91d0e970a51c8731f83ef9f5434504373)

* ##### *3rd week*

Since this week was the last one before the GSoC phase ends, so I worked on completing the work I committed for my GSoC.

My this week's work for the infinite scroll can be seen with the commit messages: [8ccd592c](8ccd592ce91afa3807efb25f7791bfc4753a8f4a),[645e41fa](645e41fac71b733e8659ee3824928b897eb0dd8e),[509f303a](509f303a452374e1680b7ac1e86440f05b9a7be0),[7145d57a](7145d57a3b351dfe079830d88f439615b25b6b46),[2f50a67e](2f50a67e8c53a6d8b1dbf71a023a2d50495ee049),[ae64345a](ae64345a9893bc1498da5db6ab9bbb46b7e79f3f),[827a2c88](827a2c881603db01bd54a95de5b6ccd6489532d8)
