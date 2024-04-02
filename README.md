# LLM - RAG with Claude for Formula 1 Grandstand Selection

This is a personal project that uses a Retrieval-Augmented Generation (RAG) Large Language Model (LLM) implementation to provide specialized guidance on selecting grandstands for Formula 1 races. This project allows me to solve that problem using Claude models (V2 and Sonnet) via Amazon Bedrock, Amazon Titan Embeddings, and Meta's Facebook AI Similarity Search (FAISS) vector store. 

My wife and I have become serious Formula 1 (F1) fans, transparently thanks to Netflix's "Drive to Survive" series. After a fun trip to Monza in 2023, we have planned an upcoming trip to the 2024 F1 Monaco Grand Prix. 

We spent hours poring through various F1-related websites to determine which grandstand we should purchase tickets in. There are many grandstand options for this race (and every other F1 race), and frankly, many grandstands seem to be similar to the next one. If I could save half a day of agonizing over which grandstand to choose, I would love to have that time back. Since the Monaco grandstands are relatively fresh in my mind, I decided to test this strategy on that race's grandstands before applying it to a race I am unfamiliar with. This will allow me to broadly provide a heuristic check based on my personal knowledge of the Monaco grandstands. 

After completing this project, my overall heuristic assessment is that I'm not convinced that this RAG implementation actually provided an improvement over the non-RAG Claude 3 implementation. My RAG implementation produced different results against the non-RAG implementation, and it I were to apply this to a track I didn't know, I would have difficulty reconciling the two results. While my own follow-up to validate each recommendation could solve this, it doesn't fully eliminate my research time. These conflicting results still provide value by narrowing my focus, which provides some time savings.

Disclaimer: This work is in a personal capacity unrelated to my employer. This package is for illustrative purposes and is not designed for end-to-end productionization as-is.

## Prerequisites

You will need your own Amazon Web Services (AWS) account with Claude and Titan Amazon Bedrock model access. Your Python environment will also require:
- langchain>=0.1.11
- langchain-community
- faiss-cpu==1.8.0

## Overview

This package will demonstrate how to:
- Import libraries
- Instantiate the LLM and embeddings models
- Load websites as documents
- Split documents into chunks
- Confirm embeddings functionality
- Create vector store
- Define Claude 3 function
- Embed question and return relevant chunks
- Create prompt template
- Produce RAG outputs with Claude V2
- Produce outputs with Claude 3 Sonnet for comparison

## Claude V2 RAG vs Claude 3 Sonnet Outputs: "If I have a mid-range budget and want a covered seat, which F1 Monaco Grand Prix grandstand should I choose?"

Claude V2 RAG:

![image](https://github.com/blallen22/llm-rag-claude-formula1/assets/4731381/6fcf2f8b-d8e9-4f4b-9b24-6099eae8b777)

Claude 3 Sonnet:

![image](https://github.com/blallen22/llm-rag-claude-formula1/assets/4731381/92bf19b8-5122-4e63-911d-cce5b2365914)

## Claude V2 RAG vs Claude 3 Sonnet Outputs: "If I have an unlimited budget and want the most beautiful view, which F1 Monaco Grand Prix grandstand should I choose?"

Claude V2 RAG:

![image](https://github.com/blallen22/llm-rag-claude-formula1/assets/4731381/778ad27a-ad8e-45d2-ac11-f8f2dff81957)


Claude 3 Sonnet:

![image](https://github.com/blallen22/llm-rag-claude-formula1/assets/4731381/53568e93-2c77-400a-94bb-f4c5a897679e)

## Input Data

The input data for this project are selected websites that I found to be valuable in previously making my grandstand decision. All rights reserved by those respective website entities. These websites specifically featured articles describing the grandstands. The websites were ingested as-is using the WebBaseLoader.

## Next Steps
Future next steps for this project include:
- Incorporating evaluation methodologies to assess the quality of the outputs beyond the current heuristic assessment
- Inspecting the methodological decisions with further granularity (e.g., the chunk size during the chunking process, etc.)
- Applying this approach to additional use cases

## License

This project is licensed under the [MIT License](https://choosealicense.com/licenses/mit/)

## Resources Referenced

  - [Amazon Bedrock Workshop - Langchain Knowledge Bases and RAG Examples](https://github.com/aws-samples/amazon-bedrock-workshop/blob/main/06_OpenSource_examples/01_Langchain_KnowledgeBases_and_RAG_examples/01_qa_w_rag_claude.ipynb)
  - [Pinecone Langchain RAG Examples](https://colab.research.google.com/github/pinecone-io/examples/blob/master/docs/langchain-retrieval-augmentation.ipynb)
