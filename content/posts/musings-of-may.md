---
title: Musings Of May
author: Arokh
description: Little update about the life of a runedragon!
summary: Life has a way of blending things together...
tags: ["Arokh's PoV", "NoMoreZeroDays"]
series: ["The Journey"]

toc: false

date: 2024-05-22T09:05:05
draft: false
showauthor: true
---

Greetings!
It's nice to see you here, thank you for checking in!

It's been a bit since I have posted anything on the Mindweb but rest assured, I've been doing well!
There are a number of little things that I have been working on recently, from getting my Audible
downloads and converting them from the native .aacx file format into .m4b so I can listen to them at
work to grabbing a new neovim configuration set up. I'll put the more technical aspects of these up
in dotfiles at some point (I'm still working on the posts) but I'll go over a bit of the trial and
error involved with these processes after I go through the personal stuff.

## Mentality and Hatchdays
> Braining is Hard

I am, for the most part, a solitary creature. I check in with Sylvio daily and there are the daily
dinner-time chats that happen with those whom I share a lair. Outside of that, however, I am quite
happy to simply keep to myself and engage with the things that I enjoy doing. Sometimes this
includes interacting with others but most often, it's something that I've hyperfocused upon. There
have been four of such things since the last time I posted to the Mindweb: Solo-Leveling, Tower of
God, Chorus of Dragons, and Dragon's Dogma 2. I'll get into these after this!

Also, I recently celebrated my hatchday; though, to be honest, those aren't much more than a typical
Tuesday. I don't generally care for the fanfare and celebration that most others do... My hatchday
is generally a day I prefer to spend taking care of myself. That said, thank you to all the friends
who sent their well-wishes along!

I've been struggling a bit with melancholy, lately, things outside of my hyperfixations have been
feeling rather... daunting. It might be from a lack of sleep, honestly. (Did I mention that hyperfocusing on
something is generally disastrous for one's sleep schedule? No? Well, let it be known... Spending
two weeks of your life getting 3-5 hours of sleep each night isn't particularly healthy. I would not
recommend it.)

### Solo-Leveling
> `ARISE`

This is like... the grandfather of the isekai genre. It's not _really_ isekai but it fills a similar
sort of style. I'll not get into too many spoilers here because I highly suggest you take a look at
this on your own and make your own memories of it. It's a lovely, cohesive story with a good, sturdy
ending that was satisfying. Again, I highly recommend taking a look at the manhwa if you get the
chance to do so.

### Tower of God
> The 25th Bamm knockin' it out of the park!

I spent about two weeks straight reading this manhwa and the entire thing was hyperfocused beyond
any expectation or proper ability to control. I don't think I've been as frustrated with a
hyperfixation as I was with this one--not because it was a bad read or story but because it was 'my
kind of story' and I literally could not get it out of my head. Also, it's long. I don't read slowly
but this thing took forever to get through; there's a lot of material. It's available online and,
like Solo-Leveling, I would highly recommend reading it if the first season of the anime grabs your
attention.

### Chorus of Dragons
> Rev'arric is a bastard.

This is a lovely little set of books by Jenn Lyons. Starting with _'The Ruin of Kings'_, the series
follows a boy who's the reincarnation of a big spooky and his struggles to overcome those who would
use both him and the big spooky to do dispicable things. The story is somewhat gritty and is not at
all what I would consider 'all smiles.' The ending is fairly predictable if you're paying attention
to the story but it has a sort of subversion of the typical 'character with god-like power can do
whatever they want' and, for that, it's a refreshing story. I wouldn't say the ending is exactly
happy but it's definitely not a 'bad guy wins' ending. The story swaps point of view with each
chapter and it's told 'after the fact' -- where the major events of the story have already happened.

### Dragon's Dogma 2
> The Neverending Ring supports another cycle...

DD2 is not as good as the original was, in my opinion. That said, it was still a fun game and it did
enough to occupy the vast majority of my attention. I ended up at level 80 or so by the time I
finished the Unmoored World. The story was not much of a departure from the first game's and you
know the premise of the game before you start it -- if you've played the first. The main story is
supposed to be short because you're supposed to play it in a series of cycles... I.E. the
Neverending Ring. The vocations for this game are all very good at what they were designed to do.
I will, however, mention that I absolutely HATE the `Trickster` vocation; it's focused upon supporting
the pawns but I am definitely not the kind of player who enjoys 'minion builds' and that is what
Trickster leans into. Similar to the first game, my favorite vocation for Dragon's Dogma 2 is
going to be `Warrior`. Sorry but I just love the BIG SWORD (or mace, depending on the enemy).

## Hijinks and Horseplay
> No, not THAT kind of horseplay.

Aside from the hyperfixations, I've embarked upon a handful of technical jaunts that have ended with
mixed success. Some of the things, like OpenRGB were a total failure. Others, like the conversion
project for .aacx files, were successful. _(I'm making a note here, **HUGE SUCCESS**)_ GLaDOS and
megalomania aside, there have been a number of technological things I'd like to mention.

### OpenRGB
> The Promise... of Fire.

OpenRGB is great. However, it has a glaring flaw in that, if you have a VEGA graphics card, the RGB
headers are protected. OpenRGB doesn't handle this. At all. And instead of gently wandering into
the night, it decides that it's going to send your kernel into a panic or just straight-up murder
your machine. It's nothing permanent, of course, but it is quite obnoxious. There's supposedly a way
to disable querying these specific interfaces but in all the posts that mentions doing so, they
never once mentioned how to actualy exclude them. 'Just exclude the graphics card RGB headers,
4Head. It's that easy!'

After 3 hours of frustration and attempts to get things to not crash, I gave up on having fancy
RGB lighting on my motherboard (honestly, I just wanted it to have some light in there).

### OpenAudible
> No, do not actually use this. Like don't.

Open source software is cool and doesn't usually have any weird obligations or pay structures in
the deliverables. If you want to assist with the project, you contribute code or you donate to the
project. It's simple.

Well, not always. OpenAudible is _technically_ open source. Technically. However, the author stole
the difficult bit of the code from someone else, claimed it as their own, and is now charging for
use of said feature. The difficult bit I'm talking about? It's a project that allows one to manage
their Audible library from a series of scripts and commands. It's a nice little CLI toolkit but it's
a little confusing for the average user because it's a CLI. The hardest part about it comes from the
need to download files from Audible in the form of an .aacx file; a proprietary format with the
data encrypted. There's a personal key that you need in order to decrypt the audiobooks/podcasts/etc
that you download from Audible. It's not easy to get hold of your own key and this CLI package did
all of that for you. _OpenAudible stole that and uses it for their own gain._

Long story short, I spent a couple of afternoons looking into how to get my audiobooks downloaded
and converted so I could listen to them offline, regardless of the environment or audio player and
without needing to go through Audible to reacquire them. It was a fun little project and I now have
close to 50gb of audiobooks converted into m4b files that I can play through any media player I
feel like using. :smile:

### LazyVim

The next project I want to talk about is a thing called LazyVim. It's a sort of plugin manager for
Vim that I started with because I didn't know any better and people recommeded it. LazyVim is a bit
confusing to set up but it works nicely and allows you to do whatever you want/need so long as you
can find a plugin for it. (Neovim uses lua and vimscript for its extensions. It's not difficult at
all to find plugins and they're all compatable with each other unless there's a _specific_
dependency that one can't simply import.)

I used this for a month or so and felt pretty good about it overall. I eventually found a little
snippet plugin and played around with that as well. Both of these things were fun to play with but I
found myself not entirely happy with the setup overall. There was a lot of extra stuff that came
with the LazyVim version I had and I really didn't feel like I needed it all.

### Mini.Nvim
> 'Mini' for minimal

Enter mini.nvim... It's a nice little set of plugin loader and minimalist plugins that acts as a
single-implementation replacement for most things that a developer would want. There are some things
missing, like the snippet plugin I mentioned earlier. Of course, that's easy enough to reinstall. I
have been using this set up for about a week now and I like it much better. There's not so many
things interacting with what I'm doing and I just feel more comfortable with it. Plus, there are a
few things that I can do with mini.nvim out of the box that I wasn't able to do with LazyVim out of
the box. Plus, one of the colorschemes is largely made of various blues and I am a fan.

---

Well, I think that's all I have to talk about for the moment... I suppose it's nothing exciting but
that's how I've been! I spend the vast majority of my time resting in my lair reading from my hoard
of books. Thanks again for taking the time to come visit and check on an old runedrake. He's quite
appreciative of your attention.
-- Arokh
