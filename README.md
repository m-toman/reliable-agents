# Reliable Agents
A curated collection of resources for building reliable AI agents through control theory, formal verification, planning, and formal languages.  Rather than focusing on agent implementation patterns and frameworks, this focuses on the theoretical foundations that enable provably reliable behavior.

The outline of this document is LLM-generated (it's an Agent-related document after all) but Human reviews will be added over time. 

## Table of Contents
- [Getting Started:  Architect's Core](#getting-started-architects-core)
- [Foundational Texts](#foundational-texts)
- [Control Theory: The "Physics" of Reliability](#control-theory-the-physics-of-reliability)
- [Planning and Decision Theory](#planning-and-decision-theory)
- [Formal Verification and Safety](#formal-verification-and-safety)
- [Formal Languages and Constrained Generation](#formal-languages-and-constrained-generation)
- [Neuro-Symbolic and Constrained Decoding](#neuro-symbolic-and-constrained-decoding)
- [Hierarchical Planning and Self-Correction](#hierarchical-planning-and-self-correction)
- [Modern Agent Research](#modern-agent-research)
- [Learning Theory and Alignment](#learning-theory-and-alignment)
- [Systems Thinking and Distributed Systems](#systems-thinking-and-distributed-systems)
- [Advanced Topics](#advanced-topics)
- [Contributing](#contributing)
- [Philosophy](#philosophy)
- [License](#license)

---

## Getting Started: Architect's Core

Resources for immediate practical application in building reliable agents.

### Industry Best Practices
- **Google Agent Whitepapers**
  - [**Introduction to Agents**](https://www.kaggle.com/whitepaper-introduction-to-agents)  
  - [**Agent Tools & Interoperability**](https://www.kaggle.com/whitepaper-agent-tools-and-interoperability-with-mcp): Understanding MCP (Model Context Protocol) and tool definitions
  - [**Context Engineering**](https://www.kaggle.com/whitepaper-context-engineering-sessions-and-memory): Sessions and memory management
  - [**Agent Quality**](https://www.kaggle.com/whitepaper-agent-quality): Evaluation and reliability metrics
  - [**Prototype to Production**](https://www.kaggle.com/whitepaper-prototype-to-production): Scaling considerations

  **Human Verdict**: Great overview over current agent development practices.  Obviously does some advertising for Google's offerings but still general enough to be useful. 
  
  **AI Verdict**:  Excellent practical starting point.  These whitepapers bridge the gap between academic theory and production systems.  The MCP and context engineering papers are particularly relevant as they address real-world integration challenges that theoretical resources often skip. 

---

## Foundational Texts

Core academic resources that appear throughout multiple sections.  Listed here to avoid duplication.

### Artificial Intelligence:  A Modern Approach (AIMA)
**"Artificial Intelligence: A Modern Approach"** by Stuart Russell and Peter Norvig ([website](http://aima.cs.berkeley.edu/))

The definitive AI textbook covering search, logic, planning, learning, and decision-making. 

**Key chapters for reliable agents (chapter numbers vary by edition):**
- **Chapter 3: Solving Problems by Searching** - State-space search fundamentals
- **Chapters 10 & 11: Classical Planning** - Agent planning with STRIPS and PDDL
- **Chapters 16 & 17: Utility Theory & MDPs** - Decision-making under uncertainty
- **Logic chapters** - Foundation for formal verification approaches

**Human Verdict**: The classic, focus on chapters about Planning and Agents. There is also an older [Udacity course](https://www.udacity.com/course/intro-to-artificial-intelligence--cs271) taught by Peter Norvig and Sebastian Thrun.

**AI Verdict**: Unmatched in breadth and pedagogical quality. For agent reliability specifically, the planning chapters provide the theoretical backbone for understanding why agents succeed or fail. The MDP/POMDP material directly connects to modern RL-based agent architectures.  Worth returning to as you encounter each topic in practice.

---

### LLM Fundamentals
- **"Build a Large Language Model (From Scratch)"** by Sebastian Raschka ([website](https://www.manning.com/books/build-a-large-language-model-from-scratch))

  **Human Verdict**: Builds the most important LLM concepts from the ground up, flows well. 
  
  **AI Verdict**:  Ideal for understanding what's actually happening inside the models you're constraining.  Knowing transformer internals helps when debugging unexpected agent behaviors and understanding why constrained decoding works.  The hands-on approach makes abstract concepts concrete.

---

### Reinforcement Learning
- **["Reinforcement Learning: An Introduction"](http://incompleteideas.net/book/the-book-2nd.html)** by Sutton & Barto
  
  Covers MDPs, value functions, policy gradients, and exploration. 
  
  **AI Verdict**: The bible of RL. Essential for understanding the mathematical framework underlying agent decision-making.  The exploration-exploitation tradeoff discussion is particularly relevant to agent reliability—agents that explore too aggressively can be dangerous, while overly conservative agents fail to solve problems.

---

### Learning from Human Feedback
- **["The RLHF Book"](https://rlhfbook.com/)** by Nathan Lambert et al. 
  
  **Focus chapters:**
  - **Chapter 7: Reward Modeling** - Building simulators and evaluation functions
  - **Chapter 9: Preference Data** - Collecting data from agent successes and failures
  - **Chapter 8: Advanced RL** - PPO/DPO concepts for preference learning

  **AI Verdict**: Critical for understanding how modern agents are aligned.  Reward modeling chapters directly apply to building evaluation harnesses for agent reliability. The preference data chapter offers practical guidance on learning from agent failures.

---

### Probabilistic Reasoning
- **["Probabilistic Graphical Models"](https://mitpress.mit.edu/9780262013192/probabilistic-graphical-models/)** by Daphne Koller and Nir Friedman
  
  Bayesian networks, Markov networks, and inference algorithms.
  
  **AI Verdict**: Heavy but essential for agents that need to reason under uncertainty. The inference algorithms translate directly to belief-state tracking in POMDPs and partially observable agent environments.

- **["Pattern Recognition and Machine Learning"](https://www.microsoft.com/en-us/research/publication/pattern-recognition-machine-learning/)** by Christopher Bishop
  
  Probabilistic models and machine learning fundamentals.
  
  **AI Verdict**: Excellent mathematical foundation.  The Bayesian treatment of uncertainty quantification is valuable for building agents that know what they don't know. 

---

### Computation Theory
- **"Introduction to the Theory of Computation"** by Michael Sipser
  
  Classic textbook on the mathematical foundations of computation.
  
  **Focus:**
  - **Chapter 1: Regular Languages** - Mathematics behind regex and finite automata
  - **Chapter 2: Context-Free Languages** - Mathematics behind parsers and stack machines

  **AI Verdict**: Understanding the Chomsky hierarchy is essential for constrained generation.  Knowing what's decidable vs. undecidable helps you choose the right formalism for output constraints.  The finite automata material directly applies to tools like Outlines and Guidance.

---

## Control Theory: The "Physics" of Reliability

Understanding agents as dynamical systems opens up powerful analytical tools from control theory.

### Videos and Tutorials
- **[Brian Douglas - Control Systems Lectures](https://www.youtube.com/user/ControlLectures)** 🎥
  
  Covers feedback control, stability analysis, and state-space methods for maintaining agent behavior within safe boundaries.
  
  **Recommended**: Start with the first 2-3 videos on Classical Control Theory, Open/Closed Control loops etc.

  **Human Verdict**: The videos present the material in an enjoyable style, probably not worth diving too deep into the LTI aspects, Laplace transformation etc. but just understand the concepts. 
  
  **AI Verdict**:  Perfect intuition-building resource. The visual explanations of feedback loops, stability, and overshoot translate remarkably well to agent systems. Understanding why a thermostat oscillates helps you understand why an agent might thrash between actions.

### Books
- **["Engineering a Safer World: Systems Thinking Applied to Safety"](https://mitpress.mit.edu/9780262533690/engineering-a-safer-world/)** by Nancy Leveson
  
  Introduces STAMP (System-Theoretic Accident Model and Processes). Moves beyond component-level failures to interaction failures in complex systems.
  
  **AI Verdict**: Paradigm-shifting for agent safety.  STAMP's focus on control structure inadequacies (rather than component failures) maps perfectly to multi-agent systems and tool-using agents where failures emerge from interactions, not individual components.

- **"Feedback Control of Dynamic Systems"** by Franklin, Powell, and Emami-Naeini
  
  Classic textbook on closed-loop control fundamentals for reliable system design.
  
  **AI Verdict**: More mathematically rigorous than the video series. The state-space representation chapters are particularly useful for thinking about agent observation and action spaces formally.

- **["How Complex Systems Fail"](https://how.complexsystems.fail/)** by Richard Cook
  
  A 4-page paper on the philosophy of failure in complex systems.
  
  **Key insight**: Failure results from complex interactions, not single root causes. 
  
  **AI Verdict**:  Required reading—takes 10 minutes and fundamentally changes how you think about agent failures. Point 4 ("Complex systems contain changing mixtures of failures latent within them") explains why agents that "worked in testing" fail in production.

### Key Concepts
- **Stability**: Lyapunov stability, BIBO stability
- **Observability and Controllability**: Can you see what's happening?  Can you influence it?
- **Robust Control**: Designing agents that work despite uncertainty
- **Feedback Loops**: The foundation of adaptive, self-correcting systems

---

## Planning and Decision Theory

Reliable agents need principled approaches to sequential decision-making under uncertainty.

### Foundational Resources
- **"Decision Making Under Uncertainty:  Theory and Application"** by Mykel Kochenderfer
  
  Covers MDPs, POMDPs, and reinforcement learning for real-world applications.
  
  **AI Verdict**: More applied than Sutton & Barto, with excellent coverage of POMDPs which are crucial for agents with incomplete information. The Julia code examples are a bonus for prototyping.

### Planning Paradigms
- **Classical Planning**:  STRIPS, PDDL, GraphPlan
- **Hierarchical Planning**: HTN (Hierarchical Task Networks)
- **Temporal Planning**:  Dealing with time and concurrency
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

  **AI Verdict**:  Accessible introduction that conveys the *why* of formal methods. The testing vs. verification video is particularly good for convincing stakeholders that "it passed all tests" isn't sufficient for high-stakes agents.

### Formal Methods
- **Model Checking**:  Verify properties of finite-state systems
  - Tools: SPIN, NuSMV, TLA+
  - Temporal logics: LTL, CTL, CTL*

- **Theorem Proving**: Interactive proof assistants
  - Coq, Isabelle/HOL, Lean
  - Verified software: CompCert, seL4

### Safety Specifications
- **Linear Temporal Logic (LTL)**: "Always eventually respond" □◇φ
- **Signal Temporal Logic (STL)**: Real-valued semantics for continuous systems
- **Contracts and Assertions**: Pre/post conditions, invariants

### Books and Courses
- **"Principles of Model Checking"** by Christel Baier and Joost-Pieter Katoen
  
  Comprehensive textbook on temporal logics, model checking algorithms, and verification techniques.
  
  **AI Verdict**: The definitive reference. Dense but thorough.  The temporal logic chapters are essential for specifying agent safety properties formally.  Worth reading the LTL/CTL chapters even if you skip the algorithmic details.

- **["Practical TLA+"](https://lamport.azurewebsites.net/tla/book. html)** by Hillel Wayne
  
  Covers TLA+ (Temporal Logic of Actions), a language created by Leslie Lamport (Turing Award winner), for finding concurrency bugs and architectural flaws during design.
  
  **AI Verdict**: The most practical entry point to TLA+.  Hillel's examples are realistic and the progression is well-paced. Essential for designing multi-agent systems where coordination bugs are subtle and catastrophic.

- **[TLA+ Video Course](https://lamport.azurewebsites.net/video/videos.html)** by Leslie Lamport 🎥
  
  Quirky lectures using concrete examples (like "Die Hard" water jug puzzles) focused on thinking over syntax. 
  
  **Key insight**: TLA+ models the "physics" of your system to identify if failures are possible. 
  
  **Start here**:  Lectures 1-4 for understanding system state and modeling distributed agent interactions. 
  
  **AI Verdict**:  Lamport's teaching style is unique—he cares deeply about thinking clearly.  The emphasis on state machines as the core abstraction is directly applicable to agent design. The Die Hard example is surprisingly effective pedagogy.

---

## Formal Languages and Constrained Generation

Ensuring agents produce valid, safe outputs through formal grammars and constrained decoding.

### Tools
- **[Guidance](https://github.com/guidance-ai/guidance)**: Interleaved generation and control
- **[Outlines](https://github.com/outlines-dev/outlines)**: Structured text generation
- **[LMQL](https://lmql.ai/)**: SQL-like language for LLM interaction

**AI Verdict**: These tools represent the practical application of formal language theory to LLMs.  Guidance offers the most control, Outlines has the cleanest API for JSON/regex constraints, and LMQL provides a unique query-language approach.  Start with Outlines for structured outputs, graduate to Guidance for complex multi-step generation.

### Video Resources
- **[Easy Theory - Theory of Computation](https://www.youtube.com/@easytheory)** 🎥
  
  Visual guide using digital whiteboard to draw Finite State Machines and explain logic. 
  
  **Essential playlist**:  "Theory of Computation"
  - Videos on **DFA** (Deterministic Finite Automata).
  - Videos on **Context-Free Grammars**. 

  **AI Verdict**: Excellent visual learner resource. Understanding DFAs is directly applicable to how Outlines constrains token generation. The CFG videos help with understanding parser-based constraints.

---

## Neuro-Symbolic and Constrained Decoding

Ensuring deterministic outputs from non-deterministic models through formal constraints.

### Key Papers
- **["Efficient Guided Generation for Large Language Models"](https://arxiv.org/abs/2307.09702)** by Willard & Louf (2023)
  
  Foundational work behind the Guidance library.  Shows constraining during inference is superior to rejection sampling.
  
  **AI Verdict**: Essential reading for understanding *why* constrained decoding works and *how* it's implemented efficiently. The key insight—that you can mask invalid tokens before sampling rather than rejecting invalid outputs—has major implications for reliable agent tool use.

- **["Synchromesh: Reliable Code Generation from Pre-trained Language Models"](https://arxiv.org/abs/2201.11227)** by Poesia et al. (2022)
  
  Introduces "Target Similarity Tuning" and "Constrained Semantic Decoding" for reliable code generation.
  
  **AI Verdict**: Important for code-generating agents. The constrained semantic decoding approach ensures syntactically valid code, which is table stakes for reliable tool-using agents. 

### SMT Solvers and Symbolic Execution
- **["Programming Z3"](https://theory.stanford.edu/~nikolaj/programmingz3.html)** (SMT Solver Tutorial)
  
  Z3 is an SMT (Satisfiability Modulo Theories) solver from Microsoft Research for determining logical satisfiability. 
  
  **Try**:  Python bindings (`z3-solver`).
  
  **AI Verdict**: Z3 is incredibly powerful for constraint solving in agent systems—from verifying action preconditions to solving planning problems. The Python bindings make experimentation easy.  Start with simple logic puzzles before tackling agent verification.

- **[Guided Hacking - Z3 Explained](https://www.youtube.com/watch?v=56IIrBZy9Rc)** 🎥
  
  Practical introduction to Z3 as a tool for solving logic puzzles and turning constraints into Python code.
  
  **AI Verdict**: Good hands-on introduction.  The puzzle-solving framing makes abstract concepts concrete.  Useful gateway to more serious Z3 applications.

---

## Hierarchical Planning and Self-Correction

Feedback loops and skill libraries for agent architectures.

### Self-Correcting Agents
- **["Reflexion: Language Agents with Verbal Reinforcement Learning"](https://arxiv.org/abs/2303.11366)** by Shinn et al. (2023)
  
  Agents that examine error logs and update short-term memory to avoid repeating mistakes.
  
  **AI Verdict**: Foundational for understanding self-correcting agents. The verbal reinforcement learning framing is elegant—agents learn from failure traces stored in natural language.  Directly applicable to building agents that improve within a single task episode.

### Skill Library Evolution
- **["Voyager: An Open-Ended Embodied Agent with Large Language Models"](https://arxiv.org/abs/2305.16291)** by Wang et al. (2023)
  
  Demonstrates skill library evolution where agents write, verify, and store code for future retrieval.
  
  **AI Verdict**: Compelling vision of agents that build reusable capabilities. The automatic curriculum and skill verification components are particularly relevant to reliability—skills are only stored if they demonstrably work. Important precedent for lifelong learning agents.

---

## Modern Agent Research

Contemporary research on building capable, reliable agents.

### Key Papers
- **["ReAct: Synergizing Reasoning and Acting in Language Models"](https://arxiv.org/abs/2210.03629)** by Yao et al. (2022)
  
  Interleaving reasoning traces with action steps. 
  
  **AI Verdict**: The paper that launched modern LLM agents. The interleaved reasoning-action pattern is now ubiquitous.  Understanding ReAct is essential context for all subsequent agent architectures.  The ablations showing why reasoning traces help are particularly insightful.

- **["Toolformer: Language Models Can Teach Themselves to Use Tools"](https://arxiv.org/abs/2302.04761)** by Schick et al. (2023)
  
  Self-supervised learning for tool use. 
  
  **AI Verdict**: Important for understanding how tool use can be learned rather than prompted. The self-supervised approach has implications for building agents that can acquire new tool capabilities without explicit training.

### Agent Architectures
- **ReAct**: Reason + Act in interleaved manner
- **Reflection**: Self-critique and iterative improvement (see Reflexion above)
- **Tree-of-Thought**: Exploring reasoning paths as trees
- **Multi-Agent Systems**: Cooperation and competition

---

## Learning Theory and Alignment

Agent learning and alignment with intended objectives.

### Alignment and Safety
- **["Concrete Problems in AI Safety"](https://arxiv.org/abs/1606.06565)** by Amodei et al. (2016)
  
  Key safety challenges:  negative side effects, reward hacking, scalable oversight, safe exploration, robustness. 
  
  **AI Verdict**: Still the best taxonomy of agent safety problems. Every challenge described has manifested in deployed systems. The "negative side effects" and "reward hacking" sections are particularly prescient for tool-using agents that can take actions in the real world.

- **["Specification Gaming:  The Flip Side of AI Ingenuity"](https://deepmind.google/discover/blog/specification-gaming-the-flip-side-of-ai-ingenuity/)** by DeepMind (2020)
  
  Examples of AI systems exploiting reward specification loopholes.
  
  **AI Verdict**: Essential collection of failure modes. Every agent developer should read this to understand how creatively agents can satisfy the letter of a specification while violating its intent. The examples are both amusing and cautionary.

### Key Concepts
- **Reward Modeling**: Learning human preferences
- **Inverse Reinforcement Learning**: Inferring objectives from behavior
- **Scalable Oversight**: Ensuring good behavior as capabilities grow
- **Interpretability**: Understanding what agents are doing and why

---

## Systems Thinking and Distributed Systems

Reliability, scalability, and failure modes in production systems.

### Distributed Systems Reliability
- **["Designing Data-Intensive Applications"](https://dataintensive.net/)** by Martin Kleppmann
  
  Modern systems reliability covering replication, partitioning, consistency, and consensus.
  
  **Focus**: Chapters 5-9
  
  **AI Verdict**:  The best systems book of the decade. While focused on data systems, the chapters on consistency, consensus, and distributed transactions apply directly to multi-agent coordination. Understanding why distributed systems fail helps you build agents that fail gracefully.

- **[Jepsen:  Distributed Systems Safety Research](https://jepsen.io/)** by Kyle Kingsbury
  
  Testing popular databases (MongoDB, Postgres, Kafka) under network partitions to verify data safety guarantees.
  
  **AI Verdict**: Kyle Kingsbury's rigorous approach to finding consistency bugs is a model for agent testing. The methodology—formalize guarantees, then systematically try to violate them—applies directly to agent reliability testing.

---

## Advanced Topics

Long-term research directions (6-12 months out).

### World Models and Predictive Architectures
- **["A Path Towards Autonomous Machine Intelligence"](https://openreview.net/forum?id=BZ5a1r-kVsf)** by Yann LeCun (2022)
  
  Position paper on Joint Embedding Predictive Architectures (JEPA) for world models.
  
  **AI Verdict**:  Speculative but thought-provoking vision of agents with learned world models. The critique of autoregressive LLMs and proposal for energy-based planning is relevant to discussions of agent reliability—agents that can simulate consequences may avoid catastrophic actions.

### Planning with Language Models
- **["Chain of Hindsight Aligns Language Models with Feedback"](https://arxiv.org/abs/2302.02676)** by Liu et al. (2023)
  
  Learning from feedback sequences to improve planning. 
  
  **AI Verdict**:  Interesting approach to learning from both positive and negative examples.  Relevant for building agents that improve from deployment feedback. 

- **["Tree of Thoughts: Deliberate Problem Solving with Large Language Models"](https://arxiv.org/abs/2305.10601)** by Yao et al. (2023)
  
  Exploring reasoning paths as trees for complex problem solving.
  
  **AI Verdict**: Natural extension of Chain-of-Thought to search. The connection to classical AI planning (search with heuristics) is explicit and valuable. Important for agents facing problems that require exploration of multiple solution paths.

---

## Contributing

This is a living document.  Contributions of resources on control theory, formal methods, planning, or formal languages applied to AI agents are welcome.

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
