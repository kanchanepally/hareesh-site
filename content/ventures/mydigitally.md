---
title: "MyDigitAlly"
date: 2024-11-06
weight: 1
description: "AI-powered platform helping parents navigate their kids' digital world"
---

## Empowering Parents in the Digital Age

**Status:** Active - Live platform with growing community

[Visit MyDigitAlly →](https://www.mydigitally.co.uk) | [Subscribe to Newsletter →](https://www.mydigitally.co.uk/#newsletter)

---

## The Problem

Parents today face an impossible challenge - guiding their children through a digital landscape they don't fully understand themselves. The pace of technological change means even tech-savvy parents struggle to keep up with new platforms, risks, and opportunities.

Most resources are either:
- Too technical for average parents
- Too judgmental about parenting choices
- Too time-consuming for busy schedules

## The Solution

MyDigitAlly converts research-based insights into accessible, 5-minute e-learning tools. We meet parents where they are - not where experts think they should be.

**What We Offer:**
- **Weekly Newsletter:** Actionable insights delivered automatically
- **Micro-Learning Modules:** 5-minute lessons based on 5-Block Framework
- **Non-Judgmental Guidance:** Research-backed, empathetic approach
- **AI Assistant** (in development): Personalized advice using RAG + MCP

## Technical Architecture

**Stack:**
- **Frontend:** React + Vite (fast iteration, modern DX)
- **Backend:** Node.js + PostgreSQL (structured curriculum data)
- **AI Layer:** RAG architecture with Claude API
- **Framework:** Proprietary 5-Block Micro-learning system based on EdTech research from University of Oxford

**The RAG Implementation:**

Curriculum content → embeddings in vector DB → user query retrieves relevant sections → Claude API generates safe, grounded response → validated against curriculum guidelines.

**Key Design Decisions:**
- Grounding AI responses in evidence-based curriculum (not generic advice)
- Balancing response quality vs. API costs at scale
- Keeping auth lightweight to maintain development velocity
- Deployed on Vercel for instant preview and zero-config deployment

## Current Metrics

- **Newsletter open rate:** 42% (vs. 20-30% industry standard)
- **Engagement:** 3-4 unsolicited replies per email
- **Growth:** Parents forwarding to other parents
- **Testing:** AI coach beta with initial parent cohort

## The Insight

Early signal from user conversations: Parents don't want to become digital literacy experts. They want **just-enough knowledge to have informed conversations with their kids**.

They're asking:
- "My 8-year-old wants Discord - what do I actually need to know?"
- "How do I talk about screen time without it becoming a fight?"
- "What's actually risky vs. what's media panic?"

**Hypothesis:** The AI coach (contextual, just-in-time answers) might be more valuable than the structured curriculum itself. Testing this now.

## The Vision

Every parent should feel confident co-piloting with their kids through the digital world. Not as experts, but as informed, engaged guides who understand the landscape well enough to have meaningful conversations.

## What I'm Learning

Building MyDigitAlly is teaching me:
- **Product-market fit discovery** with limited time and resources
- **AI safety** in educational contexts
- **Technical trade-offs** (when to over-engineer vs. ship fast)
- **The founder psychology** of building alongside full-time work

I write about these learnings in my [Notes](/notes) section.

---

## Recognition

Launched August 2024. Featured in my LinkedIn post that received strong engagement from the edtech and product management community.

---

## Get Involved

**Are you a parent?**  
[Subscribe to the newsletter →](https://www.mydigitally.co.uk/#newsletter)

**Building in edtech or AI?**  
Let's connect: [kanchanepally@gmail.com](mailto:kanchanepally@gmail.com)

**Want to beta test the AI coach?**  
Reach out - we're looking for engaged parents to help shape the product.

---

[← Back to all ventures](/ventures) | [Read my notes on building MyDigitAlly →](/notes)