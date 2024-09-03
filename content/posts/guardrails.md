+++
title = 'Guardrails/LLM Security'
draft = true
+++

Bedrock Guardrail is cheap, since we will only consider the current input query for the most cases. 10k * 10 tokens/ query = $1.

Guardrail system is something we should add before the inference.

Guardrail -> Agentic System -> Guardrail


There're several ways to strengthen the guardrails from Anthropic recommendation:
- Keep Claude in Character: The Role sets a strong foundation for consistent responses.
- Mitigate jailbreaks and prompt injections: This is about using a pre-process model to check the input and output for malicious intent. This model could be a specific agent, a fine-tuned one or a rule-based system. It's neccessary to involve this if short latency.
- Use Output Constraints


[Examples of Bedrock Langchain](https://medium.com/@vinayakdeshpande111/aws-guardrails-with-langchain-6554411d4d74):
```python
Guardrail ID = abc
Guardrail Name = cba  

from langchain_aws import ChatBedrock

model_id, Engine = ('mistral.mixtral-8x7b-instruct-v0:1', ChatBedrock) 
llm = ChatBedrock(
    model_id=model_id,
    guardrails={"guardrailIdentifier": Guardrail, "guardrailVersion": '1', "trace": True},
)
```



## Reference
- [Strengthen Guardrails](https://docs.anthropic.com/en/docs/test-and-evaluate/strengthen-guardrails/keep-claude-in-character#example-enterprise-chatbot-for-role-prompting)

## TODO:
- [ ] Optimize the agent routing prompt with role 
