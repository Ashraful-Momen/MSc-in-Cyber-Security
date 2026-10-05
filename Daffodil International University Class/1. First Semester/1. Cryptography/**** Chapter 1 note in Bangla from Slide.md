# 📘 CNS (Cryptography & Network Security) — Lecture 1 : সম্পূর্ণ নোট (বাংলা)

> **কোর্স শিক্ষক:** Dr. Md. Shafikul Islam (MSI), Assistant Professor, Dept. of Software Engineering, Daffodil International University
> **সোর্স:** CNS-L-1.pptx (৪৪ স্লাইড) — Mid-term exam প্রস্তুতির নোট
> 💡 *টেকনিক্যাল শব্দ English-এ রাখা হয়েছে যেন exam-এ সরাসরি লিখতে পারো।*

---

## 📑 সূচিপত্র

1. [Cryptography — মূল ধারণা](#1-cryptography--মূল-ধারণা)
2. [Network Security (নেটওয়ার্ক নিরাপত্তা)](#2-network-security-নেটওয়ার্ক-নিরাপত্তা)
3. [Security Attacks, Services ও Mechanisms — ভূমিকা](#3-security-attacks-services-ও-mechanisms--ভূমিকা)
4. [OSI Security Architecture (লেয়ার সমূহ)](#4-osi-security-architecture-লেয়ার-সমূহ)
5. [Security Attacks — Passive বনাম Active](#5-security-attacks--passive-বনাম-active)
6. [Security Services (নিরাপত্তা সেবা)](#6-security-services-নিরাপত্তা-সেবা)
7. [Security Mechanisms — X.800](#7-security-mechanisms--x800)
8. [Cryptography-র Features](#8-cryptography-র-features)
9. [Symmetric Key Cryptography — DES, AES](#9-symmetric-key-cryptography--des-aes)
10. [Number Theory (সংখ্যা তত্ত্ব)](#10-number-theory-সংখ্যা-তত্ত্ব)
11. [Hash Functions ও Hashing](#11-hash-functions-ও-hashing)
12. [Asymmetric Key Cryptography — RSA, ECC](#12-asymmetric-key-cryptography--rsa-ecc)
13. [Conventional Encryption Model / Cryptosystem](#13-conventional-encryption-model--cryptosystem)
14. [Classical Encryption Techniques — Caesar/Shift Cipher](#14-classical-encryption-techniques--caesarshift-cipher)
15. [⚡ দ্রুত Revision + সম্ভাব্য Exam প্রশ্ন](#15--দ্রুত-revision--সম্ভাব্য-exam-প্রশ্ন)

---

## 1. Cryptography — মূল ধারণা

### 🔑 Definition (এই লাইনটা মুখস্থ রাখো)
- **Cryptography** হলো এমন একটা **বিজ্ঞান যা mathematical algorithms ব্যবহার করে information ও communication রক্ষা (protect) করে**।
- এটা **পড়ার যোগ্য text (plaintext)-কে পড়ার অযোগ্য রূপে (ciphertext) রূপান্তর (scramble)** করে দেয়, যাতে **শুধুমাত্র authorized (অনুমোদিত) পক্ষই** সেটা পড়তে পারে।
- এটা আধুনিক **cybersecurity, secure web browsing এবং cryptocurrency-র backbone (মূল ভিত্তি)**।

### ⚙️ এটা কীভাবে কাজ করে (২টি ধাপ)
| ধাপ | কে করে | কী হয় |
|---|---|---|
| **Encryption** | প্রেরক (Sender) | একটা **mathematical algorithm + key** ব্যবহার করে **Plaintext** (পড়ার যোগ্য ডেটা)-কে অর্থহীন **Ciphertext**-এ রূপান্তর করে |
| **Decryption** | অনুমোদিত প্রাপক (Receiver) | **সংশ্লিষ্ট key** দিয়ে বিপরীত প্রক্রিয়া চালিয়ে ciphertext-কে আবার পড়ার যোগ্য **plaintext**-এ ফিরিয়ে আনে |

**গুরুত্বপূর্ণ শব্দ:**
- **Plaintext** = আসল পড়ার যোগ্য message
- **Ciphertext** = scrambled/এনক্রিপ্ট করা message
- **Key** = algorithm দিয়ে encrypt/decrypt করার জন্য ব্যবহৃত গোপন মান
- **Cipher** = algorithm নিজে

### 🏛️ Cryptography-র ৪টি Pillar/স্তম্ভ (খুবই গুরুত্বপূর্ণ — common exam প্রশ্ন)
শুধু message লুকানোই নয়, cryptography **৪টি মূল লক্ষ্য** অর্জন করে:

1. **Confidentiality (গোপনীয়তা)** → অননুমোদিত মানুষ **ডেটা পড়তে পারবে না**।
2. **Integrity (অখণ্ডতা)** → ডেটা transit-এর মধ্যে **কোনোভাবে পরিবর্তন/tamper করা হয়নি** তা নিশ্চিত করে।
3. **Authentication (পরিচয় যাচাই)** → যোগাযোগকারী **পক্ষদের পরিচয় যাচাই** করে।
4. **Non-repudiation (অস্বীকৃতি রোধ)** → প্রেরক **message পাঠানো অস্বীকার করতে পারবে না**।

> 💡 মনে রাখার কৌশল: **C-I-A-N** → "**C**an **I** **A**ctually **N**ot forget?"

### 📊 Cryptography-র প্রধান প্রকারভেদ (৩ প্রকার)
1. **Symmetric Encryption (প্রতিসম)**
   - Encrypt ও decrypt — দুটোর জন্যই **একটাই shared secret key**।
   - ✅ দ্রুত (fast), ❌ কিন্তু **আগে থেকে key নিরাপদে শেয়ার করার উপায়** দরকার।
2. **Asymmetric Encryption / Public Key (অপ্রতিসম)**
   - **গাণিতিকভাবে সম্পর্কিত দুটি key-এর জোড়া (pair)** ব্যবহার করে:
     - **Public key** → ডেটা encrypt করে (যার যেকেউ রাখতে পারে)
     - **Private key** → ডেটা decrypt করে (শুধু receiver গোপনে রাখে)
3. **Hashing**
   - **One-way mathematical function** → যেকোনো ডেটাকে **fixed-length string**-এ রূপান্তর করে।
   - একে উল্টানো (reverse) যায় না।
   - মূলত **data integrity যাচাই**-এর জন্য ব্যবহৃত হয় (ফাইল পরিবর্তন হয়েছে কিনা নিশ্চিত করতে)।

### 🌍 দৈনন্দিন জীবনে সাধারণ ব্যবহার (real-life application)
- **HTTPS/TLS** → internet browsing ও online banking নিরাপদ রাখা
- **End-to-End Messaging** → WhatsApp, Signal-এর chat সুরক্ষা
- **Digital Signatures** → software ও digital document authenticate করা
- **Blockchain & Crypto** → Bitcoin এবং digital wallet

---

## 2. Network Security (নেটওয়ার্ক নিরাপত্তা)

### 🔑 Definition
- **Network security** হলো **নেটওয়ার্ক ও ডেটার usability, integrity এবং safety রক্ষা করা**।
- এটি **hardware ও software-এর layered approach** (যেমন: **Firewalls, VPNs**) ব্যবহার করে **unauthorized access, malware এবং cyberattack**-এর মতো threat আটকায়।

### 🧩 কার্যকর Network Security-র মূল উপাদান (৫টি)
1. **Access Control** → শুধুমাত্র authorized user/device-রাই network resource ব্যবহার করতে পারবে
2. **Firewalls** → incoming/outgoing traffic নিয়ন্ত্রণ করে **network-এর perimeter (সীমানা)** রক্ষা করে
3. **Intrusion Prevention Systems (IPS)** → traffic monitor করে threat **শনাক্ত (detect) ও ব্লক** করে
4. **Encryption** → **VPN**-এর মতো protocol দিয়ে ডেটা transmission নিরাপদ করা
5. **Regular Security Audits** → vulnerability (দুর্বলতা) খুঁজে বের করা ও compliance বজায় রাখা

### ⚠️ সাধারণ Network Security Risk ও Threat (৪টি)
1. **Malware** → ক্ষতিকর software: **ransomware, viruses, worms**
2. **Unauthorized Access** → intruder (অনুপ্রবেশকারী) গুরুত্বপূর্ণ ডেটায় access নেওয়া
3. **Phishing** → **credential (লগইন তথ্য) চুরির জন্য প্রতারণামূলক যোগাযোগ** (fake email/SMS)
4. **DDoS Attacks** → সেবা বিঘ্নিত করতে নেটওয়ার্কে **ভয়াবহ ট্রাফিক প্রবাহ (flooding)**

---

## 3. Security Attacks, Services ও Mechanisms — ভূমিকা

### 🖥️ Computer Security — Definition
- **hacker-দের unauthorized access ঠেকাতে ও ডেটা রক্ষায় তৈরি tools-এর সমষ্টিকে** বলা হয় **computer security**।
- Security-কে প্রভাবিত করা আরেকটি বিষয়: **distributed systems** — যা user ↔ computer এবং computer ↔ computer-এর মধ্যে ডেটা transfer-এর জন্য network ও communication facility ব্যবহার করে।
- ছোট definition: *Computer security হলো computer system ও ডেটাকে **unauthorized access, misuse, modification বা destruction** থেকে রক্ষা করা।*

### 🆚 Safety বনাম Security (প্রায়ই exam-এ আসে)
| বিষয় | **Safety (নিরাপত্তা-দুর্ঘটনা)** | **Security (নিরাপত্তা-হামলা)** |
|---|---|---|
| কী থেকে রক্ষা | **দুর্ঘটনাজনিত** ক্ষতি | **ইচ্ছাকৃত (intentional)** ক্ষতি |
| ফোকাস | আঘাত, দুর্ঘটনা, অনিচ্ছাকৃত ক্ষতি প্রতিরোধ | সচেতন threat/অপরাধ প্রতিরোধ |
| উদাহরণ | হেলমেট, seat belt, কারখানা/ল্যাবের safety rule | Lock, alarm, CCTV, password, cybersecurity |
| লক্ষ্য | **দুর্ঘটনা, ভুল, প্রাকৃতিক বিপদের** ঝুঁকি কমানো | **অপরাধ, attack, চুরি, unauthorized access** ঠেকানো |

> 💡 সহজ কথায়: **Safety = দুর্ঘটনা (accident)**, **Security = হামলা (attack)**

### 🆚 Threat বনাম Attack (খুবই গুরুত্বপূর্ণ definition)
- **Threat (হুমকি):**
  - নিরাপত্তা লঙ্ঘনের **সম্ভাবনা (potential)**।
  - যখন এমন কোনো **পরিস্থিতি, সামর্থ্য, কাজ বা ঘটনা থাকে যা security ভেঙে ক্ষতি করতে পারে**, তখন threat বিদ্যমান।
  - → Threat হলো **এমন একটা সম্ভাব্য বিপদ যা vulnerability (দুর্বলতা)-কে কাজে লাগাতে পারে**।
- **Attack (আক্রমণ):**
  - **Intelligent threat থেকে উদ্ভূত system security-এর উপর আক্রমণ**।
  - অর্থাৎ **security service এড়িয়ে যাওয়ার এবং system-এর security policy ভঙ্গ করার একটা সচেতন (deliberate) ও বুদ্ধিমত্তাপূর্ণ চেষ্টা**।

> 💡 **Threat = সম্ভাবনা (হতে পারে), Attack = বাস্তবায়ন (ঘটে গেছে)**। প্রতিটা attack-এর পেছনে একটা threat থাকে, কিন্তু সব threat-ই attack হয় না।

### ❓ Security অর্জন করতে ৩টি বিষয় বুঝতে হবে
| প্রশ্ন | ধারণা | অর্থ |
|---|---|---|
| **কী ভুল হতে পারে?** | **Security Attack** | কোনো প্রতিষ্ঠানের information-এর security **ক্ষুণ্ণ করে এমন যেকোনো কাজ** |
| **কী ধরনের সুরক্ষা দরকার?** | **Security Service** | এমন একটি processing/communication service যা ডেটা processing system ও information transfer-এর security **বাড়ায়**; **security attack প্রতিহত করে**; এক বা একাধিক **security mechanism** ব্যবহার করে |
| **সুরক্ষা কীভাবে দেওয়া হয়?** | **Security Mechanism** | এমন একটি process (বা device) যা security attack **শনাক্ত (detect), প্রতিরোধ (prevent) বা পুনরুদ্ধার (recover)** করার জন্য ডিজাইন করা |

> 💡 চেইন: **Attack হলে → Service দরকার → Mechanism দিয়ে implement করি**

---

## 4. OSI Security Architecture (লেয়ার সমূহ)

### 🔑 Definition
- **OSI (Open Systems Interconnection) security architecture** = **protocols, standards ও mechanisms-এর একটি framework** যা **OSI model-এর layered approach অনুসরণ করে** নেটওয়ার্কের ভিতরে **ডেটা ও যোগাযোগের নিরাপত্তা** নিশ্চিত করে।

### 1️⃣ Physical Layer — কাজসমূহ
- **Bit Transmission** → Data Link layer-এর 1 ও 0-কে transmission-এর জন্য **physical signal-এ রূপান্তর** করে
- **Hardware Specification** → physical উপাদান নির্ধারণ করে: **cable (copper, fiber), connector, NIC** (Network Interface Card)
- **Signaling** → bit কীভাবে প্রকাশ পাবে (**voltage level, light pulse, radio frequency**) + sender/receiver device-এর synchronization
- **Data Rate** → speed (bits per second) ও transmission mode (**simplex, half-duplex, full-duplex**)
- **Physical Connection** → device-এর মধ্যে physical link **তৈরি, বজায় ও বন্ধ** করা

### 2️⃣ Data Link Layer — ২টি sub-layer
Data Link layer-কে **দুটি sub-layer-এ ভাগ করা হয়েছে**:

1. **LLC — Logical Link Control**
   - **Multiplexing** ও application/সার্ভিসের মধ্যে **ডেটার প্রবাহ (flow)** নিয়ন্ত্রণ করে
   - **Error message ও acknowledgment** প্রদান করে
2. **MAC — Media Access Control**
   - **Device-এর interaction পরিচালনা**, **frame-এ addressing** করে
   - **Physical media-তে access নিয়ন্ত্রণ** করে

> 📌 **প্রবাহ (Flow):** Data Link layer Network layer থেকে **packet** পায় → সেগুলোকে **frame-এ ভাগ** করে → frame গুলো **bit-by-bit** করে নিচের physical layer-কে পাঠায়।

### 3️⃣ Network Layer
- **Logical addressing ও routing** নিয়ে কাজ করে — বিভিন্ন নেটওয়ার্কের মধ্যে packet পৌঁছে দেয় (IP address, router)।
- (স্লাইড রেফারেন্স: geeksforgeeks — "Network Layer in OSI Model")

---

## 5. Security Attacks — Passive বনাম Active

### 🔑 Definition
- **Security attack** হলো **information-এর security ক্ষুণ্ণকারী যেকোনো কাজ**।

### 😴 (a) Passive Attack (নিষ্ক্রিয় আক্রমণ)
- Attacker **শুধুমাত্র ডেটা observe (দেখে/শোনে)**
- ডেটার **কোনো modification হয় না**
- **শনাক্ত করা কঠিন** (কারণ কিছুই বদলায় না!) — কিন্তু ঠেকানো তুলনামূলক সহজ (encryption দিয়ে)
- **লক্ষ্য (Goal): তথ্য সংগ্রহ (Gain information)**
- **উদাহরণ:**
  - **Eavesdropping** (message-এর বিষয়বস্তু গোপনে শোনা/পড়া)
  - **Traffic analysis** (traffic-এর pattern বিশ্লেষণ — কোথায় কত ডেটা যাচ্ছে)

### 😈 (b) Active Attack (সক্রিয় আক্রমণ)
- Attacker **ডেটা modify, delete বা fabricate (নকল তৈরি) করে**
- **শনাক্ত করা সহজ (easier to detect)** কিন্তু **ঠেকানো কঠিন (harder to prevent)**
- **লক্ষ্য (Goal): সিস্টেম বিঘ্নিত বা ক্ষতিগ্রস্ত করা**

### 🔥 Active Attack-এর ৪টি প্রকার (খুবই গুরুত্বপূর্ণ)

1. **Masquerade (ছদ্মবেশ)**
   - Attacker **নিজেকে একজন legitimate (বৈধ) user বা system হিসেবে দেখায়** যাতে unauthorized access পাওয়া যায়
   - উপায়: চুরি করা username/password, compromised login credential, session hijacking
   - **উদাহরণ:** হ্যাকার অন্য কারো password দিয়ে system-এ login করে
2. **Replay (পুনঃপ্রেরণ)**
   - Attacker একটা **valid (বৈধ) message ধরে রাখে (capture)** এবং **পরে আবার পাঠিয়ে** system-কে ধোঁকা দেয়
   - **উদাহরণ:** একটা valid login message record করে সেটা আবার replay করা — **password না জেনেই** access পাওয়া
3. **Modification of Messages (বার্তা পরিবর্তন)**
   - Transmission-এর মধ্যে attacker **message-এর content বদলে দেয়**
   - **উদাহরণ:** ব্যাংক ট্রান্সফারের সময় **$100 → $1000** করে দেওয়া
4. **Denial of Service (DoS — সেবা প্রত্যাখ্যান)**
   - **ভয়াবহ পরিমাণ request পাঠিয়ে বা operation ব্যাহত করে** system/network-কে **বৈধ user-দের জন্য অনুপলব্ধ** করে তোলে
   - **উদাহরণ:** ওয়েবসাইটে বিশাল traffic পাঠিয়ে সত্যিকারের user-দের ঢুকতে না দেওয়া

### 📋 সারণি (Summary Table — মুখস্থ করো!)
| Attack Type | কী হয় |
|---|---|
| **Masquerade** | বৈধ user সেজে নেওয়া (পরিচয় চুরি) |
| **Replay** | ধরে রাখা valid ডেটা আবার পাঠানো |
| **Modification** | Message-এর content বদলে দেওয়া |
| **Denial of Service** | সেবায় access আটকে দেওয়া |

> 💡 Passive = শুধু **দেখা**, Active = **নাড়াচাড়া/নষ্ট করা**

---

## 6. Security Services (নিরাপত্তা সেবা)

### 🔑 Definition
- **Security services** হলো এমন mechanism যা **security attack থেকে information ও system রক্ষা করে** এবং **confidentiality, integrity, authentication ও availability** নিশ্চিত করে।
- 📌 মনে রাখো: Security service গুলো মূলত OSI model-এর **উপরের লেয়ারগুলোতে (upper layers)** implement করা হয়।

### ৬টি Security Service (উদাহরণসহ)
| # | Service | কী করে | উদাহরণ |
|---|---|---|---|
| 1 | **Authentication** | User/system-এর **পরিচয় সত্যিকারের (genuine)** কিনা নিশ্চিত করে | Username ও password দিয়ে login |
| 2 | **Access Control** | **Resource-এর unauthorized ব্যবহার ঠেকায়** | File permission (read, write, execute) |
| 3 | **Data Confidentiality** | **অননুমোদিত প্রকাশ (disclosure)** থেকে ডেটা রক্ষা করে | Data encryption |
| 4 | **Data Integrity** | Transmission/storage-এর মধ্যে ডেটা **পরিবর্তিত হয়নি** তা নিশ্চিত করে | Hash function, checksum |
| 5 | **Non-repudiation** | প্রেরক তার **করা কাজ অস্বীকার করতে পারে না** | Digital signature |
| 6 | **Availability** | প্রয়োজনের সময় **system/service উপলব্ধ থাকে** | DoS attack থেকে সুরক্ষা |

### ✅ Security service গুলো যা করে দেয়:
- যাচাই করে **তুমি কে (who you are)**
- নিয়ন্ত্রণ করে **তুমি কী ব্যবহার করতে পারবে**
- রক্ষা করে **ডেটার গোপনীয়তা**
- নিশ্চিত করে **ডেটা অপরিবর্তিত আছে**
- **কর্মের প্রমাণ** দেয়
- **system চালু ও চালু রাখে**

---

## 7. Security Mechanisms — X.800

### 🔑 Definition
- **Security mechanism** হলো এমন **technique ও method যা security service implement করতে ব্যবহৃত হয়** এবং computer ও communication system-এ **security attack detect, prevent বা recover** করে।
- **ITU-T X.800** অনুযায়ী, security mechanism গুলো **authentication, confidentiality, integrity, access control ও non-repudiation**-এর মতো service-কে সাপোর্ট করে।

### 📂 শ্রেণিবিভাগ — ২টি প্রধান ভাগ:
1. **Specific Security Mechanisms** → ডেটা ও communication রক্ষায় **সরাসরি (directly) প্রয়োগ** করা হয় (৮টি)
2. **Pervasive Security Mechanisms** → **পুরো system-জুড়ে (system-wide)** থাকে, একাধিক security service-কে সাপোর্ট করে (৫টি)

### 🔧 ক. Specific Security Mechanisms (৮টি)

1. **Encipherment (Encryption)**
   - Algorithm + key দিয়ে ডেটাকে **অপঠনযোগ্য রূপে** রূপান্তর করে
   - উদ্দেশ্য: **Confidentiality**
   - প্রকার: **Symmetric (AES, DES)**, **Asymmetric (RSA, ECC)**
   - ব্যবহার: **transmission ও storage-এর সময়** ডেটা রক্ষা
2. **Digital Signature**
   - এমন cryptographic technique যা **authentication + integrity + non-repudiation** দেয়
   - প্রেরকের **PRIVATE key দিয়ে তৈরি (sign)** হয়, প্রেরকের **PUBLIC key দিয়ে যাচাই (verify)** হয়
   - ব্যবহার: e-mail security, e-commerce, legal document
3. **Access Control**
   - **শুধুমাত্র authorized user-রাই** resource ব্যবহার করতে পারে
   - পদ্ধতি: **DAC** (Discretionary), **MAC** (Mandatory), **RBAC** (Role-Based)
   - ব্যবহার: file system, database, network
4. **Data Integrity Mechanism**
   - Transmission/storage-এর মধ্যে ডেটা **পরিবর্তিত হয়নি** তা নিশ্চিত করে
   - Technique: **Hash function (SHA-256), MAC (Message Authentication Code), Checksum**
5. **Authentication Exchange**
   - যোগাযোগকারী পক্ষদের **পরিচয় যাচাই** করে
   - পদ্ধতি: password-based, **challenge-response protocol**, certificate-based
   - **Masquerade ও replay attack প্রতিরোধ** করে
6. **Traffic Padding**
   - **Dummy (নকল) ডেটা যোগ করে traffic-এর pattern লুকায়**
   - **Traffic analysis প্রতিরোধ** করে (passive attack!)
   - Military ও high-security network-এ ব্যবহৃত
7. **Routing Control**
   - **নিরাপদ communication path বেছে নেয়**, insecure network এড়িয়ে যায়
   - **অবিশ্বস্ত (untrusted) node-এর মধ্য দিয়ে** ডেটা যাওয়া ঠেকায়
8. **Notarization**
   - যোগাযোগ যাচাইয়ের জন্য **বিশ্বস্ত তৃতীয় পক্ষ (trusted third party)** ব্যবহার করে
   - **Non-repudiation নিশ্চিত** করে
   - উদাহরণ: **Time-stamping service**

### 🌐 খ. Pervasive Security Mechanisms (৫টি)

1. **Trusted Functionality**
   - System-এর উপাদানগুলো **নিরাপদ ও নির্ভরযোগ্যভাবে (secure & reliable)** আচরণ করে
   - **TCB (Trusted Computing Base)** অন্তর্ভুক্ত; unauthorized কাজ ঠেকায়
2. **Security Labels**
   - ডেটা/resource-এর সাথে **security attribute যুক্ত** করে
   - উদাহরণ: **Confidential, Secret, Top Secret**
   - Military ও সরকারি system-এ ব্যবহৃত
3. **Event Detection**
   - **Security-সংক্রান্ত ঘটনা** শনাক্ত করে (যেমন: intrusion attempt)
   - টুল: **IDS (Intrusion Detection System)**, log monitoring
4. **Security Audit Trail**
   - **Security event-এর রেকর্ড** রাখে
   - **Forensic analysis**-এ ব্যবহৃত হয়; **accountability** সাপোর্ট করে
5. **Security Recovery**
   - **Security failure-এর পরে system পুনরুদ্ধার (restore)** করে
   - Backup system, disaster recovery plan, fault tolerance

> 💡 মনে রাখার কৌশল (Specific-৮): **Encrypt, Sign, Access, Integrity, Authenticate, Pad, Route, Notarize**
> মনে রাখার কৌশল (Pervasive-৫): **T-L-E-A-R** → **T**rusted, **L**abels, **E**vent, **A**udit, **R**ecovery

---

## 8. Cryptography-র Features

### 🔑 Definition (security tool হিসেবে)
- Cryptography একটি গুরুত্বপূর্ণ **computer security tool** যা **তথ্য সংরক্ষণ (store) ও প্রেরণ (transmit) করার এমন সব technique** নিয়ে কাজ করে **যাতে unauthorized access বা interference ঠেকানো যায়**।

### ✨ Cryptography-র ৬টি Feature
1. **Confidentiality** → তথ্য **শুধুমাত্র যার জন্য তৈরি সেই access** করতে পারবে, অন্য কেউ নয়
2. **Non-repudiation** → তথ্যের creator/sender **পরে অস্বীকার করতে পারবে না** যে সে তথ্য পাঠিয়েছিল
3. **Integrity** → storage বা sender→receiver-এর মধ্যে **তথ্য পরিবর্তন করা গেলে তা ধরা পড়বে (detected)** — নীরবে বদলানো যাবে না
4. **Adaptability** → security threat ও প্রযুক্তির চেয়ে এগিয়ে থাকতে cryptography **ক্রমাগত বিবর্তিত (evolve)** হয়
5. **Interoperability** → **বিভিন্ন system ও platform-এর মধ্যে** নিরাপদ যোগাযোগ সম্ভব করে
6. **Authentication** → sender ও receiver-এর **পরিচয় নিশ্চিত** হয়; তথ্যের **উৎস/গন্তব্য (origin/destination)** নিশ্চিত হয়

---

## 9. Symmetric Key Cryptography — DES, AES

### 🔑 Definition
- এমন encryption system যেখানে **sender ও receiver message encrypt ও decrypt করতে একটাই common key ব্যবহার করে**।
- ✅ **দ্রুততর ও সহজ (faster & simpler)**
- ❌ সমস্যা: sender ও receiver-কে **কোনোভাবে key নিরাপদে exchange করতেই হবে** (key distribution সমস্যা)
- সবচেয়ে জনপ্রিয় system: **DES** এবং **AES**

### 🔒 DES — Data Encryption Standard
- একটি **পুরাতন (older) encryption algorithm**
- (স্লাইড অনুযায়ী) **64-bit plaintext**-কে **48-bit encrypted ciphertext**-এ রূপান্তর করে
- **Symmetric key** ব্যবহার করে (encrypt ও decrypt-এ একই key)
- আজকের মানদণ্ডে পুরনো, তবে **নতুন algorithm শেখার basic building block** হিসেবে ব্যবহারযোগ্য

> 📝 *Extra জ্ঞান (লিখলে extra নম্বর আসতে পারে): আসল DES standard-এ 64-bit block-এ 56-bit key ব্যবহার হয়, প্রতি round-এ 48-bit subkey তৈরি হয়। স্লাইডে যা আছে (64→48) সেটাই exam-এ লিখবে।*

### 🔒 AES — Advanced Encryption Standard
- জনপ্রিয় encryption algorithm, encrypt ও decrypt-এ **একই key** (symmetric)
- এটি একটি **symmetric BLOCK cipher**
- Block size: **128 bit, 192 bit বা 256 bit**
- ব্যাপকভাবে **DES-এর replacement হিসেবে স্বীকৃত**

> 💡 **DES বনাম AES দ্রুত তুলনা:** DES = পুরনো, ছোট, দুর্বল • AES = নতুন, বড় block, শক্তিশালী, বর্তমান standard

---

## 10. Number Theory (সংখ্যা তত্ত্ব)

### 🔑 Definition
- Number theory হলো **গণিতের সেই শাখা যা সংখ্যা — বিশেষত whole number (পূর্ণসংখ্যা)** এবং তাদের **properties ও সম্পর্ক (relationships)** নিয়ে অধ্যয়ন করে।
- বিভিন্ন পরিস্থিতিতে সংখ্যার **pattern, structure ও behavior** অনুসন্ধান করে।

### 💻 Computer Science-এ Number Theory-র Application
- **Cryptography** (RSA, ECC — সব asymmetric crypto number theory-র উপর দাঁড়ানো)
- **Hash function** (modular arithmetic)
- **Random number generation**
- **Error detection ও correction code**

---

## 11. Hash Functions ও Hashing

### 🔐 Cryptographic Hash Function
- **কোনো key-এর প্রয়োজন হয় না**
- **Mathematical algorithm** দিয়ে **যেকোনো দৈর্ঘ্যের (arbitrary length)** message-কে **fixed-length output**-এ রূপান্তর করে → একে বলে **hash value বা digest**
- **One-way** → output থেকে আসল input **বের করা সম্ভব নয়**
- মূল ব্যবহার: **data integrity**

#### SHA-1 (Secure Hash Algorithm 1)
- **NSA** (National Security Agency) কর্তৃক উদ্ভাবিত, **NIST 1995** সালে প্রকাশিত cryptographic hash function
- **যেকোনো input**-কে fixed-size **160-bit (20-byte)** hash value-তে রূপ্তরিত করে
- উদ্দেশ্য: **data integrity** নিশ্চিত করা

### 🗄️ Hashing Function (data structure দৃষ্টিতে)
Hashing function হলো এমন একটি নিয়ম (rule) যা:
- একটি **key নেয়** (যেমন: ID number, SSN, নাম)
- সেটাকে **একটি ছোট সংখ্যায় রূপান্তর** করে
- সেই সংখ্যা **বলে দেয় ডেটা memory-র কোথায় store বা খুঁজে পাওয়া যাবে**
- 💡 একে **locker number বরাদ্দ করার** সাথে তুলনা করা যায়

**Hashing কেন ব্যবহার করি?**
- **দ্রুত ডেটা store** করতে
- **দ্রুত ডেটা খুঁজে পেতে — প্রায়ই O(1) সময়ে (constant time)**
- লম্বা list-এ খোঁজার বদলে **সরাসরি সঠিক জায়গায় লাফিয়ে যাওয়া যায়**

### 📐 সূত্র (Formula)
$$h(k) = k \bmod m$$
যেখানে **m = উপলব্ধ memory location-এর সংখ্যা**

### 🧮 সমাধান করা উদাহরণ (স্লাইড থেকে — অবশ্যই practice করো!)
**সেটআপ:** 111টি locker, নম্বর 0–110। প্রতিটি customer-এর SSN আছে।
**প্রশ্ন:** h(k) = k mod 111 হলে, SSN **2848** ও **9212**-এর locker কোনটি?

**সমাধান:**
- h(2848) = 2848 mod 111 = **73** ✅ *(111 × 25 = 2775; 2848 − 2775 = 73)*
- h(9212) = 9212 mod 111 = **110** *(111 × 82 = 9102; 9212 − 9102 = 110)*

> 💡 **mod = ভাগশেষ (remainder)**। বড় সংখ্যাকে m দিয়ে ভাগ দাও → যত বাকি থাকে সেটাই উত্তর।

---

## 12. Asymmetric Key Cryptography — RSA, ECC

### 🔑 Definition
- তথ্য encrypt ও decrypt করতে **key-এর একটি জোড়া (pair)** ব্যবহৃত হয়
- **প্রেরক receiver-এর PUBLIC key দিয়ে encrypt করে**
- **Receiver নিজের PRIVATE key দিয়ে decrypt করে**
- Public ও Private key **ভিন্ন কিন্তু গাণিতিকভাবে সম্পর্কিত**
- **Public key সবাই জানলেও** শুধুমাত্র প্রকৃত receiver-ই decode করতে পারে — কারণ **private key শুধু তার কাছেই আছে**
- সবচেয়ে জনপ্রিয় algorithm: **RSA**

### 🔐 RSA (Rivest–Shamir–Adleman)
- স্যারের code example repo: `https://github.com/Shafikcse/Shafik-CNS-RSA-Algorithm.git`

#### ✅ RSA-র সুবিধা (৫টি)
1. **Security** → খুবই নিরাপদ বলে বিবেচিত, secure data transmission-এ ব্যাপক ব্যবহৃত
2. **Public-key cryptography** → দুটি ভিন্ন key; public key দিয়ে encrypt, private key দিয়ে decrypt
3. **Key exchange** → দুই পক্ষ **নেটওয়ার্কে key না পাঠিয়েই** একটি secret key exchange করতে পারে
4. **Digital signature** → sender **নিজের private key** দিয়ে message sign করে, receiver **sender-এর public key** দিয়ে signature যাচাই করে
5. **Widely used** → online banking, e-commerce, secure communication

#### ❌ RSA-র অসুবিধা (৭টি)
1. **ধীর গতি (Slow processing)** → বিশেষত বিপুল পরিমাণ ডেটায় অন্যান্য algorithm-এর তুলনায় ধীর
2. **বড় key size** → নিরাপত্তার জন্য বড় key দরকার → বেশি computation ও storage
3. **Side-channel attack-এর ঝুঁকি** → **power consumption, electromagnetic radiation, timing analysis** থেকে তথ্য লিক করে private key বের করা যেতে পারে
4. **কিছু ক্ষেত্রে সীমিত ব্যবহার** → বিশাল ডেটার নিরবচ্ছিন্ন encrypt/decrypt-এর জন্য উপযুক্ত নয় (ধীর বলে)
5. **জটিলতা (Complexity)** ও বোঝা/ব্যবহার কঠিন
6. **Key management** → private key-এর নিরাপদ রক্ষণাবেক্ষণ কঠিন হতে পারে
7. **Quantum computer-এর হুমকি** → quantum computer RSA ভেঙে **ডেটা decrypt করে ফেলতে পারে**

### 📈 ECC — Elliptic Curve Cryptography
- এক ধরনের **asymmetric encryption**
- **RSA-এর চেয়ে ছোট key দিয়ে শক্তিশালী নিরাপত্তা** দেয়
- **দক্ষ (efficient) ও দ্রুত (fast)** → **সীমিত সম্পদের ডিভাইসের জন্য আদর্শ**: smartphone, IoT device, blockchain wallet
- **TLS/SSL** (Transport Layer Security / Secure Sockets Layer) ও **cryptocurrency**-তে ব্যাপক ব্যবহৃত — হালকা কিন্তু শক্তিশালী

> 💡 **RSA বনাম ECC:** RSA = বড় key, ধীর • ECC = ছোট key, দ্রুত, mobile/IoT-এর জন্য perfect

**Practice tool (স্লাইড থেকে):**
- https://anycript.com/
- https://emn178.github.io/online-tools/

---

## 13. Conventional Encryption Model / Cryptosystem

### 🔑 Conventional Encryption Model
- **Symmetric-key বা single-key encryption** নামেও পরিচিত
- **Plaintext encrypt ও ciphertext decrypt — দুটোর জন্যই একই shared secret key** ব্যবহৃত হয়

### 🔑 Conventional Cryptosystem
- **Symmetric বা secret-key cryptography** নামেও পরিচিত
- Encrypt + decrypt-এ **একই একটি key**; sender ও receiver দুজনেই **secret key-এ অংশীদার (share)**
- ✅ **bulk data encryption-এর জন্য দ্রুত ও কার্যকর**
- ❌ চ্যালেঞ্জ: **key-এর নিরাপদ বিতরণ (secure key distribution)**
- **উদাহরণ: DES, AES**

---

## 14. Classical Encryption Techniques — Caesar/Shift Cipher

### ২টি বড় ভাগ (Family)
1. **Substitution Cipher (প্রতিস্থাপন)**
   - Plaintext-এর অক্ষরকে **অন্য অক্ষর, সংখ্যা বা প্রতীক দিয়ে replace করা হয়**
   - অক্ষরের **আসল অর্ডার/ক্রম একই থাকে** — কিন্তু **অক্ষরের পরিচয় বদলে যায়**
   - (যেমন: A → D, B → E)
2. **Transposition Cipher (স্থানান্তর)**
   - Plaintext-এর অক্ষরের **অবস্থান (position) পরিবর্তন/পুনর্বিন্যাস** করা হয়
   - **অক্ষর নিজে বদলায় না** — শুধু **জায়গা বদলায়**, একটি নির্দিষ্ট জটিল পদ্ধতি (system) অনুসরণ করে
   - (যেমন: MEET → EEMT; অক্ষর একই কিন্তু ক্রম বদলে গেছে)

> 💡 **Substitution = অক্ষর বদল, Transposition = জায়গা বদল**

### 🏛️ Caesar Cipher — সম্পূর্ণ সমাধান করা উদাহরণ (অবশ্যই practice করো!)

**সমস্যা:** Caesar cipher দিয়ে **"MEET YOU IN THE PARK"** encrypt করো।

**ধাপ ১ — অক্ষরকে সংখ্যায় রূপান্তর (A=0, B=1, ... Z=25):**
```
M  E  E  T   Y  O  U   I  N   T  H  E   P  A  R  K
12 4  4  19  24 14 20  8  13  19 7  4   15 0  17 10
```

**ধাপ ২ — প্রতিটি সংখ্যায় f(p) = (p + 3) mod 26 প্রয়োগ করো:**
```
12→15, 4→7, 4→7, 19→22, 24→1, 14→17, 20→23, 8→11, 13→16,
19→22, 7→10, 4→7, 15→18, 0→3, 17→20, 10→13
= 15 7 7 22 1 17 23 11 16 22 10 7 18 3 20 13
```

**ধাপ ৩ — সংখ্যাকে আবার অক্ষরে রূপান্তর:**
```
15=P, 7=H, 7=H, 22=W, 1=B, 17=R, 23=X, 11=L, 16=Q,
22=W, 10=K, 7=H, 18=S, 3=D, 20=U, 13=N
```

### ✅ **Encrypt করা message: "PHHW BRX LQ WKH SDUN"**

### 🔓 Decryption (আসল message ফিরে পাওয়া)
- **বিপরীত ফাংশন f⁻¹** ব্যবহার করো:
$$f^{-1}(p) = (p - 3) \bmod 26$$
- প্রতিটি অক্ষরকে **৩ ধরে পিছিয়ে** দাও; প্রথম ৩টি অক্ষর (A, B, C → অর্থাৎ 0,1,2) বর্ণমালার **শেষ ৩টি অক্ষরে** চলে যায়
- **Decryption** = encrypted message থেকে আসল message নির্ণয়ের প্রক্রিয়া
- যাচাই: P(15) − 3 = 12 = M ✓, H(7) − 3 = 4 = E ✓

### 🔀 সাধারণীকরণ — Shift Cipher
- ৩ ধরে shift না করে যেকোনো পূর্ণসংখ্যা **k ধরে shift** করা যায়:
$$f(p) = (p + k) \bmod 26 \quad \text{(encryption)}$$
$$f^{-1}(p) = (p - k) \bmod 26 \quad \text{(decryption)}$$
- **Caesar cipher = k = 3 হলে shift cipher**
- পূর্ণসংখ্যা **k-কে বলা হয় KEY** 🔑

> 💡 সংখ্যা↔অক্ষর mapping মুখস্থ রাখো: **A=0, B=1, C=2, D=3, E=4, F=5, G=6, H=7, I=8, J=9, K=10, L=11, M=12, N=13, O=14, P=15, Q=16, R=17, S=18, T=19, U=20, V=21, W=22, X=23, Y=24, Z=25**

---

## 15. ⚡ দ্রুত Revision + সম্ভাব্য Exam প্রশ্ন

### 🎯 One-line Definition (এগুলো হুবহু লিখবে)
| টার্ম | এক লাইনে |
|---|---|
| Cryptography | Mathematical algorithm দিয়ে plaintext-কে ciphertext-এ রূপান্তর করে তথ্য রক্ষার বিজ্ঞান |
| Encryption | Sender algorithm + key দিয়ে plaintext-কে ciphertext বানায় |
| Decryption | Receiver key দিয়ে ciphertext-কে আবার plaintext-এ ফেরায় |
| Network Security | Layered hardware+software দিয়ে নেটওয়ার্ক/ডেটার usability, integrity, safety রক্ষা |
| Computer Security | System ও ডেটাকে unauthorized access, misuse, modification, destruction থেকে রক্ষা |
| Threat | Security লঙ্ঘনের সম্ভাবনা — vulnerability কাজে লাগাতে পারে এমন সম্ভাব্য বিপদ |
| Attack | Security service এড়িয়ে security policy ভাঙার সচেতন ও বুদ্ধিমত্তাপূর্ণ চেষ্টা |
| Passive Attack | Attacker শুধু ডেটা observe করে, modification নেই, detect কঠিন (লক্ষ্য: তথ্য সংগ্রহ) |
| Active Attack | Attacker ডেটা modify/delete/fabricate করে — detect সহজ, prevent কঠিন |
| Security Service | Security attack প্রতিহত করে ডেটা processing ও transfer-এর নিরাপত্তা বাড়ায় এমন service |
| Security Mechanism | Security attack detect, prevent বা recover করার জন্য ডিজাইন করা process/device |
| Symmetric Encryption | Encrypt ও decrypt-এ একই shared secret key |
| Asymmetric Encryption | Key জোড়া — public key encrypt করে, private key decrypt করে |
| Hashing | যেকোনো দৈর্ঘ্যের ডেটাকে fixed-length digest-এ রূপান্তরকারী one-way function |
| Substitution Cipher | অক্ষরকে অন্য অক্ষর/প্রতীক দিয়ে replace করে (ক্রম অপরিবর্তিত) |
| Transposition Cipher | অক্ষরের অবস্থান পরিবর্তন করে (অক্ষর অপরিবর্তিত) |

### 📐 Formula Sheet
| সূত্র | ব্যবহার |
|---|---|
| `f(p) = (p + k) mod 26` | Shift cipher **encryption** (Caesar: k=3) |
| `f⁻¹(p) = (p − k) mod 26` | Shift cipher **decryption** |
| `h(k) = k mod m` | Hash function → memory location (m = location সংখ্যা) |

### ❓ সম্ভাব্য Exam প্রশ্ন
1. Cryptography কাকে বলে? এটি কীভাবে কাজ করে? *(সেকশন ১)*
2. Cryptography-র ৪টি pillar/goal ব্যাখ্যা কর। *(সেকশন ১)*
3. Symmetric বনাম asymmetric encryption-এর পার্থক্য। *(সেকশন ৯, ১২, ১৩)*
4. Threat ও attack / safety ও security-এর পার্থক্য। *(সেকশন ৩)*
5. Passive ও active attack কী? উদাহরণসহ active attack-এর ৪টি প্রকার ব্যাখ্যা কর। *(সেকশন ৫)*
6. উদাহরণসহ security service গুলো ব্যাখ্যা কর (X.800)। *(সেকশন ৬)*
7. Specific বনাম pervasive security mechanism-এর পার্থক্য — সবগুলো উদ্দেশ্যসহ লিখ। *(সেকশন ৭)*
8. Cryptography-র features লিখ। *(সেকশন ৮)*
9. DES বনাম AES। *(সেকশন ৯)*
10. RSA-র সুবিধা ও অসুবিধা। *(সেকশন ১২)*
11. ECC কী? ছোট ডিভাইসে RSA-এর বদলে ECC কেন পছন্দ করা হয়? *(সেকশন ১২)*
12. গাণিতিক সমস্যা: Caesar/shift cipher দিয়ে encrypt-decrypt। *(সেকশন ১৪)*
13. গাণিতিক সমস্যা: h(k) = k mod m দিয়ে locker নির্ণয়। *(সেকশন ১১)*
14. Substitution বনাম transposition cipher। *(সেকশন ১৪)*
15. OSI layer: Physical layer-এর কাজ, LLC বনাম MAC sub-layer। *(সেকশন ৪)*

### 🔑 Quick Comparison (শেষ মুহূর্তের এক নজরে)
- **Symmetric** = ১টি key, দ্রুত, key-distribution সমস্যা (DES, AES)
- **Asymmetric** = ২টি key (public+private), ধীর কিন্তু নিরাপদ key exchange ও signature (RSA, ECC)
- **Hashing** = key নেই, one-way, fixed output, integrity (SHA-1: 160-bit)
- **Passive** = শুধু observe, detect কঠিন (eavesdropping, traffic analysis)
- **Active** = ডেটা modify, prevent কঠিন (masquerade, replay, modification, DoS)
- **Threat** = সম্ভাব্য বিপদ • **Attack** = সচেতন বুদ্ধিমত্তাপূর্ণ কাজ
- **DES** = পুরনো, 64-bit block • **AES** = নতুন, 128/192/256-bit block (DES-এর replacement)
- **RSA** = নিরাপদ কিন্তু ধীর, বড় key, quantum-ঝুঁকি • **ECC** = ছোট key, দ্রুত, mobile/IoT-বান্ধব

---

*✍️ Lecture-1 নোট সমাপ্ত — Mid-term-এর জন্য শুভকামনা! 🍀*
