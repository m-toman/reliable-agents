# Reliable Agents: A Control-Theoretic Perspective

A curated collection of resources for building reliable AI agents through the lens of control theory, formal verification, planning, and formal languages. This is not your typical agent-building guide—instead, we focus on the mathematical and systems-engineering foundations that make agents truly reliable.

## Table of Contents
- [Control Theory: The "Physics" of Reliability](#control-theory-the-physics-of-reliability)
- [Planning and Decision Theory](#planning-and-decision-theory)
- [Formal Verification and Safety](#formal-verification-and-safety)
- [Formal Languages and Constrained Generation](#formal-languages-and-constrained-generation)
- [Foundational Texts](#foundational-texts)
- [Modern Agent Research](#modern-agent-research)
- [Learning Theory and Alignment](#learning-theory-and-alignment)

---

## Control Theory: The "Physics" of Reliability

Understanding agents as dynamical systems opens up powerful analytical tools from control theory.

### Videos and Tutorials
- **[Brian Douglas - Control Systems Lectures (YouTube)](https://www.youtube.com/user/ControlLectures)** 🎥  
  Exceptional series covering feedback control, stability analysis, and state-space methods. Essential for understanding how to maintain agent behavior within safe boundaries.

### Books
- **"Engineering a Safer World: Systems Thinking Applied to Safety" by Nancy Leveson**  
  Introduces STAMP (System-Theoretic Accident Model and Processes). Critical reading for understanding how complex systems fail and how to design safety constraints. [MIT Press](https://mitpress.mit.edu/9780262533690/engineering-a-safer-world/)

- **"Feedback Control of Dynamic Systems" by Franklin, Powell, and Emami-Naeini**  
  Classic textbook for understanding closed-loop control, which is fundamental to reliable agent design.

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
- **"Formal Verification of Hardware and Software Systems" by Anthony Widjaja Lin**
- **[TLA+ Video Course by Leslie Lamport](https://lamport.azurewebsites.net/video/videos.html)**

---

## Formal Languages and Constrained Generation

Ensuring agents produce valid, safe outputs through formal grammars and constrained decoding.

### Key Papers
- **"Efficient Guided Generation for Large Language Models"** by Willard & Louf (2023)  
  Introduces efficient algorithms for constraining LLM outputs to valid formal languages (JSON, regex, CFG). The foundational work behind the Guidance library. [Guidance Library](https://github.com/guidance-ai/guidance)

- **"Grammar Prompting for Domain-Specific Language Generation"** by Wang et al. (2023)  
  Techniques for using formal grammars to guide generation and ensure outputs conform to domain-specific languages.

### Techniques
- **Context-Free Grammars (CFG)**: BNF, EBNF for structured output
- **Regular Expressions**: Pattern-based constraints
- **Constrained Beam Search**: Incorporating hard constraints into decoding
- **Parser-Guided Decoding**: Only allow tokens that maintain validity

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

### Industry Whitepapers
- **[Google DeepMind: Agent Whitepapers](https://deepmind.google/)**
  - Gemini Agent papers
  - Planning and reasoning in language models
  - Tool use and multi-step reasoning

### Key Papers
- **"ReAct: Synergizing Reasoning and Acting in Language Models"** (Yao et al., 2022)
- **"Reflexion: Language Agents with Verbal Reinforcement Learning"** (Shinn et al., 2023)
- **"Voyager: An Open-Ended Embodied Agent with Large Language Models"** (Wang et al., 2023)
- **"Toolformer: Language Models Can Teach Themselves to Use Tools"** (Schick et al., 2023)

### Agent Architectures
- **ReAct**: Reason + Act in interleaved manner
- **Reflection**: Self-critique and iterative improvement
- **Tree-of-Thought**: Exploring reasoning paths as trees
- **Multi-Agent Systems**: Cooperation and competition

---

## Learning Theory and Alignment

Understanding how agents learn and ensuring they learn what we intend.

### Core Resources
- **"The RLHF Book" by Nathan Lambert et al.**  
  Comprehensive guide to Reinforcement Learning from Human Feedback. Covers reward modeling, preference learning, and alignment. [RLHF Book](https://rlhfbook.com/)

### Alignment and Safety
- **"Concrete Problems in AI Safety"** by Amodei et al. (2016)  
  Classic paper identifying key safety challenges: negative side effects, reward hacking, scalable oversight, safe exploration, robustness.

- **"AI Alignment: A Comprehensive Survey"** by Ji et al. (2024)  
  Comprehensive survey covering value learning, corrigibility, transparency, and verification approaches for AI alignment.

### Key Concepts
- **Reward Modeling**: Learning human preferences
- **Inverse Reinforcement Learning**: Inferring objectives from behavior
- **Scalable Oversight**: Ensuring good behavior as capabilities grow
- **Interpretability**: Understanding what agents are doing and why

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
