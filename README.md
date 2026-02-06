# basically everything, launch it and go to sleep.

```
# Download de wordlists
curl -s "https://raw.githubusercontent.com/maurosoria/dirsearch/master/db/dicc.txt" | anew -q fuzzing_wordlist.txt
curl -s "https://raw.githubusercontent.com/six2dez/OneListForAll/main/onelistforallmicro.txt" | anew -q fuzzing_wordlist.txt
curl -s "https://raw.githubusercontent.com/six2dez/OneListForAll/main/onelistforallshort.txt" | anew -q fuzzing_wordlist.txt
curl -s "https://raw.githubusercontent.com/ayoubfathi/leaky-paths/main/leaky-paths.txt" | anew -q fuzzing_wordlist.txt
curl -s "https://raw.githubusercontent.com/Bo0oM/fuzz.txt/master/fuzz.txt" | anew -q fuzzing_wordlist.txt

# Basic fuzzing
dirsearch -u 'https://target.com' -w /root/fuzzing_wordlist.txt -i 200 --full-url --random-agent --recursive -R 3 -t 50

```
**VPS TIP:**
```
# Conect to VPS via Reverse SSH
ssh -R 8080:127.0.0.1:8080 root@VPS_IP -f -N

# Send it to burp
ffuf -c -u http://target.com/FUZZ -t 3 -p 1.0-1.5 -w wordlist.txt -ac -replay-proxy http://127.0.0.1:8080
```

