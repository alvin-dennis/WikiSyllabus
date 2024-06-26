# Backtracking

- Backtracking method expresses the solution as an n-tuple (\(x_1, x_2, ..., x_n\)), where \(x_i\)'s are chosen from some finite set \(S_i\).
- The problem to be solved calls for finding one vector that maximizes (or minimizes or satisfies) a criterion function \(P(x_1, x_2, ..., x_n)\).
- Examples:
  - Sorting the array of integers in \(a[l:n]\):
    - The solution to the problem is expressed as an n-tuple, where \(x_i\) is the index of the ith smallest element.
    - The criterion function \(P\) is: \(a[x_i] \leq a[x_{i+1}]\), for \(1 \leq i < n\).
    - The set \(S_i = \{1, 2, ..., n\}\).
  - Different methods for solving this problem:
    - **Brute Force approach**:
      - Suppose \(m_i\) is the size of set \(S_i\).
      - The number of tuples (with size n) that are possible candidates for satisfying the function \(P\) is: \(m = m_1 \times m_2 \times m_3 \times ... \times m_n\).
      - Brute Force approach evaluates each one with \(P\), and saves those which yield the optimum.

    - **Backtracking algorithm**:
      - It yields the same answer with far fewer than \(m\) trials.
      - Its basic idea is to build up the solution vector one component at a time and to use modified criterion functions (bounding functions) \(P_i(x_1, x_2, ..., x_i)\) to test whether the vector being formed has any chance of success.
      - The major advantage of this method is that if it is realized that the partial vector (\(x_1, x_2, ..., x_i\)) can in no way lead to an optimal solution, then \(m_{i+1} \times m_{i+2} \times ... \times m_n\) possible test vectors can be ignored entirely.

- Backtracking method requires that all the solutions satisfy a complex set of constraints. These constraints can be divided into two categories:
    - **Explicit Constraints**:
      - Explicit constraints are rules that restrict each \(x_i\) to take on values only from a given set.
      - The explicit constraints depend on the particular instance \(I\) of the problem being solved. All tuples that satisfy the explicit constraints define a possible solution space for \(I\).
      - Example:
        ![Screenshot 2024-05-17 215544](https://github.com/athul-2003/WikiSyllabus/assets/128019369/d1d95e2d-1359-4d98-853d-19de2926e044)

        
    - **Implicit Constraints**:
      - These are rules that determine which of the tuples in the solution space of \(I\) satisfy the criterion function (Bounding Function).

# Backtracking Control Abstraction

- \( (x_1, x_2, ..., x_i) \) be a path from the root to a node in a state space tree.
- Generating Function \( T(x_1, x_2, ..., x_i) \) be the set of all possible values for \( x_{i+1} \) such that \( (x_1, x_2, ..., x_{i+1}) \) is also a path to a problem state.
- \( T(x_1, x_2, ..., x_n) = \emptyset \)
- Bounding function \( B_{i+1}(x_1, x_2, ..., x_{i+1}) \) is false for a path \( (x_1, x_2, ..., x_{i+1}) \) from the root node to a problem state, then the path cannot be extended to reach an answer node.
- Thus the candidates for position \( i+1 \) of the solution vector \( (x_1, x_2, ..., x_n) \) are those values which are generated by \( T \) and satisfy \( B_{i+1} \).
- The recursive version is initially invoked by Backtrack(1).
    ![Screenshot 2024-05-17 220015](https://github.com/athul-2003/WikiSyllabus/assets/128019369/27df2798-aad6-4ddf-a945-30af1bb2d66a)

- All the possible elements for the kth position of the tuple that satisfy \( B_k \) are generated one by one, and adjoined to the current vector \( (x_1, x_2, ..., x_{k-1}) \).
- Each time \( x_k \) is attached, a check is made to determine whether a solution has been found. Then the algorithm is recursively invoked.
- When the for loop is exited, no more values for \( x_k \) exist and the current copy of Backtrack ends. The last unresolved call now resumes.
- This algorithm causes all solutions to be printed. If only a single solution is desired, then a flag can be added as a parameter to indicate the first occurrence of success.
