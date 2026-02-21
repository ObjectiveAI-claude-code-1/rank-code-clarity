# rank-code-clarity

## Overview

`rank-code-clarity` is an ObjectiveAI Function that evaluates and ranks code snippets based on their clarity—the degree to which they effectively communicate their purpose and function to human readers. The function takes multiple implementations of the same functionality and produces a ranked ordering from clearest to least clear, enabling developers to make informed decisions about code quality and maintainability.

Code clarity is not merely an aesthetic concern; it directly impacts how quickly team members can understand, maintain, extend, and collaborate on code. `rank-code-clarity` treats clarity as a measurable, objective quality and helps teams establish and maintain high standards for readable, comprehensible code.

## Input

**Type**: Array of strings

**Description**: An array of code snippets to rank by clarity. Each snippet should be a complete, executable piece of code or a self-contained function implementation.

**Format**:
```json
[
  "function calculateTotal(items) { return items.reduce((sum, item) => sum + item.price, 0); }",
  "function calc(i) { var t = 0; for (var x = 0; x < i.length; x++) { t = t + i[x].price; } return t; }",
  "const sumPrices = (items) => items.reduce((acc, { price }) => acc + price, 0);"
]
```

**Requirements**:
- Minimum 2 snippets required
- Each snippet should implement the same or equivalent functionality
- Snippets should be in the same programming language for fair comparison

## Output

**Type**: Array of integers (indices)

**Description**: A ranking of the input code snippets' indices, ordered from clearest to least clear. The array contains the same indices as the input array, but reordered to reflect the clarity ranking.

**Format**:
```json
[2, 0, 1]
```

This means: the snippet at index 2 is clearest, followed by the snippet at index 0, and the snippet at index 1 is least clear.

## What rank-code-clarity Evaluates

The function evaluates code across two fundamental dimensions of clarity:

### 1. Semantic Clarity
Semantic clarity measures how effectively code communicates **what it does** through meaningful naming, logical organization, and explicit intent. This dimension evaluates:
- **Naming Quality**: Do variable names, function names, and identifiers directly convey their purpose and meaning?
- **Intent Communication**: Is the code's purpose immediately obvious without requiring reverse-engineering or inference?
- **Logical Organization**: Does the structure mirror the problem domain and organize concepts in a way that makes relationships clear?
- **Self-Evidence**: Can a reader understand each component's role simply by reading it?

A high semantic clarity score means readers can quickly grasp what the code is intended to do.

### 2. Structural Clarity
Structural clarity measures how effectively code communicates **how it works** through control flow, patterns, and simplicity. This dimension evaluates:
- **Control Flow**: Is the path of execution straightforward and easy to follow?
- **Pattern Recognition**: Does the code follow recognizable conventions and established patterns that experienced developers would recognize?
- **Execution Simplicity**: Is the path from input to output direct and unobscured by unnecessary complexity or deep nesting?
- **Consistency**: Are error handling, loops, conditionals, and branching logic handled predictably and uniformly?

A high structural clarity score means readers can easily trace how the code executes from beginning to end.

## Use Cases

### 1. Code Review and Implementation Selection
When a pull request has multiple implementation approaches or when team members propose different solutions, `rank-code-clarity` helps identify which version will be easiest for the team to maintain and understand. This elevates clarity as a critical factor in code selection alongside correctness and performance.

### 2. Refactoring Guidance
During refactoring efforts, developers can compare their refactored code against the original using `rank-code-clarity` to ensure that refactoring actually improves clarity rather than merely reorganizing code. This ensures refactoring efforts deliver tangible improvements.

### 3. Code Quality Standards
Organizations can use `rank-code-clarity` as part of their code quality assessment frameworks, establishing and enforcing high standards for readable code across teams and projects. It provides objective feedback that supplements subjective code review.

### 4. Educational and Onboarding
New team members learning a codebase benefit from understanding which code patterns their team considers clearest. `rank-code-clarity` accelerates onboarding by making clarity standards explicit and measurable.

### 5. Alternative Approach Evaluation
When exploring different algorithms, libraries, or architectural approaches, developers can compare how clearly each option communicates its logic. This helps identify not just the most performant solution, but the most maintainable one.

### 6. Technical Debt Assessment
As codebases evolve, `rank-code-clarity` can identify sections of code that have drifted from clarity standards, helping teams prioritize technical debt reduction based on comprehensibility impact.

## How It Works

`rank-code-clarity` accomplishes its evaluation through two complementary sub-functions:

- **[{{ .Task0 }}](https://github.com/{{ .Owner }}/{{ .Task0 }})**: Evaluates semantic clarity by analyzing naming conventions, organization, and how obviously intent is communicated
- **[{{ .Task1 }}](https://github.com/{{ .Owner }}/{{ .Task1 }})**: Evaluates structural clarity by analyzing control flow, patterns, and simplicity of execution

Each sub-function independently ranks the code snippets, and the results are combined to produce a final clarity ranking that reflects both what the code communicates and how effectively it communicates it.

## Philosophy

Code is fundamentally a form of communication between humans, and machines are merely the secondary audience. The time investment in making code clear pays dividends throughout a codebase's lifetime—in easier maintenance, faster debugging, smoother collaboration, and reduced cognitive load for every reader. `rank-code-clarity` embodies the principle that clarity is not a luxury feature but a core responsibility of every developer and should be treated as a measurable, objective quality worthy of careful evaluation and continuous improvement.