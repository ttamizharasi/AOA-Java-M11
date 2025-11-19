
# EX 1C Count Pairs using Brute Force Approach
## DATE: 10/09/2025
## AIM:
To write a Java program that counts the number of pairs 
((i,j), where i<j, such that the absolute difference between nums[i] and nums[j] is equal to k.

## Algorithm
1. Start the program.
2. Read the number of elements n.
3. Read the n integers into the array nums.
4. Read the value of k.
5. nitialize a counter to 0.
6. Use a nested loop:
    For each index i, check every index j > i.
    Calculate |nums[i] - nums[j]|.
    If the result equals k, increment the counter.
7. Print the total count.
8. End the program.
   

## Program:
```
/*
Program to implement Reverse a String
Developed by: Tamizharasi S
Register Number: 212222040170 
*/

import java.util.Scanner;
public class CountPairsWithDifference {
    public static int countKDifference(int[] nums, int k) {
        int count = 0;
        for (int i = 0; i < nums.length; i++) {
            for (int j = i + 1; j < nums.length; j++) {
                if (Math.abs(nums[i] - nums[j]) == k) {
                    count++;
                }
            }
        }
        return count;
    }
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int[] nums = new int[n];
        for (int i = 0; i < n; i++) {
            nums[i] = sc.nextInt();
        }
        int k = sc.nextInt();
        int result = countKDifference(nums, k);
        System.out.println(result);
        sc.close();
    }
}

```

## Output:

<img width="857" height="302" alt="image" src="https://github.com/user-attachments/assets/b0267a09-6300-4725-92b6-8107e8396b23" />


## Result:
The program successfully counts the number of pairs whose absolute difference is equal to k.
