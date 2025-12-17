# Reliable Agents: A Control-Theoretic Perspective

A curated collection of resources for building reliable AI agents through control theory, formal verification, planning, and formal languages. Rather than focusing on implementation patterns, this guide emphasizes the mathematical and systems-engineering foundations for agent reliability.

## Table of Contents
- [Getting Started: Architect's Core](#getting-started-architects-core)
- [Control Theory: The "Physics" of Reliability](#control-theory-the-physics-of-reliability)
- [Planning and Decision Theory](#planning-and-decision-theory)
- [Formal Verification and Safety](#formal-verification-and-safety)
- [Formal Languages and Constrained Generation](#formal-languages-and-constrained-generation)
- [Neuro-Symbolic and Constrained Decoding](#neuro-symbolic-and-constrained-decoding)
- [Hierarchical Planning and Self-Correction](#hierarchical-planning-and-self-correction)
- [Foundational Texts](#foundational-texts)
- [Modern Agent Research](#modern-agent-research)
- [Learning Theory and Alignment](#learning-theory-and-alignment)
- [Systems Thinking and Distributed Systems](#systems-thinking-and-distributed-systems)
- [Advanced Topics](#advanced-topics)

---

## Getting Started: Architect's Core

Resources for immediate practical application in building reliable agents.

### Industry Best Practices
- **[Google Agent Whitepapers](https://deepmind.google/)**
  - **Agent Tools & Interoperability**: Understanding MCP (Model Context Protocol) and tool definitions
  - **Context Engineering**: Sessions and memory management
  - **Agent Quality**: Evaluation and reliability metrics
  - **Prototype to Production**: Scaling considerations

### Core AI Textbook
- **"Artificial Intelligence: A Modern Approach" (AIMA)** by Stuart Russell and Peter Norvig ([website](http://aima.cs.berkeley.edu/))
  
  **Focus chapters:**
  - **Chapter 3: Solving Problems by Searching** - State-space search fundamentals
  - **Chapters 10 & 11: Classical Planning** - Agent planning with STRIPS and PDDL
  - **Chapters 16 & 17: Utility Theory & MDPs** - Decision-making under uncertainty

### Learning from Human Feedback
- **["The RLHF Book"](https://rlhfbook.com/)** by Nathan Lambert et al.
  
  **Focus chapters:**
  - **Chapter 7: Reward Modeling** - Building simulators and evaluation functions
  - **Chapter 9: Preference Data** - Collecting data from agent successes and failures
  - **Chapter 8: Advanced RL** - PPO/DPO concepts for preference learning

---

## Control Theory: The "Physics" of Reliability

Understanding agents as dynamical systems opens up powerful analytical tools from control theory.

### Videos and Tutorials
- **[Brian Douglas - Control Systems Lectures](https://www.youtube.com/user/ControlLectures)** 🎥  
  Covers feedback control, stability analysis, and state-space methods for maintaining agent behavior within safe boundaries.
  
  **Recommended**: Start with the first 2 videos on Classical Control Theory.

### Books
- **["Engineering a Safer World: Systems Thinking Applied to Safety"](https://mitpress.mit.edu/9780262533690/engineering-a-safer-world/)** by Nancy Leveson  
  Introduces STAMP (System-Theoretic Accident Model and Processes). Moves beyond component-level failures to interaction failures in complex systems.

- **"Feedback Control of Dynamic Systems"** by Franklin, Powell, and Emami-Naeini  
  Classic textbook on closed-loop control fundamentals for reliable system design.

- **["How Complex Systems Fail"](https://how.complexsystems.fail/)** by Richard Cook  
  A 4-page paper on the philosophy of failure in complex systems.
  
  **Key insight**: Failure results from complex interactions, not single root causes.

### Key Concepts
- **Stability**: Lyapunov stability, BIBO stability
- **Observability and Controllability**: Can you see what's happening? Can you influence it?
- **Robust Control**: Designing agents that work despite uncertainty
- **Feedback Loops**: The foundation of adaptive, self-correcting systems

---

## Planning and Decision Theory

Reliable agents need principled approaches to sequential decision-making under uncertainty.

### Foundational Resources
- **"Artificial Intelligence: A Modern Approach" (AIMA)** by Stuart Russell and Peter Norvig ([website](http://aima.cs.berkeley.edu/))  
  Chapters on planning (classical, conditional, continuous), MDPs, POMDPs, and decision theory.

- **"Decision Making Under Uncertainty: Theory and Application"** by Mykel Kochenderfer  
  Covers MDPs, POMDPs, and reinforcement learning for real-world applications.

### Planning Paradigms
- **Classical Planning**: STRIPS, PDDL, GraphPlan
- **Hierarchical Planning**: HTN (Hierarchical Task Networks)
- **Temporal Planning**: Dealing with time and concurrency
- **Probabilistic Planning**: POMDPs, online planning, Monte Carlo Tree Search

---

## Formal Verification and Safety

How do we *prove* that agents will behave correctly?

### Video Resources
- **[Computerphile - Formal Verification & Logic](https://www.youtube.com/user/Computerphile)** 🎥  
  Expert interviews visualizing formal verification concepts.
  
  **Essential videos:**
  - **"Software Testing vs. Formal Verification"** - Why testing alone is insufficient.
  - **"The Halting Problem"** - Why we can't exhaustively verify all programs.
  - **"Z3 Theorem Prover"** - Introduction to SMT solvers.

### Formal Methods
- **Model Checking**: Verify properties of finite-state systems
  - Tools: SPIN, NuSMV, TLA+
  - Temporal logics: LTL, CTL, CTL*

- **Theorem Proving**: Interactive proof assistants
  - Coq, Isabelle/HOL, Lean
  - Verified software: CompCert, seL4

### Safety Specifications
- **Linear Temporal Logic (LTL)**: "Always eventually respond" □◇φ
- **Signal Temporal Logic (STL)**: Real-valued semantics for continuous systems
- **Contracts and Assertions**: Pre/post conditions, invariants

### Resources
- **"Principles of Model Checking"** by Christel Baier and Joost-Pieter Katoen  
  Comprehensive textbook on temporal logics, model checking algorithms, and verification techniques.

- **["Practical TLA+"](https://lamport.azurewebsites.net/tla/book.html)** by Hillel Wayne  
  TLA+ (Temporal Logic of Actions) helps find concurrency bugs and architectural flaws during design. Written about a language by Leslie Lamport (Turing Award winner).

- **[TLA+ Video Course](https://lamport.azurewebsites.net/video/videos.html)** by Leslie Lamport 🎥  
  Quirky lectures using concrete examples (like "Die Hard" water jug puzzles) focused on thinking over syntax.
  
  **Key insight**: TLA+ models the "physics" of your system to identify if failures are possible.
  
  **Start here**: Lectures 1-4 for understanding system state and modeling distributed agent interactions.

---

## Neuro-Symbolic and Constrained Decoding

Ensuring deterministic outputs from non-deterministic models through formal constraints.

### Key Papers
- **["Efficient Guided Generation for Large Language Models"](https://arxiv.org/abs/2307.09702)** by Willard & Louf (2023)  
  Foundational work behind the Guidance library. Shows constraining during inference is superior to rejection sampling.

- **["Synchromesh: Reliable Code Generation from Pre-trained Language Models"](https://arxiv.org/abs/2201.11227)** by Poesia et al. (2022)  
  Introduces "Target Similarity Tuning" and "Constrained Semantic Decoding" for reliable code generation.

### Formal Language Theory
- **"Introduction to the Theory of Computation"** by Michael Sipser  
  Classic textbook on the mathematical foundations of computation.
  
  **Focus:**
  - **Chapter 1: Regular Languages** - Mathematics behind regex and finite automata
  - **Chapter 2: Context-Free Languages** - Mathematics behind parsers and stack machines

- **[Easy Theory - Theory of Computation](https://www.youtube.com/@easytheory)** 🎥  
  Visual guide using digital whiteboard to draw Finite State Machines and explain logic.
  
  **Essential playlist**: "Theory of Computation"
  - Videos on **DFA** (Deterministic Finite Automata).
  - Videos on **Context-Free Grammars**.

### SMT Solvers and Symbolic Execution
- **["Programming Z3"](https://theory.stanford.edu/~nikolaj/programmingz3.html)** (SMT Solver Tutorial)  
  Z3 is an SMT (Satisfiability Modulo Theories) solver from Microsoft Research for determining logical satisfiability.
  
  **Try**: Python bindings (`z3-solver`).

- **[Guided Hacking - Z3 Explained](https://www.youtube.com/watch?v=56IIrBZy9Rc)** 🎥  
  Practical introduction to Z3 as a tool for solving logic puzzles and turning constraints into Python code.

---

## Hierarchical Planning and Self-Correction

Feedback loops and skill libraries for agent architectures.

### Self-Correcting Agents
- **["Reflexion: Language Agents with Verbal Reinforcement Learning"](https://arxiv.org/abs/2303.11366)** by Shinn et al. (2023)  
  Agents that examine error logs and update short-term memory to avoid repeating mistakes.

### Skill Library Evolution
- **["Voyager: An Open-Ended Embodied Agent with Large Language Models"](https://arxiv.org/abs/2305.16291)** by Wang et al. (2023)  
  Demonstrates skill library evolution where agents write, verify, and store code for future retrieval.

---

## Formal Languages and Constrained Generation

Ensuring agents produce valid, safe outputs through formal grammars and constrained decoding.

### Tools
- **[Guidance](https://github.com/guidance-ai/guidance)**: Interleaved generation and control
- **[Outlines](https://github.com/outlines-dev/outlines)**: Structured text generation
- **[LMQL](https://lmql.ai/)**: SQL-like language for LLM interaction

---

## Foundational Texts

Core academic resources for theoretical foundations.

### Artificial Intelligence
- **"Artificial Intelligence: A Modern Approach"** by Russell & Norvig ([website](http://aima.cs.berkeley.edu/))  
  Comprehensive AI textbook covering search, logic, planning, and learning.

### Reinforcement Learning
- **["Reinforcement Learning: An Introduction"](http://incompleteideas.net/book/the-book-2nd.html)** by Sutton & Barto  
  Covers MDPs, value functions, policy gradients, and exploration.

### Probabilistic Reasoning
- **"Probabilistic Graphical Models"** by Daphne Koller and Nir Friedman  
  Bayesian networks, Markov networks, and inference algorithms.

- **["Pattern Recognition and Machine Learning"](https://www.microsoft.com/en-us/research/publication/pattern-recognition-machine-learning/)** by Christopher Bishop  
  Probabilistic models and machine learning fundamentals.

---

## Modern Agent Research

Contemporary research on building capable, reliable agents.

### Key Papers
- **["ReAct: Synergizing Reasoning and Acting in Language Models"](https://arxiv.org/abs/2210.03629)** by Yao et al. (2022)  
  Interleaving reasoning traces with action steps.

- **["Toolformer: Language Models Can Teach Themselves to Use Tools"](https://arxiv.org/abs/2302.04761)** by Schick et al. (2023)  
  Self-supervised learning for tool use.

### Agent Architectures
- **ReAct**: Reason + Act in interleaved manner
- **Reflection**: Self-critique and iterative improvement (see Reflexion above)
- **Tree-of-Thought**: Exploring reasoning paths as trees
- **Multi-Agent Systems**: Cooperation and competition

---

## Systems Thinking and Distributed Systems

Reliability, scalability, and failure modes in production systems.

### Distributed Systems Reliability
- **["Designing Data-Intensive Applications"](https://dataintensive.net/)** by Martin Kleppmann  
  Modern systems reliability covering replication, partitioning, consistency, and consensus.
  
  **Focus**: Chapters 5-9

- **[Jepsen: Distributed Systems Safety Research](https://jepsen.io/)** by Kyle Kingsbury  
  Testing popular databases (MongoDB, Postgres, Kafka) under network partitions to verify data safety guarantees.

### System Failure Philosophy  
- **["How Complex Systems Fail"](https://how.complexsystems.fail/)** by Richard Cook  
  4-page paper on failure philosophy (also in Control Theory section).

---

## Learning Theory and Alignment

Agent learning and alignment with intended objectives.

### Core Resources
- **["The RLHF Book"](https://rlhfbook.com/)** by Nathan Lambert et al.  
  Reinforcement Learning from Human Feedback, covering reward modeling, preference learning, and alignment.

### Alignment and Safety
- **["Concrete Problems in AI Safety"](https://arxiv.org/abs/1606.06565)** by Amodei et al. (2016)  
  Key safety challenges: negative side effects, reward hacking, scalable oversight, safe exploration, robustness.

- **["Specification Gaming: The Flip Side of AI Ingenuity"](https://deepmind.google/discover/blog/specification-gaming-the-flip-side-of-ai-ingenuity/)** by DeepMind (2020)  
  Examples of AI systems exploiting reward specification loopholes.

### Key Concepts
- **Reward Modeling**: Learning human preferences
- **Inverse Reinforcement Learning**: Inferring objectives from behavior
- **Scalable Oversight**: Ensuring good behavior as capabilities grow
- **Interpretability**: Understanding what agents are doing and why

---

## Advanced Topics

Long-term research directions (6-12 months out).

### World Models and Predictive Architectures
- **["A Path Towards Autonomous Machine Intelligence"](https://openreview.net/forum?id=BZ5a1r-kVsf)** by Yann LeCun (2022)  
  Position paper on Joint Embedding Predictive Architectures (JEPA) for world models.

### Planning with Language Models
- **["Chain of Hindsight Aligns Language Models with Feedback"](https://arxiv.org/abs/2302.02676)** by Liu et al. (2023)  
  Learning from feedback sequences to improve planning.
  
- **["Tree of Thoughts: Deliberate Problem Solving with Large Language Models"](https://arxiv.org/abs/2305.10601)** by Yao et al. (2023)  
  Exploring reasoning paths as trees for complex problem solving.

---

## Contributing

This is a living document. Contributions of resources on control theory, formal methods, planning, or formal languages applied to AI agents are welcome.

---

## Philosophy

Building reliable agents requires more than prompt engineering and fine-tuning. We need:
- **Mathematical rigor** from control theory and formal methods
- **Principled planning** from decision theory and AI planning
- **Safety guarantees** from formal verification
- **Structured outputs** from formal language theory
- **Alignment** from learning theory and human feedback

This collection focuses on these deeper foundations rather than surface-level implementation details.

---

## License

This collection is provided under the MIT License. See LICENSE for details.
