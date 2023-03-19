# NeuroDragon

NeuroDragon is a Python package for building and composing chatbot systems using a modular, layer-based architecture. Inspired by PyTorch's neural network layers, this package allows users to create chatbots with custom components and easily integrate them into a single system.

## Overview

The goal of this project is to provide a flexible and modular framework for building chatbot systems. By breaking down the chatbot into smaller, more manageable layers, users can easily customize and extend the functionality of their chatbots while maintaining a clean and organized codebase.

## Key Features

- Modular, layer-based architecture for easy customization and extensibility
- Predefined layers for common chatbot tasks
- Support for short-term memory, long-term memory, and working memory
- Flexible attention mechanism for selecting appropriate child chatbots
- Parser and action layers for processing structured inputs and triggering actions
- Completion and chat-response layers for generating responses

## Package Organization
``` NeuroDragon/
|-- neurodragon/
|   |-- __init__.py
|   |-- layers/
|   |   |-- __init__.py
|   |   |-- base.py
|   |   |-- input_layer.py
|   |   |-- short_term_memory_layer.py
|   |   |-- query_embedder_layer.py
|   |   |-- long_term_memory_layer.py
|   |   |-- working_memory_layer.py
|   |   |-- output_layer.py
|   |-- utils/
|   |   |-- __init__.py
|   |   |-- tools.py
|-- examples/
|   |-- fifo_vector_chat_example.py
|-- tests/
|   |-- __init__.py
|   |-- test_layers.py
|-- setup.py
|-- notes.md
|-- brain_inspired.md
|-- README.md
```

## Layers Overview

The NeuroDragon package contains the following predefined layers:

- Input Layer: Receives the raw text input from the user.
- Short-term Memory (STM) Layer: Handles the chatbot's short-term memory, storing recent interactions in a FIFO (First-In-First-Out) manner.
- Query Embedder Layer: Transforms the input text into an embedded representation suitable for querying long-term memory.
- Long-term Memory (LTM) Layer: Contains two components:
  - LTM Add: Adds new knowledge to long-term memory based on the embedded input.
  - LTM Search: Searches long-term memory using the embedded input and returns relevant information.
- Working Memory Layer: Integrates information from both short-term memory and long-term memory retrieval to generate a contextualized understanding of the conversation.
- Output Layer: Generates a chat-response based on the context provided by the working memory.
- Parser Layer: Extracts structured information from raw text inputs.
- Action Layer: Takes structured input and triggers generic actions, returning a string as a response.
- Attention Layer: Selects which child chatbot(s) to use based on the current context.
- Completion Layer: Generates a response by completing a partially-filled input prompt.
- Chat-Response Layer: Generates a response based on the input and other relevant information from the chatbot's memory.

## Why NeuroDragon?

NeuroDragon provides a flexible and extensible framework for building chatbot systems. By structuring the chatbot as a series of layers, users can easily customize and extend the functionality of their chatbots while maintaining a clean and organized codebase.

This modular approach enables the development of more complex chatbots and allows for easier integration of new features or technologies. Additionally, by breaking down the chatbot into smaller components, it becomes easier to understand, debug, and maintain the system.

Furthermore, this package aims to serve as a starting point for researchers and developers interested in exploring new techniques and ideas in chatbot development. By providing a common framework and set of tools, we hope to encourage collaboration and innovation in the field of chatbot research.


## ChatLayers
In this section, we'll describe how the FifoChat, VectorChat, IndexChat, and FifoVectorChat can be constructed using the basic layers provided by the Chatbot-Layers package.

#### FifoChat
The FifoChat is a simple chatbot that focuses on maintaining a short-term memory. It can be constructed using the following layers:

* Input Layer: Receives the raw text input from the user.
* Short-term Memory (STM) Layer: Handles the chatbot's short-term memory, storing recent interactions in a FIFO (First-In-First-Out) manner.
* Output Layer: Generates a chat-response based on the context provided by the short-term memory.

```
       FifoVectorChat
+---------------------------+
|        Input (Text)       |
+---------------------------+
           |
           v
+---------------------------+  
|    Short-term Memory (STM)|
+---------------------------+                     
           |                               
           v                                   
+---------------------------+
|    Working Memory         |
+---------------------------+
           |                                          
           v                                          
+---------------------------+                         
|      Chat-response        |
+---------------------------+
           |  
           v
+---------------------------+                            
|        Output             |
+---------------------------+
```
#### VectorChat
The VectorChat is a chatbot that utilizes a long-term memory based on vector space models. It can be constructed using the following layers:

* Input Layer: Receives the raw text input from the user.
* Query Embedder Layer: Transforms the input text into an embedded representation suitable for querying long-term memory.
* Long-term Memory (LTM) Layer: Contains two components:
* LTM Add: Adds new knowledge to long-term memory based on the embedded input.
* LTM Search: Searches long-term memory using the embedded input and returns relevant information.
* Output Layer: Generates a chat-response based on the context provided by the long-term memory retrieval.

```
       FifoVectorChat
+---------------------------+
|        Input (Text)       |
+---------------------------+
           |
           v
+---------------------------+  
|    Query Embedder         |
+---------------------------+ 
           |                                          
           |                                          
+---------------------------+
|   Embedded Input          |
+---------------------------+
           |                                          
 |ltm_add|   |ltm_search|      
           v     
+---------------------------+
|   Long-term Memory (LTM)  |
+---------------------------+
           |
           v                              
+---------------------------+          
|    Working Memory         
+---------------------------+           
           |                                          
           v                                          
+---------------------------+                         
|      Chat-response        |
+---------------------------+
           |  
           v
+---------------------------+                            
|        Output             |
+---------------------------+
```

#### IndexChat
The IndexChat is a chatbot that utilizes multiple knowledge indexes for answering questions. It can be constructed using the following layers:

* Input Layer: Receives the raw text input from the user.
* Query Embedder Layer: Transforms the input text into an embedded representation suitable for querying the knowledge indexes.
* Knowledge Index Layer: Performs similarity search on multiple knowledge indexes and retrieves relevant information.
* Output Layer: Generates a chat-response based on the context provided by the knowledge index retrieval.


#### FifoVectorChat
The FifoVectorChat is a chatbot that combines the short-term memory capabilities of FifoChat with the long-term memory capabilities of VectorChat. It can be constructed using the following layers:



Input Layer: Receives the raw text input from the user.
Short-term Memory (STM) Layer: Handles the chatbot's short-term memory, storing recent interactions in a FIFO (First-In-First-Out) manner.
Query Embedder Layer: Transforms the input text into an embedded representation suitable for querying long-term memory.
Long-term Memory (LTM) Layer: Contains two components:
LTM Add: Adds new knowledge to long-term memory based on the embedded input.
LTM Search: Searches long-term memory using the embedded input and returns relevant information.
Working Memory Layer: Integrates information from both short-term memory and long-term memory retrieval to generate a contextualized understanding of the conversation.
Output Layer: Generates a chat-response based on the context provided by the working memory.
By constructing these chatbots using the basic layers, we can create more complex and specialized chatbot systems that cater to various use cases and requirements.


```
       FifoVectorChat
+---------------------------+
|        Input (Text)       |
+---------------------------+
           |
           v
+---------------------------+   embed   +---------------------------+
|    Short-term Memory (STM)|---------->|    Query Embedder         |
+---------------------------+           +---------------------------+
           |                                          |
           |                                          v
           |                             +---------------------------+
           |                             |   Embedded Input          |
           |                             +---------------------------+
           |                                          |
           |                                |ltm_add|   |ltm_search|      
           v                                          v
+---------------------------+           +---------------------------+
|    Working Memory         |<----------|   Long-term Memory (LTM)  |
+---------------------------+           +---------------------------+
           |                                          ^
           v                                          |
+---------------------------+                         |
|      Chat-response        |-------------------------|
+---------------------------+
           |  
           v
+---------------------------+                            
|        Output             |
+---------------------------+
```


## Getting Started
Coming soon: installation instructions, example usage, and API documentation.

## Contributing
Coming soon: guidelines for contributing to the project.


## Acknowledgements
The design of this package was inspired by discussions on chatbot architecture, OpenAI's GPT models, and the PyTorch deep learning library.