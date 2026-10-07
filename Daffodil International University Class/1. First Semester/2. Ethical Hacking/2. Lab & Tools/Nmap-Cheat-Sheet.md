# ⚡ Nmap পেন্টেস্ট চিটশিট — দ্রুত রেফারেন্স

> মূল নোট: [Nmap.md](Nmap.md) | শুধুমাত্র **অনুমোদিত টার্গেটে** ব্যবহার করো (নিজের ল্যাব, TryHackMe/HTB, লিখিত অনুমতিসহ এনগেজমেন্ট)।

---

## 🚫 ১. ICMP Ping ছাড়া স্ক্যান (Ping ব্লক থাকলে)

ফায়ারওয়াল ICMP ব্লক করলে Nmap ভুল করে "host down" বলে — এই কমান্ডগুলো দিয়ে সেটা ফাঁকি দাও:

```bash
sudo nmap -Pn 192.168.1.10              # ⭐ হোস্ট ডিসকভারি স্কিপ — ধরে নাও হোস্ট লাইভ, সরাসরি পোর্ট স্ক্যান
sudo nmap -Pn -sS -p- 192.168.1.10      # ping ব্লক থাকলেও ফুল পোর্ট স্টেলথ স্ক্যান
sudo nmap -PS80,443 192.168.1.0/24      # TCP SYN প্রোব (ICMP ব্লক, কিন্তু ওয়েব ট্রাফিক খোলা — প্রায় সবসময় কাজ করে)
sudo nmap -PA80 192.168.1.0/24          # TCP ACK প্রোব (stateless ফায়ারওয়াল ফাঁকি)
sudo nmap -PU53 192.168.1.0/24          # UDP প্রোব (closed পোর্ট থেকে ICMP unreachable ফেরত আসলে = হোস্ট লাইভ)
sudo nmap -PO 192.168.1.10              # IP Protocol Ping (ICMP সম্পূর্ণ ব্লক থাকলে)
sudo nmap -PY 80 192.168.1.0/24         # SCTP INIT প্রোব (টেলিকম/4G ডিভাইস)
sudo nmap -PP -PM 192.168.1.0/24        # ICMP Timestamp / Address Mask (পুরনো সিস্টেম)
sudo nmap --disable-arp-ping -sn 192.168.1.0/24   # ARP বন্ধ করে IP-layer প্রোবে জোর করা
```

**মনে রাখো:** `-Pn` = "ping কোরো না, স্ক্যান শুরু করো"। আর `-PS80` হলো ICMP-নির্ভরতা এড়ানোর সবচেয়ে নির্ভরযোগ্য বিকল্প।

---

## 🥸 ২. IDS / IPS / ফায়ারওয়াল বাইপাস (Evasion)

### কম্বো কমান্ড (রেডি-টু-ইউজ)

```bash
# সম্পূর্ণ IDS-সেফ স্ক্যান (ধীর কিন্তু স্টেলথি):
sudo nmap -sS -T2 --max-rate 50 --scan-delay 3s -f -D RND:5 -p- <target>

# IDS-সেফ ভার্সনটা মাস্টার চিটশিট থেকে:
sudo nmap -sS -T2 -f -D RND:10 --source-port 53 <target>

# ফ্র্যাগমেন্টেশন + ডিকয় + সোর্স-পোর্ট + কাস্টম প্যাকেট সাইজ একসাথে:
sudo nmap -sS -f -D RND:8 -g 53 --data-length 50 --ttl 50 --max-rate 100 <target>
```

### ফ্ল্যাগ-ভিত্তিক ব্রেকডাউন

| উদ্দেশ্য | কমান্ড | কী করে |
|---|---|---|
| **ফ্র্যাগমেন্টেশন** | `sudo nmap -f <t>` | প্যাকেট ছোট টুকরোয় ভেঙে পাঠায় — সস্তা stateless ফায়ারওয়াল TCP ফ্ল্যাগ দেখতে পায় না |
| | `sudo nmap -f -f <t>` | ডাবল ফ্র্যাগমেন্টেশন (আরও ছোট টুকরো) |
| | `sudo nmap --mtu 16 <t>` | ম্যানুয়াল MTU সাইজ (8-এর multiple) |
| **ডিকয়** | `sudo nmap -D RND:10 <t>` | ১০টা র‍্যান্ডম ফেক IP — লগে অনেক IP দেখায়, আসল সোর্স লুকায় |
| | `sudo nmap -D decoy1,decoy2,ME <t>` | নির্দিষ্ট ডিকয় + নিজের IP-র পজিশন |
| **সোর্স পোর্ট** | `sudo nmap -g 53 <t>` | সোর্স পোর্ট 53 (DNS) থেকে আসছে ভান — ফায়ারওয়াল বিশ্বাস করে; `-g 80`-ও চলে |
| **টাইমিং স্টেলথ** | `sudo nmap -T1 <t>` | Sneaky — খুব ধীর, লগ/IDS এড়ানোর চেষ্টা |
| | `sudo nmap -T0 <t>` | Paranoid — প্রতি প্যাকেটে ৫ মিনিট delay (IDS টেস্টিং) |
| | `sudo nmap --scan-delay 5s <t>` | প্রোবের মাঝে ৫ সেকেন্ড ফাঁক — রেট-ভিত্তিক IDS (Snort) ট্রিগার করে না |
| | `sudo nmap --max-rate 100 <t>` | সেকেন্ডে max ১০০ প্যাকেট |
| | `sudo nmap --max-parallelism 1 <t>` | একবারে ১টা প্রোব (একদম stealth মোড) |
| **প্যাকেট কাস্টমাইজ** | `sudo nmap --data-length 50 <t>` | এক্সট্রা ডামি ডাটা — Nmap-এর signature মেলে না |
| | `sudo nmap --ttl 50 <t>` | TTL মিলিয়ে স্বাভাবিক ট্রাফিকের মতো দেখানো |
| | `sudo nmap --badsum <t>` | ভুল checksum — পথে packet-normalizing ডিভাইস (load balancer) আছে কিনা টেস্ট |
| | `sudo nmap --ip-options "SRR" <t>` | IP option দিয়ে রাউটিং ম্যানিপুলেশন |
| **MAC/হোস্ট লুকানো** | `sudo nmap --spoof-mac Cisco <t>` | ভেন্ডরের র‍্যান্ডম MAC দিয়ে ARP লেভেলে পরিচয় লুকাও |
| | `sudo nmap --randomize-hosts -iL targets.txt` | হোস্ট অর্ডার এলোমেলো — প্যাটার্ন ডিটেকশন এড়াও |
| **সোর্স IP স্পুফ** | `sudo nmap -S 192.168.1.99 -e eth0 <t>` | সোর্স IP জাল — ⚠️ রেসপন্স ফিরে আসে না, শুধু ল্যাবে শেখার জন্য |

**স্টেলথ স্ক্যান টেকনিকও IDS-বাইপাসের অংশ:** `-sS` (হাফ-ওপেন, অ্যাপ লগে পড়ে না), `-sN/-sF/-sX` (Null/FIN/Xmas — SYN-ব্লক করা ফিল্টার ফাঁকি, Linux/BSD-তে), `-sI` (Idle scan — টার্গেটে তোমার IP-ই যায় না)।

---

## 🔪 ৩. TCP হাফ-ওপেন / স্টেলথ স্ক্যান (-sS)

```bash
sudo nmap -sS 192.168.1.10                     # ⭐ SYN scan — পেন্টেস্টের স্ট্যান্ডার্ড ডিফল্ট
sudo nmap -sS -p- --min-rate 1000 -T4 <t>      # সব 65535 পোর্ট, দ্রুত
sudo nmap -sS --top-ports 100 --open -T4 <t>   # দ্রুত প্রথম ঝলক, শুধু open পোর্ট
```

**কীভাবে কাজ করে:** SYN পাঠায় → SYN/ACK পেলেই (পোর্ট open নিশ্চিত) RST পাঠিয়ে কানেকশন ছেড়ে দেয়। হ্যান্ডশেক কখনো শেষ হয় না → **Apache/SSH-এর auth লগে কোনো এন্ট্রি পড়ে না**।

| টেকনিক | ফ্ল্যাগ | কখন |
|---|---|---|
| SYN / Half-open | `-sS` | ডিফল্ট পছন্দ — দ্রুত, লগে পড়ে না (root লাগে) |
| Connect (ফুল) | `-sT` | root ছাড়া স্ক্যান; প্রতিটা কানেকশন লগে পড়ে |
| Null / FIN / Xmas | `-sN` `-sF` `-sX` | SYN-ব্লক করা stateless ফায়ারওয়াল ফাঁকি (Linux/BSD) |
| ACK (ফায়ারওয়াল ম্যাপ) | `-sA` | কোন পোর্ট filtered/unfiltered তা জানতে |
| Idle (zombie) | `-sI <zombie>` | টার্গেটে তোমার IP-ই যায় না — সম্পূর্ণ attribution hide |
| Window | `-sW` | ACK + window সাইজে open/closed আলাদা করা |

---

## 🧬 ৪. ভালনারেবিলিটি NSE স্ক্রিপ্ট

```bash
sudo nmap --script vuln <t>                                # ⭐ vuln ক্যাটাগরির সব স্ক্রিপ্ট একবারে
sudo nmap --script vuln -p 22,80,443,3306 <t>              # শুধু খোলা পোর্টে
sudo nmap -sV --script vuln -p- -T4 -oA deep_scan <t>      # ফুল পোর্ট + ভার্সন + ভালন একসাথে

# নির্দিষ্ট CVE চেক:
sudo nmap --script smb-vuln-ms17-010 -p 445 <t>            # EternalBlue (MS17-010)
sudo nmap --script ssl-heartbleed -p 443 <t>               # Heartbleed

# কমন ভালন চেক:
sudo nmap --script ftp-anon -p 21 <t>                      # FTP anonymous login খোলা কিনা
sudo nmap --script http-enum -p 80 <t>                     # লুকানো প্যাথ (/admin, /backup...)

# এনুমারেশন (রিকন গোল্ড):
sudo nmap --script smb-os-discovery -p 445 <t>             # Windows নাম, ডোমেইন, লগইন ইউজার
sudo nmap --script http-title -p 80,443 192.168.1.0/24     # নেটওয়ার্কে কোথায় কী সাইট
sudo nmap --script nfs-ls,nfs-showmount <t>                # NFS শেয়ার
sudo nmap --script snmp-sysdescr -p 161 -sU <t>            # SNMP সিস্টেম ইনফো

# ব্রুট-ফোর্স (শুধু অনুমোদিত টেস্টে):
sudo nmap --script ssh-brute -p 22 --script-args userdb=users.txt,passdb=rockyou.txt <t>
sudo nmap --script ftp-brute,mysql-brute,http-brute <t>    # একসাথে কমা দিয়ে

# প্যাটার্ন/ফিল্টার:
sudo nmap --script "http-*" <t>                            # সব http স্ক্রিপ্ট
sudo nmap --script "not dos" <t>                           # dos বাদে সব
nmap --script-help http-title                              # স্ক্রিপ্টের ডকুমেন্টেশন পড়ো
sudo nmap --script-updatedb                                # নতুন স্ক্রিপ্টের পর DB আপডেট
```

| ক্যাটাগরি | মানে |
|---|---|
| `safe` / `default` | টার্গেট ভাঙার ঝুঁকি নেই (`-sC` = default) |
| `vuln` | জানা দুর্বলতা (CVE) চেক |
| `exploit` | দুর্বলতার exploit চেষ্টা |
| `brute` | পাসওয়ার্ড ব্রুট-ফোর্স |
| `intrusive` / `dos` | চাপ দেয়/ক্র্যাশ করতে পারে — **শুধু ল্যাবে** |

---

## 🛠️ ৫. ডেইলি-ইউজ এসেনশিয়াল কমান্ড

### দ্রুত রেফারেন্স টেবিল

| উদ্দেশ্য | কমান্ড |
|---|---|
| লাইভ হোস্ট (ping sweep) | `sudo nmap -sn -PE 192.168.1.0/24` |
| লোকাল নেটে ARP স্ক্যান | `sudo nmap -PR -sn 192.168.1.0/24` |
| দ্রুত টপ পোর্ট | `sudo nmap --top-ports 100 -T4 <t>` |
| সব ৬৫৫৩৫ পোর্ট | `sudo nmap -p- <t>` |
| সার্ভিস + ভার্সন | `sudo nmap -sV <t>` |
| OS ডিটেক্ট | `sudo nmap -O --osscan-guess <t>` |
| ডিফল্ট NSE স্ক্রিপ্ট | `sudo nmap -sC <t>` |
| UDP টপ পোর্ট | `sudo nmap -sU --top-ports 20 <t>` |
| ফায়ারওয়াল ম্যাপিং | `sudo nmap -sA -p 80,443 <t>` |
| টার্গেট লিস্ট ফাইল | `sudo nmap -iL targets.txt --excludefile skip.txt` |
| রুট ম্যাপিং | `sudo nmap --traceroute <t>` |
| DNS বন্ধ (ফাস্ট) | `sudo nmap -n <t>` |
| শুধু open পোর্ট | `sudo nmap --open --reason <t>` |
| ৩ ফরম্যাটে রিপোর্ট | `sudo nmap -oA full_report <t>` |

### ⭐ অল-ইন-ওয়ান (সবচেয়ে বেশি ব্যবহৃত)

```bash
sudo nmap -sC -sV -O -p- -v -oA full_report <target>
# -sC ডিফল্ট স্ক্রিপ্ট | -sV ভার্সন | -O OS | -p- সব পোর্ট | -v লাইভ আউটপুট | -oA ৩ ফরম্যাট সেভ

# CTF-তে প্রথম কমান্ড:
sudo nmap -sV --top-ports 100 -T4 <target>
```

### ওয়ার্কফ্লো (ধাপে ধাপে — এক কমান্ডে সব নয়)

```bash
# ১. কারা লাইভ:
sudo nmap -sn -PE 192.168.1.0/24 -oA discovery
# ২. দ্রুত ঝলক:
sudo nmap -sS --top-ports 100 -T4 --open 192.168.1.10
# ৩. ফুল TCP:
sudo nmap -sS -p- -T4 --open --min-rate 1000 192.168.1.10 -oN allports.txt
# ৪. খোলা পোর্টে গভীর:
sudo nmap -sV -sC -O -p 22,80,443,3306 192.168.1.10 -oA version_scan
# ৫. ভালন:
sudo nmap --script vuln -p 22,80,443,3306 192.168.1.10
# ৬. UDP:
sudo nmap -sU --top-ports 20 -sV 192.168.1.10
```

**পরবর্তী ধাপ:** ভার্সন দেখা মাত্র → `searchsploit <service> <version>` বা CVE ডেটাবেসে মিলাও। যেমন `Apache 2.4.49` = CVE-2021-41773।

### টপ পোর্ট মুখস্থ করো

| পোর্ট | সার্ভিস | অ্যাটাক প্যাটার্ন |
|---|---|---|
| 21 | FTP | anonymous login, brute |
| 22 | SSH | brute, পুরনো CVE |
| 23 | Telnet | cleartext ক্রেডেনশিয়াল |
| 53 | DNS | zone transfer, amplification |
| 80/443 | HTTP/S | ওয়েব অ্যাপ ভালন, পুরনো CMS |
| 445 | SMB | MS17-010, শেয়ার এনুম |
| 161 | SNMP (UDP) | ডিফল্ট community string → ফুল সিস্টেম লিক |
| 3306 / 3389 | MySQL / RDP | brute / BlueKeep |

---

## 📋 সব ফ্ল্যাগ একনজরে

```bash
# Discovery (ping ছাড়া):   -Pn -PS<port> -PA<port> -PU<port> -PO -PY -PE -PP -PM -PR -sn
# Scan:                     -sS -sT -sU -sA -sN -sF -sX -sW -sM -sO -sI <zombie>
# Port:                     -p <ports>  -p-  -F  --top-ports <n>  --exclude-ports
# Version/OS:               -sV  --version-intensity <0-9>  -O  --osscan-guess
# Timing:                   -T0..-T5  --min-rate  --max-rate  --scan-delay  --host-timeout
# Evasion:                  -f  --mtu  -D  -g  --data-length  --ttl  --badsum  --spoof-mac
# NSE:                      -sC  --script <cat>  --script-args userdb=,passdb=  --script-help
# Output:                   -v  --open  --reason  -oN  -oX  -oG  -oA
```

---

*শুধুমাত্র অনুমোদিত টার্গেটে ব্যবহার করো। Recon শেখো, রিসার্চার হও — ক্রিমিনাল নয়। 🛰️🔍*
