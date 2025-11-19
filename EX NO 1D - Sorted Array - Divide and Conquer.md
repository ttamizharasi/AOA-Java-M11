
# EX 1D Reverse Pairs using Divide and Conquer Approach.
## DATE: 14/09/2025
## AIM:
To write a Java program that counts the number of reverse pairs in an array.
A reverse pair is defined as a pair (i,j) such that:
  0≤i<j<nums.length
  nums[i]>2×nums[j]

## Algorithm
1. Start the program.
2. Read the number of elements n.
3. Read the array nums of size n.
4. Use a Binary Search Tree (BST) to keep track of processed elements.
5. For each element in the array:
    Search how many previously inserted elements satisfy:
    value > 2 × nums[i]
   Insert the current number into the BST while updating counts.
6. Keep a running count of reverse pairs.
7. Display the total number of reverse pairs.
8. End the program.  

## Program:
```
/*
Program to count reverse pairs in an array
Developed by: Tamizharasi S
Register Number: 212222040170 
*/

import java.util.*;

class Node {
    Node left, right;
    int val;
    int count_ge;

    Node(int val) {
        this.val = val;
        this.count_ge = 1;
        this.left = null;
        this.right = null;
    }
}

public class Solution {

    // Insert into BST and update count_ge (count of greater or equal)
    public static Node insert(Node head, int val) {
        if (head == null)
            return new Node(val);
        else if (val == head.val)
            head.count_ge++;
        else if (val < head.val)
            head.left = insert(head.left, val);
        else {
            head.count_ge++;
            head.right = insert(head.right, val);
        }
        return head;
    }

    // Search how many values in BST are greater than 2 * target
    public static int search(Node head, long target) {
        if (head == null)
            return 0;
        else if (target == head.val)
            return head.count_ge;
        else if (target < head.val)
            return head.count_ge + search(head.left, target);
        else
            return search(head.right, target);
    }

    // Main reverse pairs function
    public static int reversePairs(int[] nums) {
        Node head = null;
        int count = 0;
        for (int i = 0; i < nums.length; i++) {
            count += search(head, 2L * nums[i] + 1);
            head = insert(head, nums[i]);
        }
        return count;
    }

    // Main method to get input from user
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // Read number of elements
        //System.out.print("Enter number of elements: ");
        int n = scanner.nextInt();

        int[] nums = new int[n];
        //System.out.println("Enter the elements:");

        for (int i = 0; i < n; i++)
            nums[i] = scanner.nextInt();

        int result = reversePairs(nums);
        System.out.println("Number of reverse pairs: " + result);
    }
}

```

## Output:
<img width="846" height="451" alt="image" src="https://github.com/user-attachments/assets/cd5f84b9-d5bb-4da2-b8ee-86210e624312" />


## Result:
The program successfully counts the number of reverse pairs where nums[i] > 2 × nums[j].
