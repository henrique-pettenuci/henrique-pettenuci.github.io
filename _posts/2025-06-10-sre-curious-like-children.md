---
layout: post
title:  "SRE – Curious Like Children"
date:   2025-06-09 22:00:00 +0000
categories: sre
tags: process
---

# SRE – Curious Like Children

Recently, in my SRE team, we had a great conversation about the importance of truly getting to the **root cause** — digging deep to understand where a certain behavior comes from, so we can handle it more clearly with the responsible teams.

At that moment, I remembered the **“Five Whys”** technique, which offers a simple approach to analyze cause-and-effect relationships in a given scenario. One of the team members quickly pointed out:  
**“My six-year-old does that really well!”**

Children are naturally curious and always want to know the “whys” behind everything. That’s why they become question machines in their quest for knowledge. Of course, as SREs, we have the maturity to know **what questions to ask and when**, but our curiosity — the drive to discover the root cause — should be like a child’s desire to understand the world!

The “Five Whys” method is very simple and not at all bureaucratic, but it can lead to great insights during an analysis. Here’s a brief example:

**Problem:** Increased memory usage in a service  
- **Why?** – Because the number of requests increased.  
- **Why?** – Because another service started sending requests in a loop.  
- **Why?** – Because it keeps retrying until it gets a 200 or 503 status code; any other status triggers an automatic retry. In this case, it was receiving a 401.  
- **Why?** – Because the internal authentication key was updated but not correctly replicated to all services.  
- **Why?** – Because the keys are updated manually, and one of the services was missed during the process.

In this example, we moved from suspecting a possible implementation bug — maybe a **memory leak** — to identifying that the real issue was in a **key rotation procedure**. And we got there by cycling through questions, trying to understand the “why” behind each symptom — that is, tracing the cause of each effect we observed.

Another benefit of this process was identifying improvement opportunities, such as making the code more robust to prevent infinite loops, and automating the key rotation process to avoid manual errors in the future.

## What is the Five Whys technique?

The **Five Whys** is a problem-solving method that involves repeatedly asking the question **“Why?”** — typically five times — to drill down into the underlying cause of an issue. Each answer forms the basis of the next question, helping to peel back layers of symptoms and get to the root cause.

This technique is widely appreciated for being:
- **Simple and accessible**: no special tools or training needed;
- **Efficient**: helps teams reach insights quickly;
- **Collaborative**: encourages discussion and reflection during incidents or retrospectives.

However, it’s important to use it with some care:
- It relies on **clear, honest observations** — inaccurate assumptions can lead you in the wrong direction;
- It can sometimes oversimplify **complex or systemic problems**;
- And if taken too far, it may create a loop of over-questioning without actionable outcomes.

### Do I always need to ask five times?

That’s not a rule — it’s just a guideline. You should ask as many “whys” as needed to uncover the root cause, but be careful not to fall into an **infinite loop chasing the “perfect root cause.”**

There are different techniques for investigating problems. The **Five Whys** is just one of them — lean, straightforward, and not reliant on complex tools. But regardless of the technique you use, the most important question is:  
**Is your SRE team curious enough to find the root cause?**