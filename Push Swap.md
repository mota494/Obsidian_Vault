
## A sorting algorithm written in [[C]]

One of the 3 projects that a [[42]] student unlocks after finishing rank 02 of the common core and the 5th project in my common core.

___

### Installation

If you want to test this code you must have GCC installed since this program uses [[Makefile]]  to compile and git so you can clone my repository.

`git clone https://github.com/mota494/42_push_swap.git`

Just run this command on your terminal than go to the folder created and run `make` after the program compiles just use `./pushswap` and some numbers after it.

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

___
### Norminette

Every 42 project has to be according to the [[Norm]] which is an extended set of rules that the student has to follow, per example, there can't be a function with more than 25 lines, a line can't have more than 80 columns and a file can't have more than 5 [[C]] functions. 

___

### Code Documentation

#### Operations

<b>Swap functions</b>

```C
void    swap_a(t_stack **stack_a)  
{  
   t_stack    *temp;  
   t_stack    *next;  
  
   temp = *stack_a;  //Set temp to the address of the start of stack_a
   next = (*stack_a)->next->next; //Save the address of the node pointed by the second node
   *stack_a = (*stack_a)->next; //Set the start of the stack to the next node
   (*stack_a)->next = temp;  //Set the swapped node to point to the old first node
   (*stack_a)->next->next = next;  //Set the old first node to point to the node that was pointed by the second node
   ft_printf("sa");  
}```

```c
void    swap_ss(t_stack **stack_b, t_stack **stack_a)  
{  
   swap_a(stack_a); //call swap_a
   swap_b(stack_b);  //call swap_b
   ft_printf("ss\n");  
}
```

<b>Rotate functions</b>

```c
void    rotate_a(t_stack **stack_a)  
{  
   t_stack    *last;  
   t_stack    *temp;  
  
   last = *stack_a;
   while (last->next)  
   {  
      last = last->next; //grab the last element of the stack
   }  
   temp = *stack_a;
   *stack_a = (*stack_a)->next; //set the begining of the list to be the second node
   temp->next = NULL; //set the first node to point to NULL  
   last->next = temp;  //set the old last node to point to the old first node
   ft_printf("ra");  
}
```

```c
void    rotate_rr(t_stack **stack_a, t_stack **stack_b)  
{  
   rotate_a(stack_a); //call rotate_a
   rotate_b(stack_b); //call rotate_b
   ft_printf("rr\n");  
}
```

<b>Push Functions</b>

```c
void    push_a(t_stack **stack_a, t_stack **stack_b)  
{  
   t_stack    *temp;  
   t_stack    *snext;  
  
   if (!*stack_b) //check if the stack b has something in it
      return ;  
   temp = *stack_b;  
   *stack_b = (*stack_b)->next; //set the start of the B stack to be the second node
   if (!stack_a)  
   {  
      *stack_a = temp; //set the new start of the A stack to the node from stack B
      (*stack_a)->next = NULL;  
   }  
   else  
   {  
      snext = *stack_a;  
	      *stack_a = temp; //set the new start of the A stack to the node from stack B
      (*stack_a)->next = snext; //point the new start of the stack to the old first node
   }  
}
```

<b>Reverse Rotate Functions</b>

```c
void    reverse_rra(t_stack **stack_a)  
{  
   t_stack    *last;  
   t_stack    *temp;  
  
   last = *stack_a;  
   temp = *stack_a;  
   while (temp->next->next)  
   {  
      temp = temp->next; //grab the third to last element of the stack 
   }  
   while (last->next)  
   {  
      last = last->next; //grab the last element of the stack
   }  
   last->next = *stack_a; //set the last element to point to the first
   *stack_a = last; //set the start of the stack to the last element
   temp->next = NULL; //set the third to last element to point to NULL
   ft_printf("rra\n");  
}
```


```c
void    reverse_rrr(t_stack **stack_a, t_stack **stack_b)  
{  
   reverse_rra(stack_a); //call reverse rotate a
   reverse_rrb(stack_b); //call reverse rotate b
   ft_printf("rrr\n");  
}
```

#### Sorting three numbers

To sort three numbers or less is better  to use a shorter more compact algorithm than a more robust one used to sort thousands of numbers.

With that in mind I "created" an algorithm that works around the position of the maximum value of the stack

```c
void    ft_sort_three(t_stack **stack_a)  
{  
   if (ft_num_elems(stack_a) == ft_node_index(stack_a, max_num(stack_a)))  
   {  
      swap_a(stack_a);  
      return ;  
   }  
   while (ft_num_elems(stack_a) != ft_node_index(stack_a, max_num(stack_a)))  
      reverse_rra(stack_a);  
   if (ft_check_sort(stack_a) == 0)  
      swap_a(stack_a);  
}
```

The function starts with an `if` that checks if the index of the node that has the maximum value is equal to the number of elements present on the stack, if that's the case the only operation we have to do is swap the two top elements and the program ends here.

If the maximum element is not already the last node of the list than the program rotates the stack until the condition is satisfied if after that the stack isn't organized the program swaps the two top elements and it's done.

temp->content % togetmod / (togetmod / 10)