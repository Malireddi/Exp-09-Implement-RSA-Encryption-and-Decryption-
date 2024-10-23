# Exp-09-Implement-RSA-Encryption-and-Decryption
## AIM:
To implement the RSA algorithm to securely encrypt and decrypt messages using public and private keys.
## ALGORITHM:
### Step 1: 
Get two distinct prime numbers p and q from the user or predefine them. 
### Step 2: 
Calculate the modulus n by multiplying p and q: n=p*q.
### Step 3:
Calculate Euler’s Totient function φ(n): φ(n) = (p-1) * (q-1)
### Step 4:
Choose a public exponent e such that: 1 < e < φ(n) = 1 and gcd(e, φ(n)) = 1(ensure e is coprime with φ(n))
### Step 5:
Calculate the private key d as the modular inverse of e modulo φ(n): d . e ≡ 1(mod φ(n))
### Step 6:
Formulate the public key as the pair (e, n) and the private key as the pair (d, n)
### Step 7:
Ask the user for an alphabetic message to encrypt.
### Step 8:
Convert each character in the message to its ASCII value.
### Step 9:
Encrypt each ASCII value using the formula: C=M^e mod n (where M is the ASCII value and C is the ciphertext)
### Step 10:
Decrypt each ciphertext using the formula: M=C^d mod n (where C is the ciphertext and M is the decrypted ASCII value).
### Step 11:
Convert the decrypted ASCII values back to characters to retrieve the original message. 
### Step 12:
Print the encrypted message and the decrypted message.
### Step 13:
End the program.

## PROGRAM:
## DEVELOPED BY : Nandyala Malyadri Reddy
## REGISTER NO. : 212223100037
```c
#include <stdio.h>
#include <math.h>

// Function to compute GCD (Greatest Common Divisor)
int gcd(int a, int h) {
    int temp;
    while (1) {
        temp = a % h;
        if (temp == 0)
            return h;
        a = h;
        h = temp;
    }
}

int main() {
    printf("Malyadri Reddy - 212223100037\n");

    // Two prime numbers
    int p = 2;
    int q = 5;

    // Public and private keys
    int n = p * q; // n is the modulus for both the public and private keys
    int phi = (p - 1) * (q - 1); // Euler's totient function
    int e = 3; // Public key exponent

    // Find e such that gcd(e, phi) = 1
    while (e < phi) {
        if (gcd(e, phi) == 1)
            break;
        else
            e++;
    }

    // Choose k (integer multiplier)
    int k = 2;

    // Calculate d (Private key)
    int d = (1 + (k * phi)) / e;

    // Message to be encrypted
    int msg = 13;
    printf("Message data = %d\n", msg);

    // Encryption: c = (msg ^ e) % n
    long long c = (long long)pow(msg, e) % n;
    printf("Encrypted data = %lld\n", c);

    // Decryption: m = (c ^ d) % n
    long long m = (long long)pow(c, d) % n;
    printf("Original Message Sent = %lld\n", m);

    return 0;
}
```
## Output:
![image](https://github.com/user-attachments/assets/267a8499-cefb-47a8-8fe5-d186176ca040)




## Result:
The program for RSA encryption and decryption is executed successfully.
