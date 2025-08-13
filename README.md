# Title
DFA Impossibility Proof: Counterexample & Corrected Method

# Abstract
This project identifies and corrects a flaw in a proof-by-contradiction method for showing that no DFA (Deterministic Finite Automaton) can represent a given language.

The original method incorrectly assumes that if a DFA can generate a string with N instances of a symbol, it must also generate a string with N+1 instances. This assumption fails when a DFA’s loops have size greater than one.

# This repository:
- Presents a counterexample with a valid DFA disproving the flawed method.
- Introduces a corrected proof technique that works for any loop size.
- Demonstrates why the correction avoids false impossibility proofs.

---

# Background
- A DFA recognizes a regular language using a finite set of states.
- A language is DFA-impossible if no DFA can accept exactly that language.
- Proof-by-contradiction is often used to show DFA-impossibility.
- However, a flawed proof method can "prove" and "disprove" the same case, leading to contradictions in even simple scenarios.

---

# Original Method
**Example**:\
**Language**: A^(i)B^(i), where i is an integer

**Steps**:\
Assume the DFA exists for the above langauge. \
It must contain the string "AAA...ABBB...B", where there are m instances of A and m instances of B. \
Because the amount of As is unlimited, it must contain a loop, so the language must accept the string above with **additional As**. \
Therefore, **with one additional A**, it must contain the string "AAAA...ABBB...B", where there are **m+1 instances of A** and m instances of B. \
Because the language only accepts strings with an equal number of instances of A and B, but the language has been proven to contain a string with one more instance of A than B, the assumption that the DFA exists for the language is incorrect. \
The key concept of this method is a proof-by-contradiction by assumming the DFA exists for the language, then using that DFA to generate a string that is not in the language. 

# Counterexample
**Language**: A^(i)B^(j), where i and j are both odd or both even integers

**Steps**:\
Assume the DFA exists for the above langauge. \
It must contain the string "AAA...ABBB...B", where there are m instances of A and n instances of B, and m and n are even. \
Because the amount of As is unlimited, it must contain a loop, so the language must accept the string above with **additional As**. \
Therefore, **with one additional A**, it must contain the string "AAAA...ABBB...B", where there are **m+1 instances of A** and n instances of B. 

**DFA**:\
Because the language only accepts strings with even m and n or odd m and n, but the language has been proven to contain a string with odd m and even n, the assumption that the DFA exists for the language is incorrect. \
However, the DFA has shown below has this language, meaning the above proof is incorrect. \
<img width="618" height="453" alt="image" src="https://github.com/user-attachments/assets/596aaa44-03dc-454e-926a-844ec4a56bca" />\
Original method implicitly assumes loop size = 1: incorrect for this DFA.

# Corrected Method
**Key Change**:\
Let i be the loop size (a positive integer). Adding i instances of a symbol means the counter-proof failed.

**Example:**\
Language: A^(i)B^(i), where i is an integer

**Steps**:\
Assume the DFA exists for the above langauge. \
It must contain the string "AAA...ABBB...B", where there are m instances of A and m instances of B. \
Because the amount of As is unlimited, it must contain a loop, so the language must accept the string above with **an additional amount of As equal to the size of the loop. Let i be the size of this loop, which must be a positive integer.**\
By adding **i additional As**, it must contain the string "AAAA...ABBB...B", where there are **m+i instances of A** and m instances of B. \
Because the language only accepts strings with an equal number of instances of A and B, but the language has been proven to contain a string with i more instances of A than B, where i is greater than 0, the assumption that the DFA exists for the language is incorrect. 

## Counter-Example Reattempt
**Language**: A^(i)B^(j), where i and j are both odd or both even integers\

**Steps:**\
Assume the DFA exists for the above langauge. \
It must contain the string "AAA...ABBB...B", where there are m instances of A and n instances of B, and m and n are even. \
Because the amount of As is unlimited, it must contain a loop, so the language must accept the string above with **an additional amount of As equal to the size of the loop. Let i be the size of this loop, which must be a positive integer.**\
By adding **i additional As**, it must contain the string "AAAA...ABBB...B", where there are **m+i instances of A** and n instances of B. \
Here, there does exist an i (2), that maintains the condition of an even n and m or an odd n and m, so DFA-Impossibility was not proven. \
The difference is this method acknowledges that the number of As that can be added is dependent on the unknown loop's size, where the original method assummed by the language must be able to support the addition of exactly one additional A. 

# Advantages & Impact
1. Prevents false impossibility proofs for representable languages. 
2. Works for any loop size. 
3. Allows insertion at any position in the string.
4. Supports non-uniform loops (e.g. ABABAB...)
5. Structured with clear axioms and theorems, making assumptions explicit

# Reference
A full formalized version with generic loop handling and position flexibility is available:\
[Restructured Proof PDF](https://github.com/MichaelVertin/DFA-impossibility-proof/blob/main/DFA-Impossibility.pdf)
