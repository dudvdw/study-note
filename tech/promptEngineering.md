## Prompt Engineering (based on chat-GPT 3.5)

### Principle 1 Write clear and specific instructions

#### Tactic 1: Use delimiters
Triple quotes: “””
Triple blackjacks: ```
Angle brackets: <>

#### Tactic 2: Ask for structured output
HTML, JSON

#### Tactic 3: Check whether conditions are satisfied
Check assumptions required to do the task

#### Tactic 4: Few-shot prompting
Give successful examples of completing tasks
Then ask model to perform the task


### Principle 2 Give the model time to think

#### Tactic 1: Specify the steps to complete a task
Step 1:
Step 2:
…
Step N:…

#### Tactic 2: Instruct the model to work out its own solution before rushing to a conclusion


### Model Limitations

#### Hallucination
Makes statements that sound plausible but are not true

Reducing hallucinations:
First find relevant information
Then answer the question based on the relevant information

### Iterative

1. Idea
2. Implementation
3. Experimental result
4. Error Analysis

### Summarizing

### Inferring

### Transforming

### Expanding
We will be using a parameter of the language model called **temperature**. It allows us to adjust the diversity of the model's response. You can think of temperature as the degree of exploration or randomness in the model.

### Chatbot
