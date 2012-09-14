---
layout: post
title: "introducing peabody"
date: 2012-09-13 18:26
comments: true
categories: linux
---

I'm proud to announce the arrival of [peabody][peabody], cron's best friend!

Peabody grew out of a need for various features I found myself continually writing into cron jobs.

Here are some of its key features:

## splay

Everyone has always told you to avoid running your cron jobs "on the hour" or "right at midnight", and you know it's bad, but you still do it, and often times, if you're using one of the `@hourly`-style features, you don't have much choice.
But you also have thousands of jobs, and you don't want to have to modify all of them to put in random sleeps to spread the spike out around the interval.
What happens if you want to change the duration of the sleep, [now you have to change a line of code][6days1line].

Not anymore!
Peabody's "splay" feature allows you to delay starting your job by a random interval up to the duration you specify.
Since this lives outside of your code, and on your systems, *you* are the one who has control over the duration, and *you* can change it any time you want should you require.
Additionally, it doesn't require modifying *any* existing code. You simply add `peabody -s <interval>` in front of the command in your cron entry, and you're done!

## concurrency protection

You have a cronjob which you want to run *every minute*.
But sometimes that job can take more than a minute to run.
And the job isn't very smart, so a second job will start working on the same things, maybe even stepping on the work the other one is doing.
How can you fix this?

Well, you *could* have your job be smarter about the work it's doing and make it so it doesn't step on its friends.
This has problems of its own if you have a high rate of queue injection and the individual tasks consume a lot of resources.
Not to mention this is a whole lot more than one line of code!

Or, you could have your job check to see if there's already a copy of itself running.
But then you'd have to do this in all of your jobs, and that's a headache.
Did I mention the line of code?

Or!
You could just let Peabody do it for you!
Simply add `peabody -l /tmp/jobname.lock` before the command in your cron entry, and now only one can run at a time and you can make *everything* run at 1 minute intervals.
Logs bedamned!

## timeouts

Maybe your job takes a while to run, but you know that if it takes over an hour, it's gone on too long.
You could write some sort of timeout into your code.
And honestly, you should.
Seriously.
Your code should time itself out.
I'm not even kidding.

But, maybe you can't!
Maybe it's a third-party program which you don't have any easy control over.
It doesn't have to be a closed source program to have issues like this.

Peabody to the rescue!
Simply put `peabody -t <softtimeout> -T <hardtimeout>` in front of your job and off you go!
Once the job has run for the softtimeout interval, Peabody will send a happy little SIGTERM to your job, asking it to stop what it's doing and get lost.
If that doesn't work (or you just want to be a little more harsh out of the gate), once it reaches the hardtimeout interval, Peabody will send your job a SIGKILL.
Not even Linus can ignore a SIGKILL (unless he's busy flirting with your NFS server).

## ok, I'm sold

Great! Head on over to the [Peabody page on GitHub][peabody] and check it out!

## where do we go from here?

Peabody was initially conceived to take the output of a cron job and shove it into [logstash][logstash].
It's actually rather ironic that it doesn't yet do this.
However, it is on the roadmap, and it is definitely still something I want to add.
I just got a bit distracted by all the other things I would want a wrapper like this to do.



[6days1line]: http://edweissman.com/it-takes-6-days-to-change-1-line-of-code "I'd rather sit through 2girls1cup"
[peabody]: https://github.com/gorillanation/peabody "Peabody, cron's best friend!"
[logstash]: http://logstash.net/ "logstash, the log stasher"
