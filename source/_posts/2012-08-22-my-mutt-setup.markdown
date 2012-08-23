---
layout: post
title: "my mutt setup"
date: 2012-08-22 21:45
comments: true
categories: linux email
---

For many years off and on, I've tinkered around with [mutt][mutt], with varying degrees of success.
At the very least, it's always been in the back of my mind every time I get fed up with my mail client du jour.
Recently, after a 3 month stint of using Outlook at work, I decided to give mutt another shot.
Fortunately, this time I was sucessful, and I'm now using mutt as my primary email client both at work and at home.
Let me tell you, it's a breath of fresh air!

 [(Pretty, ain't it?)](images/mutt.png "mutt screenshot")

Because I'd previously had so many difficulties with mutt in the past, and now have things set up fairly decently, I thought I should write something which might prove helpful for other potential mutt users, or maybe even seasoned veterans.

<!--more-->

# the .muttrc

The .muttrc is, of course, mutt's primary config file.
This is where the meat of your configuration should go.
This is the trap I fell into every time I'd tried to use mutt in the past.

In previous attempts of configuring mutt, I feel like I tried to make it do too much right out of the gate.
I wanted it to work with my Maildir++ mail store.
I wanted it to work with my IMAP account at work, too.
I wanted mail sent from my personal account to go out through my mail server, and from my work account to go out through work.

There were plenty of other things I tried to get it to do, and inevitably, it would not be to my liking and I would give up.
If it worked, it was kludgy, ugly, and difficult to use.
It also often involved a lot of hard-coded mailboxes and whatnot just to even let me look at any of my mail.
Yuck.

This time, I decided to go a different route.
I had been using Google Apps for my personal email for a long time, and have been fairly content with the web interface, at least for casual mail browsing, so I decided I only really needed to get my work email set up since it was use mutt or use Outlook, and really, it meant I had no choice at all ;-)

I went simple. I started off with a color scheme and setting up my IMAP account and a small handful of key bindings I brought over from a previous mutt attempt.

{% gist 3432100 %}

You'll notice that I'm using [Solarized][solarized] here.
I really think that this is one of the reasons this attempt at mutt has been successful.
Solarized is beautiful, and the [Solarized theme for mutt][mutt-solarized] makes mutt really gorgeous.

I used this setup for a couple of days and really started enjoying it.
I of course made some tweaks to the configuration as I stumbled across them, but nothing major, and mostly personal preferences.

# multiple accounts

Armed with the happiness of using mutt for work email for a few days, I decided I wanted to set it up for my personal email as well.
This has given me much pain in the past, however, and I was really starting to get comfortable using mutt and didn't want to ruin the fun.
I decided to split my .muttrc up into a number of files:

* rc file for work account information
* rc file for personal account information
* rc file for shared configuration (key bindings and the like)

Seems fairly logical, right?
The twist is, that instead of having the shared configuration include the work and personal account information, I went the opposite route and the account information rc files include the shared configuration.
The primary benefit of this is that I have completely separate, but equal environments for my email accounts.
Another great benefit is that I don't have to do any crazy hooks to make sure I'm sending from the right account, or through the right SMTP server, or storing the mail in the right place, or any of that.
Plus, it seems like the IMAP folder browser only works on the account in `$folder`, so in order to look at the other account I have to set up those folders with the `mailboxes` command.
Ugh.
This way, though, they're completely separate. The IMAP browser works just fine, mail is always sent from the right account, etc.

{% gist 3432326 work.rc %}
{% gist 3432326 personal.rc %}
{% gist 3432326 shared.rc %}

You'll note that I'm exclusively using IMAP now, whereas in the past I'd tried to use a local Maildir++ spool.
This is because mutt's IMAP support seems to be really solid, and then I don't have to worry about populating the `mailboxes` command, It Just Works™
I'm also using SMTP, because I don't want to have to deal with my mail being blocked because I'm at my home on a residential IP block, or because the coffee shop I'm in doesn't allow me to connect to port 25 directly, or any number of things.

So, now that I have them split up, how do I access them?
Well, in my shell I've made a couple of aliases:

    alias workmail="mutt -F ~/.mutt/work.rc"
    alias homemail="mutt -F ~/.mutt/personal.rc"

This makes it real nice and easy to keep the accounts and those details completely separate, but allow for a large amount of shared settings as well.

# finally

I've been running with this setup for a couple of weeks now, and really enjoying it.
Mutt is one of the few mail clients anymore which has proper threading.
Everyone seems to be switching over to the 'conversation view' and threading by subject.
I may just be to old-school, but I didn't see anything wrong with threads as they were, and in fact prefer them.
Flat conversations are hard to read when a thread becomes too long, look at forum threads, half of the time it's impossible to see what someone is referring to.
But... That's another post. (Sorry, Alton Brown)

I have a simple setup which mirrors the setup described in this article [over on GitHub][github-kitchen-muttrc].
Please feel free to use it, it's why I made it!

[solarized]: http://ethanschoonover.com/solarized "Solarized color scheme"
[mutt-solarized]: https://github.com/altercation/mutt-colors-solarized "Solarized mutt theme"
[mutt]: http://www.mutt.org/ "The mutt email client"
[github-kitchen-muttrc]: https://github.com/kitchen/muttrc "sample muttrc on GitHub"
