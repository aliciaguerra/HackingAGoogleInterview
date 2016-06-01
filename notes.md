                                                                 BINARY SEARCH
Best Case: O(1)
Average Case: O(logn)
Worse Case: O(logn)
Space Worst Case: O(1) Iterative, O(logn) Recursive
                                             Arrays.binarySearch(int[] a, int key)

                                                          BINARY SEARCH TREE
Access: Average O(logn), Worst O(n)
Search:  Average O(logn), Worst O(n)
Insert:  Average O(logn), Worst O(n)
Delete: Average O(logn), Worst O(n)
Space Worst: O(n)

Depth First Search
Preorder: root, traverse left, traverse right
(can make a duplicate of a BST)
Inorder: traverse left, root, traverse right
(returns values in order)
PostOrder: traverse left, right visit root
(can delete and free an entire binary search tree)

Breadth First Search
-print all nodes at a given level
-print level order traversal of tree

                                                     HASHTABLE
Search: Average O(1), Worst O(n)
Insertion: Average O(1), Worst O(n)
Deletion: Average O(1), Worst O(n)
Space: Worst O(n)

Putting and Pritning out Key-Value Pairs in HashTable

import java.util.*;  
class Solution{  
 public static void main(String args[]){  
   
  Hashtable<Integer,String> hm=new Hashtable<Integer,String>();  
  
  hm.put(100,"Amit");  
  hm.put(102,"Ravi");  
  
  for(Map.Entry m:hm.entrySet()){  
   System.out.println(m.getKey()+" "+m.getValue());  
  }  
 }  
} 


                                              ATOI (STRING TO INTEGER)
Time O(n), Space O(1)
public class Solution {
    public int myAtoi(String str) {
        if (str == null || str.length() == 0) return 0;
        //trim white spaces
        str = str.trim();
        //check whether positive or negative
        int index = 0;
        boolean isNeg = false;
        if (str.charAt(index) == '-') {
            isNeg = true;
            index++;
        } else if (str.charAt(index) == '+') {
            index++;
        }
        //use integer to store the result
        int res = 0;
        //calculate value
        while (index < str.length()) {
            char c = str.charAt(index);
            if (c > '9' || c < '0') return isNeg ? -res : res;
            if (res > Integer.MAX_VALUE / 10) {
                return isNeg ? Integer.MIN_VALUE : Integer.MAX_VALUE;
            } else if (res == Integer.MAX_VALUE / 10) {
                if (isNeg && (c - '0') > 8) return Integer.MIN_VALUE;
                else if (!isNeg && (c - '0') > 7) return Integer.MAX_VALUE;
            }
            res = res * 10 + c - '0';
            index++;
        }
        return isNeg ? -res : res;
    }
}


                                                     REVERSE A STRING
String doesn’t have built-in reverse, but StringBuilder or StringBuffer do (import java.lang.*)
String reversed = new StringBuilder(s).reverse().toString();

                                      SYNCHRONIZED METHOD (JAVA)
When a synchronized method is called, the mutex is locked. When the method is finished, the mutex is unlocked. This ensures that only one synchronized method is called at any given time on an object.

                                                                BIT MANIPULATION
BITWISE AND
-has one only where both of the inputs had a 1
     00101011 
& 10110010 
     ------------ 
     00100010


BITWISE OR
-returns a zero only where both of the inputs had a 0
   00101011 
 | 10110010 
  ------------- 
   10111011


BITWISE XOR
-adds a 1 where the bits are different
      00101011 
   ^ 10110010 
      ---------- 
      10011001

BITWISE NEGATION
-takes a number and inverts each of the bits
~ 00101011 
   ------------ 
   11010100

LEFT SHIFT
-adds
a
certain
number
of
zeros
to
the
end,
and
removes
the
same
number
of
bits
from
 the
beginning
00101011
<<4 is
equal
to
10110000

RIGHT SHIFT
-replaces
the
first
few
bits
 with
a
copy
of
the
first
bit
and shifts the rest over 10110010
>>
4
=
 11111011

ZERO FILL RIGHT SHIFT
-left is moved right by the number of bits specified and the values are filled with zero
 0011 1100 >>>2 will give 0000 1111


COMPUTE 2^x
1<<x (1-left shifted by x)

DETERMINE WHETHER X IS A POWER OF 2
Check
whether
x
&
(x
‐
1)
is
0
KNAPSACK
Number of items
Number of weights
Maximum capcity
Maximum value

TRAVELING SALESMAN
Given a list of cities and the distances between the cities, shortest route to visit each city exactly once
