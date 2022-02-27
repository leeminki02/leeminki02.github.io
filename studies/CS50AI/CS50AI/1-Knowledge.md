# 1: Knowledge

**Knowledge-based agents:**
agents that reason by operating on internal representations of knowledge

- How can we make AI logical?

## Terms and Symbols

- Sentence: an assertion about the world in a knowledge representation language
- **Propositional Logic**
    - each Propositional Symbols ($P, Q, R$) represents some sentence
    - **Locial Connectives**
        - ¬ (not)
            
            
            | ⁍ | ⁍ |
            | --- | --- |
            | false | true |
            | true | false |
        - ∧(and), ∨(or)
            
            
            | ⁍ | ⁍ | ⁍ | ⁍ |
            | --- | --- | --- | --- |
            | false | false | false | false |
            | false | true | false | true |
            | true | false | false | true |
            | true | true | true | true |
        - **⇒**(implication): implies
            
            
            | ⁍ | ⁍ | ⁍ |
            | --- | --- | --- |
            | false | false | true |
            | false | true | true |
            | true | false | false |
            | true | true | true |
            
            P가 거짓이면 Q의 상태에 무관하게 참이다
            
        - **⇔**(biconditional): if and only if
            
            
            | ⁍ | ⁍ | ⁍ |
            | --- | --- | --- |
            | false | false | true |
            | false | true | false |
            | true | false | false |
            | true | true | true |
- Model: assignment of a truth value to every propositional symbol (a “possible world”)
- Knowledge Base: a set of sentences known by a knowledge-based agent
- Entailment: $\alpha ⊨ \beta$
In every model in which sentence $\alpha$ is true, sentence $\beta$ is also true.
- Inference: the process of deriving new sentences from old ones
    - Example
        
        $P$: It is a Tuesday.
        
        $Q$: It is raining.
        
        $R$: Harry will go for a run.
        
        ---
        
        $KB$: $(P∧ ¬Q) ⇒R$ (P and not Q implies R), $P$, $¬Q$
        
        Inference: $R$
        

### Logical Symbols

| Symbol | Name | Reading | LaTex |
| --- | --- | --- | --- |
| ⁍ | implication | implies | \implies |
| ⁍ | biconditional
equivalence | if and only | \iff |
| ⁍ | not | not | \lnot |
| ⁍ | and | and | \land |
| ⁍ | or | or | \lor |
| ⁍ | entailment | entails | \models |
| ⁍ | for all | for all | \forall |
| ⁍ | exists | exists | \exist |

## Inference Algorithm

Does $KB ⊨\alpha$ ?

**Model Checking Algorithm**

- To determine if $KB ⊨\alpha$ :
    - Enumerate all possible models.
    - If in every model where $KB$ is true, $\alpha$ is true, then $KB$ entails $\alpha$.
    - Otherwise, $KB$ does not entail $\alpha$.
- Example
    
    $P$: It is a Tuesday.
    
    $Q$: It is raining.
    
    $R$: Harry will go for a run.
    
    ---
    
    $KB$: $(P∧ ¬Q) ⇒R$ (P and not Q implies R), $P$, $\lnot Q$
    
    Query: $R$
    
    | ⁍ | ⁍ | ⁍ | ⁍ |
    | --- | --- | --- | --- |
    | false | false | false | false |
    | false | false | true | false |
    | false | true | false | false |
    | false | true | true | false |
    | true | false | false | false |
    | true | false | true | true |
    | true | true | false | false |
    | true | true | true | false |

## Knowledge Engineering

**Example: Clue(board game)**

- People, rooms, weapons
    - One person, room, weapon are in the envelope
    (Consider them as True)
- Propositional Symbols
    - each of possible things that could be in the envelope
- Knowledges that we know
    - $(mustard \lor plum \lor scarlet)$
    - $(ballroom \lor kitchen \lor library)$
    - $(knife \lor revolver \lor wrench)$
    - additional informations gained as game goes on
        - $\lnot plum$
        - $\lnot mustard \lor \lnot library \lor \lnot revolver$
        - ...

**Logic Puzzles**

- Example
    - Gilderoy, Minerva, Pomona and Horace each belong to a different one of the four houses:
    Gryffindor, Hufflepuff, Ravenclaw, and Slytherin House.
    - Gilderoy belongs to Gryffindor or Ravenclaw.
    - Pomona does not belong in Slytherin.
    - Minerva belongs to Gryffindor.
- Propositional Symbols
    - 16 propositional symbols — One cross One
- Knowledges
    - $(PomonaSlytherin \implies \lnot PomonaHufflepuff)$
    - $(MinervaRavenclaw \implies \lnot GilderoyRavenclaw)$
    - $(GilderoyGryffindor \lor GilderoyRavenclaw)$

**Mastermind**

- Example
    - Red, Green, Blue, Yellow
    - 숫자 야구 같은거
    - RBGY → 2
    - BGRY → 0

→ Model Checking Algorithm becomes less and less good as numbers of variables increases.

## Inference Rules

- Modus Ponens
    
    
    | ⁍ | If it is raining, then Harry is inside.
    It is raining. |
    | --- | --- |
    | ⁍ | Harry is inside. |
- And Elimination
    
    
    | ⁍ | Harry is friends with Ron and Hermione. |
    | --- | --- |
    | ⁍ | Harry is friends with Hermione. |
- Double Negation Elimination
    
    
    | ⁍ | It is not true that Harry did not pass the test. |
    | --- | --- |
    | ⁍ | Harry passed the test. |
- Implication Elimination
    
    
    | ⁍ | If it is raining, then Harry is inside. |
    | --- | --- |
    | ⁍ | It is not raining or Harry is inside. |
- Biconditional Elimination
    
    
    | ⁍ | It is raining if and only if Harry is inside. |
    | --- | --- |
    | ⁍ | If it is raining, then Harry is inside.
    If Harry is inside, then it is raining. |
- De Morgan’s Law
    
    
    | ⁍ | It is not true that both Harry and Ron passed the test. |
    | --- | --- |
    | ⁍ | Harry did not pass the test or Ron did not pass the test. |
    
    | ⁍ | It is not true that Harry or Ron passed the test. |
    | --- | --- |
    | ⁍ | Harry did not pass the test and Ron did not pass the test. |
- Distributive Property
    
    
    | ⁍ |
    | --- |
    | ⁍ |
    
    | ⁍ |
    | --- |
    | ⁍ |

## Search and Theorem Proving

- initial state: starting knowledge base
- actions: inference rules
- transition model: new knowledge base after inference
- goal test: check statement we’re trying to prove
- path cost function: number of steps in proof

## Resolution

uses a powerful another inference rule

- Unit Resolution Rule
    
    
    | ⁍
    ⁍ | (Ron is in the Great Hall) ⁍ (Hermione is in the library)
    Ron is not in the Great Hall |
    | --- | --- |
    | ⁍ | Hermione is in the library |

This means that...

| ⁍
⁍ |
| --- |
| ⁍ |

| ⁍
⁍ | (Ron is in the Great Hall) ⁍ (Hermione is in the library)
(Ron is not in the Great Hall) ⁍ (Harry is sleeping) |
| --- | --- |
| ⁍ | (Hermione is in the library) ⁍ (Harry is sleeping) |
- **Clause**: a disjunction of literals
    
    e.g. $P \lor Q \lor R$
    
- **Conjunctive Normal Form**: logical sentence that is a conjunction of clauses
e.g. $(A \lor B \lor C) \land (D \lor \lnot E) \land (F \lor G)$

## Conversion to CNF

- Eliminate biconditionals
    
    turn $(\alpha \iff \beta)$ into $(\alpha \implies \beta) \land (\beta \implies \alpha)$
    
- Eliminate implications
    
    turn $(\alpha \implies \beta)$ into $(\lnot \alpha \lor \beta)$
    
- Move $\lnot$ inwards using De Morgan’s Laws
    
    e.g. turn $\lnot (\alpha \land \beta)$ into $\lnot \alpha \lor \lnot \beta$
    
- Use distributive law to distribute $\lor$ wherever possible
- Example
    - $(P \lor Q) \implies R$
    - $\lnot (P \lor Q) \lor R$ [by eliminate implication]
    - $(\lnot P \lor \lnot Q) \lor R$ [by De Morgan’s Law]
    - $(\lnot P \lor R) \land (\lnot Q \lor R)$ [by distributive law]

## Inference by Resolution

| ⁍
⁍ | ⁍
⁍ | ⁍
⁍ |
| --- | --- | --- |
| ⁍ | ⁍ | ⁍ False, contradiction |
- To determine if $KB \models \alpha$ :
    - Check if $(KB \land \lnot \alpha)$ is a contradiction?
        - If so, then $KB \models \alpha$.
        - Otherwise, no entailment.
- To determine if $KB \models \alpha$ :
    - Convert $(KB \land \lnot \alpha)$ to CNF(Conjuctive Normal Form).
    - Keep checking to see if we can use resolution to produce a new clause.
        - If ever we produce the **empty** clause (equivalent to Flase), we have a contradiction, and $KB \models \alpha$.
        - Otherwise, if we can’t add new clauses, no entailment.

- Example
    
    Does $(A \lor B) \land (\lnot B \lor C) \land (\lnot C)$ entail $A$?
    
    $(A \lor B) \land (\lnot B \lor C) \land (\lnot C) \models A$?
    
    Prove by Contradiction
    
    - $(A \lor B) \land (\lnot B \lor C) \land (\lnot C) \land (\lnot A)$
    - $(A \lor B) \land (\lnot B \lor C) \land (\lnot C) \land (\lnot A) \land (\lnot B)$
    - $(A \lor B) \land (\lnot B \lor C) \land (\lnot C) \land (\lnot A) \land (\lnot B) \land (A)$
    - $(A \lor B) \land (\lnot B \lor C) \land (\lnot C) \land (\lnot A) \land (\lnot B) \land (A) \land ()$
    
    ⇒ Produced the empty clause, which means the statement has contradiction
    
    $\therefore$ $(A \lor B) \land (\lnot B \lor C) \land (\lnot C) \models A$
    

# First-Order Logic

little more powerful than propositional logic

### **Propositional Logic vs First-Order Logic**

- Propositional Logic
    - Propositional Symbols
        
        *MinervaGryffindor
        MinervaHufflepuff
        MinervaRavenclaw
        MinervaSlytherin
        ...*
        
- First-Order Logic
    - Constant Symbol
        
        *Minerva
        Pomona
        Horace
        Gilderoy
        Gryffindor
        Hufflepuff
        Ravenclaw
        Slytherin*
        
    - Predicate Symbol
        
        *Person
        House
        BelongsTo*
        

### Example

- $Person(Minerva)$
”Minerva is a person.”
- $House(Gryffindor)$
”Gryffindor is a house.”
- $\lnot House(Minerva)$
”Minerva is not a house.”
- $BelongsTo(Minerva, Gryffindor)$
”Minerva belongs to Gryffindor.”
    
    → minimize number of symbols to create.
    

### **Additional Features: Quantifiers**

- Universal Qualification
    
    $\forall x. BelongsTo(x,Gryffindor) \implies \lnot BelongsTo(x, Hufflepuff)$
    
    For all objects x, if x belongs to Gryffindor, then x does not belong to Hufflepuff.
    ”Anyone in Gryffindor is not in Hufflepuff.”
    
- Existential Quantification
    
    $\exists x. House(x) \land BelongsTo(Minerva, x)$
    
    There exists an object x such that x is a house and Minerva belongs to x.
    ”Minerva belongs to a house.”
    
- $\forall x. Person(x) \implies (\exist y. House(y) \land BelongsTo(x,y))$
    
    “Every person belongs to a house.”