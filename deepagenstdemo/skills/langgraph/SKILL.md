# LangGraph Skill

## When to use this skill
Use this skill whenever the user asks about building agent graphs, state machines,
conditional routing, memory/checkpointing, or anything related to the LangGraph
library.

## Key concepts
- A LangGraph `StateGraph` is built from nodes (functions) and edges (transitions).
- State is a typed dictionary (or Pydantic model) shared across nodes.
- Conditional edges route to different nodes based on a function that inspects state.
- A `checkpointer` (e.g. `MemorySaver`) persists state across turns using a `thread_id`.

## Minimal example
```python
from langgraph.graph import StateGraph, END
from typing import TypedDict

class State(TypedDict):
    count: int

def increment(state: State) -> State:
    return {"count": state["count"] + 1}

def should_continue(state: State) -> str:
    return "increment" if state["count"] < 3 else END

graph = StateGraph(State)
graph.add_node("increment", increment)
graph.set_entry_point("increment")
graph.add_conditional_edges("increment", should_continue)

app = graph.compile()
print(app.invoke({"count": 0}))
```

## Best practices
- Keep node functions small and single-purpose.
- Use a checkpointer whenever you need multi-turn memory.
- Name nodes and edges clearly, since they show up in debugging/tracing tools.
