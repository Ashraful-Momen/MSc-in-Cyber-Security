# 📘 CNS (Cryptography & Network Security) — Lecture 1 : Complete Note

> **Course Teacher:** Dr. Md. Shafikul Islam (MSI), Assistant Professor, Dept. of Software Engineering, Daffodil International University
> **Source:** CNS-L-1.pptx (44 slides) — Mid-term exam preparation note

---

## 📑 Table of Contents

1. [Cryptography — Basics](#1-cryptography--basics)
2. [Network Security](#2-network-security)
3. [Security Attacks, Services & Mechanisms — Intro](#3-security-attacks-services--mechanisms--intro)
4. [OSI Security Architecture (Layers)](#4-osi-security-architecture-layers)
5. [Security Attacks (Passive vs Active)](#5-security-attacks-passive-vs-active)
6. [Security Services](#6-security-services)
7. [Security Mechanisms (X.800)](#7-security-mechanisms-x800)
8. [Cryptography — Features](#8-cryptography--features)
9. [Symmetric Key Cryptography (DES, AES)](#9-symmetric-key-cryptography-des-aes)
10. [Number Theory](#10-number-theory)
11. [Hash Functions & Hashing (SHA-1, h(k) = k mod m)](#11-hash-functions--hashing)
12. [Asymmetric Key Cryptography (RSA, ECC)](#12-asymmetric-key-cryptography-rsa-ecc)
13. [Conventional Encryption Model / Cryptosystem](#13-conventional-encryption-model--cryptosystem)
14. [Classical Encryption Techniques (Caesar / Shift Cipher)](#14-classical-encryption-techniques)
15. [⚡ Rapid Revision + Likely Exam Questions](#15--rapid-revision--likely-exam-questions)

---

## 1. Cryptography — Basics

### 🔑 Definition (memorize this line)
- **Cryptography** is the **science of protecting information and communications using mathematical algorithms**.
- It **scrambles readable text (plaintext) into an unreadable format (ciphertext)** so that **only authorized parties can decipher it**.
- It is the **backbone of modern cybersecurity, secure web browsing, and cryptocurrencies**.

### ⚙️ How It Works (2 steps)
| Step | Who does it | What happens |
|---|---|---|
| **Encryption** | Sender | Uses a **mathematical algorithm + key** to scramble **Plaintext** (readable data) into unintelligible **Ciphertext** |
| **Decryption** | Authorized receiver | Uses the **corresponding key** to reverse the process → ciphertext becomes readable **plaintext** again |

**Key terms:**
- **Plaintext** = original readable message
- **Ciphertext** = scrambled/encrypted message
- **Key** = secret value used by the algorithm to encrypt/decrypt
- **Cipher** = the algorithm itself

### 🏛️ The 4 Pillars of Cryptography (VERY IMPORTANT — common exam question)
Cryptography goes beyond just hiding messages; it achieves **four core goals**:

1. **Confidentiality** → Unauthorized people **cannot read** the data. *(গোপনীয়তা)*
2. **Integrity** → Data has **not been tampered/altered** in transit. *(অখণ্ডতা)*
3. **Authentication** → **Verifies the identities** of the communicating parties. *(পরিচয় যাচাই)*
4. **Non-repudiation** → Sender **cannot deny** that they sent a message. *(অস্বীকার করতে না পারা)*

> 💡 Memory trick: **C-I-A-N** → "**C**an **I** **A**ctually **N**ot forget?"

### 📊 Main Types of Cryptography (3 types)
1. **Symmetric Encryption**
   - **Single shared secret key** for both encryption **and** decryption.
   - ✅ Fast, ❌ but needs a **secure way to share the key in advance**.
2. **Asymmetric Encryption (Public Key)**
   - Uses a **pair of mathematically related keys**:
     - **Public key** → encrypts the data (anyone can have it)
     - **Private key** → decrypts the data (only the receiver keeps it secretly)
3. **Hashing**
   - **One-way mathematical function** → converts data into a **fixed-length string**.
   - Cannot be reversed.
   - Used mainly to **check data integrity** (making sure a file hasn't been modified).

### 🌍 Common Everyday Uses (real-life applications)
- **HTTPS/TLS** → securing internet browsing & online banking
- **End-to-End Messaging** → WhatsApp, Signal chats
- **Digital Signatures** → authenticating software & digital documents
- **Blockchain & Crypto** → Bitcoin and digital wallets

---

## 2. Network Security

### 🔑 Definition
- **Network security** protects the **usability, integrity, and safety of networks and data**.
- Uses a **layered approach of hardware and software** (e.g., **Firewalls, VPNs**) to block threats like **unauthorized access, malware, and cyberattacks**.

### 🧩 Key Components of Effective Network Security (5 items)
1. **Access Control** → only authorized users/devices can access network resources
2. **Firewalls** → protect the network **perimeter** by controlling incoming/outgoing traffic
3. **Intrusion Prevention Systems (IPS)** → monitor traffic to **detect and block** threats
4. **Encryption** → secure data transmission via protocols like **VPNs**
5. **Regular Security Audits** → identify vulnerabilities & maintain compliance

### ⚠️ Common Network Security Risks & Threats (4 items)
1. **Malware** → malicious software: **ransomware, viruses, worms**
2. **Unauthorized Access** → intruders gaining access to sensitive data
3. **Phishing** → deceptive communication designed to **steal credentials**
4. **DDoS Attacks** → flooding networks to cause **service disruption**

---

## 3. Security Attacks, Services & Mechanisms — Intro

### 🖥️ Computer Security — Definition
- The **collective set of tools** developed to **safeguard data and prevent unauthorized access by hackers** is known as **computer security**.
- Another factor influencing security: **distributed systems** — which rely on networks & communication facilities to transfer data between users ↔ computers and computer ↔ computer.
- Short definition: *Computer security is the protection of computer systems and data from **unauthorized access, misuse, modification, or destruction**.*

### 🆚 Safety vs Security (frequently asked comparison)
| Point | **Safety** | **Security** |
|---|---|---|
| Protects from | **Accidental** harm/hazards | **Intentional** harm |
| Focus | Preventing injuries, accidents, unintentional damage | Preventing deliberate threats/crime |
| Examples | Helmet, seat belts, factory/lab safety rules | Locks, alarms, CCTV, passwords, cybersecurity |
| Goal | Reduce risk from **accidents, mistakes, natural hazards** | Prevent **crime, attacks, theft, unauthorized access** |

> 💡 Easy way: **Safety = accident** (দুর্ঘটনা), **Security = attack** (ইচ্ছাকৃত আক্রমণ)

### 🆚 Threat vs Attack (VERY IMPORTANT definitions)
- **Threat:**
  - A **potential for violation of security**.
  - Exists when there is a **circumstance, capability, action, or event** that **could** breach security and cause harm.
  - → A threat is a **possible danger that might exploit a vulnerability**. *(সম্ভাব্য বিপদ)*
- **Attack:**
  - An **assault on system security that derives from an intelligent threat**.
  - An **intelligent act that is a deliberate attempt** to **evade security services** and **violate the security policy** of a system. (*smart + intentional*)

> 💡 **Threat = possibility (হতে পারে), Attack = execution (ঘটে গেছে)**। সব attack-এর পেছনে একটা threat থাকে, কিন্তু সব threat attack হয় না।

### ❓ To achieve security, we must understand 3 things
| Question | Concept | Meaning |
|---|---|---|
| **What can go wrong?** | **Security Attack** | Any action that **compromises the security** of information owned by an organization |
| **What protection is needed?** | **Security Service** | A processing/communication service that **enhances security** of data processing systems & information transfers; **counters security attacks**; uses one or more **security mechanisms** |
| **How is protection provided?** | **Security Mechanism** | A process (or device) designed to **detect, prevent, or recover from** a security attack |

> 💡 Chain: **Attack হলে → Service দরকার → Mechanism দিয়ে implement করি**

---

## 4. OSI Security Architecture (Layers)

### 🔑 Definition
- **OSI (Open Systems Interconnection) security architecture** = the **framework of protocols, standards, and mechanisms** designed to ensure **security of data and communications** within a network, following the **OSI model's layered approach**.

### 1️⃣ Physical Layer — functions
- **Bit Transmission** → converts 1s and 0s from the Data Link layer into **physical signals** for transmission
- **Hardware Specification** → defines physical components: **cables (copper, fiber), connectors, NICs** (Network Interface Cards)
- **Signaling** → how bits are represented (**voltage levels, light pulses, radio frequencies**) + synchronizes sending/receiving devices
- **Data Rate** → speed (bits per second) & transmission mode (**simplex, half-duplex, full-duplex**)
- **Physical Connection** → establish, maintain, deactivate the physical link

### 2️⃣ Data Link Layer — 2 sub-layers
The data link layer is divided into **two sub-layers**:

1. **LLC — Logical Link Control**
   - Deals with **multiplexing** & flow of data among applications/services
   - Provides **error messages and acknowledgments**
2. **MAC — Media Access Control**
   - Manages **device interaction**, **addressing frames**
   - Controls **physical media access**

> 📌 **Flow:** Data link layer receives **packets** from Network layer → divides them into **frames** → sends frames **bit-by-bit** to the physical layer.

### 3️⃣ Network Layer
- Deals with **logical addressing & routing** of packets between networks (IP addressing, routers).
- (Slide references: geeksforgeeks — "Network Layer in OSI Model")

---

## 5. Security Attacks (Passive vs Active)

### 🔑 Definition
- A **security attack** is **any action that compromises the security of information**.

### 😴 (a) Passive Attacks
- Attacker **only observes data** — reads/listens
- **No modification** of data
- **Difficult to detect** (because nothing changes!) — but easier to prevent (encryption)
- **Goal: Gain information**
- **Examples:**
  - **Eavesdropping** (message contents গোপনে শোনা)
  - **Traffic analysis** (pattern দেখা, কোথায় কত ট্রাফিক যাচ্ছে)

### 😈 (b) Active Attacks
- Attacker **modifies, deletes, or fabricates data**
- **Easier to detect** but **harder to prevent**
- **Goal: Disrupt or damage the system**

### 🔥 Active attacks — 4 Categories (VERY IMPORTANT)

1. **Masquerade**
   - Attacker **pretends to be a legitimate user or system** to gain unauthorized access
   - Via: stolen usernames/passwords, compromised credentials, session hijacking
   - **Example:** A hacker logs into a system using someone else's password
2. **Replay**
   - Attacker **captures a valid message** and **sends it again later** to trick the system
   - **Example:** Recording a valid login message and replaying it to gain access **without knowing the password**
3. **Modification of Messages**
   - Attacker **alters the content** of a message during transmission
   - **Example:** Changing a bank transfer from **$100 → $1000** in transit
4. **Denial of Service (DoS)**
   - Makes a system/network **unavailable to legitimate users** by **overwhelming it with requests** or disrupting operation
   - **Example:** Flooding a website with traffic so real users can't access it

### 📋 Summary Table (memorize!)
| Attack Type | What Happens |
|---|---|
| **Masquerade** | Pretending to be an authorized user |
| **Replay** | Re-sending captured valid data |
| **Modification** | Changing message contents |
| **Denial of Service** | Blocking access to services |

> 💡 Passive = শুধু **দেখা**, Active = **নাড়াচাড়া/নষ্ট করা**

---

## 6. Security Services

### 🔑 Definition
- **Security services** are mechanisms that **protect information and systems against security attacks** and ensure **confidentiality, integrity, authentication, and availability**.
- 📌 Note: Security services are mostly implemented at the **upper layers of the OSI model**.

### The 6 Security Services (with examples)
| # | Service | What it does | Example |
|---|---|---|---|
| 1 | **Authentication** | Ensures the **identity** of a user/system is **genuine** | Login with username & password |
| 2 | **Access Control** | Prevents **unauthorized use of resources** | File permissions (read, write, execute) |
| 3 | **Data Confidentiality** | Protects data from **unauthorized disclosure** | Data encryption |
| 4 | **Data Integrity** | Ensures data is **not altered** during transmission/storage | Hash functions, checksums |
| 5 | **Non-repudiation** | Prevents a sender from **denying an action** they performed | Digital signatures |
| 6 | **Availability** | Systems/services are **available when needed** | Protection against DoS attacks |

### ✅ Security services help to:
- Verify **who you are**
- Control **what you can access**
- Protect **data secrecy**
- Ensure **data is unchanged**
- Provide **proof of actions**
- Keep systems **up and running**

---

## 7. Security Mechanisms (X.800)

### 🔑 Definition
- **Security mechanisms** are the **techniques and methods used to implement security services** and to **detect, prevent, or recover from security attacks** in computer and communication systems.
- According to **ITU-T X.800**, security mechanisms support services like **authentication, confidentiality, integrity, access control, non-repudiation**.

### 📂 Classification — 2 broad classes:
1. **Specific Security Mechanisms** → directly applied to protect data & communication (8 types)
2. **Pervasive Security Mechanisms** → system-wide, support multiple security services (5 types)

### 🔧 A. Specific Security Mechanisms (8)

1. **Encipherment (Encryption)**
   - Transforms data into **unreadable form** using algorithms + keys
   - Purpose: **Confidentiality**
   - Types: **Symmetric (AES, DES)**, **Asymmetric (RSA, ECC)**
   - Used for: protecting data during **transmission and storage**
2. **Digital Signature**
   - Cryptographic technique providing **authentication + integrity + non-repudiation**
   - **Created with sender's PRIVATE key**, **verified with sender's PUBLIC key**
   - Used in: e-mail security, e-commerce, legal documents
3. **Access Control**
   - Only **authorized users** can access resources
   - Methods: **DAC** (Discretionary), **MAC** (Mandatory), **RBAC** (Role-Based)
   - Used in: file systems, databases, networks
4. **Data Integrity Mechanism**
   - Ensures data is **not altered** during transmission/storage
   - Techniques: **Hash functions (SHA-256), MAC (Message Authentication Code), Checksums**
5. **Authentication Exchange**
   - Verifies the **identity of communicating entities**
   - Methods: password-based, **challenge-response protocols**, certificate-based
   - Prevents **masquerade and replay attacks**
6. **Traffic Padding**
   - Hides **traffic patterns** by adding **dummy data**
   - Prevents **traffic analysis** (passive attack!)
   - Used in military & high-security networks
7. **Routing Control**
   - **Selects secure communication paths**, avoids insecure networks
   - Prevents data passing through **untrusted nodes**
8. **Notarization**
   - Uses a **trusted third party** to validate communication
   - Ensures **non-repudiation**
   - Example: **time-stamping services**

### 🌐 B. Pervasive Security Mechanisms (5)

1. **Trusted Functionality**
   - System components behave in a **secure & reliable manner**
   - Includes **TCB (Trusted Computing Base)**; prevents unauthorized actions
2. **Security Labels**
   - Attach **security attributes** to data/resources
   - Example: **Confidential, Secret, Top Secret**
   - Used in military & government systems
3. **Event Detection**
   - Detects **security-relevant events** (e.g., intrusion attempts)
   - Tools: **IDS (Intrusion Detection Systems)**, log monitoring
4. **Security Audit Trail**
   - Maintains **records of security events**
   - Used for **forensic analysis**; supports **accountability**
5. **Security Recovery**
   - **Restores systems after a security failure**
   - Backup systems, disaster recovery plans, fault tolerance

> 💡 Memory trick (Specific-8): **"E-DSA-ATRN"** → **E**ncipherment, **D**igital signature, **A**ccess control, (data) **I**ntegrity... সহজ হিসেবে মনে রাখো: **Encrypt, Sign, Access, Integrity, Authenticate, Pad, Route, Notarize**
> Memory trick (Pervasive-5): **T-L-E-A-R** → **T**rusted, **L**abels, **E**vent, **A**udit, **R**ecovery

---

## 8. Cryptography — Features

### 🔑 Definition (as a security tool)
- Cryptography is an important **computer security tool** that deals with **techniques to store and transmit information** in ways that **prevent unauthorized access or interference**.

### ✨ 6 Features of Cryptography
1. **Confidentiality** → information can be accessed **only by the intended person**, no one else
2. **Non-repudiation** → creator/sender **cannot deny** later that they sent the information
3. **Integrity** → information **cannot be modified** in storage or transit **without detection**
4. **Adaptability** → cryptography **continuously evolves** to stay ahead of security threats & technology
5. **Interoperability** → allows **secure communication between different systems and platforms**
6. **Authentication** → identities of sender & receiver confirmed; **origin/destination** of information confirmed

---

## 9. Symmetric Key Cryptography (DES, AES)

### 🔑 Definition
- An encryption system where **sender and receiver use a single common key** to **encrypt and decrypt** messages.
- ✅ **Faster and simpler**
- ❌ Problem: sender & receiver must **exchange the key securely** somehow (key distribution problem)
- Most popular systems: **DES** and **AES**

### 🔒 DES — Data Encryption Standard
- An **older encryption algorithm**
- (As per slide) converts **64-bit plaintext** into **48-bit encrypted ciphertext**
- Uses **symmetric keys** (same key for encryption & decryption)
- Old by today's standards, but useful as a **basic building block for learning** newer algorithms

> 📝 *Extra knowledge (লিখলে extra নম্বর আসতে পারে): আসল DES স্ট্যান্ডার্ডে 64-bit block-এ 56-bit key ব্যবহার হয়, প্রতি round-এ 48-bit subkey তৈরি হয়। স্লাইডে যা আছে (64→48) সেটাই exam-এ লিখবে।*

### 🔒 AES — Advanced Encryption Standard
- Popular encryption algorithm, **same key** for encryption & decryption (symmetric)
- **Symmetric BLOCK cipher**
- Block sizes: **128 bits, 192 bits, or 256 bits**
- Widely regarded as the **replacement of DES**

> 💡 **DES vs AES quick compare:** DES = older, smaller, weaker • AES = newer, bigger blocks, stronger, current standard

---

## 10. Number Theory

### 🔑 Definition
- Number theory is a **branch of mathematics** that studies **numbers, particularly whole numbers**, and their **properties and relationships**
- Explores **patterns, structures, and behaviors** of numbers in different situations

### 💻 Applications of Number Theory in Computer Science
- **Cryptography** (RSA, ECC — সব asymmetric crypto number theory-র উপর দাঁড়ানো)
- **Hash functions** (modular arithmetic)
- **Random number generation**
- **Error detection & correction codes**

---

## 11. Hash Functions & Hashing

### 🔐 Cryptographic Hash Functions
- **Do NOT require a key**
- Use **mathematical algorithms** to convert messages of **any arbitrary length** into a **fixed-length output** → called **hash value / digest**
- **One-way** → original input **cannot** be derived from the output
- Main use: **data integrity**

#### SHA-1 (Secure Hash Algorithm 1)
- Cryptographic hash function developed by **NSA** (National Security Agency), published by **NIST in 1995**
- Converts **any input** into a fixed-size **160-bit (20-byte)** hash value
- Purpose: ensure **data integrity**

### 🗄️ Hashing Function (data-structure view)
A hashing function is a rule that:
- **Takes a key** (like an ID number, SSN, or name)
- **Converts it into a small number**
- That number tells **where to store or find the data** in memory
- 💡 Think of it like **assigning locker numbers**

**Why use hashing?**
- **Store data quickly**
- **Find data fast — O(1) constant time**
- Instead of searching a long list, we **jump directly** to the correct location

### 📐 Formula
$$h(k) = k \bmod m$$
where **m = number of available memory locations**

### 🧮 Worked Example (from slide — MUST practice!)
**Setup:** 111 lockers numbered 0–110. Customers have SSN numbers.
**Given:** h(k) = k mod 111. Find lockers for SSN **2848** and **9212**.

**Solution:**
- h(2848) = 2848 mod 111 = **73** ✅ *(111 × 25 = 2775; 2848 − 2775 = 73)*
- h(9212) = 9212 mod 111 = **110** *(111 × 82 = 9102; 9212 − 9102 = 110)*

> 💡 **mod = ভাগশেষ (remainder)**। বড় সংখ্যাকে m দিয়ে ভাগ দাও → যত বাকি থাকে, সেটাই answer।

---

## 12. Asymmetric Key Cryptography (RSA, ECC)

### 🔑 Definition
- A **pair of keys** is used to encrypt and decrypt information
- **Sender uses receiver's PUBLIC key to encrypt**
- **Receiver uses own PRIVATE key to decrypt**
- Public & private keys are **different but mathematically related**
- Even if the **public key is known to everyone**, only the intended receiver can decode — because **only they hold the private key**
- Most popular algorithm: **RSA**

### 🔐 RSA (Rivest–Shamir–Adleman)
- Teacher's code example repo: `https://github.com/Shafikcse/Shafik-CNS-RSA-Algorithm.git`

#### ✅ RSA Advantages (5)
1. **Security** → very secure, widely used for secure data transmission
2. **Public-key cryptography** → two different keys; public encrypts, private decrypts
3. **Key exchange** → two parties can exchange a secret key **without sending the key over the network**
4. **Digital signatures** → sender signs with **private key**, receiver verifies with **public key**
5. **Widely used** → online banking, e-commerce, secure communications

#### ❌ RSA Disadvantages (7)
1. **Slow processing speed** → slower than other algorithms, especially with large data
2. **Large key size** → needs big keys for security → more computation & storage
3. **Side-channel attacks** → attacker can leak the private key via **power consumption, EM radiation, timing analysis**
4. **Limited use in some applications** → not suitable for constant encryption/decryption of large data (due to slowness)
5. **Complexity** → sophisticated math, hard to comprehend/use
6. **Key management** → secure administration of the private key is difficult
7. **Quantum computing threat** → quantum computers can potentially break RSA

### 📈 ECC — Elliptic Curve Cryptography
- A type of **asymmetric encryption**
- Provides **strong security with SMALLER keys than RSA**
- **Efficient, fast** → ideal for **devices with limited resources**: smartphones, IoT devices, blockchain wallets
- Widely used in **TLS/SSL** (Transport Layer Security / Secure Sockets Layer) and **cryptocurrencies**
- Lightweight yet powerful

> 💡 **RSA vs ECC:** RSA = বড় key, ধীর • ECC = ছোট key, দ্রুত, mobile/IOT-এ perfect

**Practice tools (from slide):**
- https://anycript.com/
- https://emn178.github.io/online-tools/

---

## 13. Conventional Encryption Model / Cryptosystem

### 🔑 Conventional Encryption Model
- Also known as **symmetric-key / single-key encryption**
- Uses the **same shared secret key** for both **encrypting the plaintext** and **decrypting the ciphertext**

### 🔑 Conventional Cryptosystem
- Also known as **symmetric / secret-key cryptography**
- **Same single key** for encryption + decryption; both sender & receiver **share the secret key**
- ✅ **Fast and efficient** for **bulk data encryption**
- ❌ Challenge: **secure key distribution**
- **Examples: DES, AES**

---

## 14. Classical Encryption Techniques

### 2 Big Families
1. **Substitution Ciphers**
   - **Replace** plaintext letters with **other letters, numbers, or symbols**
   - Original **order stays the same** — but the **identity/character changes**
   - (যেমন: A → D, B → E)
2. **Transposition Ciphers**
   - **Rearrange/re-position** the original plaintext characters
   - Characters **themselves don't change** — only their **positions** change, following a specific complex system
   - (যেমন: MEET → EEMT, অক্ষর একই কিন্তু জায়গা বদল)

> 💡 **Substitution = অক্ষর বদল, Transposition = জায়গা বদল**

### 🏛️ Caesar Cipher — Complete Worked Example (MUST PRACTICE!)

**Problem:** Encrypt **"MEET YOU IN THE PARK"** using the Caesar cipher.

**Step 1 — Replace letters with numbers (A=0, B=1, ... Z=25):**
```
M  E  E  T   Y  O  U   I  N   T  H  E   P  A  R  K
12 4  4  19  24 14 20  8  13  19 7  4   15 0  17 10
```

**Step 2 — Apply f(p) = (p + 3) mod 26 to each number:**
```
12→15, 4→7, 4→7, 19→22, 24→1, 14→17, 20→23, 8→11, 13→16,
19→22, 7→10, 4→7, 15→18, 0→3, 17→20, 10→13
= 15 7 7 22 1 17 23 11 16 22 10 7 18 3 20 13
```

**Step 3 — Translate numbers back to letters:**
```
15=P, 7=H, 7=H, 22=W, 1=B, 17=R, 23=X, 11=L, 16=Q,
22=W, 10=K, 7=H, 18=S, 3=D, 20=U, 13=N
```

### ✅ **Encrypted message: "PHHW BRX LQ WKH SDUN"**

### 🔓 Decryption (getting original back)
- Use the **inverse function f⁻¹**:
$$f^{-1}(p) = (p - 3) \bmod 26$$
- Each letter is **shifted BACK 3 letters**; the first 3 letters (A, B, C → i.e., 0,1,2) wrap to the **last three letters** of the alphabet
- **Decryption** = the process of determining the original message from the encrypted message
- Verify: P(15) − 3 = 12 = M ✓, H(7) − 3 = 4 = E ✓

### 🔀 Generalization — Shift Cipher
- Instead of shifting by 3, shift by any integer **k**:
$$f(p) = (p + k) \bmod 26 \quad \text{(encryption)}$$
$$f^{-1}(p) = (p - k) \bmod 26 \quad \text{(decryption)}$$
- **Caesar cipher = shift cipher with k = 3**
- The integer **k is called the KEY** 🔑

> 💡 Number↔Letter mapping মুখস্থ রাখো: **A=0, B=1, C=2, D=3, E=4, F=5, G=6, H=7, I=8, J=9, K=10, L=11, M=12, N=13, O=14, P=15, Q=16, R=17, S=18, T=19, U=20, V=21, W=22, X=23, Y=24, Z=25**

---

## 15. ⚡ Rapid Revision + Likely Exam Questions

### 🎯 One-line Definitions (write these exactly)
| Term | One-liner |
|---|---|
| Cryptography | Science of protecting information using mathematical algorithms by scrambling plaintext into ciphertext |
| Encryption | Sender uses algorithm + key to turn plaintext into ciphertext |
| Decryption | Receiver uses key to turn ciphertext back to plaintext |
| Network Security | Protects usability, integrity, safety of networks/data using layered hardware+software |
| Computer Security | Protection of systems & data from unauthorized access, misuse, modification, destruction |
| Threat | Potential violation of security — a possible danger that might exploit vulnerability |
| Attack | Intelligent act / deliberate attempt to evade security services & violate security policy |
| Passive Attack | Attacker only observes data, no modification, hard to detect (goal: gain info) |
| Active Attack | Attacker modifies/deletes/fabricates data — easier to detect, harder to prevent |
| Security Service | Service that counters security attacks, enhances security of data processing & transfer |
| Security Mechanism | Process/device to detect, prevent, or recover from a security attack |
| Symmetric Encryption | Single shared secret key for both encryption & decryption |
| Asymmetric Encryption | Key pair — public key encrypts, private key decrypts |
| Hashing | One-way function converting any-length data into fixed-length digest |
| Substitution Cipher | Replaces letters with other letters/symbols (order unchanged) |
| Transposition Cipher | Rearranges positions of characters (characters unchanged) |

### 📐 Formula Sheet
| Formula | Use |
|---|---|
| `f(p) = (p + k) mod 26` | Shift cipher **encryption** (Caesar: k=3) |
| `f⁻¹(p) = (p − k) mod 26` | Shift cipher **decryption** |
| `h(k) = k mod m` | Hash function → memory location (m = number of locations) |

### ❓ Likely Exam Questions
1. Define cryptography. How does it work? *(Section 1)*
2. Explain the 4 pillars/goals of cryptography. *(Section 1)*
3. Differentiate symmetric vs asymmetric encryption. *(Sections 9, 12, 13)*
4. Difference between threat and attack / safety and security. *(Section 3)*
5. What are passive and active attacks? Explain 4 types of active attacks with examples. *(Section 5)*
6. Explain security services with examples (X.800). *(Section 6)*
7. Differentiate specific vs pervasive security mechanisms — list all with purpose. *(Section 7)*
8. Features of cryptography. *(Section 8)*
9. DES vs AES. *(Section 9)*
10. Advantages & disadvantages of RSA. *(Section 12)*
11. What is ECC? Why preferred over RSA for small devices? *(Section 12)*
12. Mathematical problem: Caesar/shift cipher encrypt-decrypt. *(Section 14)*
13. Mathematical problem: h(k) = k mod m locker computation. *(Section 11)*
14. Substitution vs transposition cipher. *(Section 14)*
15. OSI layers: physical layer functions, LLC vs MAC sub-layers. *(Section 4)*

### 🔑 Quick Comparison Tables (last-minute glance)
- **Symmetric** = 1 key, fast, key-distribution problem (DES, AES)
- **Asymmetric** = 2 keys (public+private), slow but secure key exchange & signatures (RSA, ECC)
- **Hashing** = no key, one-way, fixed output, integrity (SHA-1: 160-bit)
- **Passive** = observe only, hard detect (eavesdropping, traffic analysis)
- **Active** = modify data, hard prevent (masquerade, replay, modification, DoS)
- **Threat** = potential danger • **Attack** = deliberate intelligent act
- **DES** = old, 64-bit block • **AES** = new, 128/192/256-bit block (DES-এর replacement)
- **RSA** = secure but slow, big keys, quantum-vulnerable • **ECC** = small keys, fast, mobile/IoT-friendly

---

*✍️ End of Lecture-1 Note — Good luck with your mid-term! 🍀*
