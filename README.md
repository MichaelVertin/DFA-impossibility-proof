# Title
DFA Impossibility Proof: Counterexample & Corrected Method

# Abstract
This project addresses a flaw in a proof-by-contradiction method for showing that no DFA can represent a given language. The original method assumes that if a DFA can produce a string with N instances of a symbol, it must also produce a string with N + 1 instances, which is not necessarily true. This repository presents a counterexample with a valid DFA, and introduces a corrected method that accounts for loop sizes greater than one. The corrected method is robust against such false impossibility proofs and supports more complex loop structures.

# Introduction
A DFA is a finite-state machine that recognizes a regular language. A language is DFA-impossible if no DFA exists that accepts exactly that language. Proving impossibility is an important tool in theoretical computer science, but incorrect proof methods can create contradictions, even among simple languages. This document examines a widely taught impossibility proof method, demonstrates a counterexample that exposes its flaw, and presents a corrected version that eliminates this error.

This correction is important because the original method allows students to both prove and disprove that a language can be represented as a DFA, leading to potential contradictions among student responses. For more complex languages such as identifying a prime number of instances of any symbol, the original method may coincidentally or incorreclty disprove the existince of its DFA. 

# Original Method
Example: 

Language: A^(i)B^(i), where i is an integer

DFA-Impossibility Proof:

Assume the DFA exists for the above langauge. 

It must contain the string "AAA...ABBB...B", where there are m instances of A and m instances of B. 

Because the amount of As is unlimited, it must contain a loop, so the language must accept the string above with **additional As**. 

Therefore, **with one additional A**, it must contain the string "AAAA...ABBB...B", where there are **m+1 instances of A** and m instances of B. 

Because the language only accepts strings with an equal number of instances of A and B, but the language has been proven to contain a string with one more instance of A than B, the assumption that the DFA exists for the language is incorrect. 

The key concept of this method is a proof-by-contradiction by assumming the DFA exists for the language, then using that DFA to generate a string that is not in the language. 

# Counterexample
Language: A^(i)B^(j), where i and j are both odd or both even integers

DFA-Impossibility Proof:

Assume the DFA exists for the above langauge. 

It must contain the string "AAA...ABBB...B", where there are m instances of A and n instances of B, and m and n are even. 

Because the amount of As is unlimited, it must contain a loop, so the language must accept the string above with **additional As**. 

Therefore, **with one additional A**, it must contain the string "AAAA...ABBB...B", where there are **m+1 instances of A** and n instances of B. 

Because the language only accepts strings with even m and n or odd m and n, but the language has been proven to contain a string with odd m and even n, the assumption that the DFA exists for the language is incorrect. 

However, the DFA has shown below has this language, meaning the above proof is incorrect. 

<img width="618" height="453" alt="image" src="https://github.com/user-attachments/assets/596aaa44-03dc-454e-926a-844ec4a56bca" />

Original method implicitly assumes loop size = 1 - incorrect for this DFA.


# Corrected Method
Example:

Language: A^(i)B^(i), where i is an integer

DFA-Impossibility Proof:

Assume the DFA exists for the above langauge. 

It must contain the string "AAA...ABBB...B", where there are m instances of A and m instances of B. 

Because the amount of As is unlimited, it must contain a loop, so the language must accept the string above with **an additional amount of As equal to the size of the loop. Let i be the size of this loop, which must be a positive integer.**

By adding **i additional As**, it must contain the string "AAAA...ABBB...B", where there are **m+i instances of A** and m instances of B. 

Because the language only accepts strings with an equal number of instances of A and B, but the language has been proven to contain a string with i more instances of A than B, where i is greater than 0, the assumption that the DFA exists for the language is incorrect. 


Counter-Example Reattempt:
Language: A^(i)B^(j), where i and j are both odd or both even integers

DFA-Impossibility Proof:

Assume the DFA exists for the above langauge. 

It must contain the string "AAA...ABBB...B", where there are m instances of A and n instances of B, and m and n are even. 

Because the amount of As is unlimited, it must contain a loop, so the language must accept the string above with **an additional amount of As equal to the size of the loop. Let i be the size of this loop, which must be a positive integer.**

By adding **i additional As**, it must contain the string "AAAA...ABBB...B", where there are **m+i instances of A** and n instances of B. 

Here, there does exist an i (2), that maintains the condition of an even n and m or an odd n and m, so DFA-Impossibility was not proven. 

The difference is this method acknowledges that the number of As that can be added is dependent on the unknown loop's size, where the original method assummed by the language must be able to support the addition of exactly one additional A. 

# Restructured Version (Cleaner Design)
The restructured version described in the link below supports generic loops and does not restrict the position of symbol insertion. 

<Link to the separate file containing the “clean” fully-restructured method.>

# Advantages & Impact
1. Cannot prove DFA-Impossibility for languages that can be represented by DFA. 
2. Less restrictive insertion locations. 
3. Supports generic loops. For example, it can represent a loop that repeats ABABAB.... 
4. Clearer use of axioms and theorems to move between steps, making flaws such as the loop size assumption obvious. 
