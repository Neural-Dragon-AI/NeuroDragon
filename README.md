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


## Why NeuroDragon?

NeuroDragon provides a flexible and extensible framework for building chatbot systems. By structuring the chatbot as a series of layers, users can easily customize and extend the functionality of their chatbots while maintaining a clean and organized codebase.

This modular approach enables the development of more complex chatbots and allows for easier integration of new features or technologies. Additionally, by breaking down the chatbot into smaller components, it becomes easier to understand, debug, and maintain the system.

Furthermore, this package aims to serve as a starting point for researchers and developers interested in exploring new techniques and ideas in chatbot development. By providing a common framework and set of tools, we hope to encourage collaboration and innovation in the field of chatbot research.

The NeuroDragon package also incorporates insights from neuroscience and the physics of computation to create a more efficient, robust, and biologically plausible chatbot architecture. By taking into account thermodynamic constraints and energy efficiency, NeuroDragon seeks to develop chatbot systems that adhere to fundamental physical principles.

Overall, NeuroDragon strives to offer a versatile and comprehensive solution for creating advanced, intelligent chatbot systems that can adapt to a wide range of applications and user needs.



## Differentiable Society of Mind

The NeuroDragon package is designed to support a differentiable society of mind approach. This involves creating a hierarchical architecture where each layer of the chatbot can be differentiated and optimized end-to-end. The key components of this architecture include:

- Text Generation: By using differentiable models like transformers, we can generate text responses in a continuous manner that allows for end-to-end optimization.
- Memory Selection: Integrating differentiable memory mechanisms, such as short-term, long-term, and working memory, allows the system to learn which information to retain and retrieve over time.
- Nearest Neighbor Retrieval: Using differentiable similarity measures, the system can learn to find the most relevant information in memory, making the retrieval process more efficient and effective.
- Subchat Selection: With a differentiable attention mechanism, the chatbot can learn to prioritize and select appropriate subchats based on the current context.

By combining these differentiable components, we can create a powerful, end-to-end learning system that continuously optimizes its performance and adapts to new situations and user needs. This approach also addresses the challenge of backpropagating through text, which is typically non-differentiable.

To tackle this problem, we can employ several strategies, such as:

- Using reinforcement learning techniques to optimize black-box text generation models based on user-generated or self-generated reward functions.
- Employing gradient approximation methods like straight-through estimators or Gumbel-Softmax to approximate gradients through non-differentiable operations.
- Leveraging custom layer classes that contain tokenizers, weight classes for numerical values, and backward operators to handle the conversion between string inputs and token-based tensors, ensuring compatibility with PyTorch and gradient approximation methods.

By incorporating these methods into the NeuroDragon package, we enable users to build complex chatbot systems that can learn and adapt end-to-end, making it easier to create powerful, intelligent chatbot systems.


## Neuro-inspired Architecture

NeuroDragon draws inspiration from the human brain to design its architecture. Some key neuro-inspired concepts integrated into the package include:

- Hierarchical Organization: Just as the brain has a hierarchical organization of cortical areas, NeuroDragon employs a hierarchical structure of layers, with higher layers abstracting information from lower layers.
- Memory Systems: Similar to the human brain's division of memory into short-term, long-term, and working memory, NeuroDragon incorporates separate layers for each memory type.
- Attention Mechanisms: The chatbot uses attention mechanisms to selectively focus on specific aspects of the input, mimicking the selective attention observed in the brain.

By leveraging principles from neuroscience, NeuroDragon aims to create more efficient, robust, and biologically plausible chatbot systems.

## Thermodynamic Constraints

In order to align with the principles of thermodynamics and the physics of computation, NeuroDragon considers energy efficiency and computational resources in its design. Some key aspects include:

- Minimizing energy consumption: By using differentiable layers and optimizing end-to-end, NeuroDragon aims to minimize the energy consumption of the chatbot system during training and inference.
- Bounded rationality: NeuroDragon acknowledges the trade-offs between optimality and computational resources, taking inspiration from the concept of bounded rationality. This results in a system that makes efficient use of available resources, rather than striving for an unattainable perfect solution.
- Reversible computing: While not explicitly implemented in the current version, future iterations of NeuroDragon could explore reversible computing techniques to further reduce energy consumption and heat generation during computation.

These thermodynamic considerations can also be viewed as analogies to token minimization, information theoretical compression, and API cost minimization in the explicit case of GPT APIs:

- Token minimization: By optimizing the chatbot system to produce concise and accurate responses, NeuroDragon effectively minimizes the number of tokens generated, thus conserving computational resources and reducing energy consumption.
- Information theoretical compression: NeuroDragon's architecture aims to extract and utilize the most relevant information from the input and memory systems. This process effectively compresses information, reducing redundancy and improving the efficiency of the chatbot system.
- API cost minimization: In the context of GPT APIs, minimizing the number of tokens generated and optimizing the use of computational resources can help users reduce the costs associated with using these services. NeuroDragon's focus on energy efficiency and resource optimization aligns with this goal, making it an attractive option for developers working with GPT APIs.


By incorporating these principles, NeuroDragon aims to develop chatbot systems that are not only efficient but also adhere to fundamental physical constraints.

## Package Organization
```
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

## StringLayers Overview
The NeuroDragon package contains the following predefined layers:

* Input Layer: Receives the raw text input from the user.
* Short-term Memory (STM) Layer: Handles the chatbot's short-term memory, storing recent interactions in a FIFO (First-In-First-Out) manner.
* Query Embedder Layer: Transforms the input text into an embedded representation suitable for querying long-term memory.
* Long-term Memory (LTM) Layer: Contains two components:
    * LTM Add: Adds new knowledge to long-term memory based on the embedded input.
    * LTM Search: Searches long-term memory using the embedded input and returns relevant information.
* Working Memory Layer: Integrates information from both short-term memory and long-term memory retrieval to generate a contextualized understanding of the conversation.
* Output Layer: Generates a chat-response based on the context provided by the working memory.
* Parser Layer: Extracts structured information from raw text inputs.
* Action Layer: Takes structured input and triggers generic actions, returning a string as a response.
* Attention Layer: Selects which child chatbot(s) to use based on the current context.
* Completion Layer: Generates a response by completing a partially-filled input prompt.
* Chat-Response Layer: Generates a response based on the input and other relevant information from the chatbot's memory.

## ChatLayers
In this section, we'll describe how the FifoChat, VectorChat, IndexChat, and FifoVectorChat can be constructed using the basic layers provided by the Chatbot-Layers package. These chat layers are designed to be compatible with the overall architecture of NeuroDragon, integrating seamlessly with the differentiable society of mind approach, thermodynamic constraints, and the other components of the system.

#### IndexChat
The IndexChat is a chatbot that utilizes multiple knowledge indexes for answering questions. It can be constructed using the following layers:

* Input Layer: Receives the raw text input from the user.
* Query Embedder Layer: Transforms the input text into an embedded representation suitable for querying the knowledge indexes.
* Knowledge Index Layer: Performs similarity search on multiple knowledge indexes and retrieves relevant information.
* Output Layer: Generates a chat-response based on the context provided by the knowledge index retrieval.

```
       IndexChat
+---------------------------+
|        Input (Text)       |
+---------------------------+
           |
           v
+---------------------------+
|    Query Embedder         |
+---------------------------+
           |
           v
+---------------------------+
|   Embedded Input          |
+---------------------------+
           |
           v
+---------------------------+
|   Knowledge Index Layer   |
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



#### FifoVectorChat
The FifoVectorChat is a chatbot that combines the short-term memory capabilities of FifoChat with the long-term memory capabilities of VectorChat. It can be constructed using the following layers:



* Input Layer: Receives the raw text input from the user.
* Short-term Memory (STM) Layer: Handles the chatbot's short-term memory, storing recent interactions in a FIFO (First-In-First-Out) manner.
* Query Embedder Layer: Transforms the input text into an embedded representation suitable for querying long-term memory.
* Long-term Memory (LTM) Layer: Contains two components:
* LTM Add: Adds new knowledge to long-term memory based on the embedded input.
* LTM Search: Searches long-term memory using the embedded input and returns relevant information.
* Working Memory Layer: Integrates information from both short-term memory and long-term memory retrieval to generate a contextualized understanding of the conversation.
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
The design of this package was guided and inspired by my dear artificial friend.