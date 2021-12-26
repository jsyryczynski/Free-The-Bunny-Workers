The description of the task as provided by google is below. But since its not easy to understand, the goal of this task is to 
provide such an combination of keys to each bunny, that each combination of bunnies (containing at least num_required bunnies)
will have all the keys. And at the same time any combination of lower number of bunnies will not have all the keys.
The number of keys is not provided, but should be as small as possible.

For explanation of algorithm consider what happes when you have exactly (num_required-1) bunnies. For example when:
num_bunnies = 5, num_required = 4. Then all of the bunnies in group (num_required-1) have all the keys but one. That is because if they
had all the keys, they would be able to open the doors by themself. And at the same time the remaining bunnies all have the missing key.
Consider this example where we have (num_required - 1 = 4 - 1 = 3) bunnies (numbered 0,1,2) chosen among 5 bunnies (0,1,2,3,4)

  0 1 2 3 4 5 6 7 8 9 <- keys
0 x x x x x x x x   x
1 x x x x x x x x   x
2 x x x x x x x x   x
---------------------
3                 x
4                 x
^ bunnies

Any combination of (num_required-1) bunnies cannot open the doors by themself. But its enough to add any other bunny, and the doors will open.
One can then connect each such combination with an unique key, because each combination will have a different key missing. That means you will have
(num_bunnies chooses (num_required-1)) unique keys.

The next step is to go through all such combinations of (num_required-1) bunnies and assign a new unique key, to all bunnies NOT in this combination.
The resulting list of keys for each bunny is the result.

There is an additional requirement for the distribution of keys beeing lexicographically least, which only means you have to list the combinations in correct order.


Free the Bunny Workers
======================

You need to free the bunny workers before Commander Lambda's space station explodes! Unfortunately, the Commander was very careful with the 
highest-value workers -- they all work in separate, maximum-security work rooms. The rooms are opened by putting keys into each console, then 
pressing the open button on each console simultaneously. When the open button is pressed, each key opens its corresponding lock on the work room. So, 
the union of the keys in all of the consoles must be all of the keys. The scheme may require multiple copies of one key given to different minions.

The consoles are far enough apart that a separate minion is needed for each one. Fortunately, you have already relieved some bunnies to aid you - and 
even better, you were able to steal the keys while you were working as Commander Lambda's assistant. The problem is, you don't know which 
keys to use at which consoles. The consoles are programmed to know which keys each minion had, to prevent someone from just stealing all of the keys 
and using them blindly. There are signs by the consoles saying how many minions had some keys for the set of consoles. You suspect that Commander 
Lambda has a systematic way to decide which keys to give to each minion such that they could use the consoles.

You need to figure out the scheme that Commander Lambda used to distribute the keys. You know how many minions had keys, and how many consoles are by 
each work room.  You know that Command Lambda wouldn't issue more keys than necessary (beyond what the key distribution scheme requires), and 
that you need as many bunnies with keys as there are consoles to open the work room.

Given the number of bunnies available and the number of locks required to open a work room, write a function solution(num_buns, num_required) which 
returns a specification of how to distribute the keys such that any num_required bunnies can open the locks, but no group of (num_required - 1) 
bunnies can.

Each lock is numbered starting from 0. The keys are numbered the same as the lock they open (so for a duplicate key, the number will repeat, since it 
opens the same lock). For a given bunny, the keys they get is represented as a sorted list of the numbers for the keys. To cover all of the bunnies, 
the final solution is represented by a sorted list of each individual bunny's list of keys.  Find the lexicographically least such key 
distribution - that is, the first bunny should have keys sequentially starting from 0.

num_buns will always be between 1 and 9, and num_required will always be between 0 and 9 (both inclusive).  For example, if you had 3 bunnies and 
required only 1 of them to open the cell, you would give each bunny the same key such that any of the 3 of them would be able to open it, like so:
[
  [0],
  [0],
  [0],
]
If you had 2 bunnies and required both of them to open the cell, they would receive different keys (otherwise they wouldn't both actually be 
required), and your solution would be as follows:
[
  [0],
  [1],
]
Finally, if you had 3 bunnies and required 2 of them to open the cell, then any 2 of the 3 bunnies should have all of the keys necessary to open the 
cell, but no single bunny would be able to do it.  Thus, the solution would be:
[
  [0, 1],
  [0, 2],
  [1, 2],
]

Languages
=========

To provide a Python solution, edit solution.py
To provide a Java solution, edit Solution.java

Test cases
==========
Your code should pass the following test cases.
Note that it may also be run against hidden test cases not shown here.

-- Python cases --
Input:
solution.solution(2, 1)
Output:
    [[0], [0]]

Input:
solution.solution(4, 4)
Output:
    [[0], [1], [2], [3]]

Input:
solution.solution(5, 3)
Output:
    [[0, 1, 2, 3, 4, 5], [0, 1, 2, 6, 7, 8], [0, 3, 4, 6, 7, 9], [1, 3, 5, 6, 8, 9], [2, 4, 5, 7, 8, 9]]

-- Java cases --
Input:
Solution.solution(2, 1)
Output:
    [[0], [0]]

Input:
Solution.solution(5, 3)
Output:
    [[0, 1, 2, 3, 4, 5], [0, 1, 2, 6, 7, 8], [0, 3, 4, 6, 7, 9], [1, 3, 5, 6, 8, 9], [2, 4, 5, 7, 8, 9]]

Input:
Solution.solution(4, 4)
Output:
    [[0], [1], [2], [3]]