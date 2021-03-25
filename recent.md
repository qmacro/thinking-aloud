[**2021-03-24 15:44:46**](https://github.com/qmacro/thinking-aloud/issues/2)

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

<br>

[**2021-03-24 10:55:54**](https://github.com/qmacro/thinking-aloud/issues/1)

Can't help overthinking what I should have as my first entry in this journal. Reminds me of the feeling of starting a new notebook, and agonising over what should be on the first page - it must be neat and permanently relevant. Of course, that's nonsense.

So I thought I'd just start typing. After all, the idea of this journal is to allow me to record thoughts in as friction-free a way as possible. Part of that is having a low barrier to writing, but also a low filter threshold.

Anyway, as usual, I've spent the last hour yak shaving, setting up a little system where I can just hit `j` and get directly to typing in my thoughts.

Hitting `j` starts a new `tmux` 'JOURNAL' session, or attaches to an existing one, and then uses `gh issue create` to initiate the process. The title is easy - I wanted to avoid having to think about what I should title each journal entry, so I'm simply using a timestamp. The `gh issue create` process then takes me into `vim` whereupon some `vim` configuration notices that it's a Markdown buffer that I'm editing, and throws me into `Goyo` which is a fantastic way to focus on writing.

And that's it. I'm not exactly sure whether things will work when I exit this buffer, I guess the only way to find out is to try it. Here goes.

