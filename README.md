# Crack the hash

Notes on the CTF from TryHackMe.

The trick with this one is playing around to figure out what hash type each of these are.

https://hashcat.net/wiki/doku.php?id=example_hashes shows what mode each hash is in for hashcat.

## 48bb6e862e54f2a795ffc4e541caed4d

`root@ip-10-10-90-157:~# hashid 48bb6e862e54f2a795ffc4e541caed4d`

```
Analyzing '48bb6e862e54f2a795ffc4e541caed4d'
[+] MD2
[+] MD5
[+] MD4
[+] Double MD5
[+] LM
[+] RIPEMD-128
[+] Haval-128
[+] Tiger-128
[+] Skein-256(128)
[+] Skein-512(128)
[+] Lotus Notes/Domino 5
[+] Skype
[+] Snefru-128
[+] NTLM
[+] Domain Cached Credentials
[+] Domain Cached Credentials 2
[+] DNSSEC(NSEC3)
[+] RAdmin v2.x
```

`root@ip-10-10-90-157:~# hashcat -m 0 hash.txt /usr/share/wordlists/rockyou.txt`

```
48bb6e862e54f2a795ffc4e541caed4d:easy            
```

## CBFDAC6008F9CAB4083784CBD1874F76618D2A97 

`root@ip-10-10-90-157:~# hashid hash.txt`

```
--File 'hash.txt'--
Analyzing 'CBFDAC6008F9CAB4083784CBD1874F76618D2A97'
[+] SHA-1 
[+] Double SHA-1 
[+] RIPEMD-160 
[+] Haval-160 
[+] Tiger-160 
[+] HAS-160 
[+] LinkedIn 
[+] Skein-256(160) 
[+] Skein-512(160) 
--End of file 'hash.txt'--
```

`root@ip-10-10-90-157:~# hashcat -m 100 hash.txt /usr/share/wordlists/rockyou.txt `

```
cbfdac6008f9cab4083784cbd1874f76618d2a97:password123
```

## 1C8BFE8F801D79745C4631D09FFF36C82AA37FC4CCE4FC946683D7B336B63032

`root@ip-10-10-90-157:~# hashid hash.txt`

```
--File 'hash.txt'--
Analyzing '1C8BFE8F801D79745C4631D09FFF36C82AA37FC4CCE4FC946683D7B336B63032'
[+] Snefru-256 
[+] SHA-256 
[+] RIPEMD-256 
[+] Haval-256 
[+] GOST R 34.11-94 
[+] GOST CryptoPro S-Box 
[+] SHA3-256 
[+] Skein-256 
[+] Skein-512(256) 
--End of file 'hash.txt'--
```

`root@ip-10-10-90-157:~# hashcat -m 1400 hash.txt /usr/share/wordlists/rockyou.txt `

```
1c8bfe8f801d79745c4631d09fff36c82aa37fc4cce4fc946683d7b336b63032:letmein
```

## $2y$12$Dwt1BZj6pcyc3Dy1FWZ5ieeUznr71EeNkJkUlypTsgbX1H68wsRom

`root@ip-10-10-90-157:~# hashid hash.txt`

```
--File 'hash.txt'--
Analyzing '$2y$12$Dwt1BZj6pcyc3Dy1FWZ5ieeUznr71EeNkJkUlypTsgbX1H68wsRom'
[+] Blowfish(OpenBSD) 
[+] Woltlab Burning Board 4.x 
[+] bcrypt 
--End of file 'hash.txt'--
```


The AttackBox crashes when I run hashcat. 


`grep -w '^....$' /usr/share/wordlists/rockyou.txt > 4letterwords.txt` to shorten the list.

`root@ip-10-10-123-97:~# hashcat -m 3200 hash.txt 4letterwords.txt`

```
$2y$12$Dwt1BZj6pcyc3Dy1FWZ5ieeUznr71EeNkJkUlypTsgbX1H68wsRom:bleh
```

## 279412f945939ba78ce0758d3fd83daa

`root@ip-10-10-123-97:~# hashid hash.txt`

```
--File 'hash.txt'--
Analyzing '279412f945939ba78ce0758d3fd83daa'
[+] MD2 
[+] MD5 
[+] MD4 
[+] Double MD5 
[+] LM 
[+] RIPEMD-128 
[+] Haval-128 
[+] Tiger-128 
[+] Skein-256(128) 
[+] Skein-512(128) 
[+] Lotus Notes/Domino 5 
[+] Skype 
[+] Snefru-128 
[+] NTLM 
[+] Domain Cached Credentials 
[+] Domain Cached Credentials 2 
[+] DNSSEC(NSEC3) 
[+] RAdmin v2.x 
--End of file 'hash.txt'--
```

Hashcat had trouble with this one.

https://md5decrypt.net/en/Md4/#answer


`279412f945939ba78ce0758d3fd83daa : Eternity22`


## F09EDCB1FCEFC6DFB23DC3505A882655FF77375ED8AA2D1C13F640FCCC2D0C85

`root@ip-10-10-123-97:~# hashid hash.txt `

```
--File 'hash.txt'--
Analyzing 'F09EDCB1FCEFC6DFB23DC3505A882655FF77375ED8AA2D1C13F640FCCC2D0C85'
[+] Snefru-256 
[+] SHA-256 
[+] RIPEMD-256 
[+] Haval-256 
[+] GOST R 34.11-94 
[+] GOST CryptoPro S-Box 
[+] SHA3-256 
[+] Skein-256 
[+] Skein-512(256) 
--End of file 'hash.txt'--
```

`root@ip-10-10-123-97:~# hashcat -m 1400 hash.txt /usr/share/wordlists/rockyou.txt `

```
f09edcb1fcefc6dfb23dc3505a882655ff77375ed8aa2d1c13f640fccc2d0c85:paule
```

## 1DFECA0C002AE40B8619ECF94819CC1B

```
--File 'hash.txt'--
Analyzing '1DFECA0C002AE40B8619ECF94819CC1B'
[+] MD2 
[+] MD5 
[+] MD4 
[+] Double MD5 
[+] LM 
[+] RIPEMD-128 
[+] Haval-128 
[+] Tiger-128 
[+] Skein-256(128) 
[+] Skein-512(128) 
[+] Lotus Notes/Domino 5 
[+] Skype 
[+] Snefru-128 
[+] NTLM 
[+] Domain Cached Credentials 
[+] Domain Cached Credentials 2 
[+] DNSSEC(NSEC3) 
[+] RAdmin v2.x 
--End of file 'hash.txt'--
```

`root@ip-10-10-123-97:~# hashcat -m 1000 hash.txt /usr/share/wordlists/rockyou.txt `

```
1dfeca0c002ae40b8619ecf94819cc1b:n63umy8lkf4i    
```

## Hash: $6$aReallyHardSalt$6WKUTqzq.UQQmrm0p/T7MPpMbGNnzXPMAXi4bJMl9be.cfi3/qxIf.hsGpS41BqMhSrHVXgMpdjS6xeKZAs02. Salt: aReallyHardSalt

`root@ip-10-10-123-97:~# echo '$6$aReallyHardSalt$6WKUTqzq.UQQmrm0p/T7MPpMbGNnzXPMAXi4bJMl9be.cfi3/qxIf.hsGpS41BqMhSrHVXgMpdjS6xeKZAs02.' > hash.txt `

`root@ip-10-10-123-97:~# hashid hash.txt `

```
--File 'hash.txt'--
Analyzing '$6$aReallyHardSalt$6WKUTqzq.UQQmrm0p/T7MPpMbGNnzXPMAXi4bJMl9be.cfi3/qxIf.hsGpS41BqMhSrHVXgMpdjS6xeKZAs02.'
[+] SHA-512 Crypt 
--End of file 'hash.txt'
```

This takes forever so let's take the face we know the password is 6 characters.

`root@ip-10-10-123-97:~# grep -x '.\{6\}' /usr/share/wordlists/rockyou.txt > 6letterwords.txt`


`root@ip-10-10-123-97:~# hashcat -m 1800 hash.txt 6letterwords.txt `

After 30 minutes...

```
$6$aReallyHardSalt$6WKUTqzq.UQQmrm0p/T7MPpMbGNnzXPMAXi4bJMl9be.cfi3/qxIf.hsGpS41BqMhSrHVXgMpdjS6xeKZAs02.:waka99
```



## Hash: e5d8870e5bdd26602cab8dbe07a942c8669e56d6 Salt: tryhackme

```
--File 'hash.txt'--
Analyzing 'e5d8870e5bdd26602cab8dbe07a942c8669e56d6'
[+] SHA-1 
[+] Double SHA-1 
[+] RIPEMD-160 
[+] Haval-160 
[+] Tiger-160 
[+] HAS-160 
[+] LinkedIn 
[+] Skein-256(160) 
[+] Skein-512(160) 
--End of file 'hash.txt'--
```

`e5d8870e5bdd26602cab8dbe07a942c8669e56d6:tryhackme` added salt to the end of `hash.txt`

`root@ip-10-10-123-97:~# hashcat -m 160 hash.txt /usr/share/wordlists/rockyou.txt `

```
e5d8870e5bdd26602cab8dbe07a942c8669e56d6:tryhackme:481616481616
```
