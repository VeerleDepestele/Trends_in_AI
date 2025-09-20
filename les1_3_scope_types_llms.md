# Scope

## Define the use case - examples

LLMs can be used for:

- question & answering (Q\&A) tasks:
  - Chatbots
- various text generation tasks:
  - Writing essays based on prompts.
  - Summarizing conversations by providing dialogue as input.
    ![chatgpt_summary.jpg](img/chatgpt_summary.jpg)
- translation tasks:
  - traditional translations between languages (e.g., French–German, English–Spanish)
  - translation from natural language to machine code (e.g., asking to calculate the average of columns in a dataframe).
    ![python\_code\_gemiddelde\_kolom\_dataframe](img/python_code_gemiddelde_kolom_dataframe.png)
- a specific task, such as retrieving information.
  For example, you can ask the model to identify all people and places mentioned in a news article. This is known as named entity recognition, a word classification task. The model’s encoded knowledge, stored in its parameters, enables it to perform this task correctly and return the requested information to you.
   
   ![NER](img/NER.png)
   
   ![NER2](img/NER2.png)

## Types of LLMs

We are going to explore the current landscape of LLMs and try to gain insight into which LLM is suitable for which use case.

This choice depends on 
- what you want to use it for, 
- on your data, 
- on how much you are willing to pay for it, 
- …

Depending on whether you want to use the model for text, audio, video, or image generation, you will choose a different type of model.

* For **audio and speech recognition**, Whisper-type models are a good choice.
  These are trained on diverse audio messages and can recognize speech in multiple languages.

* **Image generation.** For generating images, DALL-E (by OpenAI) and Midjourney are two well-known choices.

* **Text generation.** Most models are trained for text generation, e.g., GPT-4, …

* **Multi-modality.** There are models that can handle different types of data input and output, e.g., both text and images. See GPT-4o. This model is capable of combining natural language processing with *visual understanding*.

Here's a tabular overview of model examples for each type of application.

| Application                    | Example Models                                                                                                                                                        |
| ------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Audio / Speech Recognition** | **Whisper** (OpenAI, proprietary API) • **Mistral Voxtral Small/Mini** (open-weight) • **OWSM-CTC** (open-source) • **Deepgram Nova-2** (proprietary API)             |
| **Image Generation**           | **DALL-E 3** (OpenAI, proprietary API) • **Midjourney** (proprietary API) • **Stable Diffusion XL** (open-source) • **FLUX.1** (open-weight)                          |
| **Text Generation**            | **GPT-4.1 / GPT-4o** (OpenAI, proprietary API) • **Claude 3.7 Sonnet** (Anthropic, proprietary API) • **Moonshot AI K2** (open-source) • **Qwen 3-72B** (open-weight) |
| **Multi-Modality**             | **GPT-4o** (OpenAI, proprietary API) • **Gemini 2.5 Pro** (Google, proprietary platform) • **Cohere Aya Vision** (open-weight) • **Qwen QvQ** (open-weight)           |

**table:** Examples of models for a variety of application types. (Remark: GPT-5 generated, their classification as being proprietary, open-weight or open source might be not entirely correct).

## Open source, open weights and proprietary models
Another way to categorize LLMs (Large Language Models) is by whether they are open-source, open-weight, or proprietary.

### Proprietary models

A proprietary AI model refers to any model whose architecture, training data, and weights are kept confidential by the developing organization. Typically, access is restricted—users interact with it via closed APIs or licensed software, and cannot inspect, modify, redistribute, or retrain the model.

Think of proprietary AI as "private property"—fully controlled by its owner.

Proprietary models are models that are owned by a company and are not made publicly available.

**Pros:**

- These models are often optimized for production use.

**Cons:**

- They may not be inspected, modified, or customized for different applications.
- They are not always available for free; a subscription or payment may be required to use them.
- Users also have no control over the data used to train the model, which means they must trust that the model’s owner is committed to data privacy and the responsible use of AI.

Examples of popular proprietary models are (most) models from OpenAI (e.g., GPT-5), Gemini (by Google DeepMind), and BingAI (by Microsoft).


| Provider / Model        | Status      | Access Type            |
| ----------------------- | ----------- | ---------------------- |
| OpenAI – GPT series     | Proprietary | API / licensed access  |
| Anthropic – Claude      | Proprietary | API only               |
| Google – Gemini         | Proprietary | Platform (Vertex AI)   |
| IBM – Granite (Watsonx) | Proprietary | Enterprise ecosystem   |
| Huawei – PanGu family   | Proprietary | Closed, internal-use   |
| Upstage – Solar Pro 2   | Proprietary | Closed, select clients |

**tabel:** Examples of proprietary models and their access type

### Open-weight modellen

These are models whose trained weights (the parameters learned during training) are made publicly available. This means you can download, run, and fine-tune the model, but you might not get:

- the original training code,
- the training dataset,
- full reproducibility instructions

This means, you get the final product (the neural network's learned parameters), not necessarily the recipe. Transparency is limited — you can inspect the model’s outputs and potentially the architecture, but can’t always retrain from scratch.

Open-weight models are often released under restricted licenses (e.g., research only, non-commercial).

Examples:
- Meta’s LLaMA 2 — you can download the weights, run them locally, but the full dataset and training scripts are not public,
- GPT-OSS series: gpt‑oss‑120b and gpt-oss-20b.

### Open-source models
In the AI context, this follows the principles of open-source software:

- Weights
- Model architecture code
- Training code
- Training dataset (or a way to regenerate it)
- Documentation & reproducibility instructions

Open-source models are models that are made available to the public and can be used by anyone. They are often released by the company that created them or by the research community.

Pros:

- These models can be fully reproduced from scratch. 
- they can be inspected/audited,
- they can be modified or customized,
- there is maximum transparency, which may lead to trust.

Potential cons:

- They are not always optimized for production use.
- They may often perform less well than proprietary models.
- Funding for open-source models can be limited.
- They may not be maintained or updated in the long term with the latest research.

Open-source models are usually licensed under OSI-approved* licenses like Apache 2.0, MIT, etc.
* OSI: Open Source Intiative
  
Examples of fully open source models:

| Model        | 
| ------------ |
| GPT-NeoX-20B |
| OLMo 7B      | 
| OpenCoder    | 

**Table:** examples of fully open source models

These models truly qualify as open-source, offering full transparency and the freedom to use, modify, and distribute them without hidden restrictions. They are ideal for fully reproducible research, development, and educational use.

### Exercise

Examine whether the following models are truly open source models, rather open-weight models or proprietary models.

The goal of this exercise is to use a critical mindset. You can use language models to get (non-fully reliable) information, the websites of the models itself (often marketing their product), articles. Give a special attention to the licence when deciding whether the model is for example truly open source or rather open weight.

- Llama 3 series of models,
- Deepseek-coder V2,
- Open-Mistral 7b.
- Deepseek V3

## Encoder-Decoder versus Decoder-only  
To discuss the different types of LLM (Large Language Model) architectures, let’s use an analogy.

Imagine you are asked to write a course. You have two colleagues: one is responsible for creating the content, and the other for reviewing/interpreting it.

The content creator is like a Decoder-only model: they can look at the topic, see what you have already written, and then write a course based on that. They are very good at writing engaging and informative content (that is, generating text), but they are not as good at truly understanding the topic. Some examples of decoder models are models from the GPT family, such as GPT-3. **Decoder-only models are also called auto-regressive models**.

The reviewer is like an Encoder-only model: the reviewer looks at the written course and the answers, and understands the relationship between them. The reviewer understands the context but is not good at generating content. An encoder-only model, for example, is good at classification tasks such as sentiment analysis. An example of an encoder-only model is BERT*.
**Encoder-only models are also called auto-encoding models.**

* BERT: Bidirectional Encoder Representations from Transformers

Imagine we have someone who can both create and review the course — that is an **Encoder-Decoder model**. This type of model works well for tasks such as translations or creating summaries. For these tasks, there must be both an understanding of the text and the ability to generate text. Examples of this are BART* and T5.

* BART: Bidirectional and Auto-Regressive Transformers

![encoder_decoder](img/encoder_decoder.png)

![encoder_decoder_models](img/encoder_decoder_models.png)

## Model, service, platform 

### Model

Models are simply the neural network, with the parameters, weights, and so on. Companies can run these locally, but they need to purchase equipment, set up an infrastructure for scaling, and buy a license or use an open-source model. Open-source and open-weight models are (sometimes with restrictions – see license) available for use, but they often require computing power to run the model.

### Service

A service is a ready-to-use AI capability provided by a vendor, usually through an API or graphical interface, that hides the complexity of the underlying model and infrastructure.

As a service user, you consume the capability, you don’t manage the model training, nor the hosting.

Examples:
- Azure OpenAI Service – Access GPT models via API without managing servers.
- EdenAI – Aggregates different AI APIs for easy integration.
- Amazon Polly – Text-to-speech as a cloud service.

###Platform

A platform is an integrated environment that offers 
- tools, 
- infrastructure, and 
- workflows 
to 
- develop, 
- train, 
- deploy, and 
- manage AI models or applications.

Key point: You control and build with the tools; the platform supports the entire development lifecycle.

Examples:

- Hugging Face – Model hub, dataset hosting, training tools, and deployment options.
- Google Vertex AI – End-to-end model building and deployment on Google Cloud.
- IBM Watsonx – AI lifecycle management including governance, data, and model serving.


## **AI Services, Platforms, and Hybrids**

| Category                      | Examples                                                                                   | Description                                                                                                                                                                                                         |
| ----------------------------- | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Pure Services**             | **Azure OpenAI Service** • **EdenAI**                                                      | Primarily API-driven access to AI models (hosted by the provider). Minimal infrastructure setup for the user. Often tied to subscription or pay-per-use billing.                                                    |
| **Development Platforms**     | **Google Colab** • **Databricks AI Platform**                                              | Cloud environments to run, train, and experiment with models. Provide compute resources and integration tools, but not necessarily a pre-bundled suite of proprietary models.                                       |
| **Hybrid Service & Platform** | **Hugging Face** • **Google Vertex AI** • **IBM Watsonx** • **Amazon Bedrock / SageMaker** | Combine hosted AI services (inference endpoints, APIs) with model repositories, development tools, training pipelines, and community collaboration features. Often support both proprietary and open-weight models. |

**Table:** AI Services, Platforms, and Hybrids (source: GPT-5)
