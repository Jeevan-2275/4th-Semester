# CIA2 Exam Master MCQ Question Bank - Artificial Intelligence (AI)

**Subject:** Artificial Intelligence  
**Pattern:** Multiple Choice Questions (MCQs) with Detailed Explanations  
**Coverage:** 100% Exhaustive Topic Coverage across ALL Units (Units 1, 2, and 3)  

---

## 🤖 Unit 1: Introduction to AI & Intelligent Agents

#### Q1. Which property of an agent environment implies that the agent's current state depends on past actions, making current decisions affect future states?
- (A) Static Environment
- (B) Sequential Environment
- (C) Episodic Environment
- (D) Deterministic Environment
**Answer:** (B) Sequential Environment  
**Explanation:** In a sequential environment, current decisions affect all future decisions and states (e.g., Chess, autonomous driving). In an episodic environment, each episode is independent.

#### Q2. In the PEAS framework for an automated taxi driver, which of the following represents an "Actuator"?
- (A) Cameras, radar, and LiDAR sensors
- (B) Steering wheel, accelerator pedal, and hydraulic brakes
- (C) Distance traveled and speed limit compliance
- (D) Road conditions and traffic light signals
**Answer:** (B) Steering wheel, accelerator pedal, and hydraulic brakes  
**Explanation:** PEAS stands for Performance measure, Environment, Actuators (output devices like steering/brakes), and Sensors (input devices like cameras/radar).

#### Q3. What is the key distinction between a Model-Based Reflex Agent and a Simple Reflex Agent?
- (A) Model-based agents use utility functions to evaluate happiness.
- (B) Model-based agents maintain an internal state to track unobserved aspects of a partially observable environment.
- (C) Simple reflex agents use goal states to select actions.
- (D) Simple reflex agents plan multi-step paths into the future.
**Answer:** (B) Model-based agents maintain an internal state to track unobserved aspects of a partially observable environment.  
**Explanation:** Model-based reflex agents maintain an internal state representing how the world evolves and how the agent's actions affect the world.

#### Q4. According to John Searle's Chinese Room Thought Experiment, what does a computer executing a program lack?
- (A) Syntactic processing capability
- (B) Symbol manipulation speed
- (C) Intentionality and true semantic understanding
- (D) Deterministic logic execution
**Answer:** (C) Intentionality and true semantic understanding  
**Explanation:** Searle argued that symbol manipulation (syntax) does not equate to genuine understanding or consciousness (semantics), refuting Strong AI claims based on the Turing Test.

#### Q5. Which agent architecture evaluates states using a real-valued function to trade off speed, safety, and cost when multiple paths achieve the goal?
- (A) Simple Reflex Agent
- (B) Goal-Based Agent
- (C) Utility-Based Agent
- (D) Model-Based Reflex Agent
**Answer:** (C) Utility-Based Agent  
**Explanation:** Utility-based agents use a utility function mapping states to real numbers to measure how desirable a particular state is.

#### Q6. An environment is classified as "Semi-Dynamic" if:
- (A) The environment changes while the agent is deliberating.
- (B) The environment does not change with time, but the agent's performance score does.
- (C) The environment state is completely static and performance measurement is ignored.
- (D) The environment continuously changes state at random intervals.
**Answer:** (B) The environment does not change with time, but the agent's performance score does.  
**Explanation:** If the environment itself doesn't change over time but the agent's performance score decreases as time passes (e.g., timed chess), it is semi-dynamic. If the world changes during deliberation, it is dynamic.

#### Q7. Which view of AI evaluates systems based on whether they produce optimal actions regardless of human cognitive limitations?
- (A) Thinking Humanly
- (B) Acting Humanly (Turing Test)
- (C) Thinking Rationally (Laws of Thought)
- (D) Acting Rationally (Rational Agent Approach)
**Answer:** (D) Acting Rationally (Rational Agent Approach)  
**Explanation:** The Rational Agent approach focuses on acting so as to achieve the best outcome or best expected outcome given the available information.

---

## 🔍 Unit 2: Problem Solving, Search Techniques & Game Playing

#### Q8. If $b$ is the branching factor and $d$ is the depth of the shallowest goal node, what is the space complexity of Breadth-First Search (BFS)?
- (A) $O(b \cdot d)$
- (B) $O(b^d)$
- (C) $O(d^b)$
- (D) $O(1)$
**Answer:** (B) $O(b^d)$  
**Explanation:** BFS stores all generated nodes in memory within its frontier queue, resulting in exponential space complexity $O(b^d)$.

#### Q9. Under what condition is the $A^*$ Search algorithm guaranteed to be optimal when conducting a Tree Search?
- (A) The heuristic function $h(n)$ is consistent ($h(n) \le c(n, a, n') + h(n')$).
- (B) The heuristic function $h(n)$ is admissible ($0 \le h(n) \le h^*(n)$).
- (C) The step cost is uniform across all edges.
- (D) The heuristic function $h(n)$ overestimates the true cost to goal.
**Answer:** (B) The heuristic function $h(n)$ is admissible ($0 \le h(n) \le h^*(n)$).  
**Explanation:** Admissibility means $h(n)$ never overestimates the actual cost to reach the goal. For Tree Search, admissibility guarantees $A^*$ optimality.

#### Q10. For $A^*$ Graph Search to be optimal without reopening closed nodes, the heuristic function $h(n)$ must be:
- (A) Admissible only
- (B) Consistent (Monotonic), satisfying $h(n) \le c(n, a, n') + h(n')$
- (C) $h(n) = 0$ for all nodes
- (D) Strictly negative
**Answer:** (B) Consistent (Monotonic), satisfying $h(n) \le c(n, a, n') + h(n')$  
**Explanation:** Consistency ensures $f(n) = g(n) + h(n)$ is non-decreasing along any path, guaranteeing that when a node is expanded, its optimal path has been found.

#### Q11. In Alpha-Beta Pruning, an Alpha cutoff occurs at a MIN node when:
- (A) $\alpha \ge \beta$
- (B) $\alpha < \beta$
- (C) $\alpha = 0$
- (D) $\beta = +\infty$
**Answer:** (A) $\alpha \ge \beta$  
**Explanation:** Alpha ($\alpha$) is MAX's best guaranteed score; Beta ($\beta$) is MIN's best guaranteed score. When $\alpha \ge \beta$, the current branch cannot influence the final decision, so it is pruned.

#### Q12. Which local search failure mode occurs when the algorithm reaches a flat area of the state space landscape where all neighbor states have the exact same heuristic evaluation?
- (A) Local Maximum
- (B) Ridge
- (C) Plateau / Shoulder
- (D) Local Minimum
**Answer:** (C) Plateau / Shoulder  
**Explanation:** A plateau is a flat region where $h(n)$ is constant, causing pure hill-climbing to take random walks or get stuck.

#### Q13. In Constraint Satisfaction Problems (CSPs), the AC-3 algorithm enforces Arc Consistency over variable pair $(X_i, X_j)$ by:
- (A) Removing values from domain $D_i$ that have no allowed value in $D_j$ according to constraint $R_{ij}$.
- (B) Assigning random values to $X_i$ and $X_j$.
- (C) Merging domains $D_i$ and $D_j$.
- (D) Removing all constraints between $X_i$ and $X_j$.
**Answer:** (A) Removing values from domain $D_i$ that have no allowed value in $D_j$ according to constraint $R_{ij}$.  
**Explanation:** Arc consistency $X_i \to X_j$ ensures that for every value $x \in D_i$, there exists at least one value $y \in D_j$ satisfying the constraint.

#### Q14. Iterative Deepening DFS (IDDFS) combines which two properties of BFS and DFS?
- (A) Exponential space of BFS and sub-optimal search of DFS
- (B) Completeness & Optimality of BFS with $O(b \cdot d)$ linear space memory of DFS
- (C) $O(1)$ space of BFS and infinite loop vulnerability of DFS
- (D) Greedy path expansion of $A^*$ and random selection of Hill Climbing
**Answer:** (B) Completeness & Optimality of BFS with $O(b \cdot d)$ linear space memory of DFS  
**Explanation:** IDDFS repeatedly applies depth-limited DFS with increasing depth limits ($0, 1, 2 \dots d$). It is complete and optimal like BFS, but uses linear $O(b \cdot d)$ memory like DFS.

#### Q15. Uniform Cost Search (UCS) expands nodes in order of:
- (A) Lowest heuristic estimate $h(n)$
- (B) Highest evaluation function $f(n)$
- (C) Lowest path cost $g(n)$ from the start node
- (D) Shallowest tree depth
**Answer:** (C) Lowest path cost $g(n)$ from the start node  
**Explanation:** UCS expands the frontier node with the lowest path cost $g(n)$, making it equivalent to Dijkstra's algorithm on a search graph.

#### Q16. With optimal move ordering, Alpha-Beta Pruning reduces the effective branching factor from $b$ to $\sqrt{b}$, reducing total search time complexity to:
- (A) $O(b^m)$
- (B) $O(b^{m/2})$
- (C) $O(m^b)$
- (D) $O(b \cdot m)$
**Answer:** (B) $O(b^{m/2})$  
**Explanation:** Perfect move ordering allows Alpha-Beta pruning to evaluate only $O(b^{m/2})$ nodes instead of $O(b^m)$, effectively doubling the search depth achievable in the same time.

---

## 🧠 Unit 3: Knowledge Representation, Logic, Expert Systems & Uncertainty

#### Q17. What is the result of converting the First-Order Logic sentence $\forall x \exists y \, \text{Loves}(x, y)$ into Conjunctive Normal Form (CNF) using Skolemization?
- (A) $\text{Loves}(x, y)$
- (B) $\text{Loves}(x, F(x))$
- (C) $\text{Loves}(F(y), y)$
- (D) $\text{Loves}(A, B)$
**Answer:** (B) $\text{Loves}(x, F(x))$  
**Explanation:** Since existential quantifier $\exists y$ follows universal quantifier $\forall x$, $y$ is replaced by a Skolem function $F(x)$ depending on $x$.

#### Q18. In a Frame-Based Knowledge Representation system, what is a "Daemon"?
- (A) A background OS multi-threading process.
- (B) A procedural attachment (e.g., `if-needed`, `if-added`) that automatically executes code when a slot value is accessed or modified.
- (C) An unassigned slot value representing `NULL`.
- (D) A superclass link for default property inheritance.
**Answer:** (B) A procedural attachment (e.g., `if-needed`, `if-added`) that automatically executes code when a slot value is accessed or modified.  
**Explanation:** Daemons in frame systems are procedural code attachments triggered by actions like reading (`if-needed`) or writing (`if-added`) to a slot.

#### Q19. Which conceptual dependency (CD) primitive action represents the transfer of mental information into memory or consciousness (e.g., "thinking" or "deciding")?
- (A) ATRANS
- (B) MTRANS
- (C) MBUILD
- (D) PTRANS
**Answer:** (C) MBUILD  
**Explanation:** In Roger Schank's CD theory, MBUILD represents building new mental information (deciding), whereas MTRANS represents transferring information (telling).

#### Q20. In Roger Schank's Conceptual Dependency (CD) theory, which primitive action represents the transfer of physical possession of an object (e.g., "giving" or "buying")?
- (A) PTRANS
- (B) ATRANS
- (C) MTRANS
- (D) PROPEL
**Answer:** (B) ATRANS  
**Explanation:** ATRANS represents transfer of an abstract relationship such as ownership/possession (e.g., give, take, buy). PTRANS represents changing physical location.

#### Q21. In Bayesian Networks, two variables $A$ and $B$ are conditionally independent given $C$ if:
- (A) $P(A, B \mid C) = P(A \mid C) \cdot P(B \mid C)$
- (B) $P(A \mid B) = P(B \mid A)$
- (C) $P(A, B) = P(A) \cdot P(B)$
- (D) $P(A \mid C) = 0$
**Answer:** (A) $P(A, B \mid C) = P(A \mid C) \cdot P(B \mid C)$  
**Explanation:** Conditional independence means knowing $B$ provides no additional information about $A$ once $C$ is known.

#### Q22. In Fuzzy Logic, what does the process of "Defuzzification" accomplish?
- (A) Converts crisp numbers into fuzzy set membership grades.
- (B) Converts fuzzy set membership output values into a single crisp numerical value (e.g., using Centroid Method).
- (C) Eliminates logical contradictions in rules.
- (D) Converts Propositional Logic into First-Order Logic.
**Answer:** (B) Converts fuzzy set membership output values into a single crisp numerical value (e.g., using Centroid Method).  
**Explanation:** Defuzzification maps the fuzzy output set generated by the rule evaluation engine back to a crisp control signal.

#### Q23. In Expert Systems, Forward Chaining is a data-driven reasoning approach that starts from:
- (A) Known facts in working memory and applies inference rules to derive new facts until a goal is reached.
- (B) A hypothesis goal and works backward to check supporting facts.
- (C) Random probabilities using Monte Carlo search.
- (D) Genetic mutations of rule bases.
**Answer:** (A) Known facts in working memory and applies inference rules to derive new facts until a goal is reached.  
**Explanation:** Forward chaining starts with known data/facts in working memory and triggers rules whose antecedents match, driving forward to discover conclusions. Backward chaining is goal-driven.

#### Q24. In Script Representation, which component describes the initial conditions that must be true for the script to be activated?
- (A) Track
- (B) Entry Conditions
- (C) Props
- (D) Scenes
**Answer:** (B) Entry Conditions  
**Explanation:** Entry conditions are preconditions that must be satisfied before the events described in the script can take place (e.g., customer is hungry and has money for Restaurant script).

#### Q25. What is the Match-Resolve-Act cycle in a Rule-Based Expert System's inference engine?
- (A) Matching rules against facts, resolving conflicts to pick 1 rule, and executing the rule's action.
- (B) Matching user inputs to HTML forms, resolving CSS, and acting on database queries.
- (C) Resolving compilation errors in C++ code.
- (D) Matching neural network weights to target labels.
**Answer:** (A) Matching rules against facts, resolving conflicts to pick 1 rule, and executing the rule's action.  
**Explanation:** The inference engine repeatedly matches working memory facts against IF conditions (Match), selects one rule from the conflict set (Resolve), and executes its THEN action (Act).

---
