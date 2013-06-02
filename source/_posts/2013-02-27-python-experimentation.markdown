---
layout: post
title: "Python Experimentation"
date: 2013-02-27 13:13
comments: true
categories: [ linux, python ]
---

I've been a perl user for about 10 years, but recently I decided I should start learning another language.
Not that I don't like perl or anything, but I wanted to branch out and learn something new.
After doing some quick research and listening to my gut, I decided [python][python] would be my language of choice.

I'm an interactive learner.
I can read a book on a language, tool, whatever, but if I'm not actually using it my knowledge retention is quite low.
Fortunately, I've also been getting into [logstash][logstash] lately, and have some real needs which I can use python to fill.

So far I have 2 projects I'm working on: [peabody][peabody] which I've [already written about][peabody-blogpost], and now [pipestash][pipestash] which I'm hoping to use for shipping apache log messages over to pipestash.

I'm not just venturing into unknown territory with python as the unknown territory, I'm trying to learn some more general programming strategies as well.
Pipestash makes use of a queue and multiple processes (thanks to python's [multiprocessing module][multiprocessing]) and talks to a redis server.
Peabody makes use of multiple file descriptors and polling and also a redis output.
I might even throw some of my new multiprocessing knowledge into peabody, so instead of using select on multiple file descriptors, I might use 2 threads, one to read stdout and one to read stderr, which should simplify the code a bit and make it easier for my brain to work!

I'd like to get to the point where I'm as proficient with python as I am with perl, and actually where I'm much more proficient.
It's going to be a long, interesting journey!

[python]: http://python.org/ "python programming language"
[logstash]: http://logstash.net/ "logstash - open source log management"
[peabody]: http://github.com/kitchen/peabody "peabody - cron's best friend!"
[peabody-blogpost]: /archive/2012/09/13/introducing-peabody/ "Introducing peabody!"
[pipestash]: http://github.com/kitchen/pipestash
[multiprocessing]: http://docs.python.org/2/library/multiprocessing.html "python - multiprocessing"
