<H1 align="center">An Agent: Introduction</H1>

### 1. Introduction

Welcome to the **Introduction Of Agents**, where we will **build a solid foundation in the fundamentals of AI Agents** including:

- **Understanding Agents**
  - What is an Agent, and how does it work?
  - How do Agents make decision using reasoning and planning?

- **Role of LLMs (Large Language Models) in Agents**
  - How LLMs serve as the "brain" behind an agent.
  - How LLMs structure conversation via the Messages system.

- **Tools and Actions**
  - How Agents use external tools to interact with the environment.
  - How to build and integrate tools for the Agent.

- **The Agent workflow**
  - Think $\rightarrow$ Act $\rightarrow$ Observe

### 2. What is an Agent?

> _"An Agent is a system that leverages an AI model to interact with its environment in order to achieve a user-defined objective. It combines reasoning, planning and execution of actions (often via external tools) to fulfill tasks"_

An Agent can be visualized as bellow:

```
             (Cortex: AI Model)
                  * Thinking *
                  * Planning *
                   ---------
                 /           \
(Arms & Tools) -               - (Legs & Tools)
 |   Execute  |                 |  Act         |
 \                                   /
  ----------> Environment <----------
```

| Component                             | Description                                                                                                                                   |
|---------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| **The Brain (AI Model)**              | This is where all the thinking happens. The AI model handles reasoning and planning. It decides which Actions to take based on the situation. |
| **The Body (Capabilities and Tools)** | This part represents everything the Agent is equipped to do.                                                                                  |

The scope of possible actions depends on what the agent has been equipped with. For example, because humans lack wings, they can’t perform the “fly” Action, but they can execute Actions like “walk”, “run” ,“jump”, “grab”, and so on.

#### 2.1 The Spectrum of "Agency"

Following this definition, Agents exist on a continuous spectrum of increasing agency:

| Agency Level | Description                                              | What that's called | Example pattern                                    |
|--------------|----------------------------------------------------------|--------------------|----------------------------------------------------|
| ☆☆☆          | Agent output has no impact on program flow               | Simple processor   | `process_llm_output(llm_response)`                 |
| ★☆☆          | Agent output determines basic control flow               | Router             | `if llm_decision(): path_a() else: path_b()`       |
| ★★☆          | Agent output determines function execution               | Tool caller        | `run_function(llm_chosen_tool, llm_chosen_args)`   |
| ★★★          | Agent output controls iteration and program continuation | Multi-step Agent   | `while llm_should_continue(): execute_next_step()` |
| ★★★          | One agentic workflow can start another agentic workflow  | Multi-Agent        | `if llm_trigger(): execute_agent()`                |

#### 2.2 Type of AI models we use for Agents.

The most common AI model found in Agents is an LLM (Large Language Model), which takes Text as an input and outputs Text as well.
Well known examples are **GPT4 from OpenAI, LLama from Meta, Gemini from Google**, etc.

> _It's also possible to use models that accept other inputs as the Agent's core model. For example, a Vision Language Model (VLM), which is like an LLM but also understands images as input. We'll focus on LLMs for now and will discuss other options later._

#### 2.3 Type of tasks Agent cam perform.

An Agent perform any task we implement vai **Tool** to complete action.

For example, if I write an Agent to act as my personal assistant (like Siri) on my computer, and I ask it to “send an email to my Manager asking to delay today’s meeting”, I can give it some code to send emails. This will be a new Tool the Agent can use whenever it needs to send an email. We can write it in Python:

```python
def send_message_to(recipient, message):
    """Useful to send an e-mail message to a recipient"""
    ...
```

The LLM, as we’ll see, will generate code to run the tool when it needs to, and thus fulfill the desired task.

```python
send_message_to("Manager", "Can we postpone today's meeting?")
```

The design of the **Tools is very important and has a great impact on the quality of your Agent**. Some tasks will require very specific Tools to be crafted, while others may be solved with general purpose tools like “web_search”.

> "Note that Actions are not the same as Tools. An Action, for instance, can involve the use of multiple Tools to complete."

Allowing an agent to interact with its environment allows real-life usage for companies and individuals.

##### Example 1: Personal Virtual Assistant

They act as agents by interpreting user requests, retrieving data, and performing tasks in a digital environment.

| Agent Example    | Typical Tasks                      |
|------------------|------------------------------------|
| Siri             | Sets alarms, sends texts           |
| Alexa            | Plays music, controls lights       |
| Google Assistant | Manages reminders, answers queries |

These assist by performing context-based actions, showcasing how agents can automate daily tasks.

##### Example 2: Customer Service Chatbots

They interpret queries, guide resolution steps, record issues, and handle transactions.

| Tasks           | Capabilities                 |
|-----------------|------------------------------|
| FAQs            | Provides quick answers       |
| Troubleshooting | Suggests problem resolutions |
| Issue Logging   | Opens support tickets        |

Their predefined objectives might include improving user satisfaction, reducing wait times, or increasing sales conversion rates. By interacting directly with customers, learning from the dialogues, and adapting their responses over time, they demonstrate the core principles of an agent in action.

##### Example 3: AI NPCs in Games

They adapt behavior in real time, generating situational dialogue and actions for immersive experiences.

| Feature            | Benefit                         |
|--------------------|---------------------------------|
| Evolving dialogue  | More human-like interactions    |
| Flexible responses | Greater engagement with players |

#### 2.4 Summary

To summarize, an Agent is a system that uses an AI Model (typically an LLM) as its core reasoning engine, to:

- **Understand natural language:** interpret and respond to human instructions.  
- **Reason and plan:** analyze information, make decisions, and devise strategies.  
- **Interact with its environment:** gather information, take actions, and observe the results.

----

### Quiz

#### Q1: What is an Agent?

**Which of the following best describes an AI Agent?**

- [x] An AI model that can reason, plan, and use tools to interact with its environment to achieve a specific goal.  
  <sub>Correct! This definition captures the essential characteristics of an Agent.</sub>
- [ ] A system that solely processes static text, without any inherent mechanism to interact dynamically with its surroundings or execute meaningful actions.
- [ ] A conversational agent restricted to answering queries, lacking the ability to perform any actions or interact with external systems.
- [ ] An online repository of information that offers static content without the capability to execute tasks or interact actively with users.

#### Q2: What is the Role of Planning in an Agent?

**Why does an Agent need to plan before taking an action?**

- [ ] To primarily store or recall past interactions, rather than mapping out a sequence of future actions.
- [x] To decide on the sequence of actions and select appropriate tools needed to fulfill the user’s request.  
  <sub>Correct! Planning helps the Agent determine the best steps and tools to complete a task.</sub>
- [ ] To execute a sequence of arbitrary and uncoordinated actions that lack any defined strategy or intentional objective.
- [ ] To merely convert or translate text, bypassing any process of formulating a deliberate sequence of actions or employing strategic reasoning.

#### Q3: How Do Tools Enhance an Agent’s Capabilities?

**Why are tools essential for an Agent?**

- [ ] Tools serve no real purpose and do not contribute to the Agent’s ability to perform actions beyond basic text generation.
- [ ] Tools are solely designed for memory storage, lacking any capacity to facilitate the execution of tasks or enhance interactive performance.
- [ ] Tools severely restrict the Agent exclusively to generating text, thereby preventing it from engaging in a broader range of interactive actions.
- [x] Tools provide the Agent with the ability to execute actions a text-generation model cannot perform natively, such as making coffee or generating images.  
  <sub>Correct! Tools enable Agents to interact with the real world and complete tasks.</sub>

#### Q4: How Do Actions Differ from Tools?

**What is the key difference between Actions and Tools?**

- [x] Actions are the steps the Agent takes, while Tools are external resources the Agent can use to perform those actions.  
  <sub>Correct! Actions are higher-level objectives, while Tools are specific functions the Agent can call upon.</sub>
- [ ] Actions and Tools are entirely identical components that can be used interchangeably, with no clear differences between them.
- [ ] Tools are considered broad utilities available for various functions, whereas Actions are mistakenly thought to be restricted only to physical interactions.
- [ ] Actions inherently require the use of LLMs to be determined and executed, whereas Tools are designed to function autonomously without such dependencies.

#### Q5: What Role Do Large Language Models (LLMs) Play in Agents?

**How do LLMs contribute to an Agent’s functionality?**

- [ ] LLMs function merely as passive repositories that store information, lacking any capability to actively process input or produce dynamic responses.
- [x] LLMs serve as the reasoning 'brain' of the Agent, processing text inputs to understand instructions and plan actions.  
  <sub>Correct! LLMs enable the Agent to interpret, plan, and decide on the next steps.</sub>
- [ ] LLMs are erroneously believed to be used solely for image processing, when in fact their primary function is to process and generate text.
- [ ] LLMs are considered completely irrelevant to the operation of AI Agents, implying that they are entirely superfluous in any practical application.

#### Q6: Which of the Following Best Demonstrates an AI Agent?

**Which real-world example best illustrates an AI Agent at work?**

- [ ] A static FAQ page on a website that provides fixed information and lacks any interactive or dynamic response capabilities.
- [ ] A simple calculator that performs arithmetic operations based on fixed rules, without any capability for reasoning or planning.
- [x] A virtual assistant like Siri or Alexa that can understand spoken commands, reason through them, and perform tasks like setting reminders or sending messages.  
  <sub>Correct! This example includes reasoning, planning, and interaction with the environment.</sub>
- [ ] A video game NPC that operates on a fixed script of responses, without the ability to reason, plan, or use external tools.
