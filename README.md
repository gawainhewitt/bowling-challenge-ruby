Bowling Challenge in Ruby
=================

This is the week 5 weekend challenge for Makers Academy Bootcamp. <br>

For this challenge we have been asked to make a scoring programme for ten pin bowling. 

Planning
=======

```mermaid

flowchart LR
    
    C{Is it a strike?}
    D(Log 'strike' in previous_round for next frame)
    E(Did previous rounds have a strike or spare?)
    F(Is the previous_round a strike or spare?)
    G(next frame log 'strike' in two_rounds_ago)
    H(Calculate score for spare in previous round)
    I((Is it a Spare?))
    J(Log the score in pins_down)
    K(Log 'spare' in previous_round for next frame)
    L(Does this frame have a strike in previous_round_roll_2?)
    P(Not a spare)
    R(Yes a spare)
    S(Yes a strike)
    T(Not a strike)
    U(Calculate score for strike two rounds ago)
    V(Did previous rounds have a strike or spare?)
    W(This frame log 'strike' in previous_round_roll_2)
    X(Calculate score for strike in previous round)
    Y(Is it round 10?)
    Z(Round 10 Strike Roll 2)
    AA(Round 10 Roll 3)
    BA(Calculate Final Score)
    CA(How many pins?)
    DA(Next Frame)
    EA(Is it round 10?)

    subgraph START
        A(Frame Number n)
    end
    subgraph ROLL_1
        C -->|Yes| S
        C -->|No| T
        subgraph STRIKE
            S --> D
            S --> EA
        end
        subgraph NOT_A_STRIKE
            T --> J
        end
    end
    subgraph ROLL_2
        I -->|Yes|R
        I --> P
        R --> K
        subgraph SPARE
            R --> Y
        end
        subgraph NOT_A_SPARE
            P
        end
    end
    
    subgraph TRACKING
        STRIKE --> E
        E -->|previous_round| F
        E -->|two_rounds_ago| U
        F -->|Strike| G
        F -->|Spare| H
        V -->|Spare|H
        V -->|Strike|W
    end
    subgraph ROUND_10
    Z
        AA --> CA
        CA --> BA
    end
    subgraph NEXT_FRAME
        DA
    end
    
    START --> ROLL_1
    NOT_A_STRIKE --> V
    NOT_A_STRIKE --> ROLL_2
    Y -->|Yes|ROUND_10
    Y -->|No| NEXT_FRAME
    NOT_A_SPARE --> NEXT_FRAME
    EA -->|Yes|ROUND_10
    EA -->|No|NEXT_FRAME
    
    
    P --> J
    K --> L
    L -->|Yes|X
    P --> L

```
