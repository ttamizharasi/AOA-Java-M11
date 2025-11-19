
# EX 1B Perfect Square Checker
## DATE: 2/09/2025
## AIM:
To write a Java program that takes a positive integer num from the user and checks whether it is a perfect square without using any built-in functions like sqrt().

## Algorithm
1. Start the program.
2. Read the integer num from the user.
3. If num < 2, return true (since 1 is a perfect square).
4. Use Newton’s method to approximate the square root:
   Start with x = num / 2.
   While x * x > num, update x using:
   x = (x + num / x) / 2
5. After convergence, check if x * x == num.
6. Print true if it is a perfect square, otherwise false.
7. End the program. 

## Program:
```
/*
Program to check whether a number is a Perfect Square
Developed by: Tamizharasi S
Register Number: 212222040170  
*/

import java.util.Scanner;
public class Solution {
    public boolean isPerfectSquare(int num) {
        if (num < 2) return true;
        long x = num / 2;
        while (x * x > num) {
            x = (x + num / x) / 2;
        }
        return (x * x == num);
    }
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Solution sol = new Solution();
        int num = scanner.nextInt();
        boolean result = sol.isPerfectSquare(num);
        System.out.println(result);
        scanner.close();
    }
}

```

## Output:

<img width="831" height="226" alt="image" src="https://github.com/user-attachments/assets/31642c16-3b2a-4024-b517-251385a9ad22" />


## Result:
The program successfully checks whether the given number is a perfect square without using built-in square-root functions.
