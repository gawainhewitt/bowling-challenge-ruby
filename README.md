Bowling Challenge in Ruby
=================

This is the week 5 weekend challenge for Makers Academy Bootcamp. <br>

For this challenge we have been asked to make a scoring programme for ten pin bowling. 

Planning
=======



```mermaid

flowchart TD
    
    C{Is it a strike?}
    S(Yes a strike)
    T(Not a strike)
    D(Log 'strike' in previous_round for next frame)
    EA(Is it round 10?)

    subgraph ROLL_1
        direction LR
        C -->|Yes| S
        C -->|No| T
        subgraph STRIKE
            S --> D
            S --> EA
        end
        subgraph NOT_A_STRIKE
            T 
        end
    end

```

```mermaid

flowchart TD

    I((Is it a Spare?))
    R(Yes a spare)
    P(Not a spare)
    K(Log 'spare' in previous_round for next frame)
    Y(Is it round 10?)


    subgraph ROLL_2
        direction LR
        I -->|Yes|SPARE
        I --> |No|NOT_A_SPARE
        subgraph SPARE
            R --> Y
            R --> K
        end
        subgraph NOT_A_SPARE
            P
        end
    end

```

```mermaid

flowchart TD

    subgraph START
        A(Frame Number n)
    end

```
```mermaid

flowchart TD
    
    DA(Next Frame)

    subgraph NEXT_FRAME
        DA
    end

```

```mermaid

flowchart TD

    subgraph LOG_SCORE
        Log_score
    end
    
```

```mermaid

flowchart TD
    
    E(Did previous rounds have a strike or spare?)
    F(Is the previous_round a strike or spare?)
    G(next frame log 'strike' in two_rounds_ago)
    H(Calculate score for spare in previous round)
    L(Does this frame have a strike in previous_round_roll_2?)
    U(Calculate score for strike two rounds ago)
    V(Did previous rounds have a strike or spare?)
    W(This frame log 'strike' in previous_round_roll_2)
    X(Calculate score for strike in previous round)
    
    subgraph TRACKING
        
        L -->|Yes|X
        E -->|previous_round| F
        E -->|two_rounds_ago| U
        F -->|Strike| G
        F -->|Spare| H
        V -->|Spare|H
        V -->|Strike|W
    end

```

```mermaid

flowchart TD
    
    Z(Round 10 Strike Roll 2)
    AA(Round 10 Roll 3)
    BA(Calculate Final Score)
    CA(How many pins?)

    subgraph ROUND_10
    Z
        AA --> CA
        CA --> BA
    end

```