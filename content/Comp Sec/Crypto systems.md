
> [!NOTE]
> a = b mod m if and only if a − b = λ · m for some integer λ.
> (a mod m) + (b mod m) = (a + b) mod m;
   (a mod m) · (b mod m) = (a · b) mod m;
  for every a != 0 mod p, p prime, there exists an integer a^(−1) so that a · a^(−1) = 1 mod p.


==Let p be a prime and a an arbitrary integer. The multiplicative order of a modulo p is the
smallest positive integer n such that a^n = 1 mod p.==

![[Pasted image 20260214094753.png]]

![[Pasted image 20260214095225.png]]

> Cipher text Only
> 	  ↓
> Known Plain text
>       ↓
> Chosen Plain text
>       ↓
> Chosen Cipher text
>       ↓
> Chosen Text (Strongest)


### Substitution technique
It is one in which letters of the plain text is replaced by other letters or numbers or symbols

✅ Advantages of Substitution Cipher
1. Simple to understand and implement
2. More secure than Caesar cipher
3. Large key space (26! possible keys for English alphabet)
4. Harder to break by brute force compared to simple shift cipher

❌ Disadvantages of Substitution Cipher
1. Vulnerable to frequency analysis
    - English letter frequency (E, T, A...) remains visible.
2. Pattern of letters does not change.
3. Not secure against modern computing power.
4. Not suitable for sensitive data.

## **Ceaser Cipher**
substituting the alphabet with the letter standing  three places further down in  the list.
$$
C = E (3,p) = (p+3) mod 26
$$
In general,
$$
C = E(k,p) = (k+p) mod 26 $$
$$
p = D(k,C) = (C-k) mod 26
$$

✅Advantages of Caesar Cipher
1. Very simple and easy to use
2. Easy to implement manually
3. Good for learning basic cryptography concepts
4. Very fast encryption and decryption

 ❌ Disadvantages of Caesar Cipher
5. Very small key space (only 25 possible shifts) 
6. Easily broken using brute force
7. Easily broken using frequency analysis
8. Not secure for real-world applications



#### Permutation Cipher
A permutation of a finite set of elements S is an ordered sequence of all elements of S, with each element appearing exactly once.

#### Transposition Cipher
A transposition cipher is a type of encryption technique in which the positions of the letters in the message are changed, but the letters themselves remain the same.
**The characters are rearranged, not replaced.**
A **transposition cipher** encrypts a message by **reordering the plaintext letters according to a fixed system**, creating ciphertext.
 examples : Rail Fence Cipher, Columnar Transposition Cipher, Double Transposition Cipher

#### Vernam Cipher (stream cipher)
The **Vernam cipher** is a cipher technique that encrypts the plain text by working on the binary level of the text. Although not widely used due to its simplicity and being more prone to be cracked by any outsider, still this cipher holds much value as it is amongst the firstly developed encryption techniques (like the [Caesar cipher](https://www.includehelp.com/cryptography/caesar-cipher.aspx)).

Now, talking about its characteristics and details, **Vernam cipher** is a cipher in which we consider both the plain text and the key string in its binary form.

The following key points can be drawn for the **Vernam cipher**,

- The key chosen here is a string whose length must be either less or equal to the length of the plain text.
- It is a type of [symmetric-key cryptography](https://www.includehelp.com/cryptography/types-of-cryptography-symmetric-and-asymmetric.aspx).
- It is a type of poly-alphabetic cipher, being a part of the [substitution ciphe](https://www.includehelp.com/cryptography/substitution-techniques.aspx)

> [!NOTE] Encryption Process
> - Here, firstly, we convert both our plain text and the key string into its binary form.
> - The key can be either in string form or directly in binary form also.
> - The bits of the key string is repeated again and again until its length becomes equal to that of the plain text.
> - Perform XOR operation between the elements of the plain text with the respective elements of the ley string which hold the same positions.
> - Therefore, the encryption on the plain text to convert it into ciphertext is performed as follows,
>     
$$
 E (Pi , Ki) =  Pi  (XOR)  Ki
$$


> [!NOTE] Decryption Process
> 
> The process of decrypting the ciphertext to convert it back into plain text is performed in the same way as the encryption process. Therefore, the formula for decryption of the text under Vernam cipher is as follows,
> 
$$ 
D (Ci , Ki) =  Ci (XOR)  Ki 
$$

[[Crypto systems [CONTD..]]]


