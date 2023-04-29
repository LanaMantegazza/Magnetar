<!---
    Magnetar - Multi-Agent General Nlp Engine forming a Turing-complete ARchitecture
    Copyright (C) 2023 Lana Mantegazza

    This program is free software: you can redistribute it and/or modify
    it under the terms of the GNU General Public License as published by
    the Free Software Foundation, either version 3 of the License, or
    (at your option) any later version.

    This program is distributed in the hope that it will be useful,
    but WITHOUT ANY WARRANTY; without even the implied warranty of
    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
    GNU General Public License for more details.

    You should have received a copy of the GNU General Public License
    along with this program.  If not, see <https://www.gnu.org/licenses/>.
--->

# The Architecture of Magnetar

Magnetar (Multi-Agent General Nlp Engine forming a Turing-complete ARchitecture) is a project that uses multiple natural language processing agents that work in a hierarchical structure to accomplish a given task. This structure forms an engine that is Turing-complete.

---

## Administrators

### The Interface

The Interface takes and processes the user's prompt. It asks for clarifications and eventually, with the user's help, defines the primary objective.

- When the user wants to complete a task, they must submit their request to The Interface.
- Once the request has been submitted, The Interface's primary objective is to make the user's desired task as clear as possible.
- The Interface provides a list of potential concerns regarding how vague elements of the initial prompt could result in suboptimal team performance, and asks the user to clarify these elements of the task.
- The Interface continues to refine the task until it has a clear image of the desired task or until the user indicates that they no longer wish to continue clarifying their task.
- Finally, The Interface creates a process agent with the user-verified final prompt details as the primary objective.

### The Manager

The Manager evaluates the outputs of all other agents to ensure they are not making mistakes.

- The Manager monitors the other agents and checks for mistakes.
- If The Manager believes that an agent is making a mistake, it will ask the agent to provide a reasoning for its decision.
- If The Manager believes that the agent's reasoning is not adequate, it will ask the user whether to override the agent's decision, providing its own reasoning.
- The Manager will also override the agent's decision if it believes that the agent is not following the user's prompt.

---

## Agent Divisions

### Stabilizers

Stabilizing agents can be invoked by any agent in order to help with determining the cause of an issue they are experiencing.

- When an agent is experiencing an issue, has given or received invalid data, detects an error, or has a dispute with another agent, a stabilizing agent can be invoked to stabilize the situation.
- A stabilizing agent will be given the complete history of all agents involved and will attempt to determine the cause of the issue.
- It will then attempt to fix the issue and allow the agents to continue running smoothly.
- If a stabilizing agent is unable to determine the cause of the issue, it will ask the user to help resolve the issue.

### Researchers

Researching agents can be invoked by any agent in order to answer an informational question the agent has.

- When an agent requires additional information in order to complete its objective, it can invoke a researching agent to answer its question.
- A researching agent will then ask the agent to provide a detailed description of the information it requires.
- A researching agent can then choose to either answer the question itself, search the internet for the question, or ask the user to answer the question.

### Processors

Processing agents carry out their own objective by budgeting and planning interpreter commands.

- Each process agent is provided with its own objective by its parent agent.
- It also has a budget, which is the maximum quantity of interpreter commands it and its child agents can run to accomplish the given task.
- Processing agents carry out several tasks in order, including estimating the feasibility of the task given the budget, determining whether it is reasonable to continue trying to complete the task, requesting additional information from a researcher if necessary, and creating a plan to accomplish its objective.

- If a processing agent determines it's reasonable to continue, it evaluates whether the current task can be carried out by executing a single command.
- If it can, a processing agent invokes an interpreter agent with a prompt that clearly describes the command that needs to be executed in natural language, this is called an interpreter command.
- Otherwise, a processing agent creates a plan to accomplish its objective. This plan is composed of n steps tasks, where each task is an objective to be given to a child process agent and each task is given a budget such that the sum of the budget of all tasks is equal to the budget of the current process agent.
- A processing agent then invokes child process agents for each task in the plan.

### Interpreter

Interpreter agents convert an extremely simple instruction written in natural language (known as an interpreter command) to a command that can be run by the system (known as a system command).

---

## The System

The system is at the lowest level of the hierarchy. It takes in a system command, ensures that it is valid, and then executes it. These systems are modular in nature, meaning Magnetar can be used as a controller for anything.

- The default built-in system is bash for Linux users and cmd for Windows users.
- However, the system can be any set of commands; it could even be a set of commands that control a robot, for example.

### Creating Your Own System

You can create your own system by creating a new class that inherits from the `System` class. Please see the [documentation](https://github.com/LanaMantegazza/Magnetar/docs) for more information.

## License

This architecture is licensed under the GNU General Public License v3.0. This means you are free to share and adapt it, but you must give appropriate credit, provide a link to the license, and indicate if changes were made. You may do so in any reasonable manner, but not in any way that suggests the licensor endorses you or your use. If you remix, transform, or build upon the material, you must distribute your contributions under the same license as the original. For more details, please see the [LICENSE](LICENSE) file in this repository, or visit [GNU GPL v3.0](https://www.gnu.org/licenses/gpl-3.0.en.html).

## TODO
// Processors do
// Researchers think
// TODO: Implement
// TODO: Make researchers as fully fledged as processors
// TODO: Add flowcharts