+++
title = "What is the Algorithm that Protects our Communication Every Day?"
date = "2026-03-02"
author = "Abhay"
cover = ""
tags = []
keywords = ["encryption", "explanation"]
description = "What is the Diffie-Hellman Key Exchange protocol? How is it relevant in today’s world?"
showFullContent = false
readingTime = true
hideComments = false
+++
# Introduction
Every single day, millions of people send messages that can travel almost invisibly across the world in milliseconds. Users of WhatsApp, iMessage, Signal, and many other popular apps are all told their messages are "end-to-end encrypted," but what does that truly mean? What does it mean for communication to have **End-to-End encryption (E2EE)**, and what is going on behind the scenes?

To answer that, one must first define the problem and history at hand. In Ancient Rome, Julius Caesar protected military messages using the Caesar Cipher, a letter shifting technique scrambled such that only someone with the correct shift amount would be able to read it. In World War II, Germany's Enigma device mechanized encryption and the sharing of messages, increasing complexity massively. But one problem still remained throughout all of history: both parties needed to know what that secret, shared key was. There has to have been some communication between the parties at some point so that the secret key could be shared in some way. But how could you share that secret key securely, if you don't have your secured form of communication? The most obvious physical method is to meet in person, but in the world of the computers, people needed a way to share these secret keys without ever meeting or seeing one another. How could one securely share messages over computers otherwise? This issue is known as the key distribution problem. How can we share keys securely over an insecure, unknown middle channel.

A solution did appear however, thanks to the work of Whitfield Diffie and Martin Hellman, who introduced the groundbreaking algorithm for key exchange in their paper *New Directions in Cryptography* (Diffie & Hellman, 1976). Their work outlined how two parties, even over a public channel where a hacker could be listening in, could securely exchange and arrive at a shared secret key. Their solution became known as Diffie-Hellman Key Exchange, and it solved the deeper problem of how two parties could agree on a secret key in the first place without ever meeting each other.

Their solution and cryptography has allowed the internet to become what is is today. It laid the conceptual foundation for modern protocols such as HTTPS and SSH, and is the single most important baseline algorithm in allowing for E2EE in messaging. While we once needed in person meetups, we can now handle communication elegantly with computers and mathematics.

# How does this algorithm work?
![Wikipedia Image showing the algorithm in action with mock numbers](/diffiehellman/wikipic.png)
> (Wikipedia, 2019)

To understand the Diffie-Hellman Key exchange protocol, let's begin by imagining two friends, named Alice and Bob. They want to communicate in private but there is only a public channel where they can exchange messages. Diffie-Hellman allows them to arrive at at a shared secret, symmetric key that can be used to send messages across the network.
> Symmetric Encryption - Encryption where the same key is used to encrypt and decrypt data. In modern computing, it is fast and secure when both the encrypting and decrypting party know the secret key used, but it does not tell us how that secret key should be exchanged in the first place. Diffie-Hellman helps solve this problem.

Let's walk through the protocol step by step:

#### Step 1: Agree on the Public Numbers
Alice and Bob publicly agree on two numbers:
- A **large prime number** `p`
- A **base (generator)** `g`
These public numbers are used for the overall key exchange process, and they are shared in open to the public.
For this example, we will use
- `p = 23` (a prime number)
- `g = 5` (a base number)

#### Step 2: Choose Private Numbers
Next, both Alice and Bob choose their own private numbers, which they will never share.
- Alice chooses a Prime number `a = 4`
- Bob chooses a Prime number `b = 3`
These numbers must remain secret and not leave their computers.

#### Step 3: Create Public Values
Using **modular exponentiation**, Alice and Bob combine their private values with public values to create new numbers to exchange.
- Alice calculates `A = g^a mod p`
    - `A = 5^4 mod 23`
    - `A = 4`
- Bob calculates `B = g^a mod p`
    - `B = 5^3 mod 23`
    - `A = 10`
Alice sends `A` to Bob, while Bob sends `B` to Alice. These calculated values are public and are visible to anyone peering into the public network.

> Modular Exponentiation is a mathematical operation involving exponents and the remainders in division, also called the modulo. Imagine a clock with 12 hours. If you add 3 hours to 11 o'clock, you get 2 o'clock. This is because 11 + 3 = 14, which when divided by 12 gives a remainder of 2. Even if you added 15 hours to 11 o'clock, you would still get 2 o'clock because 11 + 15 = 25, which divided by 12 still gives a remainder of 2. In the context of Diffie-Hellman, modular exponentiation helps create values that are really easy to compute in one direction, (going from 11 to 2 o'clock), but super difficult to go backwards (just because you have 2 o'clock, you can't easily figure out if it came from 11 o'clock + 3 hours, or 11 o'clock + 15 hours, or any other similar combination). This helps keep the algorithm secure, because it is super difficult to take the public values and figure out the private numbers used to make them.

#### Step 4: Compute the Shared Secret Key
Here is where the encryption and mathematical magic happens. Each person receives the other person's public value, and then combines it with their own private number to compute the shared secret key `K`.
- Alice calculates `K = B^a mod p`
    - `K = 10^4 mod 23`
    - `K = 18`
- Bob calculates `K = A^b mod p`
    - `K = 4^3 mod 23`
    - `K = 18`
Even though Alice and Bob use separate calculations to arrive at K, they still arrive at the same K value (TutorialsPoint, 2024). This number `K` can now be used as a symmetric encryption key to securely communicate, and the middle server never learned what `K`, the secret key, ever was!

Here is a visual table representing the steps for this key exchange.

| Alice | Public Middleman / Network | Bob |
|------|-----------------------------|-----|
| Private number `a = 4` | Public parameters `p = 23`, `g = 5` | Private number `b = 33` |
| Computes `A = 5^4 mod 23 = 4` | Values `A` and `B` are transmitted across the network | Computes `B = 5^33 mod 23 = 20` |
| Sends `A = 4` | Anyone can see these numbers | Sends `B = 20` |
| Computes `K = 20^4 mod 23 = 6` | The middleman cannot compute `K` because `a` and `b` remain secret | Computes `K = 4^33 mod 23 = 6` |

#### Further Explanation of the Numbers

**Prime number (`p`)**  
A large prime number is chosen publicly by both parties. Prime numbers are useful in cryptography because modular arithmetic over primes has strong mathematical properties that make reversing exponentiation extremely difficult. 

**Base / Generator (`g`)**  
The base (sometimes called a generator) is another public value used to create exponentiation values. When combined with modular arithmetic, it produces numbers that appear random but still follow predictable mathematical rules for both participants.

**Private numbers (`a` and `b`)**  
Alice and Bob choose a secret number that is never shared. These numbers are core secrets of the exchange. They stay private so that attackers cannot reproduce the calculations needed to generate the shared key.

**Public exchange values (`A` and `B`)**  
These values are calculated using modular exponentiation (`g^a mod p` and `g^b mod p`). They can safely be transmitted over a public network because reversing them to discover `a` or `b` would require solving the **discrete logarithm problem**, which is computationally infeasible for large numbers. Even if an attacker knows `p`, they cannot easily derive the private numbers `a` or `b` from the public values due to the complexity of the discrete logarithm problem (Computerphile, 2017).
> To learn more about the discrete logarithm problem, see this video: https://www.youtube.com/watch?v=SL7J8hPKEWY2MQGI. This problem is the mathematical foundation of the security of the Diffie-Hellman algorithm, and is what makes it so secure against eavesdropping.

**Final shared key (`K`)**  
After receiving the other party’s public value, each participant performs another exponentiation step. Due to the mathematical properties of modular exponentiation: `(B^a mod p) = (A^b mod p)`. Both of these calculations arrive at the same value: `(g^ab mod p)`. This means both parties independently arrive at the same secret value `K`, which can then be used as the symmetric encryption key for secure communication.


# Are there limitations or vulnerabilities?
While the Diffie-Hellman Key Exchange is a powerful tool for secure communication, it is not without its limitations and vulnerabilities. One of the main vulnerabilities is the **Man-in-the-Middle (MitM) attack**, where an attacker intercepts the public values exchanged between Alice and Bob and replaces them with their own. This allows the attacker to establish separate shared keys with both parties, effectively eavesdropping on all communication without either party realizing it. You may have noticed that in this algorithm, there is no actual verification that the one you are communicating with is the person you think it is. The algorithm only ensures that the shared key is secure, but it does not authenticate the parties involved in the exchange.
Real protocols that implement Diffie-Hellman, such as TLS, often include additional steps to authenticate the parties and prevent MitM attacks, such as using digital certificates or pre-shared keys or authentication protocols like the Station-to-Station (STS) protocol. However, if Diffie-Hellman is implemented without proper authentication, it can be vulnerable to such attacks. Man-in-the-Middle attacks do pose a concern, but they can be mitigated with proper authentication mechanisms.

# What are some real life instances where this algorithm is used?
The Diffie-Hellman Key Exchange is widely used in various real-world applications to secure communication. One of the most common applications is in the aforementioned **Transport Layer Security (TLS)** protocol, which is used to secure web traffic (HTTPS). When you visit a secure website, your browser and the server use a form of Diffie-Hellman to establish a shared secret key that encrypts the data transmitted between them. This ensures that information, such as passwords and credit card numbers, cannot be intercepted by attackers.
Another application is in **Virtual Private Networks (VPNs)**, where Diffie-Hellman is used to establish secure tunnels for data transmission over the internet. It is also used in **Secure Shell (SSH)** for secure remote login and command execution. Additionally, many messaging apps that offer end-to-end encryption, such as [WhatsApp](https://www.whatsapp.com/) and [Signal](https://signal.org/), use variations of the Diffie-Hellman algorithm to establish E2EE between users. The algorithm's ability to securely exchange keys over an insecure channel has made it a fundamental component of modern digital security, enabling private communication in a wide range of applications across the internet.

# What are some extensions or variants of this algorithm?
Over the years, several extensions and variants of the Diffie-Hellman Key Exchange have been developed to enhance security and address specific use cases. One notable variant is the **Elliptic Curve Diffie-Hellman (ECDH)**, which uses elliptic curve cryptography to achieve the same level of security as traditional Diffie-Hellman but with smaller key sizes, making it more efficient and faster, especially for mobile devices.
The signal protocol, used in apps like Signal, is an example of a more complex key exchange protocol that builds upon Diffie-Hellman. It incorporates multiple rounds of key exchange and additional cryptographic techniques to provide forward secrecy and resistance against various types of attacks.
> Forward secrecy makes sure that even if a key is compromised in the future, past communication stays secure because the session keys used for encryption are not derived from the long-term key. This is achieved through the use of ephemeral keys that are generated for each session and discarded afterward. (ephemeral keys are temporary keys used for a single session and discarded).
> The signal protocol is computationally, one of the most secure and robust key exchange protocols in use today. To learn more, visit https://signal.org/docs/. The articles on extended triple Diffie-Hellman (X3DH) and the Double Ratchet algorithm are the most relevant. They are technically complex, but these algorithms form the backbone for Signal's E2EE.

# Conclusion
Diffie-Hellman key exchange has revolutionized the way we secure communication in the modern era. The human necessity to send and secure messages between parties in earlier eras has ultimately resulted in incredibly complex and elegant mathematical solutions to be created for today. The encryption that we use for something as simple as texting a friend or opening google.com in orders of magnitude better than the encryption used by Julius Caesar, and we have mathematics and pioneers like Diffie and Hellman to thank for that.

# Works Cited
Computerphile. (2017, December 15). Secret key exchange (Diffie-Hellman) – Computerphile [Video]. YouTube. https://www.youtube.com/watch?v=NmM9HA2MQGI

Diffie, W., & Hellman, M. E. (1976). New directions in cryptography. IEEE Transactions on Information Theory, 22(6), 644–654. https://doi.org/10.1109/TIT.1976.1055638

TutorialsPoint. (2024). Cryptography – Diffie-Hellman algorithm. https://www.tutorialspoint.com/cryptography/cryptography_diffie_hellman_algorithm.htm

Wikipedia contributors. (2019, December 10). Diffie–Hellman key exchange. Wikipedia. https://en.wikipedia.org/wiki/Diffie%E2%80%93Hellman_key_exchange