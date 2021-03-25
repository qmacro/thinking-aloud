## 2021-03-25 09:53:26
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

## 2021-03-24 15:44:46
So I've got the bare minimum set up for this journal, in the [thinking-aloud][thinking-aloud] repository:

* issues to contain my journal entries, and possibly conversations about them (via the comments)
* a simple [Atom feed generator](https://github.com/qmacro/thinking-aloud/blob/main/feed) that will build an Atom 1.0 feed from a JSON list of issues that I can retrieve from the GitHub API - the feed's URL is <https://raw.githubusercontent.com/qmacro/thinking-aloud/main/feed.xml>
* labels that I can assign to the issues for eventual categorisation (I have [made provision for this in the feed generator already](https://github.com/qmacro/thinking-aloud/blob/08bf3f98064237c35b3bf7ae4fb16b5ecb9608b6/feed#L44)
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

If you're interested in following these journal entries, add the feed URL to your favourite feed reader: <https://raw.githubusercontent.com/qmacro/thinking-aloud/main/feed.xml>, and if you want to comment on any of the entries, you can do so in the comments to the corresponding issue.

[thinking-aloud]: https://github.com/qmacro/thinking-aloud

[Discuss](https://github.com/qmacro/thinking-aloud/issues/2)

<hr>

## 2021-03-24 10:55:54
Can't help overthinking what I should have as my first entry in this journal. Reminds me of the feeling of starting a new notebook, and agonising over what should be on the first page - it must be neat and permanently relevant. Of course, that's nonsense.

So I thought I'd just start typing. After all, the idea of this journal is to allow me to record thoughts in as friction-free a way as possible. Part of that is having a low barrier to writing, but also a low filter threshold.

Anyway, as usual, I've spent the last hour yak shaving, setting up a little system where I can just hit `j` and get directly to typing in my thoughts.

Hitting `j` starts a new `tmux` 'JOURNAL' session, or attaches to an existing one, and then uses `gh issue create` to initiate the process. The title is easy - I wanted to avoid having to think about what I should title each journal entry, so I'm simply using a timestamp. The `gh issue create` process then takes me into `vim` whereupon some `vim` configuration notices that it's a Markdown buffer that I'm editing, and throws me into `Goyo` which is a fantastic way to focus on writing.

And that's it. I'm not exactly sure whether things will work when I exit this buffer, I guess the only way to find out is to try it. Here goes.


[Discuss](https://github.com/qmacro/thinking-aloud/issues/1)
