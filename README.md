## EX-NO-10-Diffie-Hellman-Key-Exchange-Algorithm


## AIM:
To implement the Diffie-Hellman algorithm to securely exchange keys and generate a shared secret key.
## ALGORITHM:
Step 1: Design the Diffie-Hellman key exchange algorithm.
Step 2: Implement the algorithm using C.
Step 3: The Diffie-Hellman algorithm uses a large prime number p and a primitive root g. Both Alice and Bob select private keys and exchange public keys computed using the formula:
Public Key = (g^Private Key) % p
After exchanging public keys, both compute a shared secret key using:
Shared Secret = (Other's Public Key^Private Key) % p
## PROGRAM:
```
#include <stdio.h>
#include <math.h>

int modExp(int base, int exp, int mod) {
    int result = 1;
    base = base % mod;
    while (exp > 0) {
        if (exp % 2 == 1) {
            result = (result * base) % mod;
        }
        exp = exp >> 1;
        base = (base * base) % mod;
    }
    return result;
}

int main() {
   
    int p = 23;  
    int g = 5;   
    
    int a, b;
    printf("Enter Alice's private key: ");
    scanf("%d", &a);
    printf("Enter Bob's private key: ");
    scanf("%d", &b);
    
    int A = modExp(g, a, p);  
    int B = modExp(g, b, p);  
    
    printf("Alice's Public Key: %d\n", A);
    printf("Bob's Public Key: %d\n", B);
    
   
    int sharedKeyAlice = modExp(B, a, p);  
 
    int sharedKeyBob = modExp(A, b, p);   
    
    printf("Shared Secret Key (Alice): %d\n", sharedKeyAlice);
    printf("Shared Secret Key (Bob): %d\n", sharedKeyBob);
    
    if (sharedKeyAlice == sharedKeyBob) {
        printf("Key Exchange Successful! Shared Secret Key: %d\n", sharedKeyAlice);
    } else {
        printf("Key Exchange Failed!\n");
    }
    return 0;
}
```
## OUTPUT:
 
![image](https://github.com/user-attachments/assets/a74a706e-0e74-45a0-9231-86d9a1f21009)

## RESULT:
The program for the Diffie-Hellman algorithm is executed successfully, and Alice and Bob have securely derived a shared secret key.

