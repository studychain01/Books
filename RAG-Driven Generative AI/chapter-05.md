# Chapter 5: Hybrid and Adaptive RAG Systems

## Overview

This chapter explores advanced RAG (Retrieval-Augmented Generation) systems that integrate human feedback and adaptive mechanisms to improve performance in real-world scenarios. The focus is on two key concepts: **Hybrid RAG** and **Adaptive RAG**, which address the limitations of purely theoretical frameworks by incorporating human expertise and dynamic adjustments.

## Boosting RAG Performance with Expert Human Feedback

Human feedback (HF) is not just useful but essential for generative AI, particularly for models that utilize RAG. While the data used to train an AI model and its parameters are generally fixed unless retrained, information within retrieval-based text and multimodal datasets can be observed and adjusted. This is where HF becomes crucial. By providing feedback on the data an AI model retrieves from its datasets, human feedback can directly improve the quality of the model's future responses. This engagement makes humans active participants in the development of RAG systems, adding a new dimension to AI projects: **adaptive RAG**.

## Introduction to Adaptive RAG

Adaptive RAG represents an advancement beyond "naïve, advanced, and modular RAG." Even highly-rated generative AI systems may not satisfy users if they aren't truly helpful. The system becomes adaptive because the documents used for retrieval are continuously updated. Integrating human feedback into RAG creates a "pragmatic hybrid approach," involving humans in an otherwise automated generative process.

### Learning Outcomes

By the end of this chapter, readers will:
- Gain theoretical understanding of the adaptive RAG framework
- Acquire practical experience in building an AI model based on Human Feedback
- Learn to develop and customize RAG systems when pre-built solutions fail
- Understand the importance of human user satisfaction over mere performance metrics

## Chapter Topics Covered

- Defining the adaptive RAG ecosystem
- Applying adaptive RAG to augmented retrieval queries
- Automating augmented generative AI inputs with HF
- Automating end-user feedback rankings to trigger expert HF
- Creating an automated feedback system for a human expert
- Integrating HF with adaptive RAG for GPT-4o

---

## Adaptive RAG: Beyond Traditional Limitations

No, RAG cannot solve all our problems and challenges. RAG, just like any generative model, can also produce irrelevant and incorrect output! RAG might be a useful option, however, because we feed pertinent documents to the generative AI model that inform its responses. Nonetheless, the quality of RAG outputs depends on the accuracy and relevance of the underlying data, which calls for verification! That's where adaptive RAG comes in. Adaptive RAG introduces human, real-life, pragmatic feedback that will improve a RAG-driven generative AI ecosystem.

## Information in Generative AI Models

The core information in a generative AI model is "parametric (stored as weights)." In the context of RAG, data can be "visualized and controlled," as referenced in "Chapter 2, RAG Embedding Vector Stores with Deep Lake and OpenAI." Challenges such as "fuzzy queries" from end-users or "faulty" RAG data retrieval can occur. To mitigate these issues, an "HF process" (Human Feedback process) is "highly recommended to ensure the system's reliability."

Figure 1.3 from Chapter 1, Why Retrieval Augmented Generation?, represents the complete RAG framework and ecosystem. We will zoom in on the adaptive RAG ecosystem and focus on the key processes that come into play.

---

## Adaptive RAG Ecosystem (Figure 5.1)

The adaptive RAG ecosystem consists of four main components that interact through feedback loops:

### Main Components

1. **Retriever (D):** Represented by stacked books, responsible for collecting and retrieving relevant information
2. **Trainer (T):** Labeled with "1010 1010," trains the Retriever to improve data retrieval capabilities
3. **Generator (G):** Depicted with a robot icon, takes augmented input and generates output
4. **Evaluator (E):** Represented by a person icon, assesses quality and provides feedback

### System Flow

**Data Collection and Retrieval (Retriever Path):**
- `D1. Collect` - Gathering data
- `D4. Retrieval query` - Formulating queries for retrieval
- Output serves as `G1. Input` for the Generator
- `D1. Collect` feeds into `T1. Train`

**Training (Trainer Path):**
- `T1. Train` - Central training component receiving input from `D1. Collect`
- After training, feeds back into the **Retriever (D)**

**Generation (Generator Path):**
- `G1. Input` (from Retriever) becomes `G2. Augmented input with HF`
- `G2. Augmented input with HF` leads to `G4. Generation and output`
- `G4. Generation and output` feeds back into the **Generator (G)**

**Evaluation and Feedback Loops (Evaluator Path):**
- `G4. Generation and output` → `E1. Metrics` (performance metrics calculation)
- `E1. Metrics` → **Evaluator (E)** (assessment using metrics)
- **Evaluator (E)** → `E2. Human feedback` (critical adaptive component)

**Adaptive Feedback Loops:**
1. **Generator Augmentation:** `E2. Human feedback` → `G2. Augmented input with HF`
2. **Trainer/Retriever Improvement:** `E2. Human feedback` → `T1. Train`

### Key Characteristics

- **Adaptive Nature:** Continuously learning and improving through feedback loops
- **Human Feedback (HF):** Central component directly influencing both input augmentation and training
- **Modular Design:** Distinct, interacting modules with specialized functions
- **Continuous Improvement:** Cyclical nature with ongoing refinement
- **Metrics-Driven Evaluation:** Quantitative measurement before human evaluation

---

## System Components

### Retriever Components

**D1:** Collect and process Wikipedia articles on LLMs by fetching and cleaning the data.

**D4:** Retrieval query to query the retrieval dataset.

### Generator Components

**G1:** Input entered by an end-user.

**G2:** Augmented input with HF that will augment the user's initial input and prompt engineering to configure the GPT-4o model's prompt.

### Evaluator Components

**E1:** Metrics to apply a cosine similarity measurement.

**E2:** Human feedback to obtain and process the ultimate measurement of a system through end-user and expert feedback.

---

## Practical Implementation: Company C Case Study

### Company C Scenario

Company C intends to deploy a conversational AI agent to educate its employees on the basic terms, concepts, and applications of AI. The ML engineer overseeing this RAG-driven generative AI project aims for future users to enhance their AI knowledge while working on other AI initiatives across sales, production, and delivery departments.

### Current Challenges

Company C's "C-phone series" smartphones are experiencing technical issues, leading to a high volume of customer requests. The IT department proposes setting up a conversational agent to assist these customers, but the internal teams are not convinced. Consequently, the IT department has decided to first implement a conversational agent whose purpose is to explain what a Large Language Model (LLM) is and how it can be beneficial for the C-phone series customer support service.

### Program Requirements

The program will be hybrid and adaptive to fulfill the needs of Company C:

#### Hybrid System

Real-life scenarios necessitate going beyond theoretical frameworks. A system is considered hybrid because it integrates "HF" (Human Feedback) within the real-time retrieval process. The system will not rely solely on keywords to parse document content. Instead, it will label documents (specifically Wikipedia URLs in this case). This labeling process can be automated, controlled, and improved by human intervention when needed. Some documents will be replaced and relabeled based on human-expert feedback. The program automatically retrieves both human-expert feedback documents and raw retrieved documents, forming a "hybrid (human-machine) dynamic RAG system."

#### Adaptive System

We will introduce human user ranking, expert feedback, and automated document re-ranking. This HF loop takes us deep into modular RAG and adaptive RAG. Adaptive RAG leverages the flexibility of a RAG system to adapt its responses to the queries. In this case, we want HF to be triggered to improve the quality of the output.

### Real-Life Project Considerations

Real-life projects will inevitably require an ML engineer to go beyond the boundaries of pre-determined categories. Pragmatism and necessity encourage creative and innovative solutions. For example, for the hybrid, dynamic, and adaptive aspects of the system, ML engineers could imagine any process that works with any type of algorithm: classical software functions, ML clustering algorithms, or any function that works. In real-life AI, what works, works!

---

## Proof of Concept Benefits

It's time to build a proof of concept to show Company C's management how hybrid adaptive RAG-driven generative AI can successfully help their teams by:

1. **Proving AI's viability:** Proving that AI can work with a proof of concept before scaling and investing in a project
2. **Customization:** Showing that an AI system can be customized for a specific project
3. **Skill development:** Developing solid ground-up skills to face any AI challenge
4. **Data governance:** Building the company's data governance and control of AI systems
5. **Scalability foundation:** Laying solid grounds to scale the system by solving the problems that will come up during the proof of concept

---

## Implementation Approach

In this chapter, we will illustrate adaptive RAG by building a hybrid adaptive RAG program in Python on Google Colab. We will build this program from scratch to acquire a clear understanding of an adaptive process, which may vary depending on a project's goals, but the underlying principles remain the same. Through this hands-on experience, you will learn to develop and customize a RAG system when a ready-to-use one fails to meet the users' expectations. This is important because human users can be dissatisfied with a response no matter what the performance metrics show. We will also explore the incorporation of human user rankings to gather expert feedback on our RAG-driven generative AI system. Finally, we will implement an automated ranking system designed to augment user input for a generative model, providing practical insights into the successful implementation of a RAG-driven system within a company.

---

## Building Hybrid Adaptive RAG in Python

Let's now start building the proof of concept of a hybrid adaptive RAG-driven generative AI configuration. Open `Adaptive_RAG.ipynb` on GitHub. We will focus on HF and, as such, will not use an existing framework. We will build our own pipeline and introduce HF.

As established earlier, the program is divided into three separate parts: the retriever, generator, and evaluator functions, which can be separate agents in a real-life project's pipeline. Try to separate these functions from the start because, in a project, several teams might be working in parallel on separate aspects of the RAG framework.

---

## 1. Retriever

This section covers the initial steps to set up the environment for a RAG-driven generative AI model. This process involves installing essential software components and libraries for data retrieval and processing, specifically mentioning the downloading of crucial files and the installation of packages for effective data retrieval and web scraping.

### 1.1. Installing the retriever's environment

Let's begin by downloading `grequests.py` from the `commons` directory of the GitHub repository. This repository contains resources common to several programs, thus helping to avoid redundancy. The download is standard and built around the request.

---

## 2. Generator

### 2.1. Adaptive RAG selection based on human rankings

The selection process will be determined by the ratings provided by a user panel over time. In a practical, real-life pipeline, this specific functionality could operate as a standalone program.

### 2.2. Input

For a real-life project, a user interface (UI) will be responsible for managing the input. It's important to carefully design this interface and its associated processes in collaboration with the users, ideally within a workshop environment, to ensure their needs and preferences are thoroughly understood.

### 2.3. Mean ranking simulation scenario

This scenario focuses on calculating the average value of user evaluation scores and the system's functionality. The human user feedback panel evaluates a "hybrid adaptive RAG system" multiple times. The system automatically updates these rankings by calculating the mean of the ratings, stored in a "ranking" variable. This score is used by a management team to decide whether to downgrade, upgrade, or suppress documents. The simulation begins with a "1 to 5 ranking" designed to "deactivate RAG," allowing observation of the "native response of the generative model" without RAG's influence.

### 2.4. Checking the input before running the generator

This step involves displaying the input data before the generator is executed.

### 2.5. Installing the generative AI environment

The installation of the generative AI model's environment, specifically mentioning OpenAI, can be integrated as part of another environment within the overall pipeline. Within this pipeline, other team members can work on, implement, and deploy components in production independently of the retriever functionality.

### 2.6. Content generation

An OpenAI model will be used to process input and generate a response, which will then be evaluated by an evaluator.

### Score-Based System Behavior

**Scores of 1 to 2:** Indicates a "lack of compensatory capability by the RAG system." Suggests a need for "maintenance or possibly model fine-tuning." RAG will be temporarily deactivated until the system is improved. The "user input will be processed but there will be no retrieval."

**Scores of 3 to 4:** Initiates "an augmentation with human-expert feedback only." The system will utilize "flashcards or snippets to refine the output." "Document-based RAG will be deactivated, but the human-expert feedback data will augment the input."

**Scores of 5:** Initiates "keyword-search RAG enhanced by previously gathered HF when necessary." The system will utilize "flashcards or targeted information snippets to refine the output." In this case, "The user is not required to provide new feedback."

---

## 3. Evaluator

Depending on each project's specifications and needs, we can implement as many mathematical and human evaluation functions as necessary. In this section, we will implement two automatic metrics: response time and cosine similarity score. We will then implement two interactive evaluation functions: human user rating and human-expert evaluation.

### 3.1. Response time

The response time was calculated and displayed in the API call with:

```python
import time
...
start_time = time.time() # Start timing before the request
...
response_time = time.time() - start_time # Measure response time
print(f"Response Time: {response_time:.2f} seconds") # Print response time
```

In this case, we can display the response time without further development:

```python
print(f"Response Time: {response_time:.2f}
```

### 3.2. Cosine similarity score

Cosine similarity is a measure of "the cosine of the angle between two non-zero vectors." In the context of text analysis, these vectors are typically "TF-IDF (Term Frequency-Inverse Document Frequency) representations of the text." TF-IDF is a method that "weighs terms based on their importance relative to the document and a corpus."

GPT-4o's input, which is `text_input`, and the model's response, which is `gpt4_response`, are treated by TF-IDF as two separate 'documents.' A "vectorizer" is used to "transform the documents into vectors." The process of vectorization considers "how terms are shared and emphasized between the input and the response." A code snippet, `vectorizer.fit_transform([text1, text2])`, is provided, illustrating the function used for this transformation.

### 3.3. Human user rating

The human user rating interface provides human user feedback. It's recommended to design this interface and process after fully understanding user needs through a workshop. For the purpose of this section, it assumes the human user panel is a group of software developers testing the system.

The code begins with the interface's parameters:

```python
# Score parameters
counter=20 # number of feedback queries
score_history=30 # human feedback
threshold=4 # minimum rankings to trigger human expert feedback
```

### 3.4. Human-expert evaluation

Metrics such as cosine similarity indeed measure similarity but not in-depth accuracy. Time performance will not determine the accuracy of a response either. But if the rating is too low, why is that? Because the user is not satisfied with the response! The code first downloads thumbs-up and thumbs-down images for the human-expert user.

---

## Key Points Summary

### Adaptive RAG Ecosystem
- **Four Main Components:** Retriever (D), Trainer (T), Generator (G), Evaluator (E)
- **Feedback Loops:** Critical for continuous improvement and adaptation
- **Human Feedback Integration:** Central to system quality and reliability
- **Metrics-Driven Evaluation:** Quantitative assessment before human evaluation

### Hybrid RAG Characteristics
- **Real-world Integration:** Addresses limitations of theoretical frameworks
- **Human-Machine Collaboration:** Combines automated processes with human expertise
- **Document Labeling:** Advanced document processing with human oversight
- **Dynamic Adaptation:** Real-time adjustments based on expert feedback

### Adaptive RAG Features
- **Feedback Mechanisms:** Human user ranking, expert feedback, automated re-ranking
- **Flexible Response:** Tailors responses to specific query requirements
- **Continuous Learning:** HF loop enables ongoing system improvement
- **Quality Enhancement:** Focus on triggering human feedback for better outputs

### Human Feedback (HF) Importance
- **Essential Component:** Not just useful but critical for generative AI
- **Real-time Processing:** Enables immediate system improvements
- **Quality Assurance:** Ensures high-quality outputs through oversight
- **Bridge Technology:** Connects automated systems with human expertise

### Practical Implementation
- **Company C Case Study:** Real-world application demonstrating hybrid adaptive RAG
- **Proof of Concept:** Essential for proving AI viability before scaling
- **Customization:** Ability to adapt systems for specific project requirements
- **Skill Development:** Building ground-up skills for AI challenges
- **Data Governance:** Establishing control and governance of AI systems

### System Benefits
- **Enhanced Accuracy:** Human expertise improves document relevance and quality
- **Real-time Adaptation:** System can adjust based on changing requirements
- **Quality Control:** Expert oversight ensures high-quality outputs
- **Scalability:** Can handle diverse use cases and requirements
- **Continuous Improvement:** Ongoing refinement through feedback loops

### Technical Implementation
- **Modular Architecture:** Three separate components (retriever, generator, evaluator)
- **Score-Based Behavior:** Different system responses based on performance scores
- **Response Time Metrics:** Performance measurement for API calls
- **Cosine Similarity:** Text analysis using TF-IDF vectorization
- **Human Evaluation:** User satisfaction and expert feedback integration

---

## Conclusion

Hybrid and Adaptive RAG systems represent the evolution of traditional RAG architectures by incorporating human expertise and feedback mechanisms. These systems address real-world challenges by integrating human feedback directly into retrieval processes, enabling dynamic adaptation based on expert input, providing quality assurance through human oversight, supporting continuous learning and improvement, and handling complex scenarios that require human expertise. The combination of automated efficiency with human expertise creates more robust, accurate, and adaptable RAG systems suitable for real-world applications.
