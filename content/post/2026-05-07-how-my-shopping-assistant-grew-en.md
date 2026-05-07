---
title: "How My Shopping Assistant Grew, One Step at a Time"
date: 2026-05-07
draft: false
tags: ["AI", "Agent", "OpenClaw", "shopping assistant", "browser automation", "Xiaohongshu", "price comparison"]
categories: ["Tech Experience"]
---

After I started using OpenClaw, I kept tinkering with different ways to use it—except when work got busy or I was too tired to bother. Recently I've been thinking about sharing some of my hands-on experiences from time to time.

This time it's about a shopping assistant that started as a simple shopping list and gradually grew into something that could search Xiaohongshu, compare prices, and add items to my cart.

---

## The List of Things to Buy Kept Growing

Lately our household needed quite a few things—picture books and a microscope and roller skates for the kid, plus all sorts of daily necessities. Every time I shopped for something, I'd bounce between Taobao, JD.com, and Xiaohongshu—comparing prices, checking reviews, picking styles. Pretty annoying.

I had previously set up an Agent called "Shopping List Manager" to help me keep track of things I wanted to buy. Whenever something came to mind, I'd just tell it, and it would categorize and organize everything—basically a shopping memo.

But a memo is just a starting point. Once you have a basic feature in place, you can't help but wonder—can it also check prices for me? Can it go look at Xiaohongshu reviews? Can it just add stuff to my cart directly?

---

## First Evolution: From Memo to Auto Price Comparison

After using the shopping memo for a while, I started feeling that just recording things wasn't enough. I knew what I wanted to buy, but I still had to look up prices myself.

Then one day, my Skill Researcher—an Agent that automatically searches for new Skills every day—found a price comparison Skill (something like "maishou"). Once installed, it could search across Taobao, JD.com, Pinduoduo, and other platforms, telling me roughly what options were available and what the price range looked like.

With price comparison in place, the shopping assistant went from "only records, doesn't search" to "records and searches."

---

## Second Evolution: Bringing Xiaohongshu On Board

Price comparison was great, but when it came to reviews and recommendations, I mainly relied on Xiaohongshu. Just knowing the price range wasn't enough—I also wanted to know "which brand is good" and "what pitfalls others had stepped into."

There was no ready-made Skill for Xiaohongshu, but I had already been using OpenClaw's browser Skill—through Brave Browser's CDP protocol (basically opening the browser's debugging port), the Agent could open a browser and operate web pages like a human would. So I had the Agent use this capability to search Xiaohongshu and see what users were saying.

Later I used the Skill Creator to gradually polish a Xiaohongshu search Skill, specifically handling search and content extraction. It wasn't written in one go—I debugged it repeatedly, hit snags, and revised it through several iterations before it stabilized.

Early on, it actually fooled me once. It said "I looked it up for you" and gave a convincing-sounding recommendation. It looked legit at first glance. But when I asked it to actually open Xiaohongshu and search the posts, I realized the whole thing was basically made up.

I also found issues with search sorting later. Xiaohongshu sorts by likes by default, but high-like posts aren't always useful—a lot of them are fluff or ads. The genuinely valuable information is often in the comments. So I changed it to sort by comment count—posts with more comments are more likely to have real user experiences shared.

After that, to prevent it from just making things up, I added a rule: when giving recommendations, it must include evidence—which post said it, what the post link is. Actually, from the very first time I asked it to search Xiaohongshu, I required it to include data sources. It's just that over time this rule got stricter and stricter, from simple screenshots to complete post links and citations.

---

## Third Evolution: From Searching to Buying—Adding to Cart, Delegated

Once when buying picture books, I really couldn't be bothered to open Taobao, search one by one, and add them to the cart one by one. I thought—could I just let the Agent handle this step?

At first the Agent actually refused me, saying it wasn't safe and it didn't recommend operating shopping websites directly. I said just add to cart—I'll handle payment myself. So I used the browser Skill again to build a Taobao cart Skill. The Agent would open Taobao's web version, search for products, compare prices and specs in the results, and add the suitable ones to the cart. Same principle as Xiaohongshu—both powered by the browser Skill, just targeting a different website. After a few tries, it actually worked.

From memo to price comparison, to Xiaohongshu search, to adding items to Taobao cart—capabilities got stitched together one by one. First it could record, then it could search, then it could verify, and finally it could take action.

---

## In Practice: Buying Picture Books

Buying picture books was the most complete run-through of the whole process.

I didn't jump straight to having it search Taobao. Instead, I did a round of deep research with Gemini first—telling it the kid's age and interests, asking it to do a thorough investigation and recommend suitable picture books. After getting those recommendations, I passed the results to the shopping assistant and asked it to check editions, prices, and parent reviews.

The most critical part was the Xiaohongshu verification: sorted by comments, checking which recommendations were genuine and which looked like ads, and whether parents were complaining in the comment sections. In the end, it organized the recommendations into batches—what to buy first, what to buy second—and I just had it add everything to the Taobao cart. I opened my phone, glanced at the cart, thought the prices were fine, and paid.

Individually, none of these steps are magical. But connected end to end, I didn't have to bounce between several apps anymore.

---

## A Few Other Shopping Trips

For the microscope, the Agent helped me search and recommend options, but I ended up buying a different model—its recommendations gave me a reference direction, but the final decision was still based on my own judgment.

The roller skates were bought earlier than the picture books, back when adding to cart wasn't possible yet. The Agent helped search Xiaohongshu for brand recommendations, and then I went to Taobao myself to buy.

These three purchases happened to land in three different stages: roller skates could only search Xiaohongshu, the microscope could search and recommend, and the picture books went through the full pipeline from research to checkout. Each evolution came about naturally through actual use.

---

It started as just a shopping list. Then it learned to search, to filter, to verify, to add to cart. Originally I just wanted to be a little lazy—and the lazier I got, the more it turned out it could actually save me from switching between apps. When I have time, I'll write a separate piece on how to build one from scratch.
