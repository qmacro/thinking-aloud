## 2021-12-23 15:31:30 Owning one's words, blogging, group chat and Docker
Different things have been colliding in my head about owning one's own words, decentralisation, group chat and Docker.

Today in a coffee break I read a few posts, including the classic [Your words are wasted](https://www.hanselman.com/blog/your-words-are-wasted) by Scott Hanselman, and [Blogodammerung](http://www.tbray.org/ongoing/When/201x/2012/08/18/Blogodammerung) by Tim Bray. Both written in 2012 but just as relevant today, if not more. I also read and commented in a [Twitter thread started by Christian Drumm](https://twitter.com/ceedee666/status/1473923174261829634) on the search for a usable discussion forum platform.

There may be an element of rose-tinted spectacles here, but I'm minded to think that communication and content on the Internet (yes, the Internet, not just the Web) was better in the past. Better in a number of ways:

- we blogged more, article-length and longer-form content
- we managed references to and comments on those blog posts and articles
- we owned our own words by blogging on platforms that we owned or built
- group conversation was supported by protocols that allowed us to choose our own clients
- group conversation felt also more ... asynchronous

Regarding group conversation - I'm thinking of mailing lists, where threaded conversation was the norm, and we all enjoyed participating from the comfort of our choice of email clients (not to mention the simplicity and focus of plain text email rather than the monstrous HTML based email that people can't seem to live without). I'm also thinking of Usenet, via the Network News Transfer Protocol (NNTP) which served a similar but different purpose but had the same ideas.

And then there's microblogging - I was a user of "identi.ca" before Twitter came along, and I resisted joining Twitter for a while because of the appeal of "identi.ca"'s decentralised approach (I eventually succumbed in [January 2007](https://twitter.com/qmacro)).

Talking of decentralisation - how can one not mention instant messaging here, and the wonderful Extensible Messaging and Presence Protocol (XMPP) (neé Jabber)? One could run one's own XMPP server, and control one's own identity, participating in a federated set of connections.

What's happened? Has independence and content ownership lost out to commercialism and centralisation? I'm not going to try to answer that, but instead, have a question to ponder.

What would it take to set up a starter set of tools, of clients and federated server mechanisms, in one or more coordinated Docker images, for individuals to pull, run and manage? It's not a magic bullet - some of the non-trivial challenges are in the area of connectivity and server persistence (where should the Docker containers run for long-lived lifetimes, for example?).

In my blog post from earlier today ([Truncation and neat terminal output](https://qmacro.org/autodidactics/2021/12/23/truncation-and-neat-terminal-output/)) I showed the output from `docker ps` running against the Docker context provided by the engine in [my Synology NAS](https://www.google.com/search?q=site%3Aqmacro.org+synology). In that output you can see that I'm just beginning to scratch the surface of older tools wrapped up in Docker - Weechat (an IRC client) being one of them. What might the next level of containerised tools (and federated servers) look like?

It might be a pipedream, but definitely worth thinking about. I for one would love to see more folks owning their own words, blogging on platforms they control, connecting as they see fit while disconnecting from the large centralised commercial organisations.


[Discuss](https://github.com/qmacro/thinking-aloud/issues/36)

<hr>

## 2021-12-03 13:46:58 Fast, Elegant, Instructive - Pick One #AdventOfCode
I'm intentionally only dabbling in [this year's Advent of Code](https://adventofcode.com/2021) because I know that the puzzles will get harder over the month, so much so that I won't have the time to dedicate to solving them.

This approach has at least given me the "excuse" to just use whatever technique or language I feel like to solve the puzzles. I tried a bit of APL for day 1, used Bash for day 2, and have used standard JavaScript (rather than, say, [Ramda-flavoured](https://ramdajs.com)) for day 3. Moreover, I won't feel as guilty if I don't solve day 4. Then again, I'm on a private leaderboard and can't help seeing what others are up to, and feeling some competition and pressure!

Anyway, I realised the eternal dilemma I face during December because of Advent of Code and it's similar to what we know from "Fast, Cheap, Good - Pick Two". This version is "Fast, Elegant, Instructive - Pick One". In other words, my small brain allows me to solve a puzzle in only one of these modes:

* fast: just getting it done quick (and most likely dirty)
* elegant: writing something tidy, that I could show to others
* instructive: using the puzzle to learn something new, either in a new language (especially if it's from a different [descendant](https://madhadron.com/posts/seven_languages.html)), or a new technique

![Fast, Elegant, Instructive - pick one](https://pbs.twimg.com/media/FFr3RxZWUAMBGkO?format=jpg&name=medium)

Do you feel the same?





[Discuss](https://github.com/qmacro/thinking-aloud/issues/35)

<hr>

## 2021-12-01 08:48:33 Valid JSON and what to call each piece?
I've been thinking recently about what name to use for something. That something is a piece of JSON. A JSON "thing". These thoughts have become more frequent as I've been digging deeper into `jq`, the command line JSON processor.

`jq` will accept a piece of JSON and process it as expected. But it will also accept multiple, err, pieces, and process them in sequence. Why is this important? Well, lists of such JSON pieces are common in various APIs that emit data represented in records, records that have potentially complex structure beyond just a list of fields. And often these records are represented as JSON objects.

There's even a recognised format for this type of "records of JSON" data, and that is [ndjson](http://ndjson.org/) - "newline-delimited JSON". This makes a lot of sense, and also lends itself to streaming APIs and pipelines, where individual JSON objects can be emitted as and when ready, as self-contained records, one at a time.

However these pieces are sometimes something other than JSON objects (JSON objects are recognisable by the enclosing braces, like this: `{ ... }`). They could be JSON arrays, which are recognisable by the enclosing square brackets: `[ ... ]`.

What's going to make you sit up and take a double gulp of coffee, perhaps, is that while we can agree or at least guess that an object `{ ... }` or array `[ ... ]` is valid JSON, there are other values that are valid too. A double-quoted string is valid JSON. A number is valid JSON. Even the following values are valid JSON: `true`, `false` and `null`. And by "valid JSON" I mean they could be alone in a file with a 'JSON' extension, or returned in an HTTP response, with `application/json` as the declared content type, and everything would be well with the world.

Getting back to my conundrum - what to call individual JSON "pieces"? Well, I gave myself a clue just then - the following are all valid JSON values:

* an object
* an array
* a string
* a number
* a boolean
* null

So it makes complete sense to me to use the word "value" to refer to a piece, a lump, a stanza, of JSON. A JSON **value**. That's the ticket!


[Discuss](https://github.com/qmacro/thinking-aloud/issues/34)

<hr>

## 2021-11-05 10:39:42 Starting my journey to Frankfurt for SAP TechEd
I'm travelling for work for the first time since lockdown started. I'm quite happy working quietly from home, but this is a welcome break from that, especially given the circumstances and context.

I'm travelling to Frankfurt, to work on some SAP TechEd preparations (we're doing another Developer Keynote this year) and I'm going by train. First, it's better for the planet, but second, I enjoy it a whole lot more. Most of all though, I'm going to get to see my son Joseph who's in Duesseldorf. It's been over a year since I saw him last and it will be brilliant to see him and hug him.

I've spent the entirety of my working life in the SAP ecosphere, since leaving University in 1987 and joining Esso in London, where I started to work on a project implementing SAP R/2 4.1. Throughout that working life I've travelled as a consultant, as a contractor, as an employee of customers and of partners, and I can say without hesitation that I've "done enough" travelling, at least for work.

There was one period of around 7 years where I flew at least twice -- sometimes four times -- every week, a practice that took me, as a contractor working for a large consultancy, to SAP customers in Europe and beyond. There was another time, when I was employed as a consultant for an SAP partner, that I more or less commuted between Manchester and Fort Worth, Texas. That was rather extreme, but it still happened.

Before joining SAP as an employee in 2018, most of my working weeks involved travel but by train, within the UK. I enjoyed that immensely, regardless of the pressures I might have been under at the time in relation to whatever project I was involved in. And that enjoyment is still with me, when it comes to train journeys.

So here I am, taking the train from Manchester Piccadilly to London Euston, the first main part of my journey. When I arrive in London I'll make my way over to St Pancras station where I'll take the Eurostar to Brussels. That's coming up, and I'm looking forward to that too.

Right, it's now time to walk down the train to pick up a cup of tea. Until next time.


[Discuss](https://github.com/qmacro/thinking-aloud/issues/33)

<hr>

## 2021-08-09 11:51:29 Demo journal creation in tmux popup
Here's an example of writing a new journal entry, invoked from the tmux binding "prefix M-j", in a popup window.

I'll record with asciinema (I need to fix that vim hack) and share it online.

![journal](https://user-images.githubusercontent.com/73068/128700002-5403c26c-5d2c-419e-a1c9-d7b061c9c31d.gif)


Asciinema link ☞ https://asciinema.org/a/429621

[Discuss](https://github.com/qmacro/thinking-aloud/issues/30)

<hr>

## 2021-08-08 21:28:34 Revisiting my tmux workflow and journalling
I've been learning lots about `tmux` over the last few days, both from long time friend Rob Muhlestein and latterly from Waylon Walker. So much so that I am at the state where I want to refresh my workflow which is based upon it. New and improved key bindings, better use of sessions, and looking at employing popups, a new feature introduced with `tmux` version 3.2.

I'm writing this journal entry within a popup; I've re-jigged the `j` function to become a more fully fledged `journal` script that I can then invoke with a key binding in `tmux`, which will then launch the script in a popup, like this:

```bash
tmux display-popup -E journal
```

The `journal` script is still very raw (I'm even writing it on a machine that doesn't have `shellcheck` installed yet, shame on me) but this is what it looks like so far:

```bash
#!/usr/bin/env bash

declare tmpfile repo title
tmpfile=$(mktemp /tmp/journal.XXXXXX)
repo="$HOME/Projects/gh/github.com/qmacro/thinking-aloud"

vim "$tmpfile"\
&& cd "$repo" \
&& echo -n "Title? " \
&& read title \
&& [ -n "$title" ] \
&& gh issue create \
 --label entry \
 --title "$(date '+%Y-%m-%d %H:%M:%S') $title" \
 --body-file "$tmpfile"
```

So for those who have seen how I've created journal entries thus far, the main difference here is that I'm opening up the editor _first_, then asking for a journal title, and only if I get both do I use `gh issue create` as I have been doing already (but this time, taking the issue body from the temporary file I've just created and edited).

I've just realised I should clean up that `$tmpfile` too. By the time this script hits my dotfiles repo, I'll have added that, and also tidied it up a bit more.

I like the idea of writing a journal entry in a modal popup; I'm pondering whether I should do it in the context of a (new) `tmux` session, so I can switch back into a half-written journal entry later, but I also like the idea that a journal entry should be short - certainly short enough for a single popup session. So that's what I'm doing right now.

Let's see how it goes.


[Discuss](https://github.com/qmacro/thinking-aloud/issues/28)

<hr>

## 2021-07-26 07:08:57 I listened to a @betatalksnl podcast on a walk this morning …
I listened to a @betatalksnl podcast on a walk this morning with guest @irina_scurtu. The title of the episode is [10. Teaching developers & the importance of sharing knowledge, REST API and GraphQL - with Irina Scurtu](https://podcasts.google.com/feed/aHR0cHM6Ly9mZWVkcy5idXp6c3Byb3V0LmNvbS8xNjIyMjcyLnJzcw/episode/QnV6enNwcm91dC04ODYyMDY4) and it was an enjoyable 50 minutes. Here are a few items that I picked out, items that resonated with me and made me think some more:

**The "Senior" prefix**

The addition of the adjective "Senior" to a title, such as "Senior Developer". What does that imply? What _should_ that imply? The case was made for "Senior" to denote, to require, a degree of mentorship. Teaching, training, mentoring more junior colleagues as part of the role description. This gets us away from using the "Senior" prefix for pure longevity in the position.

**Your knowledge tank**

Irina, a teacher and educator, showed a strong degree of awareness with regards to how full or empty her knowledge tank is. That is such an underrated ability - first to even realise that this is even a thing, and second, to recognise when one's tank is running close to empty.

Teaching and sharing is built on a foundation of knowledge, but that knowledge can become depleted, in a way, and certainly in our field it can become stale and lose relevance over time. And there's always new stuff to learn (and subsequently teach). Over the years I've come to recognise this empty tank; sometimes it takes me longer than it should for me to do anything about it, but I do, eventually.

**APIs**

This podcast episode covered teaching and sharing knowledge, but there was also a section on APIs, particularly REST, gRPC and GraphQL. Irina started to recount her experience in how folks failed to properly implement a RESTful approach in their API design, and I was expecting some references to the lack of HATEOAS and auto-navigable resources*, but I was somewhat dismayed to hear more fundamental crimes are being perpetrated:

- adding action verbs to URLs (that are supposed to represent resources, not actions)
- not using the HTTP methods appropriately
- not even returning appropriate status codes

This last point made me think of something I'd like to get put on my next nerdy custom tshirt:

```
200 NOT OK
```

Irina's thoughts on GraphQL made me smile, as they reflect my own, similar thoughts. GraphQL has arrived on the scene as a shiny new tool, and this is causing folks to want to use it ... for everything. Moreover, I'm seeing folks champion GraphQL because it lets them get just the data they want, rather than (as they maintain) "the kitchen sink" that they'd get with a REST or plain HTTP call.

That is rather narrow thinking, and based on, I suspect, their possibly limited experience of what a good RESTful or HTTP based API looks like. There are a lot of bad API designs out there - that's the fault of the designer, not the fault of REST or HTTP. So I see a lot of folks [throwing the baby out with the bathwater](https://en.wikipedia.org/wiki/Don%27t_throw_the_baby_out_with_the_bathwater) because of this.

What's more - and this was so wonderful to hear someone else (other than me) say this - _a lot of what GraphQL promises is already being delivered with OData_. I'll leave the explanation of that to another post, and instead leave you with a deliberately incendiary thought - GraphQL is OData, but in a far worse context, where processing and logic is pushed to the client, and the abuse of HTTP makes me categorise it in the same bucket as SOAP.

Anyway, give the episode a listen, the [Beta Talks](https://twitter.com/betatalksnl) folks ask great questions, and [Irina](https://twitter.com/irina_scurtu) was a great guest.

\*(I [recorded a podcast episode](https://anchor.fm/blog-cast/episodes/Ep-3-Kieran-Potts-Should-we-rebrand-REST-e12g3bi) for [Blog Cast](https://anchor.fm/blog-cast/), reading aloud Kieran Potts' [blog post of the same name](https://kieranpotts.com/rebranding-rest/) - I recommend this post or podcast for more information on this.)


[Discuss](https://github.com/qmacro/thinking-aloud/issues/26)

<hr>

## 2021-07-20 08:42:14 I've decided to double down on my tmux fu …
I've decided to double down on my `tmux` fu by re-reading the man page and picking out groups of related commands that I can stick to my screen and practise when I remember.

This week it's the set of commands related to panes. Here's what I have on my post-it note; they're all commands that are to be invoked following the prefix-key, and all relate to panes in the current window.

|Command|Description|
|-|-|
|`o`|select the next pane|
|`C-o`/`M-o`|rotate panes forwards / backwards|
|`;`|move to the previously active pane
|`!`|break the current pane out into a new window|
|`m`/`M`|mark / unmark a pane|
|`q`|briefly display the pane indices|
|`x`|kill the current pane|
|`z`|toggle the zoom state of the current pane|
|`{`/`}`|swap the current pane with the previous / next one|
|`M-1` to `M-5`|arrange panes in presets 1 through 5|
|`space`|cycle through to next preset layout|

I think having these commands written down, and then writing them down again in this journal entry, helps my mind assimilate them.

I had to look up what "marking" a pane was all about - it's to mark a pane as the subject of a subsequent action. For example, you can identify a pane by marking it, and then using `join-pane` in another window to move that pane from where it was to the window you're now in. Like moving a window from one workspace to another, in the context of a window manager.

Anyway, let's see how I get on. If I become more comfortable with these commands and remember to use them, I can move onto another group and repeat the learning process.


[Discuss](https://github.com/qmacro/thinking-aloud/issues/25)

<hr>

## 2021-04-09 13:17:08 I've been thinking about field naming conventions …
I've been thinking about field naming conventions today, after the pleasantly opinionated threads on Twitter.

I expressed that I like the old 5 character (usually uppercase) field names that appeared with R/2. Anyone who's been working in the SAP ecosphere will know what I'm taking about, fields like BUKRS, LIFNR, MANDT, WAERS, and so on.

For me, there's a certain beauty about them, a uniformity and a neatness that I haven't seen elsewhere.

Of course, this beauty can't be seen by some folks - they express a preference for longer names, but for me, those longer names are ugly, bring about a requirement for extra brain cycles to determine whether they should be camelCased, TitleCased, kebab-cased, snake_cased or some combination thereof.

And what about how long they're allowed to be, or how short? There's another decision right there. Moreover, it's often the case that naming conventions are loose, so you see all sorts of ugly mismatched cases for variables scattered throughout code.

Worst of all though are those variables that are so long (I'm thinking longer than 10 chars, that's double what my favourite style restricts itself to) makes code much harder to read. For me it's similar to reading a paragraph of prose when it's stretched out across the width of a widescreen monitor. Very hard on the eyes and the brain. There's a reason newspapers print articles in narrow columns.

There's more. I've not even got on to prefixes. Hungarian notation, anyone? What do you prefer there? And should the prefix be separated by some sort of symbol, or be part of the variable name directly?

Moreover, some folks have expressed an opinion (to which they're naturally entitled, we all are) that fields like BUKRS, MANDT and so on are restrictive because they're short forms of German words, and that's a barrier to entry.

When I started in 1987 in the SAP world, with R/2 4.1d, I was awash with these field names. What's more, I didn't speak a word of German. But it wasn't a problem - the brain is good at pattern matching in the first instance, and then when I had time, I looked up what they meant. BUKRS - Buchungskreis - Company Code (posting area). Right! And that served only to strengthen the slot in my brain that remembered that field name.

This argument reminds me of an exhortation I saw the other day in a handbook for writing documentation, or even blog posts. Write using simple words, in simple terms. To be honest, I find that ever so slightly insulting to the reader. 

English is my first language. I could say that German is my second language, and that's pushing it, a lot. While I was learning German in the early days (mostly by osmosis), I used to read technical articles and came across words that I hadn't seen before. Guess what? I looked them up, and my knowledge expanded. Not only relating directly to that word, but also to other future words that shared the same root.

Anyway, what am I saying here in this journal entry? I guess, at the end of the day, it's a lovely first world problem - debating what convention we prefer for our field names. It's pleasant to discuss, expressing our opinions is a healthy way to pass the time, and helps me keep sharp, as there are always great alternative opinions out there that challenge my thinking. And I like that. For me, sharing my thoughts, having them challenged, and learning - that's what it's all about. 

And for those who still can't figure out why I like the 5 char uppercase names, it's because they don't have all the problems that longer, mixed case names have, that I described above :-)


[Discuss](https://github.com/qmacro/thinking-aloud/issues/19)

<hr>

## 2021-04-07 16:27:58 One consequence of using repo issues for journal e…
One consequence of using repo issues for journal entries is that it's quite open.

I just noticed that someone has added an issue (#14) recently and I'm currently not quite sure how I feel about it. The content of the issue is innocuous enough, and I think on balance I currently like how open things are. I've made efforts in the mechanics to guard against this sort of thing in that issues that are not created by me are not going to trigger any sort of update or processing.

In the workflow (which is triggered when an issue is created or updated), there are two jobs, `generate` (generate the feed and recent content flow) and `tweet` (tweet that there's a new entry).

The `generate` job has an `if` condition like this:

```yaml
if: github.actor == github.repository_owner && contains(github.event.issue.labels.*.name, 'entry')
```

This checks that the `actor` (the person involved in the event that triggered the workflow) is the same person as the `repository_owner`, in other words, me. It also checks that the issue has the `entry` label (see #9 as to why this is).

The second job, `tweet`, also has an `if` condition, like this:

```yaml
if: github.event.action == 'opened'
```

This ensures that a tweet is only sent when an issue is created, not also if it's updated.

But the `tweet` job also has this:

```yaml
needs: generate
```

Which means that `tweet` only runs if `generate` completes successfully. Which in turn implies that `generate`'s checks also apply here, indirectly.

That's good enough for me for now.

I'm still not sure how I want to proceed with this external issue. I'll have to think about it. It's a chance for engagement, but perhaps I should just automatically delete them. Let's see.



[Discuss](https://github.com/qmacro/thinking-aloud/issues/18)

<hr>

## 2021-04-07 09:04:01 Does it make sense to create a workflow to clean u…
Does it make sense to create a workflow to clean up old workflow runs?

I'm using my dwr script right now to clean up some of the workflow runs in my repositories. It got me thinking - what about an automatic cleanup? Would it make sense to write a workflow ... to delete old workflow runs on a regular basis? There's a sort of pleasant balance in there as well, in that eventually, the runs from these cleanup workflows would be themselves cleaned up too.

In case you're interested in the `dwr` script as it stands right now, you can find it [here](https://github.com/qmacro/dotfiles/blob/master/scripts/dwr) in my dotfiles.

What do you think? Is it worth following this thought to an experimental cleanup workflow definition? What would that look like?


[Discuss](https://github.com/qmacro/thinking-aloud/issues/15)

<hr>

## 2021-03-25 16:39:40 I love the "Today I Learned" (TIL) idea, and even …
I love the "Today I Learned" (TIL) idea, and even have a TIL style blog called [autodidactics][autodidactics]. That said, I'm wondering if there's also value in reifying what might be the other side of the TIL coin, i.e. the "Want To Learn" (WTL) idea.

There are plenty of things that I wish I knew, from understanding specific concepts, to being able to achieve specific goals. At the very small end of the "achieve specific goals" stage there's Stack Overflow to give me answers, and that's fine. But sometimes I don't want the answer on a plate, I want to work for it, as - if time permits - the journey of effort is often fun and nearly always rewarding.

Here's an example:

* WTL the best way to mass-delete logs from GitHub Actions workflow runs

I've read somewhere that right now it's not possible from the Actions web interface, so I'm guessing the answer might be in the use of one or more API endpoints. I know that going from where I am now to understanding how to do it will improve my knowledge and be useful too.

The essence of this WTL is that it's tangible and I'll know when I've flipped it into a TIL. I know that some of the other stuff I wish I knew is less like that (grokking specific technical concepts) but not everything is black and white.

I think that now I have given a name to this type of thought ("how do I do / understand that?") that swirl around my brain, bumping into and otherwise disturbing what I'm actually trying to think about, it will help. I can capture the thought as a WTL and move on.

Now, where are those GitHub API docs?


[autodidactics]: https://qmacro.org/autodidactics/


[Discuss](https://github.com/qmacro/thinking-aloud/issues/13)

<hr>

## 2021-03-25 12:09:25 What else do I need for the basic setup of my jour…
What else do I need for the basic setup of my journalling here with Thinking Aloud?

On the one hand, I don't want to over-complicate things - part of the idea is to have a minimal setup. On the other hand, there are probably aspects that I'm still missing.

One in particular is the ability to "go meta". In other words, I want to be able to raise issues for the repo-based journalling mechanism itself, so I can record something that's amiss and then get around to addressing that.

But while I'm using issues in the simplest possible way, that's not going to work, as I'll pick up those "real" issues too in my journalling output. So it's time to turn to labels. I've alluded to the use of labels, which can be assigned to issues on GitHub, and while I was thinking more about journal entry categories, I really need a label to distinguish actual journal entries from non-journal entries.

I was originally thinking of having a label for non-journal entries, such as "issue", but that seems a little silly; better to have a positive "entry" label, as I can easily add that to my "new journal entry" mechanism - the `gh` GitHub CLI lets me assign labels on issue creation, [like this](https://cli.github.com/manual/gh_issue_create):

```shell
; gh issue create --label entry --title "..."
```

Then it's easy to show the list of actual journal entry issues, using the very capable [search & filter syntax](https://docs.github.com/en/github/searching-for-information-on-github/searching-issues-and-pull-requests). I think this is what I'll implement next, and then I can record this sort of "missing feature" entry as an actual issue rather than an entry.


[Discuss](https://github.com/qmacro/thinking-aloud/issues/9)

<hr>

## 2021-03-25 09:53:26 Some thoughts on learning, and how I pick the topi…
Some thoughts on learning, and how I pick the topics. 

Starting from a [tweet from Alex Ellis on learning & age](https://twitter.com/alexellisuk/status/1374657364813619201), in one of the ensuing threads, Jeroen Jacobs described the challenges of learning while working, and the challenge of that learning being non-billable and / or fleeting due to lack of opportunities to practise.

I've been a life long learner, not initially consciously by any means, but, helped by my [impostor syndrome][impostor-syndrome] I've always strived to flesh out my knowledge and remain above water. With computing in general, and enterprise computing in particular, I've found that it was usually natural to discover related topics that I had little idea about.

So those were the natural targets for new learning efforts. Not only because I could relate to them because they were to some degree relevant to the task at hand, but also because I had started to figure out that the more I knew about those related topics, the greater my overall understanding of things and the more useful I became.

To take an example - in the early days of APIs, when we started to move beyond the proprietary protocols and approaches (such as remote function calls and the RFC SDK), it was HTTP that sat firmly front and centre as the protocol around which the API world was beginning to revolve. While I could have got by with just a shallow understanding of HTTP, enough to create, make and debug API calls, I dove right in, to the extent that I call [RFC 2616](https://tools.ietf.org/html/rfc2616) a friend. Moreover, that journey led me to properly understand that HTTP is an *application* protocol, which in turn helped me understand why the whole Web Services Deathstar was destined from birth for self-destruction, because it was built on false foundations (the abuse of HTTP as a *transport* protocol). And of course, those investigations led me to Roy Fielding's thesis and the concepts of Representational State Transfer (REST), which -- to an extent -- underpins much of the API surface area today.

In my journey of discovery here, everything I did eventually became relevant to my work. Not by chance, but, I think, by relation.

So now where do I go with that? Well, while I'm not yet using GraphQL (except for an experiment with GitHub's API surface), I have at least [looked into it](https://blogs.sap.com/2018/09/03/monday-morning-thoughts-considering-graphql/), at least enough for now to understand how it differs from, say, RESTful approaches, and, as [Molesworth](https://en.wikipedia.org/wiki/Nigel_Molesworth) might say, in a "kno yore enemie" kind of way. And I do know that GraphQL most likely *will* feature in my future, so it's something I'll look into.

Anyway, what am I saying here? I think I'm saying that there's a semi-conscious filtering that goes on in my head when it comes to continuous learning; filtering that is designed to protect me from burnout, from learning stuff that I'll never get a chance to practise, but most of all to take advantage of a key aspect of learning - helping me to build the next layer of understanding.

An additional thought here relates to the need for practice. Jeroen [commented](https://twitter.com/JeroenJacobs79/status/1374977310491836420):

> ... the things I learn outside business hours, well it seems I forget most of it if I don't apply it during the work day

This reminded me of a great conversation between Scott Hanselman and Romain Goyet on a new pocket calculator, in the Hanselminutes podcast episode [It's time for a new kind of calculator with NumWorks' Romain Goyet](https://hanselminutes.com/779/its-time-for-a-new-kind-of-calculator-with-numworks-romain-goyet). Romain talked about energy consumption and eventual battery drain in devices, and drew out the distinction between dynamic RAM and static RAM. 

I think our minds are a lot like dynamic RAM, in that they need to be regularly refreshed (perhaps not as frequently as dynamic RAM!) with the same information, lest that information loses synaptic relevance and fades away. 

[impostor-syndrome]: https://blogs.sap.com/2018/10/01/monday-morning-thoughts-impostor-syndrome/



[Discuss](https://github.com/qmacro/thinking-aloud/issues/7)

<hr>

## 2021-03-24 15:44:46 So I've got the bare minimum set up for this journ…
So I've got the bare minimum set up for this journal, in the [thinking-aloud](https://github.com/qmacro/thinking-aloud) repository:

* issues to contain my journal entries, and possibly conversations about them (via the comments)
* a simple [Atom feed generator](https://github.com/qmacro/thinking-aloud/blob/main/feed) that will build an Atom 1.0 feed from a JSON list of issues that I can retrieve from the GitHub API - the feed's URL is https://raw.githubusercontent.com/qmacro/thinking-aloud/main/feed.xml
* labels that I can assign to the issues for eventual categorisation (I have [made provision for this in the feed generator already](https://github.com/qmacro/thinking-aloud/blob/08bf3f98064237c35b3bf7ae4fb16b5ecb9608b6/feed#L44))
* a GitHub Actions [workflow](https://github.com/qmacro/thinking-aloud/actions/workflows/generate-feed.yml) that is triggered when an issue is created or edited and causes the feed to be rebuilt

This was a pleasant few hours messing around on a day off. Well, I say pleasant, there was one unpleasant part which was trying (and failing) to parse and use the output from the [octokit/request-action](https://github.com/octokit/request-action).

The silver lining in this though is that I realised that I could just use the `gh` CLI, as long as I supply the `GITHUB_TOKEN` env var with the appropriate (and auto-generated) secret value, [like this](https://github.com/qmacro/thinking-aloud/blob/a8fda4c7705d26a30d47001885e6f20d4669a987/.github/workflows/generate-feed.yml#L21-L27):

```yaml
- name: Generate feed
  env:
    GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
  run: |
    gh api "/repos/${GITHUB_REPOSITORY}/issues?sort=created&direction=descending" \
      | ./feed \
      | tee feed.xml
```

If you're interested in following these journal entries, add the feed URL to your favourite feed reader: https://raw.githubusercontent.com/qmacro/thinking-aloud/main/feed.xml, and if you want to comment on any of the entries, you can do so in the comments to the corresponding issue.



[Discuss](https://github.com/qmacro/thinking-aloud/issues/2)

<hr>

## 2021-03-24 10:55:54 Can't help overthinking what I should have as my f…
Can't help overthinking what I should have as my first entry in this journal. Reminds me of the feeling of starting a new notebook, and agonising over what should be on the first page - it must be neat and permanently relevant. Of course, that's nonsense.

So I thought I'd just start typing. After all, the idea of this journal is to allow me to record thoughts in as friction-free a way as possible. Part of that is having a low barrier to writing, but also a low filter threshold.

Anyway, as usual, I've spent the last hour yak shaving, setting up a little system where I can just hit `j` and get directly to typing in my thoughts.

Hitting `j` starts a new `tmux` 'JOURNAL' session, or attaches to an existing one, and then uses `gh issue create` to initiate the process. The title is easy - I wanted to avoid having to think about what I should title each journal entry, so I'm simply using a timestamp. The `gh issue create` process then takes me into `vim` whereupon some `vim` configuration notices that it's a Markdown buffer that I'm editing, and throws me into `Goyo` which is a fantastic way to focus on writing.

And that's it. I'm not exactly sure whether things will work when I exit this buffer, I guess the only way to find out is to try it. Here goes.


[Discuss](https://github.com/qmacro/thinking-aloud/issues/1)
