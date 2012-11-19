---
layout: post
title: "Mailing List Subscriptions"
date: 2012-11-19 11:51
comments: true
categories: email
---

How I handle mailing list subscriptions:
* extension addresses
kitchen+listname@kitchen.io

setting up delivery for various mailing list managers
* majordomo
  send nomail to list command address
* mailman
  2 subs, one with mail delivery disabled
* ezmlm-idx
  subscribe to listname-allow
* ezmlm-vanilla (can't do it, but I don't know of any list using ezmlm which doesn't use -idx other than djb's lists which just have qsecretary handling the "subscribers only" thing

how to go about filtering these:
* qmail, use .qmail-extension and add a Maildir
* postfix, use .forward+extension and add a maildir
* gmail/google apps use deliveredto: filter

those are really the only 3 I have come across in terms of discussion lists.



