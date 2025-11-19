
# EX 1E Multiply Strings
## DATE: 20/09/2025
## AIM:
To write a Java program that multiplies two non-negative integers represented as strings without using built-in BigInteger or converting the inputs to integers directly.

## Algorithm
1. Start the program.
2. Read the two numeric strings num1 and num2 from the user.
3. Use Karatsuba multiplication, a divide-and-conquer algorithm, to multiply large number strings:
4. Implement functions to add, subtract, and shift numeric strings.
5. Recursively split each number string into two halves.
    Compute the products:
    ac,
    bd,
    (a+b) * (c+d)
    Use Karatsuba identity to compute the middle term.
6. Remove leading zeros from the final product.
7. Display the resulting product as a string.
8. End the program.
 

## Program:
```
/*
Program to multiply two numeric strings without using BigInteger
Developed by: Tamizharasi S
Register Number: 212222040170 
*/

import java.util.Scanner;

public class KaratsubaMultiply {

    // Add two numeric strings
    private static String addStrings(String num1, String num2) {
        StringBuilder result = new StringBuilder();
        int carry = 0, i = num1.length() - 1, j = num2.length() - 1;

        while (i >= 0 || j >= 0 || carry != 0) {
            int x = (i >= 0) ? num1.charAt(i--) - '0' : 0;
            int y = (j >= 0) ? num2.charAt(j--) - '0' : 0;
            int sum = x + y + carry;
            result.append(sum % 10);
            carry = sum / 10;
        }

        return result.reverse().toString();
    }

    // Subtract two numeric strings (assume num1 >= num2)
    private static String subtractStrings(String num1, String num2) {
        StringBuilder result = new StringBuilder();
        int borrow = 0, i = num1.length() - 1, j = num2.length() - 1;

        while (i >= 0) {
            int x = num1.charAt(i) - '0';
            int y = (j >= 0) ? num2.charAt(j) - '0' : 0;
            x -= borrow;
            if (x < y) {
                x += 10;
                borrow = 1;
            } else {
                borrow = 0;
            }
            result.append(x - y);
            i--; j--;
        }

        // Remove leading zeros
        while (result.length() > 1 && result.charAt(result.length() - 1) == '0') {
            result.deleteCharAt(result.length() - 1);
        }

        return result.reverse().toString();
    }

    // Append zeros for shifting
    private static String shiftString(String s, int zeros) {
        StringBuilder shifted = new StringBuilder(s);
        for (int i = 0; i < zeros; i++) {
            shifted.append('0');
        }
        return shifted.toString();
    }

    // Recursive Karatsuba function
    private static String karatsuba(String num1, String num2) {
        num1 = num1.replaceFirst("^0+(?!$)", "");
        num2 = num2.replaceFirst("^0+(?!$)", "");

        if (num1.length() == 0 || num2.length() == 0) return "0";

        if (num1.length() == 1 && num2.length() == 1) {
            return Integer.toString((num1.charAt(0) - '0') * (num2.charAt(0) - '0'));
        }

        int maxLen = Math.max(num1.length(), num2.length());
        if (maxLen % 2 != 0) maxLen++;
        num1 = String.format("%" + maxLen + "s", num1).replace(' ', '0');
        num2 = String.format("%" + maxLen + "s", num2).replace(' ', '0');

        int half = maxLen / 2;
        String a = num1.substring(0, half);
        String b = num1.substring(half);
        String c = num2.substring(0, half);
        String d = num2.substring(half);

        String ac = karatsuba(a, c);
        String bd = karatsuba(b, d);
        String ab_cd = karatsuba(addStrings(a, b), addStrings(c, d));
        String ad_plus_bc = subtractStrings(subtractStrings(ab_cd, ac), bd);

        String part1 = shiftString(ac, 2 * (num1.length() - half));
        String part2 = shiftString(ad_plus_bc, num1.length() - half);
        return stripLeadingZeros(addStrings(addStrings(part1, part2), bd));
    }

    // Remove leading zeros
    private static String stripLeadingZeros(String str) {
        return str.replaceFirst("^0+(?!$)", "");
    }

    // Public method
    public static String multiply(String num1, String num2) {
        return karatsuba(num1, num2);
    }

    // Main method to get user input
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        //System.out.print("Enter the first number (num1): ");
        String num1 = scanner.nextLine().trim();

        //System.out.print("Enter the second number (num2): ");
        String num2 = scanner.nextLine().trim();

        String result = multiply(num1, num2);
        System.out.println("Product: " + result);

        scanner.close();
    }
}

```

## Output:

<img width="852" height="270" alt="image" src="https://github.com/user-attachments/assets/d95505d1-36a1-4d06-b719-27282224e093" />


## Result:
The program successfully implemented and the expected output is verified.
