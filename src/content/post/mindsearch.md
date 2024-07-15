---
publishDate: 2024-07-15T00:00:00Z
author: Zehui Chen
title: An open-source AI Search Engine Framework with Perplexity.ai Pro performance
# excerpt: For detailed description of MindSearch, please see our technical report (http://).
# image: https://images.unsplash.com/photo-1516996087931-5ae405802f9f?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2070&q=80
category: Tutorials
tags:
  - search engine
  - LLM Agents
metadata:
  canonical: https://astrowind.vercel.app/get-started-website-with-astro-tailwind-css
---

Technical Report: https://arxiv.org/abs

<div style="font-size: 20px">
Search engines provide extensive and the latest web information but often fail to tailor search results to align with complex human intentions.
Inspired by the remarkable progress of Large Language Models (LLMs), recent works enhance search engines with LLMs. However, these methods still obtain unsatisfying performance due to three critical problems: 

- LLMs fail to decompose complex requests into atomic queries, which adds difficulty in accurately and completely retrieving relevant information.
- search results are relatively massive compared to other tasks, requiring dedicatedly pre-selection.
- iterative web search content may quickly exceed the maximum capacity of LLM input length.

<img src="https://github.com/user-attachments/assets/15990c0d-cc9a-4302-b005-3f1f23441cc9">
<div style="font-size: 15px"><b>Figure 1</b>: The overall framework of MindSearch. It consists of two main ingredients: WebPlanner and WebSearcher. WebPlanner acts as a high-level planner, orchestrating the reasoning steps and multiple WebSearchers. WebSearcher conducts fine-grained web searches and summarizes valuable information back to the planner, formalizing a simple yet effective multi-agent framework.</div>

To address these issues, we introduce MindSearch, a simple yet effective LLM-based multi-agent framework for web search, consisting of a Web Planner and Web Searcher. WebPlanner models the complex problem-solving minds as a dynamic graph construction process: it decomposes the question into sub-queries as graph nodes and progressively extends the graph based on the search result from WebSearcher. Tasked with each sub-query, WebSearcher performs hierarchical information retrieval with search engines and collects valuable information for WebPlanner.

<img src="https://github.com/user-attachments/assets/c104c0a7-d93c-4459-96b9-9bf8c5cb5fb8">
<div style="font-size: 15px"><b>Figure 2</b>: Subjective evaluation results judged by human experts on open-set QA questions. MindSearch outperforms ChatGPT-Web and Perplexity.ai Pro by a large margin in terms of depth, breadth, and factuality.</div>

The multi-agent design of MindSearch dispatches a load of processing massive information to different agents, enabling the whole framework to process a much longer context i.e., of more than 300 web pages). To validate the effectiveness of our approach, we extensively evaluate MindSearch on both closed-set and open-set QA problems with GPT-4o and InternLM2.5-7B models. Experimental results demonstrate that our approach significantly improves the response quality in terms of depth and breadth. Besides, we also show that responses from MindSearch based on InternLM2.5-7B are preferable by humans to ChatGPT-Web (by GPT-4o) and Perplexity.ai applications, which implies that MindSearch delivers a competitive solution to the AI search engine. Code is available at <a href="https://github.com/InternLM/lagent">https://github.com/InternLM/lagent</a>.

</div>