---
title: "How I Use AI in Work and Life Lately"
featureimage: "covers/using-ai-in-community-ops.svg"
date: 2026-05-11T16:17:02+08:00
categories:
- AI
tags:
- ai
- gemini
- codex
- deepseek
- openclaw
- opencode
- community
description: "From building official websites and data dashboards to creating stickers and AI agents — how I use AI these days"
weight: # Set to 1 to pin this post; leave empty to sort by date.
draft: false
comments: true
showToc: true
TocOpen: true
hidemeta: false
disableShare: false
showbreadcrumbs: true
cover:
    image: ""
    caption: ""
    alt: ""
    relative: false
---

In my [previous article](https://faweizhao26.github.io/posts/ai/codex-ai-website/), I shared the story of how I used AI to build a navigation website. Some of you might have already read it.

AI is no longer news — it has quietly "infiltrated" our daily lives, work, and learning, and has become an essential part of many people's routines. As a community operator, AI has become my right-hand helper. In this article, I want to share what I have been doing with AI lately, hoping to spark some ideas for you.

## Part 1: How I Use AI at Work

Those of you who know me or have been following me for a while probably know that my day job is community operations. I have also written a few articles about operational experience, methods, and tools before.

So, how have I been using AI at work recently?

Things like using AI to help with planning proposals or generating images are probably already common practice for most people, so I will skip those. Let me focus on a few use cases that some of you might not have tried yet.

### 1. Front-End Website Design

The open-source project I currently manage is a database project called **IvorySQL**. Since I took over, I always felt the official website was a bit too basic. I have thought about redesigning it countless times, but since I know neither design nor front-end development, I felt completely stuck.

Last December, I got a free one-year Gemini membership and started using it heavily. I had heard that Gemini is quite good at front-end design, so I thought: why not let it help me design some pages for the official website?

With Gemini's help, I built several new pages: the [Events page](https://www.ivorysql.org/zh-cn/events), the [Partners page](https://www.ivorysql.org/zh-cn/partners-page), and the [News page](https://www.ivorysql.org/zh-cn/news). Although I used AI tools, the time and effort I invested were far from trivial. Of course, there was a prerequisite: I had asked our company's designer to create a rough front-end UI mockup first, which I then fed into Gemini as a foundation.

Later, I decided to revamp the official [Homepage](https://www.ivorysql.org/zh-cn/). By then I had started using Codex, which made things even simpler — I could just give verbal commands without editing files manually or even submitting PRs myself, drastically reducing the human effort. That said, the current homepage was further refined by a colleague using Claude Code on top of my PR.

Since things got busy, I haven't continued polishing the UI for a few pages, but they are already much better than the original versions.

### 2. Building Small Utility Tools for Myself

I often recommend small tools to others — PDF editors, image processors, format converters, etc. At work, you constantly run into little needs: format conversion, image cropping, photo layouts... My old approach was to search my bookmarks first, then search online, but most online tools eventually require payment.

Besides text conversations and image generation, Gemini can actually write small applications too. So I used it to build some online utilities, like converting SVG images to PNG or JPG, converting PowerPoint slides to images, image cropping, and so on. These apps all live within Gemini, accessible only to me — convenient and cost-free.

### 3. Building a Data Dashboard

Almost every role has data metrics, and community operations is no exception: GitHub stars for open-source projects, official site PV/UV, WeChat Official Account followers and article views, contributor count — and the list goes on.

We need to monitor changes in these metrics regularly, which means doing repeated statistics. To be honest, data tracking has always been my biggest headache. There are too many metrics scattered everywhere, and you have to constantly compile, aggregate, and analyze changes — it's a real hassle.

A while ago, I wondered: could I build a data dashboard that consolidates all the metrics I care about into one place, giving me a clear overview while saving tons of time and energy? So I started building this dashboard using **Codex** first, then **opencode**. I used two AI agents because the relay provider token I had purchased expired, and the minimax and DeepSeek tokens I switched to didn't work with Codex's Mac desktop app — so I have temporarily stopped using Codex.

In the end, I built this work-in-progress: https://ivorysql-dashboard.vercel.app/

I call it a work-in-progress because some data tracking logic isn't quite right yet, some data pipelines haven't been connected, and some data still requires manual entry.

Here is a quick rundown of the implementation: create a new repository on GitHub, write the website code, deploy it on Vercel, and connect Supabase as the backend database. No paid features were used at all.

So if you want to build something similar, just fork my repo: https://github.com/faweizhao26/ivorysql-dashboard

This is a Next.js-based open-source project operations data dashboard that supports both automatic GitHub data fetching and manual data entry.

**Features:**

- **GitHub Data**: Stars, Forks, Watchers, Contributors, Open Issues/PRs, Releases, etc.
- **Social Media**: WeChat Official Account, Twitter, Bilibili, YouTube follower and engagement data
- **Technical Content Platforms**: CSDN, Juejin, Modb, OSChina, SegmentFault, 51CTO, ITPUB, Toutiao, IFCLUB
- **Official Site Data**: PV/UV, traffic sources, popular pages, search keywords
- **Trend Charts**: Supports daily/weekly/monthly/quarterly/yearly view switching
- **Community Feed**: Aggregates GitHub Issues/PRs/Releases, blog updates, and event updates
- **Automatic Updates**: Daily automated data fetching via GitHub Actions
- **Access Control**: Vercel Password Protection

Every project has different operational priorities, and this dashboard only reflects my current needs. I will continue updating it. If you have good ideas, feel free to reach out and discuss.

### 4. Building a Conference (Event) Website

In the year and a half since joining Highgo, I have organized two major conferences: HOW 2025 last year and HOW 2026 this year.

After experiencing the organizational pain points of both conferences, an idea popped into my head: why not use AI vibe coding to build the HOW 2027 website from scratch? This website won't just display key information — it also needs to support talk submissions, agenda scheduling, registration, and on-site check-in. This way, I no longer need to pay for agenda management systems or event management tools — I'll have a fully-featured, all-in-one official website.

The implementation approach is the same as the dashboard website above. This one is also still a work-in-progress, continuously being refined.

The open-source repo is here — feel free to use it: https://github.com/faweizhao26/HOW-WEBSITE

Considering data security and privacy, if this goes live in the future, the backend database can't stay on Supabase (it's currently on Supabase Cloud). Fortunately, Highgo is building a China-local Supabase alternative. Once it's ready, I'll make the switch.

## Part 2: My Personal AI Adventures

The above is mainly about my work-level practices. On the personal side, I have a few experiments going on too.

### 1. Making Stickers

I wrote an earlier article about using AI to make WeChat stickers: [AI Tutorial: Make Custom WeChat Stickers for Your Cat in 5 Minutes](https://mp.weixin.qq.com/s/eeWQZJ-Wk78iFOg7f_8LPQ). I won't repeat it here — check it out if you're interested.

### 2. Building a Navigation Site

I won't repeat this either. If you want to learn more, check out this article: [How a Non-Technical Person Built a Website with Codex + AI in Two Hours](https://faweizhao26.github.io/posts/ai/codex-ai-website/).

### 3. "Raising a Lobster"

A while ago, there was a wave of "raising lobsters" in China. Of course, this isn't about actual lobsters — it's about a very popular AI agent project called **openclaw**. The project logo is a lobster, so everyone just calls it "the lobster." This trend even sparked a domestic "Hundred Lobsters War," with many companies creating their own lobster agents.

As someone who loves chasing trends, I immediately deployed openclaw and, following online tutorials, connected it to Feishu (Lark). But at first, I couldn't find a truly suitable use case.

Following the principle of "if there is no need, create one," I eventually found some tasks for it:

**(1) Running a WeChat Official Account**

Last year, I registered a new WeChat Official Account. I wasn't sure what to write about at first, so it was practically dormant. Then it hit me: since AI is such a hot topic, why not let AI write about AI? To avoid being flagged or banned, I won't disclose the specific direction or the account name — just offering the idea as inspiration.

After many rounds of iteration and optimization, the current workflow is: every day, openclaw runs a scheduled task to generate articles using DeepSeek, then pushes the content to me via Feishu and local Markdown files. I handle the final formatting and publishing.

**(2) Pushing AI News**

I have always closely followed AI trends and news, and I follow a ton of AI-related WeChat Official Accounts. Later, I thought: why not let openclaw curate and push AI news to me? Coincidentally, a well-known AI influencer recently opened up their AI hot-topic monitoring site and turned it into a skill. I quickly had openclaw install this skill, which improved the quality of news delivery.

### 4. Trying to Write Fiction

Honestly, I wasn't really planning to mention this. My experience with AI-generated fiction so far has been underwhelming — maybe my tools just aren't good enough yet. No results worth mentioning so far. Just putting it out there as an idea.

## Part 3: A Quick Summary

The above is what I have been tinkering with using AI recently.

**The AI tools I currently use most and what I use them for:**

- **Gemini**: I don't use it as much anymore. I use Lovart (powered by Gemini) to generate cover images for my WeChat Official Account articles.
- **ChatGPT**: Now mainly used for image generation — the results are seriously impressive.
- **DeepSeek**: Used for content generation, and for taking advantage of their free token quota.
- **openclaw**: Already covered above, won't repeat.
- **opencode**: For building all kinds of websites I need.

**The tokens I have tried:**

- **Relay Provider**: It worked really well, but it was unstable and relatively expensive.
- **minimax**: Not great, honestly — possibly because the plan I bought was too cheap.
- **DeepSeek-v4**: The million-token context is seriously impressive, and the usage-based pricing is not expensive.

As I said in my last article, AI has lowered the barrier for many things, allowing us to accomplish things we could only dream of before. Going forward, I'll continue using AI to build what I need, and I'm always open to exchanging ideas with you all.
