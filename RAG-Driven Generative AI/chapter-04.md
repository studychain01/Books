# Multimodular RAG for Drone Technology

This chapter explores how to build a modular Retrieval-Augmented Generation (RAG) system for drone technology, integrating both textual and image data. The system leverages LlamaIndex, Deep Lake, and OpenAI LLMs to process and generate responses from multimodal datasets.

## Chapter Summary

This chapter presents a step-by-step approach to building an educational, modular RAG question-answering system for drone technology. The system is designed to handle both text and image data using a modular architecture, as illustrated in Figure 4.1 (A Multimodal Modular RAG System). The workflow includes:

- Loading and indexing textual and image datasets (using Deep Lake and LlamaIndex)
- Initializing the LLM query engine and defining user input for both text and multimodal queries
- Retrieving relevant data and generating responses with OpenAI LLMs
- Merging outputs from text and image modules for comprehensive answers
- Evaluating system performance using defined metrics

The process is modular and extensible, allowing for the integration of new data types and tasks. The chapter also emphasizes the importance of performance metrics and provides practical code examples for loading datasets and building the system in Python.

## Overview

A modular RAG system consists of distinct components, each responsible for handling specific data types and tasks:
- **Text Module:** Processes and retrieves information from textual datasets using LLMs.
- **Image Module:** Manages and analyzes image data, identifying and labeling objects within drone images.

The integration of these modules enables the system to generate comprehensive responses by combining insights from both text and images.

## Key Technologies
- **Deep Lake (Activeloop):** Efficiently manages and stores multimodal data.
- **LlamaIndex:** Indexes and retrieves relevant information from both text and image datasets.
- **OpenAI LLMs:** Generates natural language responses and augments user queries.

## What is Multimodal Data?
Multimodal data combines various forms of information—such as text, images, audio, and video—to enrich data analysis and interpretation. In this system, we focus on text and images to enhance the quality of generated responses.

## What is a Modular System?
A modular system is composed of independent modules, each designed to handle a specific data type or task. This architecture allows for:
- Flexibility in integrating new data types
- Scalability for larger datasets
- Enhanced response generation by leveraging specialized modules

## System Architecture

- The system contains two main datasets:
  - **Textual Dataset:** Contains information about drones.
  - **Image Dataset:** Contains drone images with object labels.
- The workflow involves:
  1. Loading and indexing both datasets using Deep Lake and LlamaIndex.
  2. Defining user input for both text and image queries.
  3. Retrieving relevant data based on the query.
  4. Generating responses using OpenAI LLMs, merging outputs from both modules as needed.
  5. Evaluating system performance using defined metrics.

## Benefits
- **Enhanced Data Analysis:** By combining text and images, the system provides richer, more informative responses.
- **Modular Design:** Each module can be developed, tested, and improved independently.
- **Scalability:** Easily extend the system to include additional data types or tasks.

---

## Multimodal Performance Metrics and Evaluation

### Multimodal Performance Metric

Evaluating images returned by a system presents unique challenges, especially at scale where automation is required. Relying solely on dataset labels is insufficient for comprehensive assessment. The proposed method leverages GPT-4o's computer vision capabilities to analyze images, identify objects, and provide detailed descriptions that can be compared against expected labels using cosine similarity.

**Key Components:**
- **GPT-4o Integration:** A multimodal generative AI model capable of analyzing complex visual data
- **Base64 Encoding:** Converts binary image data into ASCII text characters for smooth transmission over HTTP protocols
- **Cosine Similarity:** Measures the similarity between expected and generated descriptions

### Image Encoding Process

Images must be encoded for data transmission to GPT-4o. Base64 encoding transforms binary data into standard ASCII text characters, ensuring smooth transmission over text-handling protocols and preventing data corruption or interpretation errors.

**Implementation:**
```python
import base64

IMAGE_PATH = "/content/boxed_image.jpg"

def encode_image(image_path):
    with open(image_path, "rb") as image_file:
        return base64.b64encode(image_file.read()).decode("utf-8")

base64_image = encode_image(IMAGE_PATH)
```

### OpenAI Client Setup and Response Processing

**Client Initialization:**
```python
from openai import OpenAI

client = OpenAI(api_key=openai.api_key)
MODEL = "gpt-4o"
```

**Response Processing:**
```python
u_word = unique_words[0]
print(u_word)
```

### Image Analysis with GPT-4o

The system instructs GPT-4o to analyze images looking for specific target labels (e.g., "truck"). The model receives both system and user role instructions to identify and describe objects within bounding boxes.

**Analysis Request:**
```python
response = client.chat.completions.create(
    model=MODEL,
    messages=[
        {"role": "system", "content": f"You are a helpful assistant that analyzes images that contain {u_word}."},
        {"role": "user", "content": [
            {"type": "text", "text": f"Analyze the following image, tell me if there is one {u_word} or more in the bounding boxes and analyze them:"},
            {"type": "image_url", "image_url": {"url": f"data:image/png;base64,{base64_image}"}}
        ]}
    ],
    temperature=0.0
)

response_image = response.choices[0].message.content
print(response_image)
```

### Performance Evaluation

**Cosine Similarity Calculation:**
```python
resp = u_word + "s"  # Align with multiple objects in response
multimodal_similarity_score = calculate_cosine_similarity_with_embeddings(resp, str(response_image))
print(f"Cosine Similarity Score: {multimodal_similarity_score:.3f}")
```

**Overall System Performance:**
```python
score = (llm_similarity_score + multimodal_similarity_score) / 2
print(f"Multimodal, Modular Score: {score:.3f}")
```

### Key Insights and Challenges

1. **Complex Image Analysis:** Even with high similarity scores, complex images remain challenging to analyze with precision, though continuous progress is being made in this area.

2. **Human Feedback Importance:** The metric can be improved because human observers can identify relevant images that automated systems might miss. This explains why top AI agents like ChatGPT, Gemini, and Bing Copilot always include feedback processes with thumbs up and thumbs down mechanisms.

3. **Automated Assessment Limitations:** While automated metrics provide valuable insights, they may not capture the full context and relevance that human observers can identify, especially for complex visual data.

4. **Performance Metrics:** The multimodal modular score combines LLM and multimodal similarity scores to provide a comprehensive evaluation of system performance.

### Key Points Summary

- **Multimodal Evaluation:** Uses GPT-4o's vision capabilities to analyze images and compare descriptions with expected labels
- **Base64 Encoding:** Essential for transmitting image data to multimodal AI models
- **Cosine Similarity:** Measures the alignment between expected and generated descriptions
- **Human Feedback Integration:** Critical for improving automated assessment systems
- **Modular Scoring:** Combines multiple similarity scores for comprehensive performance evaluation
- **Complex Image Challenges:** Automated analysis of complex images remains an ongoing challenge requiring human oversight

---

## Summary of Chapter 4: Multimodular RAG for Drone Technology

This chapter introduces a modular Retrieval-Augmented Generation (RAG) system designed for drone technology, integrating both textual and image data. The system is built using LlamaIndex, Deep Lake, and OpenAI LLMs, and is structured to handle different data types through specialized modules:

- **Text Module:** Processes and retrieves information from textual datasets using LLMs.
- **Image Module:** Manages and analyzes image data, identifying and labeling objects within drone images.

### Key Concepts and Workflow

- **Multimodal Data:** Combines text and images to enrich analysis and response generation.
- **Modular Design:** Each module is responsible for a specific data type, allowing for flexible and scalable integration.

#### System Flow

1. Load and index both textual and image datasets (using Deep Lake and LlamaIndex).
2. Define user input for both text and image queries.
3. Retrieve relevant data (text or images) based on the query.
4. Generate responses using OpenAI LLMs, merging outputs from both modules as needed.
5. Evaluate system performance using defined metrics.

### Implementation Steps

- **Load the LLM dataset:** Import textual drone data using Deep Lake.
- **Initialize the LLM query engine:** Set up LlamaIndex for efficient retrieval.
- **Define user input:** Support both text and multimodal queries.
- **Image handling:** Load and visualize the image dataset, enabling navigation and selection (e.g., bounding boxes).
- **Build a multimodal query engine:** Retrieve and process both text and image data.
- **Generate and merge responses:** Combine outputs from both modules for comprehensive answers.
- **Apply performance metrics:** Evaluate the accuracy and efficiency of the system.

---