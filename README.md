# WebCTF_CheatSheet
WebCTF_CheatSheet

# 1. nmap scanning
```
# 1. 상위 1000개 포트 서비스 확인
nmap -T4 --top-ports 1000 -sV --open [타겟 IP]

#2. 전체 TCP 포트 스캔
sudo nmap -p- -T4 --open [타겟 IP]

#3. 전체 포트 스캔 + 기본 NSE 스크립트
sudo nmap -p- -sS -sV -sC -T4 --open [타겟 IP]

#4. 웹 포트 집중 스캔 (특히 http- 헤더)
sudo nmap -p 80,443,8080,8000,8443 -sV --script "http-server-header,http-cookie-flags,http-enum" -T4 --open -n [타겟 IP]
```

# 2. gobuster
```
gobuster dir -u https://example.com -w ~/wordlists/shortlist.txt
gobuster dir -u https://example.com -w /usr/share/dirbuster/wordlists/directory-list-2.3-medium.txt -x php,php3, html
```

# 3. OWASP zap
Automated Scan ㄱㄱ


