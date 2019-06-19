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

Apart from bonding with the community, I worked on the display of MUC name along with JID in the status bar".

Related issue: [#3448](https://lab.louiz.org/poezio/poezio/issues/3448).

Related merge request: [!30](https://lab.louiz.org/poezio/poezio/merge_requests/30).

#### *Coding period*  

* ##### *1st week*  

I have implemented scrollback feature in my first week of GSoC.
Scrollback basically scrolls back to the messages in the buffer.

I tried to implement it the way Irssi uses it, so most of it's usage is the same as that explained by [Irssi](https://irssi.org/documentation/help/scrollback/)

This command would be helpful when someone wants to go a particular part of the conversation and roughly remember when the conversation took place (days-ago, date, time of the conversation). The user can then use /sb command with 'goto' argument along with <+|-linecount>|<linenum>|<timestamp>, to go to that part of the conversation in the tab.

The exact usage of /scrollback command is explained in the issue: [#3481](https://lab.louiz.org/poezio/poezio/issues/3481).

Related merge request: [!31](https://lab.louiz.org/poezio/poezio/merge_requests/31).

* ##### *2nd week*  

I worked on lastlog plugin in my 2nd week of GSoC.
Lastlog searches the current tab for messages with matching <keyword> in them and displays them all in the current tab.

There was already some work done on this plugin by Maxime "pep." Buquet. So, I continued my implementation on the same work.

This plugin can be helpful when someone remember some part of a past message but don't remember when the message happened or there are too many messages in the buffer to scrollback.
Using /lastlog with the 'search keyword' as an argument, messages with that word in them can be found.

Issue on which I worked: [#2950](https://lab.louiz.org/poezio/poezio/issues/2950).

Related merge request: [!35](https://lab.louiz.org/poezio/poezio/merge_requests/35).

* ##### *3rd week*  

I planned to start work on implementation of message fetching using XEP-0313: Message Archive Management in my 3rd week of GSoC.
But, there were few things I was stuck at and was not able to understand why I wasn't getting the complete archive.
I tried querying for messages using /rawxml, then I found that I wasn't using XEP-0059: Result Set Management correctly.
Thus, I was getting limited number of message. On changing that limit I was then able to get complete archive of messages for all type of chats.

I am currently working on [#3053](https://lab.louiz.org/poezio/poezio/issues/3053)
The issue is about getting the current mam preferences, changing the preferences for a particular JID and getting complete archive of messages on a particular JID.

Once it is done, then implementing scrollback using MAM [#3052](https://lab.louiz.org/poezio/poezio/issues/3052)should be really easy.

