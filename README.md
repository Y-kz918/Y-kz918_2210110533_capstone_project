## Title: Trip PLanner using Langgraph

## Overview

For this project, I built a structured travel assistant that helps users plan a trip in stages. Instead of generating a generic itinerary all at once, this application finds flight options first, pauses to let the user choose and then plans activities based on that specific flight.
It uses the LangGraph framework to split the logic into two separate "sub-teams" (one for flights, one for activities) and manages the data flow between them using a shared state.

## Reason for picking up this project

I chose this project to apply the concepts from Modules 1–4, specifically focusing on architecture and control.

Through this project, I practiced:
**Sub-graphs** (Module 4): Learning how to isolate logic by building smaller graphs (`flight_graph` and `activity_graph`) and using them inside a larger parent graph.

**Data Flow** (Module 2): Understanding how to pass data from a global "Parent State" to a local "Child State" and back again.

**Human-in-the-Loop** (Module 3): This was my main learning goal. I wanted to implement a real "breakpoint" where the code stops and waits for human input, rather than just running automatically from start to finish.

## Plan

I plan to excecute these steps to complete my project.

- [DONE] Step 1: Set up the environment and initialize the `ChatGroq` model (Llama 3.1) to ensure fast, open-source inference.
- [DONE] Step 2: Define the State Schemas. I will create a main `TripState` for the overall plan, and separate `FlightState` and `ActivityState` for the specific sub-tasks.
- [DONE] Step 3: Build and compile the Flight Scout Sub-graph. This involves creating the specific nodes to simulate searching for flights and processing the results into a clean list.
- [DONE] Step 4: Build and compile the Activity Planner Sub-graph. This involves creating logic that generates an itinerary specifically based on the arrival time of the selected flight.
- [DONE] Step 5: Construct the Parent Graph. I will create wrapper nodes that handle the input/output mapping to connect the global state to the sub-graphs.
- [DONE] Step 6: Compile the final graph with Memory and Interrupts. I will configure the graph to explicitly pause (`interrupt_before`) right before the activity planning step.
- [DONE] Step 7: Implement the execution and interactive loop. I will run the graph, catch the pause, ask the user to select a flight via `input()`, and use `graph.update_state()` to save their choice before resuming.
- [DONE] Step 8: I observed and validated the working and execution of all states in the Graph in LangSmith Traces.

## Conclusion:

I had planned to achieve a workflow where the AI and the user work together, I think I have achieved the conclusion satisfactorily.

The project works as intended. The agent successfully hands off tasks to the sub-graphs, and the interrupt mechanism functions correctly. When I tested it, I was able to manually select "Flight C," and the Activity Planner correctly recognized the new arrival time and adjusted the plan accordingly. I even observed the dataflow on LangSmith Traces. This confirmed that I successfully implemented the idea.

Here is the video explanation of the project: https://drive.google.com/file/d/1Vr4eLaaAGl4nA6Wjh73S_YnESvJnKz9X/view?usp=drivesdk
