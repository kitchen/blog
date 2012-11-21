---
layout: post
title: "Mailing List Subscriptions"
date: 2012-11-20 18:32
comments: true
categories: email
---

For a long time I've been a huge fan of email discussion lists.
It's how I've learned about a lot of the software I use.
I hop on the list, try to read and absorb most every post, and get ideas about various uses.
Mailing lists are incredibly valuable to me, and since I've been on so many in the past, I have my own way of handling them.

<!--more-->

# Strategy

Every mail server I've used since I started with qmail over 10 years ago supports some notion of "extension addresses".
These addresses are on-the-fly "pseudo" addresses which still end up going to your mailbox.
By default, qmail uses a hyphen (-) to delimit the user from the extension, and postfix and Google both use + (though [postfix's delimiter is configurable](http://www.postfix.org/postconf.5.html#recipient_delimiter "postfix's recipient_delimiter documentation")).

These are really handy for other things besides mailing lists.
For instance, I used to also use a fresh one anywhere I entered my email address so I could track who was selling my address.
This is how I found out that GameFly either sold my address or was compromised, neither of which they were willing to admit to.

Anywho, I do this so I can configure my mail filtering to drop any mail coming into these addresses into a separate mailbox I create just for the list.
This is also useful in case the list server is compromised and that extension address is leaked, I know that it occurred and can take action, rather than just seeing an increase in spam.

# Filtering

The 3 different mail servers/services I've used over the years have slightly different ways of actually handling these extension addresses.

## qmail

Say your extension address is `user-listname1@example.com`

In your home directory, simply create a `.qmail-listname1` file with instructions for what to do with the message.
See [dot-qmail](http://www.qmail.org/man/man5/dot-qmail.html "dot-qmail(5)")(5) for more information about what you can do with these files.
Typically, you'll want to put these messages in a different maildir, which is quite simple:

	/home/user/Maildir/.listname1/

That should do the trick!

## Postfix

Postfix's mechanism is quite similar.
Say your extension address is `user+listname1@example.com`.

In your home directory, simply create a `.forward+listname1` file with delivery instructions.
See [local](http://www.postfix.org/local.8.html "local(8)")(8) for more information about the available instructions in `.forward` files.
Again, delivery to different maildir is quite simple:

	/home/user/Maildir/.listname1/

## GMail / Google Apps

A year or so ago, I switched all of my personal email from being self-hosted (after nearly 10 years of using qmail and then postfix).
One of the big things that prevented me from doing so before was because I couldn't filter incoming emails based on extension address (even though GMail has support for them).
Fortunately, this actually is possible, it's just not very well documented.

1. Search for `deliveredto:user+listname1@example.com` in the search bar at the top of the GMail interface.
2. Click on the drop-down arrow at the right end of the search box.
3. Click on "create filter for this search" at the lower right of the dialog which pops up.
4. If you want to put the message *only* into your new mailing list folder (or label, in GMail's terms) then check "Skip the inbox".
5. Choose a label to apply to the incoming message, or create a new label to apply.
6. Click on "Create filter".

You're all done! This works very well.

# Mailing list software

Most mailing lists require you to be subscribed to the list to post, to prevent spam.
This doesn't actually prevent a spammer from simply using a list member's address as an envelope sender and spamming the list anyways, but it does make the spammer have to actually find one of those before the spams can be posted, so it's pretty effective.
Unfortunately, in order to use the filtering schemes from above, we need to subscribe to the list from our extension address so the messages get filed appropriately.
Because of this, we now have to change our sender for every message we want to post to the list to match the list subscription address.

Or do we?

There are 4 major mailing list software packages I've encountered out there, and each of them has a method for dealing with this.
It may not be the reason these features exist, but we can certainly abuse these features to achieve our goals.

## ezmlm-idx

ezmlm-idx has a really brilliantly simple method for subscribers using this type of setup.
Each list has the list itself, and a special 'allow' list, which you can subscribe to.
The strategy with ezmlm lists is such:

Say we're dealing with an ezmlm-idx list at `discussion@lists.example.com`

1. Send an email to `discussion-subscribe@lists.example.com` from your extension address.
2. Send an email to `discussion-allow-subscribe@lists.example.com` from your posting address.
3. Confirm both subscriptions.

Now, you'll be able to post from your posting address (and your extension address, too, but that's not important) and receive list mails only to your extension address.
This method works great, and is one of the many reasons I really prefer ezmlm-idx for mailing list software.

### vanilla ezmlm?

So, I should note here that the -allow feature is a feature of ezmlm-idx, and is not part of the stock ezmlm software.
However, the only ezmlm lists that I'm aware of which are *not* running ezmlm-idx are djb's mailing lists, which don't have posting restrictions at all.
The method of restricting posting to the lists is called 'qsecretary' and is a simple challenge-response system which you are required to pass for every post to one of his lists.
In these cases, you simply subscribe with your extension address and post from wherever you'd like.

## Mailman

Mailman is probably the most common mailing list software I encounter in my travels.
I am not a huge fan of having to deal with web interfaces or passwords for managing mailing list subscriptions, but I'm also biased because I'm such a huge fan of ezmlm-idx.

The setup with mailman is quite simple.

1. Subscribe to the list with your extension address.
2. Subscribe to the list with your posting address.
3. Log in to manage your posting address and disable mail delivery.

You're all set!
You can now post to the list from your posting address, and posts to the list will be delivered to your extension address.

## Majordomo

Majordomo used to be the king of mailing list software.
However, very few majordomo lists still operate.

Until recently, I wasn't aware of a way to do this split-subscription with majordomo, but thanks to a post on the mutt mailing list (which uses majordomo), I've [discovered that it is possible](http://www.cyber-hacks.org/help.htm#nomail "majordomo nomail command").

To send commands to the majordomo, simply send an email to the control address with your commands in the message body.
To set up the subscriptions for `discussion@lists.example.com`, send emails with the following commands to `majordomo@lists.example.com` (we'll assume your posting address is `user@example.org` and your extension address is `user+listname1@example.org`)

1. subscribe discussion user+listname1@example.org
2. subscribe discussion user@example.org
3. nomail discussion user@example.org

You'll need to confirm the commands, but once that's done you should be all set!

Note that the 'nomail' setting of majordomo is an administrator-configurable option, so it may not be possible to set this up with the majordomo list you're subscribed to.
As always, your mileage may vary.

## Google Groups

Google groups, sadly, doesn't seem to have a way to be set up on a list without having a Google account.
Fortunately, Google adds a distinct header into each email delivered by the list which you can filter by:

    List-ID: <listname.googlegroups.com>

While your emails may be delivered to your posting address, at least you can differentiate the messages coming from the list via that header.
You can use something like procmail or maildrop to handle filtering based on message headers.
If you're using GMail for your email, filtering by this is as simple as changing your search from 'deliveredto:extension' to 'listid:listname.googlegroups.com' and this seems to work pretty well also.

There is one other way which may work. Apparently anyone can subscribe to a Google Group via email, by sending a message to `groupname+subscribe@googlegroups.com`.
If you have a Google Account, you can join the group with that address, which will allow you to post from there, disable mail delivery, and then subscribe to the list via email from your extension address. I have not yet tested this means, however, so it may be problematic or it may not even work!

# Finally

So, that's how I do my mailing list filtering and mailing list subscriptions.
I used to also have something which would bark at people if they reply-alled to a mailing list post of mine (it would look for the list's name in the headers of mail going to my post address and send them back a reply), but since I no longer use qmail for my email, I haven't bothered setting this up again.
Also, the automated replies tended to get some angry emails from people, which, while I found them to be entertaining at the time, I look back and realize it was quite pedantic of me to be doing that in the first place.
I mean, I already knew they were duplicates, I could have just silently thrown them away.
