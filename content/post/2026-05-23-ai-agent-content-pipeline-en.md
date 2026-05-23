---
title: "How My AI Agent Content Pipeline Writes Articles for Me"
date: 2026-05-23T10:00:00+08:00
draft: false
tags: ["AI Agent", "Content Creation", "Automation", "Multi-Agent", "Workflow"]
categories: ["Tech"]
---

## I Only Do Two Things Now

Record thoughts. Review drafts. And finally click publish.

Recording thoughts means speaking into my phone. Reviewing means reading finished articles in Feishu documents and leaving comments paragraph by paragraph. Clicking publish is the very last step. Everything else — topic selection, writing, multi-round review, distribution — is handled by a team of AI agents.

I call this system the "Content Collaboration Pipeline." It's not fully automatic. It's semi-automatic.

Before, I had plenty of ideas but not enough energy to turn them into consistently published articles. The sheer thought of sitting down and writing from scratch was exhausting. Now this pipeline has lowered the cost enough that I actually write.

Three articles have been published so far. This one is the fourth. It's also a product of this same pipeline.


## Ideas From Running, Captured Completely

I have a habit of thinking through complex problems while running. Ideas tend to hit during those moments.

When something comes to mind, I use an input method app on my phone. Push a button, start talking, push again to stop. Sometimes one short recording, sometimes a dozen in a row.

I call these "thought snippets." They're not formal notes or outlines. They're whatever comes out of my head — opinions, emotions, examples, and plenty of filler.

I send these voice transcriptions to my "Thought Recorder" agent. Its job is simple: record everything faithfully, in its original form. No editing, no summarization, no commentary. Just preservation.

Why did I need to train a dedicated agent that only records without giving advice? Because default LLMs can't resist offering suggestions. Once I complained "the code flowed really well today," and the recorder couldn't help adding, "You should note down why it went well so you can reproduce it." I was furious. I wanted recording, not advice. I added this rule to the prompt: record only, no evaluation, no suggestions. It hasn't happened since. These tiny details need separate tuning for every agent.

One thing I appreciate: after recording, it replies with the total word count, first 100 characters, last 100 characters, and the output directory. This way I can confirm it actually recorded correctly, not just pretended to. This verification mechanism matters — if I find content missing later while writing, it'd be too late.


## From Snippet to Article: I Don't Participate

After the Thought Recorder finishes, everything runs automatically.

The Writing Agent has a daily scheduled task. It pulls the latest thought snippets, analyzes which ones can become articles, decides how to split them, and drafts the core content for each piece. Then it writes directly and pushes the result to the local article review platform.

What I see is the finished draft. It never asks me "should I write this?" or "which topic should I pick?"

The Writing Agent also has a daily learning routine. It reviews past critique comments, identifies recurring issues, and improves its own writing. A self-iteration loop.

The quality of this initial draft varies, but I don't intervene at this stage. What determines quality is the review cycle that follows.


## Review: Three Rounds Before Feishu

I built an automated overnight review pipeline. Every night, one round of review runs automatically: the Writing Style Analyst reviews, the Writing Agent revises, then reviews again. After three rounds, the article gets uploaded to Feishu for me.

The core of the review process is a dual-model approach. The Writing Style Analyst reviews by itself, then has ChatGPT produce a separate version as reference. Different models catch different things. ChatGPT's perspective helps the Writing Agent break out of its usual patterns.

After three rounds, the article status changes to "ready for confirmation." Only then does it go to Feishu.


## Feishu Document: My Turn

After three rounds of review on the local platform, the article is uploaded to Feishu.

I leave comments in Feishu. I don't switch between phone and computer — I read for overall feel on my phone, make substantial edits on my computer. When something feels off, I comment directly in the document. After reviewing, the Writing Style Analyst fetches my comments from Feishu on its own.

From first draft to my final confirmation, one article takes about a week. Mostly because I don't have dedicated time to sit down and review — I can only do it in fragmented moments. Most of the waiting time is on me, not on the agents.


## Publishing: An Engineering Problem That Keeps Evolving

The publishing stage has a dedicated agent called the "Publishing Butler." It controls a browser and operates websites like a human: opening platforms, logging in, pasting content, uploading images, clicking publish.

At first, every platform required back-and-forth communication with the Publishing Butler. Let it try, then check the results. Now it runs on a schedule: every night it scans for unpublished articles and spends 7 consecutive hours pushing them to multiple platforms. A single article goes to over a dozen platforms, both Chinese and English.

The Publishing Butler has a special trait: it self-evolves. After each publish, it updates its own publishing skill, mainly the reference files. One reference per platform, documenting that platform's quirks and procedures. The more it publishes, the more familiar it becomes.

This is far less stable than it sounds. Browser automation doesn't face fixed APIs — it faces web UIs that change without notice. The first WeChat article hit a major problem: code blocks turned into plain text, indentation was completely lost, and images were compressed into illegibility. I spent half an hour manually fixing it. The Publishing Butler learned the lesson and now automatically checks code block formatting before every publish.

There are even stranger issues. Some platforms log you out every few days and require re-scanning QR codes. Some require a cover image with exact dimensions or they reject the submission. Some platforms can't render Markdown tables and need them converted to images. The Publishing Butler saves a lot of time, but it can't run fully unattended yet.

After publishing, the Butler records links for each article on each platform, opens the published pages, and checks the layout. I also take a look.


## Problems That Surfaced After a Few Articles

Facts are often made up in initial drafts. Events that never happened, exaggerated numbers, wrong process descriptions. Every single article has this problem. The only fix is multi-round review plus my own reading.

Review feedback needs to accumulate. If you just say "review this," agents return generic advice that could apply to anything. I later made the review criteria very specific: check for logical jumps, AI-speak, empty filler, and factual accuracy. The Writing Style Analyst maintains a style guide skill that gets more accurate with every round.

Version control needs a system. Early on, directory structure conventions were enough. Later I built a dedicated article review platform to manage state and versions. After several rounds of edits, things get messy fast without a proper system.

Publishing automation is the most fragile. Browser control, platform UIs, login states, preview checks — every link can break. The Publishing Butler saves time but can't fully replace human oversight yet.


## In the End

The core value of this entire pipeline is one thing: it lowered the cost.

It wasn't that I had no ideas before. It was that the cost from idea to article to publish was too high. Just the thought of sitting at a computer and writing from scratch was enough to kill the desire to write. Now the agents break down the process, orchestrate it, automate it, and continuously improve it. All I do is talk into my phone when I have an idea, spend some focused time in Feishu reviewing and commenting, edit until I'm satisfied, and the system publishes automatically.

The agents keep learning. The Writing Style Analyst's review skill keeps accumulating knowledge. The Publishing Butler's platform references are constantly updated. Everything keeps iterating. It's not a one-time build.

---

*Written in May 2026. This article itself is a product of this pipeline.*
