# Reliable Agents: A Control-Theoretic Perspective

A curated collection of resources for building reliable AI agents through the lens of control theory, formal verification, planning, and formal languages. This is not your typical agent-building guide—instead, we focus on the mathematical and systems-engineering foundations that make agents truly reliable.

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

Essential resources for immediate utility in building reliable agents. Start here to understand industry baselines and fundamental approaches.

### Industry Best Practices
- **[Google Agent Whitepapers](https://deepmind.google/)**
  - **Agent Tools & Interoperability**: Understanding MCP (Model Context Protocol) and tool definitions
  - **Context Engineering**: Sessions and memory management
  - **Agent Quality**: Evaluation and reliability metrics
  - **Prototype to Production**: Scaling considerations
  
  **Goal**: Understand the industry baseline to know what you're improving upon.

### Core AI Textbook
- **"Artificial Intelligence: A Modern Approach" (AIMA) by Stuart Russell and Peter Norvig** [AIMA Website](http://aima.cs.berkeley.edu/)
  
  **Focus chapters:**
  - **Chapter 3: Solving Problems by Searching** - The basis of "reasoning" through state-space search
  - **Chapters 10 & 11: Classical Planning** - The foundation of agent plans (STRIPS, PDDL)
  - **Chapters 16 & 17: Utility Theory & MDPs** - How agents make decisions under uncertainty
  
  **Goal**: Replace "prompt engineering" with principled state-space search and planning.

### Learning from Human Feedback
- **"The RLHF Book" by Nathan Lambert et al.** [RLHF Book](https://rlhfbook.com/)
  
  **Focus chapters:**
  - **Chapter 7: Reward Modeling** - Crucial for building simulators and evaluation functions
  - **Chapter 9: Preference Data** - Collecting data from agent successes and failures
  - **Chapter 8: Advanced RL** - PPO/DPO concepts for preference learning
  
  **Goal**: Understand how to teach an agent to prefer valid plans over invalid ones.

---

## Control Theory: The "Physics" of Reliability

Understanding agents as dynamical systems opens up powerful analytical tools from control theory.

### Videos and Tutorials
- **[Brian Douglas - Control Systems Lectures (YouTube)](https://www.youtube.com/user/ControlLectures)** 🎥  
  Exceptional series covering feedback control, stability analysis, and state-space methods. Essential for understanding how to maintain agent behavior within safe boundaries.
  
  **Recommended**: Start with the first 2 videos on Classical Control Theory to grasp the fundamentals of feedback loops and stability.

### Books
- **"Engineering a Safer World: Systems Thinking Applied to Safety" by Nancy Leveson**  
  Introduces STAMP (System-Theoretic Accident Model and Processes). Critical reading for understanding how complex systems fail and how to design safety constraints. This moves beyond "component failure" (the LLM hallucinated) to "interaction failure" (the system allowed the hallucination to crash the DB). [MIT Press](https://mitpress.mit.edu/9780262533690/engineering-a-safer-world/)

- **"Feedback Control of Dynamic Systems" by Franklin, Powell, and Emami-Naeini**  
  Classic textbook for understanding closed-loop control, which is fundamental to reliable agent design.

- **"How Complex Systems Fail" by Richard Cook**  
  A short 4-page paper from the medical domain on the philosophy of failure. Key insight: "Failure is not a root cause; it is a consequence of complex interactions." Essential reading for understanding why "user error" is a myth.

### Key Concepts
- **Stability**: Lyapunov stability, BIBO stability
- **Observability and Controllability**: Can you see what's happening? Can you influence it?
- **Robust Control**: Designing agents that work despite uncertainty
- **Feedback Loops**: The foundation of adaptive, self-correcting systems

---

## Planning and Decision Theory

Reliable agents need principled approaches to sequential decision-making under uncertainty.

### Foundational Resources
- **"Artificial Intelligence: A Modern Approach" (AIMA) by Stuart Russell and Peter Norvig**  
  Chapters on planning (classical, conditional, continuous), MDPs, POMDPs, and decision theory. The definitive reference. [AIMA Website](http://aima.cs.berkeley.edu/)

- **"Decision Making Under Uncertainty: Theory and Application" by Mykel Kochenderfer**  
  Covers MDPs, POMDPs, and reinforcement learning with a focus on real-world applications.

### Planning Paradigms
- **Classical Planning**: STRIPS, PDDL, GraphPlan
- **Hierarchical Planning**: HTN (Hierarchical Task Networks)
- **Temporal Planning**: Dealing with time and concurrency
- **Probabilistic Planning**: POMDPs, online planning, Monte Carlo Tree Search

---

## Formal Verification and Safety

How do we *prove* that agents will behave correctly?

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
- **"Principles of Model Checking" by Christel Baier and Joost-Pieter Katoen**  
  Comprehensive textbook covering temporal logics, model checking algorithms, and verification techniques.

- **"Practical TLA+" by Hillel Wayne**  
  TLA+ (Temporal Logic of Actions) is a language for modeling systems to find concurrency bugs and architectural flaws in the design phase. Written by Leslie Lamport (Turing Award winner). Read the first half and apply it to simple agent protocols.
  
  **The moat**: Most architects guess how their distributed agents will interact. With TLA+, you can model interactions, run the model checker, and find the exact sequence that causes failures.

- **[TLA+ Video Course by Leslie Lamport](https://lamport.azurewebsites.net/video/videos.html)**  
  Learn TLA+ (Temporal Logic of Actions) from its creator for specifying and verifying concurrent and distributed systems.

---

## Neuro-Symbolic and Constrained Decoding

The "compiler layer" for reliable code generation - ensuring deterministic outputs from non-deterministic models.

### Key Papers
- **"Efficient Guided Generation for Large Language Models"** (The Guidance Paper) by Willard & Louf (2023)  
  The foundational Microsoft Research paper behind the Guidance library. Proves that constraining the model during inference (not after) is mathematically superior to rejection sampling. Explains the "prefix matching" algorithm you need to understand. [Guidance Library](https://github.com/guidance-ai/guidance)

- **"Synchromesh: Reliable Code Generation from Pre-trained Language Models"** by Poesia et al. (2022)  
  A simpler, more readable introduction to constrained decoding. Introduces "Target Similarity Tuning" and "Constrained Semantic Decoding." Academic proof that you can force a non-deterministic model to output deterministic code 100% of the time.

### Formal Language Theory
- **"Introduction to the Theory of Computation" by Michael Sipser**  
  The classic CS textbook on the mathematical foundations of computation.
  
  **Focus:**
  - **Chapter 1: Regular Languages** - The math behind Regex and Outlines
  - **Chapter 2: Context-Free Languages** - The math behind parsers and stack machines
  
  Skip the complexity theory (P vs NP) unless you enjoy the mathematics.

### SMT Solvers and Symbolic Execution
- **"Programming Z3"** (SMT Solver Tutorial)  
  Z3 is a "theorem prover" from Microsoft Research. State a logic problem (e.g., "Is there any input X that crashes this function?"), and it finds the answer. This is the engine behind symbolic execution and modern verification - the "reasoning engine" for code.
  
  **Action**: Try the Python bindings (`z3-solver`). It feels like magic.

---

## Hierarchical Planning and Self-Correction

Adding feedback loops and skill libraries to agent architectures - the "manager layer."

### Self-Correcting Agents
- **"Reflexion: Language Agents with Verbal Reinforcement Learning"** by Shinn et al. (2023)  
  Instead of just planning, this paper adds self-correction. Connects control theory (feedback loops) with agents - showing how an agent can examine its own error logs and update short-term memory to avoid repeating mistakes.

### Skill Library Evolution
- **"Voyager: An Open-Ended Embodied Agent with Large Language Models"** by Wang et al. (2023)  
  A Minecraft agent paper that demonstrates "skill library evolution." The agent writes code, verifies it works, and saves it to a permanent library for future retrieval. The blueprint for agents that get smarter over time through experience accumulation.

---

## Formal Languages and Constrained Generation

Ensuring agents produce valid, safe outputs through formal grammars and constrained decoding.

### Tools
- **[Guidance](https://github.com/guidance-ai/guidance)**: Interleaved generation and control
- **[Outlines](https://github.com/outlines-dev/outlines)**: Structured text generation
- **[LMQL](https://lmql.ai/)**: SQL-like language for LLM interaction

---

## Foundational Texts

Core academic resources that provide rigorous theoretical foundations.

### Artificial Intelligence
- **"Artificial Intelligence: A Modern Approach" by Russell & Norvig**  
  The comprehensive AI textbook. Covers search, logic, planning, learning, and more.

### Reinforcement Learning
- **"Reinforcement Learning: An Introduction" by Sutton & Barto**  
  The definitive RL textbook. Covers MDPs, value functions, policy gradients, and exploration.

### Probabilistic Reasoning
- **"Probabilistic Graphical Models" by Daphne Koller and Nir Friedman**  
  Bayesian networks, Markov networks, inference algorithms.

- **"Pattern Recognition and Machine Learning" by Christopher Bishop**  
  Comprehensive coverage of probabilistic models and learning.

---

## Modern Agent Research

Contemporary research on building capable, reliable agents.

### Key Papers
- **"ReAct: Synergizing Reasoning and Acting in Language Models"** (Yao et al., 2022)  
  Interleaving reasoning traces with action steps for improved agent performance.

- **"Toolformer: Language Models Can Teach Themselves to Use Tools"** (Schick et al., 2023)  
  Self-supervised learning for tool use without human demonstrations.

### Agent Architectures
- **ReAct**: Reason + Act in interleaved manner
- **Reflection**: Self-critique and iterative improvement (see Reflexion above)
- **Tree-of-Thought**: Exploring reasoning paths as trees
- **Multi-Agent Systems**: Cooperation and competition

---

## Systems Thinking and Distributed Systems

Understanding reliability, scalability, and how complex systems fail in production.

### Distributed Systems Reliability
- **"Designing Data-Intensive Applications" (DDIA) by Martin Kleppmann**  
  If you haven't read this, drop everything and read it. The definitive guide to modern systems reliability, explaining "reliability," "scalability," and "maintainability" not as buzzwords but as trade-offs in data encoding, replication, and partitioning.
  
  **Focus**: Chapters 5-9 (Replication, Partitioning, Consistency, Consensus)

- **[Jepsen: Distributed Systems Safety Research](https://jepsen.io/)** by Kyle Kingsbury  
  A legendary series where Kyle takes popular databases (MongoDB, Postgres, Kafka) and subjects them to network partitions to see if they lose data. Bridges the gap between theory (CAP Theorem) and reality (what actually happens when a node fails).
  
  **The lesson**: "Distributed systems are always broken." This teaches you how they break.

### System Failure Philosophy  
- **"How Complex Systems Fail" by Richard Cook**  
  A short 4-page read on the philosophy of failure. Already mentioned in Control Theory section above - essential reading on understanding that "user error" is a myth and failure is a consequence of complex interactions.

---

## Learning Theory and Alignment

Understanding how agents learn and ensuring they learn what we intend.

### Core Resources
- **"The RLHF Book" by Nathan Lambert et al.**  
  Comprehensive guide to Reinforcement Learning from Human Feedback. Covers reward modeling, preference learning, and alignment. [RLHF Book](https://rlhfbook.com/)

### Alignment and Safety
- **"Concrete Problems in AI Safety"** by Amodei et al. (2016)  
  Classic paper identifying key safety challenges: negative side effects, reward hacking, scalable oversight, safe exploration, robustness.

- **"Specification Gaming: The Flip Side of AI Ingenuity"** by DeepMind (2020)  
  Catalog of examples where AI systems exploit loopholes in their reward specifications, demonstrating the importance of careful objective design.

### Key Concepts
- **Reward Modeling**: Learning human preferences
- **Inverse Reinforcement Learning**: Inferring objectives from behavior
- **Scalable Oversight**: Ensuring good behavior as capabilities grow
- **Interpretability**: Understanding what agents are doing and why

---

## Advanced Topics

Strategic horizon resources for long-term research and development (6-12 months out).

### World Models and Predictive Architectures
- **JEPA Papers (Joint Embedding Predictive Architectures)** by Yann LeCun  
  Theory behind "world models" - predicting abstract states rather than pixels. The mental model for building data simulators and abstract representations of state spaces.

### Planning with Language Models
- **Google's "Learning to Plan" Papers**  
  Search for papers on "Chain of Hindsight" and "Tree-of-Thoughts" to see how leading labs merge classical planning (Tier 1) with modern learning approaches (Tier 2). Shows the evolution from prompt engineering to structured search.

---

## Contributing

This is a living document. If you know of excellent resources on control theory, formal methods, planning, or formal languages applied to AI agents, please contribute!

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
