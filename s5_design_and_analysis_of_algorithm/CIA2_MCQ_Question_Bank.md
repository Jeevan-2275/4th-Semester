# CIA2 Exam Master MCQ Question Bank - Design and Analysis of Algorithms (DAA)

**Subject:** Design and Analysis of Algorithms  
**Pattern:** Multiple Choice Questions (MCQs) with Detailed Explanations  
**Coverage:** 100% Exhaustive Topic Coverage across Units 1 to 5  

---

## ⚡ Unit 1 & 2: Asymptotic Analysis, Recurrences & Divide-and-Conquer

#### Q1. According to the Master Theorem for recurrences $T(n) = a T(n/b) + f(n)$, what is the solution if $f(n) = \Theta(n^{\log_b a})$?
- (A) $T(n) = \Theta(n^{\log_b a})$
- (B) $T(n) = \Theta(n^{\log_b a} \log n)$
- (C) $T(n) = \Theta(f(n))$
- (D) $T(n) = \Theta(n^2)$
**Answer:** (B) $T(n) = \Theta(n^{\log_b a} \log n)$  
**Explanation:** Case 2 of the Master Theorem applies when $f(n) = \Theta(n^{\log_b a})$, resulting in $T(n) = \Theta(n^{\log_b a} \log n)$.

#### Q2. Strassen's Matrix Multiplication algorithm multiplies two $n \times n$ matrices using how many sub-matrix multiplications?
- (A) 8 sub-multiplications yielding $O(n^3)$ time
- (B) 7 sub-multiplications yielding $O(n^{\log_2 7}) \approx O(n^{2.81})$ time
- (C) 6 sub-multiplications yielding $O(n^{2.58})$ time
- (D) 4 sub-multiplications yielding $O(n^2)$ time
**Answer:** (B) 7 sub-multiplications yielding $O(n^{\log_2 7}) \approx O(n^{2.81})$ time  
**Explanation:** Strassen reduced recursive sub-matrix multiplications from 8 to 7, bringing down complexity from $O(n^3)$ to $O(n^{2.81})$.

#### Q3. What is the worst-case time complexity of Quick Sort, and when does it occur?
- (A) $O(n \log n)$ when pivot splits array into equal halves.
- (B) $O(n^2)$ when array is already sorted and smallest/largest element is chosen as pivot.
- (C) $O(n)$ when all elements are distinct.
- (D) $O(n^{1.5})$ when Lomuto partitioning is used.
**Answer:** (B) $O(n^2)$ when array is already sorted and smallest/largest element is chosen as pivot.  
**Explanation:** Worst-case partitioning occurs when one subproblem has $0$ elements and the other has $n-1$ elements, yielding recurrence $T(n) = T(n-1) + \Theta(n) = O(n^2)$.

#### Q4. What is the tight asymptotic bound ranking of functions from slowest growing to fastest growing?
- (A) $O(1) < O(\log n) < O(\sqrt{n}) < O(n) < O(n \log n) < O(n^2) < O(2^n) < O(n!)$
- (B) $O(n!) < O(2^n) < O(n^2) < O(n \log n) < O(n) < O(1)$
- (C) $O(n) < O(n \log n) < O(\log n) < O(2^n)$
- (D) $O(1) < O(n^2) < O(n) < O(n!)$
**Answer:** (A) $O(1) < O(\log n) < O(\sqrt{n}) < O(n) < O(n \log n) < O(n^2) < O(2^n) < O(n!)$  
**Explanation:** Correct growth rate ranking is constant $<$ logarithmic $<$ square-root $<$ linear $<$ linearithmic $<$ quadratic $<$ exponential $<$ factorial.

---

## 💡 Unit 3 & 4: Greedy Strategy & Dynamic Programming

#### Q5. What is the main structural difference between Dynamic Programming (DP) and Divide-and-Conquer?
- (A) DP splits problems into independent subproblems; Divide-and-Conquer solves overlapping subproblems.
- (B) DP solves overlapping subproblems by storing results (memoization/tabulation); Divide-and-Conquer solves independent subproblems recursively.
- (C) DP guarantees greedy choice property; Divide-and-Conquer does not.
- (D) Divide-and-Conquer works bottom-up only; DP works top-down only.
**Answer:** (B) DP solves overlapping subproblems by storing results (memoization/tabulation); Divide-and-Conquer solves independent subproblems recursively.  
**Explanation:** DP is designed for problems with overlapping subproblems and optimal substructure, avoiding redundant computations by caching subproblem solutions.

#### Q6. Why can Fractional Knapsack be solved greedily in $O(n \log n)$, while 0/1 Knapsack requires Dynamic Programming $O(n W)$?
- (A) Fractional Knapsack allows taking partial items based on value-to-weight ratio; 0/1 Knapsack enforces binary choice (0 or 1), generating overlapping subproblems.
- (B) 0/1 Knapsack has no optimal substructure.
- (C) Fractional Knapsack has an exponential state space.
- (D) Dynamic Programming cannot be applied to Fractional Knapsack.
**Answer:** (A) Fractional Knapsack allows taking partial items based on value-to-weight ratio; 0/1 Knapsack enforces binary choice (0 or 1), generating overlapping subproblems.  
**Explanation:** Greedy choice works for Fractional Knapsack because partial items can be taken to fill remaining capacity. For 0/1 Knapsack, taking a high-ratio item may leave unusable empty space, requiring DP.

#### Q7. Which Minimum Spanning Tree (MST) algorithm uses a Disjoint Set Union (DSU / Union-Find) data structure to detect cycles while greedily processing edges in ascending weight order?
- (A) Prim's Algorithm
- (B) Kruskal's Algorithm
- (C) Dijkstra's Algorithm
- (D) Bellman-Ford Algorithm
**Answer:** (B) Kruskal's Algorithm  
**Explanation:** Kruskal's algorithm sorts all edges by weight and adds edges using Union-Find to prevent cycles in $O(E \log E)$ time.

#### Q8. What is the time complexity to find the Longest Common Subsequence (LCS) of two strings of lengths $m$ and $n$ using Dynamic Programming?
- (A) $O(m + n)$
- (B) $O(m \cdot n)$
- (C) $O(2^{m+n})$
- (D) $O(\min(m, n))$
**Answer:** (B) $O(m \cdot n)$  
**Explanation:** DP LCS builds a 2D table of size $(m+1) \times (n+1)$, calculating each entry in $O(1)$ time $\implies O(m \cdot n)$ total time.

---

## 🔤 Unit 5: String Matching & Complexity Classes (P, NP, NP-Hard, NP-Complete)

#### Q9. In the Knuth-Morris-Pratt (KMP) string matching algorithm, what does the Longest Proper Prefix which is also Suffix (LPS) array store?
- (A) The hash values of pattern substrings.
- (B) The length of the longest proper prefix of $P[0 \dots i]$ that is also a suffix of $P[0 \dots i]$.
- (C) The ASCII character counts of pattern $P$.
- (D) The count of mismatched text characters.
**Answer:** (B) The length of the longest proper prefix of $P[0 \dots i]$ that is also a suffix of $P[0 \dots i]$.  
**Explanation:** The LPS table ($\pi$) allows KMP to shift the pattern upon mismatch without moving the text index $i$ backward, guaranteeing $O(n + m)$ linear time.

#### Q10. What is the formal definition of Class NP?
- (A) The set of decision problems solvable in non-polynomial time.
- (B) The set of decision problems solvable in polynomial time $O(n^k)$ by a deterministic Turing Machine.
- (C) The set of decision problems whose proposed solutions can be verified in polynomial time $O(n^k)$ by a deterministic Turing Machine.
- (D) The set of optimization problems with exponential lower bounds.
**Answer:** (C) The set of decision problems whose proposed solutions can be verified in polynomial time $O(n^k)$ by a deterministic Turing Machine.  
**Explanation:** Class NP stands for Nondeterministic Polynomial time. A problem belongs to NP if a certificate/hint can be verified in polynomial time.

#### Q11. A decision problem $B$ is formally defined as **NP-Complete** if it satisfies which two conditions?
- (A) $B \in P$ and $B \in NP$
- (B) $B \in NP$ and $B$ is NP-Hard ($\forall L \in NP, L \le_P B$)
- (C) $B$ is undecidable and $B \notin NP$
- (D) $B \in P$ and $B$ is NP-Hard
**Answer:** (B) $B \in NP$ and $B$ is NP-Hard ($\forall L \in NP, L \le_P B$)  
**Explanation:** NP-Complete problems are the intersection of NP and NP-Hard ($NPC = NP \cap NP\text{-Hard}$). They are verifiable in polynomial time $O(n^k)$ and at least as hard as any problem in NP.

#### Q12. Which theorem established that the Boolean Satisfiability Problem (SAT) is the first ever proven NP-Complete problem?
- (A) Master Theorem
- (B) Cook-Levin Theorem
- (C) Church-Turing Thesis
- (D) Bellman-Ford Theorem
**Answer:** (B) Cook-Levin Theorem  
**Explanation:** Proven by Stephen Cook (1971) and Leonid Levin (1973), the Cook-Levin Theorem proved that SAT is NP-Complete by encoding non-deterministic Turing Machine computations into Boolean logic formulas.

#### Q13. How does the Rabin-Karp string matching algorithm achieve $O(1)$ average hash updates when sliding the text window?
- (A) Re-calculating full string hashes from scratch.
- (B) Using a Rolling Hash formula $t_{s+1} = (d(t_s - T[s]\cdot h) + T[s+m]) \pmod q$.
- (C) Sorting window characters alphabetically.
- (D) Using bitwise XOR on adjacent characters.
**Answer:** (B) Using a Rolling Hash formula $t_{s+1} = (d(t_s - T[s]\cdot h) + T[s+m]) \pmod q$  
**Explanation:** Rabin-Karp uses a rolling hash polynomial equation that subtracts the outgoing character and adds the incoming character in $O(1)$ constant time.

#### Q14. What is the fundamental difference between an NP-Complete problem and an NP-Hard problem?
- (A) NP-Complete problems are in Class P; NP-Hard problems are not.
- (B) NP-Complete problems must be in Class NP (verifiable in $O(n^k)$); NP-Hard problems do NOT need to be in Class NP (can be optimization or undecidable).
- (C) NP-Hard problems are solvable in $O(n)$; NP-Complete problems take $O(n^2)$.
- (D) There is no difference; the terms are identical.
**Answer:** (B) NP-Complete problems must be in Class NP (verifiable in $O(n^k)$); NP-Hard problems do NOT need to be in Class NP (can be optimization or undecidable).  
**Explanation:** NP-Complete is a subset of NP-Hard ($NPC = NP \cap NP\text{-Hard}$). NP-Hard includes problems like the Halting Problem or TSP Optimization that aren't in NP.

---
