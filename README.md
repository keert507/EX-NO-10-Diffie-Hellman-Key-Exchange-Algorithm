# EX-NO-10-Diffie-Hellman-Key-Exchange-Algorithm

## AIM:
To Implement Diffie Hellman Key Exchange Algorithm 

## Algorithm:

1. Diffie-Hellman Key Exchange is used for securely sharing a secret key between two parties over an insecure channel.

2. Initialization: Agree on a large prime number \( p \) and a primitive root \( g \) modulo \( p \) (both are public values).

3. Key Exchange Process: 
   - Each party selects a private key and calculates their public key using the formula \( g^{\text{private key}} \mod p \).
   - Each party then shares their public key with the other.

4. Secret Key Computation: 
   - Each party computes the shared secret key using the received public key and their own private key.

5. Security: The difficulty of computing discrete logarithms ensures that the shared key remains secure even if public values are intercepted.

## Program:

```

#include <stdio.h>

long long power(long long base, long long exp, long long mod)
{
    long long result = 1;
    base = base % mod;
    while (exp > 0)
    {
        if (exp % 2 == 1)
            result = (result * base) % mod;
        base = (base * base) % mod;
        exp = exp / 2;
    }
    return result;
}

int main()
{
    long long p, g, a, b, A, B, secretAlice, secretBob;

    /
    printf("Enter a prime number (p): ");
    scanf("%lld", &p);
    printf("Enter a primitive root of p (g): ");
    scanf("%lld", &g);


    printf("Enter Alice's private key (a): ");
    scanf("%lld", &a);
    printf("Enter Bob's private key (b): ");
    scanf("%lld", &b);

    /* Public keys */
    A = power(g, a, p);   /* A = g^a mod p */
    B = power(g, b, p);   /* B = g^b mod p */

    /* Shared secret key */
    secretAlice = power(B, a, p);   /* B^a mod p */
    secretBob = power(A, b, p);     /* A^b mod p */

    printf("\nAlice's public key: %lld\n", A);
    printf("Bob's public key: %lld\n", B);
    printf("Secret key computed by Alice: %lld\n", secretAlice);
    printf("Secret key computed by Bob: %lld\n", secretBob);

    if (secretAlice == secretBob)
        printf("Key exchange successful. Shared secret key = %lld\n", secretAlice);
    else
        printf("Key exchange failed.\n");

    return 0;
}
```

## Output:

<img width="555" height="435" alt="image" src="https://github.com/user-attachments/assets/92584864-1bc3-46eb-8e36-8367fe4ad9be" />


## Result:
  The program is executed successfully

