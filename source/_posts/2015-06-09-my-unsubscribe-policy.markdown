---
layout: post
title: "My Unsubscribe Policy"
date: 2015-06-29 16:35:33 -0700
comments: true
categories: journal
---

Email marketing has come a long way since I first started using email.
Back in the day, it was conventional wisdom that you never click unsubscribe, because that just lets the spammers know they have a legit email address.
Nowadays, however, it is *my* recommendation that you *always* click unsubscribe, even if it *is* a spammer, because honestly they don't really care, and the folks who are doing legit email marketing stuff *will* remove you from their lists.
Spam report button feedback loops have gotten sophisticated to the point that mailers have to pay attention to their spam reports because if they get too many they can start being impacted in their ability to send mail.

However, not all unsubscribe buttons are created equal. I have a grading system which I've put into place to judge the quality of a mailer's unsubscribe link, and based on that grade, I decide whether or not I'm going to proceed through the process or if I'm going to just report the email as spam.

# Grading

I use letter grades because it's simple. And also allows for an unsubscribe link with a few minor annoyances to still receive a pretty passing grade.
A+, A, A-, B+, etc. Each unsubscribe starts with an A by default.
Any failing grades are marked as spam.

# Criteria

These are the criteria I use to grade each unsubscribe experience. Each one has varying degrees of penalty, and some are instant fails.

## Clicks

Each and every unsubscribe link gets 1 free click. A lot of unsubscribe links ask you to confirm your unsubscribe, and that's totally fine. It's a better user experience to have an extra click than to have to somehow resubscribe if you accidentally unsubscribe.

For every other click after that, it's a third of a letter grade penalty.

An example of this is a site that has multiple mailing lists, and it wants you to confirm which ones you want to unsubscribe from.
Extra annoying is that sometimes the boxes are checked, and leaving them checked and clicking means that you continue to receive the mails.
Extra extra annoying is that sometimes you have to uncheck all of the boxes and click (the "update preferences" style) or check all of the boxes and click (the "unsubscribe me from these" style)

## Typing

The absolute last thing I want to do is to type in my email address to unsubscribe.
The site should already know my email address.
It should know this because it's either directly embedded in the unsubscribe url, or because it's somehow encoded into the url, or referenced via a unique identifier which is encoded in the url.
Because of this, there are varying penalties surrounding 

If the unsubscribe link doesn't contain any information which could be used to look up my email address, and the site asks me for my email address, it's a full letter grade off.

If it does, or should (because the url contains information which should be able to identify me and my email address) know my email address and forces me to enter one, that's 2 full letter grades off.

If the site goes as far as to present me my own email address, and asks me to type it in anyways, I take 3 full letter grades off.

Note that a form asking for my email address and already filled in with my email address that functions just fine receives no penalty.
I have no problem with sites which allow me to unsubscribe someone else.

## 3 weeks later

For every day past greater than 1 the unsubscribe link says it may take to stop receiving emails, I remove a third of a letter grade.
I understand that mailings are often already prepped, ready to roll, and out the door in advance.
However, generating the actual email list is the easy part, and it's not difficult to quickly cleanse the list of last minute unsubscribes just prior to sending.
It should not take 7-10 business days for emails to stop coming.
It's not like someone is hand-typing my email address into every mailing, and if there is, then I definitely don't want to receive the emails anymore.

## Instant F

If any of the following occurs, the unsubscribe link receives an instant fail, and the message is immediately marked as spam.

### No unsubscribe link

Obviously, if there is no unsubscribe link, and I don't want the email, it will be marked as spam.

### Extra trick question

This is a variant of the "update preferences" style from above, except that it automatically has all of the boxes checked, even for things you aren't subscribed to.
If you screw up and don't check the boxes properly, you could end up being on more or different lists from this company.
This is a hard one to judge objectively, as I from an initial contact perspective, I don't know what all I was signed up for.
This is more of a "if I catch you doing this" sort of thing.
I have a feeling it's a lot more prevalent than it should be.

### Log in

If the unsubscribe link takes me to a login page, or if the email itself suggests I log in somewhere and update my email preferences, it is an immediate fail.
Often I am trying to unsubscribe from emails from a service I am no longer a user of.
Perhaps I don't even know my credentials anymore (rarer nowadays, due to 1Password).
The last thing I want to do is try to guess my credentials, or jump through a bunch of hoops to reset my password, just to unsubscribe from emails.
Log in? Nah. I'll just report as spam.

### Second chance? Nope

If I receive emails after 24 hours or after the stated number of days on the unsubscribe page, then I wasn't unsubscribed.
The email will be immediately marked as spam.


