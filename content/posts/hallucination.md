+++
title = 'Cause of Hallucination'
date = 2024-08-28T20:02:20+08:00
draft = true
+++

Some glitch:
The Great Firewall is not just blocking the user from checking outside world, but also blocking the outside to check
what China really is.
And that's why a lot of foreigners deceased their passion on exploring the mainland. The majority voice has been
replaced by HK and TW.
Now in AI era, LLM can't learn from the majority voice for Chinese and which could broadcasting non-factual knowledge
and opinions. which could be toxical in some case.
therefore, building the dataset for China ecosystem is really important for especially open-source model training.


### Identify the cause of hallucination:

1. Feed the contexts irrelevant to the query, check if the hallucination is related to the context.
2. Prompt is little too complex. and model is not powerful enough.
3. Smaller temperature, 0.1 for mixtral 8x7b, 0.5 for GPT-4o.

Evidence:

- Not always hallucination, ~~could related with temperature. Not so consistent for same prompt. Temperature is not
  useful to constraint.~~
- Answer is too long, it's not suppose/possible to cover all the details in the context. Could be optimized.
- Prompt is little too complex. and model is not powerful enough.
- How to add a camera API to Meraki resources is a bad query. Even GPT-4o failed with inaccurate answer. Could be
  improved by rewritten.

Some recommendation from [Anthropic](https://docs.anthropic.com/en/docs/test-and-evaluate/strengthen-guardrails/reduce-hallucinations#advanced-techniques):
- Chain-of-thought verification: Ask Claude to explain its reasoning step-by-step before giving a final answer. This can reveal faulty logic or assumptions.
- Best-of-N verficiation: Run Claude through the same prompt multiple times and compare the outputs. Inconsistencies across outputs could indicate hallucinations. 
  - This is costly, and could be improved by a more powerful model, a hyperpameter like top-k or top-p.
- Iterative refinement: Use Claude’s outputs as inputs for follow-up prompts, asking it to verify or expand on previous statements. This can catch and correct inconsistencies.
  - Is what agentic QA does
- External knowledge restriction: Explicitly instruct Claude to only use information from provided documents and not its general knowledge.



## TODO:
- [ ] A standard process for quickly rolling out new prompt evaluations
- [ ] Building a positive and negative dataset for evaluation, using GPT-4o to evaluate.
- [ ] Add a hallucination check step after QA during inference? It's costly, and what's the next step?
  - Filtering the retrieval to eliminate hallucination instead of repeating.
  - A different prompt with more rigorous checks.


