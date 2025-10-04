# WebCTF_CheatSheet
WebCTF_CheatSheet

# 1. nmap scanning
```
sudo nmap -p 80,443 -sV --script "http-server-header,http-cookie-flags,http-enum" -T4 --open -n [타겟 IP]
```
