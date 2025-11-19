
# EX 1A Palindrome Number 
## DATE: 22/08/2025
## AIM:
To write a Java program that takes an integer input x from the user and checks whether it is a palindrome, i.e., it reads the same forward and backward.

## Algorithm
1.Start the program.

2.Read an integer x from the user.

3.If x is negative or ends with 0 (but is not 0), it is not a palindrome.

4.Reverse half of the digits of the number.

5.Compare the reversed half with the remaining half.

6.If both halves match, the number is a palindrome.

7.Display the result.

8.End the program.

## Program:
```
/*
Program to check whether a number is a Palindrome
Developed by: Tamizharasi S
Register Number: 212222040170 
*/

import java.util.Scanner;
public class Solution {
    public boolean isPalindrome(int x) {
        if (x < 0 || (x % 10 == 0 && x != 0)) {
            return false;
        }
        int revertedNumber = 0;
        while (x > revertedNumber) {
            revertedNumber = revertedNumber * 10 + x % 10;
            x /= 10;
        }
        return x == revertedNumber || x == revertedNumber / 10;
    }
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int x = scanner.nextInt();
        Solution solution = new Solution();
        System.out.println(solution.isPalindrome(x));
        scanner.close();
    }
}

```

## Output:
<img width="1031" height="231" alt="image" src="https://github.com/user-attachments/assets/0633fe2e-4de7-4721-bdf9-dc485803a61d" />


## Result:
The program successfully checks whether the given integer is a palindrome.
