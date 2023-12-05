
## A sorting algorithm written in [[C]]

One of the 3 projects that a [[42]] student unlocks after finishing rank 02 of the common core and the 5th project in my common core.
### Introduction

There are two stacks A and B, the stack A starts with a random number of negative and positive numbers which can't be duplicated and the stack B starts completely empty and the goal is to sort in ascending order into the stack A using only a limited amount of operations.

| Operations      |                                Description                                |
|:--------------- |:-------------------------------------------------------------------------:|
| Swap A (sa)     |             Swap the first two elements at the top of stack A             |
| Swap B (sb)     |             Swap the first two elements at the top of stack B             |
| SS              |                    Swap A and Swap B at the same time                     |
| Push A (pa)     |   Takes the first element of the stack B and inserts it at the top of A   |
| Push B (pb)     |   Takes the first element of the stack A and inserts it at the top of B   |
| Rotate A (ra)   |  Shift up all elements of the stack A the last element becomes the first  |
| Rotate B (rb)   |  Shift up all elements of the stack B the last element becomes the first  |
| RR              |                  Rotate A and Rotate B at the same time                   |
| Reverse A (rra) | Shift down all elements of the stack A the first element becomes the last |
| Reverse B (rrb) | Shift down all elements of the stack B the first element becomes the last |
| RRR             |                 Reverse A and Reverse B at the same time                  |

