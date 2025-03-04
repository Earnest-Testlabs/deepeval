# DeepEval - Unit Testing for LLMs


<p align="center">
    <a>
        <img alt="Pepy Total Downlods" src="https://img.shields.io/pepy/dt/deepeval">
    </a>
    <a href="https://github.com/vector-ai/vectorhub">
        <img alt="Release" src="https://img.shields.io/github/v/tag/confident-ai/deepeval?label=release">
    </a>
    <a href="https://discord.gg/a3K9c8GRGt">
        <img alt="discord-invite" src="https://dcbadge.vercel.app/api/server/a3K9c8GRGt?style=flat">
    </a>
</p>


**DeepEval** is a simple, yet powerful open source package that allows any developer to unit test LLM outputs in python. DeepEval also integrate seamlessly with CI/CD pipelines, and provide out-of-the-box metrics for you to evaluate your LLM applications on things you care about - such as output factuality, relevancy, bias, and toxicity. 

Whether you're using RAG or fine-tuning, we make it easy to develop, deploy, and productionize LLM applications with confidence.

<br />

## Getting Started 🚀
Let's pretend your LLM application is a customer support chatbot, here's how Deepeval can help test what you've built.

### Installation
```
pip install -U deepeval
```
### Writing your first test case
Create a test file:
``` bash
touch test_chatbot.py
```

Open `test_chatbot.py` and write your first test case using Deepeval:
``` python
import pytest
from deepeval.metrics.factual_consistency import FactualConsistencyMetric
from deepeval.test_case import LLMTestCase
from deepeval.run_test import assert_test

def test_case():
    query = "What if these shoes don't fit?"
    context = "All customers are eligible for a 30 day full refund at no extra costs."

    # Replace this with the actual output from your LLM application
    actual_output = "We offer a 30-day full refund at no extra costs."
    factual_consistency_metric = FactualConsistencyMetric(minimum_score=0.7)
    test_case = LLMTestCase(query=query, output=actual_output, context=context)
    assert_test(test_case, [factual_consistency_metric])
```
Run `test_chatbot.py` in the CLI:
```
deepeval test run test_chatbot.py
```
**Your test should have passed** ✅ Let's breakdown what happened. 

The variable `query` mimics a user input, and `actual_output` is a placeholder for what your chatbot's supposed to output based on this query. The variable `context` contains the relevant information from your knowledge base, and `FactualConsistencyMetric(minimum_score=0.7)` is an out-of-the-box metric provided by DeepEval for you to evaluate how factually correct your chatbot's output is based on the provided context. This metric score ranges from 0 - 1, which the `minimum_score=0.7` threshold ultimately determines if your test have passed or not.

[Read our documentation](https://docs.confident-ai.com/docs/) for more information on how to use additional and create your own custom metric, and tutorials on how to integrate with other tools like LangChain and lLamaIndex.

<br />

## Evaluate your test results on the web
We offer a [web platform](https://app.confident-ai.com) for you to log and view all test results from `deepeval test run`. Our platform allows you to quickly draw insights on how your metrics are improving with each test run, and to determine the optimal parameters (such as prompt templates, models, retrieval pipeline) for your specific LLM application.

To begin, login from the CLI:
``` bash
deepeval login
```
Follow the instructions to login, create your account, and paste in your API key in the CLI. 

Now run your test file again:
``` bash
deepeval test run test_chatbot.py
```

You should see a link being displayed in the CLI once the test has finished running. Paste it in your browser to view results!

<br />

## Contributing

Please read [CONTRIBUTING.md](https://github.com/confident-ai/deepeval/blob/main/CONTRIBUTING.md) for details on our code of conduct, and the process for submitting pull requests to us.

<br />

## Authors
Built by co-founders of Confident AI. 
- for anything related to the package, contact jacky@confident-ai.com or [![Twitter](https://img.shields.io/twitter/url/https/twitter.com/cloudposse.svg?style=social&label=Stay%20Updated%20On%20X)](https://twitter.com/colabdog)
- for anything related to the web platform, contact jeffreyip@confident-ai.com

## License
DeepEval is licensed under Apache 2.0 - see the [LICENSE.md](https://github.com/confident-ai/deepeval/blob/main/LICENSE.md) file for details.

