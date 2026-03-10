
## Side by Side Comparison

```
Approach 1 (Insecure):          Approach 2 (Secure):
————————————————————            ————————————————————
Send M + Hash(M)                Send M + Encrypt(Hash(M), PrivKey)
        ↓                               ↓
Hash is PUBLIC                  Encryption needs PRIVATE KEY
        ↓                               ↓
Eve computes Hash(M')           Eve can't encrypt without private key
        ↓                               ↓
Eve replaces hash               Eve can't fake signature
        ↓                               ↓
Bob fooled ❌                   Bob detects tampering ✅
```

![[Pasted image 20260223115444.png]]

This is where most students get confused — let me make it crystal clear:

```
Pre-image Resistance:
——————————————————————————————
Given:   h (just the hash)
Goal:    find M where Hash(M) = h
Attacker starts with: HASH ONLY

Second Pre-image Resistance:
——————————————————————————————
Given:   M1 (a specific message)
Goal:    find M2 where Hash(M2) = Hash(M1)
Attacker starts with: A SPECIFIC MESSAGE

Collision Resistance:
——————————————————————————————
Given:   Nothing!
Goal:    find ANY M1 and M2 where Hash(M1) = Hash(M2)
Attacker starts with: NOTHING — complete freedom!
```
## Weaknesses of Password Schemes

MOV honestly lists these weaknesses — exam important!

```
1. Weak passwords chosen by users
   → "password", "123456", "admin" ❌

2. Password reuse across multiple sites
   → One site breached → all accounts at risk ❌

3. Phishing attacks
   → Fake login page → user enters real password ❌

4. Shoulder surfing
   → Someone watches you type password ❌

5. Brute force
   → Try all combinations until match found ❌
```

## So The Main Points Were:

```
1. Authentication = Proving WHO you are
        ↓
2. Two Types:
   → Entity Authentication (verify the person)
   → Data Origin Authentication (verify the message)
        ↓
3. Three Factors of proving identity:
   → Something you KNOW (password)
   → Something you HAVE (phone/card)
   → Something you ARE (fingerprint)
        ↓
4. Password Schemes — most common method
   → Problems: plaintext storage, dictionary attack, replay attack
   → Solutions: hashing, salting, nonces, timestamps
```

![[Pasted image 20260223192312.png]]
