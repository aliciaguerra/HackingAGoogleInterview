#Question: Deck Shuffling
Given an array of distinct integers, give an algorithm to randomly reorder the integers so that each possible reordering 
is equally unlikely. In other words, given a deck of cards, how can you shuffle them in such a way thatany permutation of
cards is equally unlikely?
Good answer: Go through the elements in order, swapping each element with a random element in the array that does not
appear earlier than the element. This takes O(n) time. 
Note that there are several possible solutions to this problem, as well as several good-looking answers that are incorrect.
For example, a slight modification to the above algorithm whereby one switches the element with any element in the array
does not give each reordering in equality probability. The answer given here is, in my opinion, the best solution. If you
want to see other solutions, click shuffling on Wikipedia.

#Binary Search Trees
A binary search tree is a data structure that keep items in sorted order. It consists of a binary tree. Each node has a 
pointer with two children (one or both of which may be null), an optional pointer to its parent, and one element that is
being stored in the tree. For a bianry search tree to be valid, each node's element must be greater then every element
in its left subtree and less than every element in its right subtree.

To check whether an element appears in a binary search tree, one only need to follow the appropriate links from parent
to child. For example, if we want to search for 15 in the above tree, we start at the root 17. Since 15<17, we move to the
left child, 6. Since 15>6, we move to the right child, 12. Since 15>12, we move to the right child again, 15. Now we have
found the number that we're looking for, so we're done. 

To add an element to a binary search tree, we begin as if we were searching for the element, following the appropriate links
from parent to child. When the desired child is null, we add the element as a new child node. For example, if we were to
add 14 to the above tree, we would go down the tree. Once we reached 15, we would see that the node has no left child, so
we would add 14 as a right child. 

To remove an element to a binary search tree, we first find the node containing the element. If the node has zero children,
we simply remove it. If it has one child, we replace the node with its child. If it has two children, we identify the
next-smaller or next-larger element in the tree (it doesn't matter which), using an algorithm which we do not describe
here for the sake of brevity. We set the element stored in the node to this value. Then, we splice the node that contained the
value from the node from the tree. This will be relatively easy since the node will have at most one child. For example,
to remove 6 from the tree, we first change the node to have the value 3. Then we remove the node that used to have the value
3. Then, we remove the node that used to have the value 3, and we move the left child of the node that used to have the value
6.

A small modification of binary search tree allows it to be used to associate keys with values,as in a hash table. Instead of
storing a single value in a node, one could store a key value in each node. The tree would be ordered based on the node's 
keys.

Interviewers sometimes ask about binary search trees. In addition, binary search trees are often useful as a component 
of an answer to interview questions. The important thing to rememember is that insertion, removal and lookup take 
O(logn) time (where n is the number of elements in the tree), since the height of a well-balanced binary search tree
that periodically reorganizes a BST to ensure a height of O(logn). Many self-balancing BSTs guarantee that BSTs take 
O(logn) time. If you want to learn more about particular types of binary search trees, such as red-black trees, we recommend
looking them up.

#Question: Path Between Nodes in a Binary Tree
Describe an algorithm to find a path from one node in a binary tree to another. 
Good answer: there will always be one path: from the starting node to the lowest common ancestor to the nodes of the second
node.

For each node, keep track of a set of nodes in the binary tree (using a hash table or a BST). At each iteration, for each of the
two current nodes, change the current node to be its parent and add it to the appropriate set. The first elememt that is 
added to one set when it is already present in the other set is the lowest common ancestor. This takes O(logn) time, where n
is the length of a path. For example, if we are finding the lowest common ancestor of 3 and 15 in the above tree, our algorithm
would do the following:

Current Node 1   Current Node 2   Set 1      Set 2
3                     15           3           15
6                     12           3,6        15,12
17                    6            3,6,17     15,12,6

#BitWise Operations
Integers are represented in a computer by using base 2, using only 0's and 1's. Each place in a binary number represents
a power of two. The rightmost bits correspond to 2^0 , the second digit to the right corresponds to 2^1, and so on. 
For example, the number 11000101 in binary is equal to 2^0 + 2^2 + 2^6 + 2^7 = 197. Negative integers can also be represented
in binary; look up two's complement on wikipedia.

There are a few operations that a computer can perform quickly on one or two integers. The first is "bitwise AND" which takes
two integers and returns an integer that has a 1 only in places where both of the inputs had a 1.

 00101011
& 10110010
----------
 00100010
 
 Another operation is "bitwise or", which takes two integers and returns an integer that has a 0 only in places where both
 of the inputs had a 0. For example:
 
  00101011
| 10110010
----------
 10111011
 
 "Bitwise xor" has a 1 in each place where the bits in the two integers is different.  
For example:
 00101011
^ 10110010
----------
 10011001

"Bitwise negation" takes a number and inverts each of the bits. For example:
~ 00101011
----------
 11010100

"Left shifting" takes a binary number, adds a certain number of zeros to the end, and removes the same number of bits 
from the beginning. For example, 00101011 << 4 is equal to 10110000.  Likewise, right shifting takes a binary number, adds a certain 
number of zeros to the beginning, and removes the same number of bits from the 
end.  For instance, 00101011 >>> 4 = 00000010.  Actually, there is a more common 
form of right shifting (the "arithmetic right shift") that replaces the first few bits 
with a copy of the first bit instead of with zeros.  For example, 10110010 >> 4 = 
11111011.
Interviewers like to ask questions related to bitwise logic.  Often, there is a tricky 
way to solve these problems.  Bitwise xor can often be used in a tricky way because 
two identical numbers in an expression involving xor will "cancel out".  For example, 
15 ^ 12 ^ 15 = 12.

#Question: Compute 2^x
How can you quickly compute 2^x?
Good answer: 1 << x (1 left‐shifted by x)

#Question: Is Power of 2
How can you quickly determine whether a number is a power of 2?
Good answer: Check whether x & (x ‐ 1) is 0.If x is not an even power of 2, the 
highest position of x with a 1 will also have a 1 in x ‐ 1; otherwise, x will be 100...0 
and x ‐ 1 will be 011...1; and'ing them together will return 0.
