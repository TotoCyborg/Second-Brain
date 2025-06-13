---
connections:
  - "[[MOC/Inglese]]"
---

**Cryptography** is the study and practice of protecting information so that only those with special knowledge can read or use it. It works by turning a **plaintext** into **ciphertext** through **encryption**, and then back to its original form through **decryption**.

- **Encryption** uses an algorithm (called a cipher) and a **key** to make data unreadable to unauthorised users;

- **Decryption** is the reverse process: it uses the key to restore the original data.

There are two main types of cryptography based on the type of key used:

- **Symmetrical cryptography** uses the **same key** for both encryption and decryption. A good example of an algorithm that works with symmetrical cryptography is RES or Triple DES;
    
- **Asymmetrical cryptography** uses **two related keys**: a **public key** to encrypt and a **private key** to decrypt. An example of asymmetrical cryptography is the **digital signature**: a message signed with the sender’s private key can be verified by anyone using the public key.
    

**Modern cryptography** has four main goals:

1. **Confidentiality**: only the person who should receive the message can read it. Other people cannot understand it;
    
2. **Integrity**: the message must stay the same. It cannot be changed or damaged during transmission;
    
3. **Non-repudiation**: the sender cannot say later that they didn’t send the message. There is proof of who sent it;
    
4. **Authentication**: the sender and the receiver can check each other’s identity. This means they are sure they are talking to the right person.
    