Bowling Challenge in Ruby
=================

This is the week 5 weekend challenge for Makers Academy Bootcamp. <br>

For this challenge we have been asked to make a scoring programme for ten pin bowling. 

Planning
=======

```mermaid

flowchart TD
    A(START HERE Frame Number n)
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
    M(Roll 1)
    N(Roll 2)
    P(Not a spare)
    Q(Next Frame)
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

    subgraph STRIKE
        S --> D
    end
    subgraph NOT A STRIKE
        T --> N
        T --> J
    end
    subgraph TRACKING
        S --> E
        E -->|previous_round| F
        E -->|two_rounds_ago| U
        F -->|Strike| G
        F -->|Spare| H
        J --> V
        V -->|Spare|H
        V -->|Strike|W
    end
    subgraph START
        A --> M
    end
    
    N --> I
    M --> C
    C -->|Yes| S
    S --> Y
    Y -->|Yes_Roll_3| AA
    Y -->|Yes_Roll_2| Z
    Z --> C
    Y -->|No| Q
    
    
    
    C -->|No| T
    I -->|No| P
    P --> J
    P --> Q
    I -->|Yes|R
    R --> K
    K --> L
    L -->|Yes|X
    R --> Q
    
    
    
    AA --> CA
    CA --> BA
    R --> Y
    P --> L


```
