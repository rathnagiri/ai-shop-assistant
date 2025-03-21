# ai-shop-assistant: GenAI-based Shopping Assistant

## Project Overview

### Project Name:
**ShopAssist 2.0 - GenAI-based Laptop Shopping Assistant**

### Objective:
Create a chatbot that recommends laptops based on user requirements by leveraging a dataset containing laptop specifications, product names, descriptions, and other relevant details.

### Problem Statement:
Given a dataset containing information about laptops (such as product names, specifications, descriptions), build a chatbot that can parse this data and provide accurate laptop recommendations aligned with user requirements.

### Solution Summary:
ShopAssist 2.0 is designed to interact with users conversationally, asking relevant questions to capture their needs and preferences for a laptop. Using advanced language model capabilities, it provides tailored recommendations, narrowing the selection to the top 3 laptops best matching the user’s profile.

## Approach

The development of ShopAssist can be broken down into several stages:

### 1. Conversation and Information Gathering:
- **Goal**: Engage the user to understand their requirements, such as display quality, processing speed, GPU intensity, portability, multitasking capability, and budget.
- **Implementation**: The chatbot uses natural language processing (NLP) to manage conversational flow, asking targeted questions to gather detailed specifications from the user.

### 2. Information Extraction:
- **Goal**: Transform user inputs into structured data that can be used to filter and score laptops from the dataset.
- **Implementation**: Once sufficient information is gathered, rule-based functions are used to extract key data points and rank laptops based on compatibility with the user’s requirements.

### 3. Personalized Recommendation:
- **Goal**: Provide a shortlist of suitable laptops and continue the conversation to refine recommendations based on follow-up user questions.
- **Implementation**: Using the extracted information, ShopAssist presents a list of up to 3 laptops that align with the user's preferences and further engages with the user to address any specific concerns or questions about the recommendations.

## Technical Design

The chatbot’s technical design involves a combination of APIs, function calling, and custom functions to meet the requirements. The core components are outlined below:

### 1. Language Model Integration:
- **Platform**: OpenAI language models power the conversational and recommendation abilities, utilizing GPT for generating responses.
- **Function Calling API**: Function calls help capture structured user preferences into a “user requirements dictionary.”

### 2. Dialogue Management System:
- **Overview**: A loop-based dialogue system guides the conversation, handles moderation checks, and ensures responses align with the user’s intent.
- **Key Functions**:
  - `dialogue_mgmt_system`: Initializes the conversation and continues until either a suitable recommendation is found or the conversation is terminated.
  - `moderation_check`: Verifies responses to filter inappropriate content.
  - `get_chat_completions_with_function_calling`: Creates a structured dictionary containing user specifications by calling custom functions.

### 3. Laptop Recommendation Process:
- **Comparison and Filtering**: The chatbot compares user preferences with available laptops using `compare_laptops_with_user`.
- **Validation**: Validates the top 3 recommendations through `recommendation_validation` to ensure they closely match user criteria.

### 4. Final Interaction:
- Confirms the final recommendations through an additional conversation round, allowing the user to make the final decision or restart the process if requirements change.

## Key Functions and Components

1. **`get_chat_completions_with_function_calling(input, include_budget)`**:
   - Collects user input, invokes OpenAI’s function calling API, and returns a structured dictionary representing the user’s laptop specifications, including attributes like GPU intensity, display quality, and budget if applicable.

2. **`extract_user_profile_info`**:
   - A custom function to extract and structure user information based on inputs (e.g., GPU intensity, display quality, portability).

## Results and Insights

Through a structured conversation flow and precise information extraction, ShopAssist 2.0 effectively narrows down the available options and recommends laptops based on specific user needs. Testing indicates that ShopAssist 2.0 can provide personalized recommendations with high accuracy, improving user experience and satisfaction.

## Technologies Used

- **Python**
- **OpenAI GPT-4o-mini-2024-07-18** for natural language processing and recommendation generation
- **Tenacity** for implementing retry logic with exponential backoff
- **Pandas** for data manipulation and analysis
- **IPython.display** for displaying HTML and other outputs
- **OpenAI API** for function calling and conversational abilities
- **Natural Language Processing (NLP)** for managing conversation flow and extracting user specifications
- **Machine Learning** for recommendation algorithms

## Copyright and License Information
This project is licensed under the MIT License. See the LICENSE file for more details.

Copyright (c) 2024 Rathnagiri Nagarajan. All rights reserved.

## Acknowledgments
- OpenAI for the GPT-3 language model.
- The dataset used for laptop specifications and descriptions.
