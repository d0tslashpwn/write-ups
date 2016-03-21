---
title:   "Write-up - Sunshine CTF 2016 - That's No Moon"
date:    2016-03-14 00:00:00
tags:    [Write-up, Sunshine CTF 2016]
summary: "Write-up about Sunshine CTF 2016 - That's No Moon"
---

For this Forensics challenge, we need to download a picture of a moon. The file is available [here](https://raw.githubusercontent.com/d0tslashpwn/ctf-files/master/Sunshine-CTF-2016/forensics/thats-no-moon/moon.png). After trying to play with colors with [Steganabara](https://www.wechall.net/downloads/by/user_name/ASC/page-1) or [Stegsolve](https://www.wechall.net/forum/show/thread/527/Stegsolve_1.3/page-1) to find a hidden text, we change of strategy. We use the `strings` command. By the end of the output, we can see a `flag.txt` is hidden inside the file.

```
% strings moon.png
...
flag.txtUT  
*nAb(
flag.txtUT)
```

Let is change the extension of the file to a `zip` archive and extract it.

```
% mv moon.png moon.zip
% unzip moon.zip
Archive:  moon.zip
warning [moon.zip]:  411781 extra bytes at beginning or within zipfile
  (attempting to process anyway)
[moon.zip] flag.txt password: 
```

A password is required. After some guessing, we notice that the challenge is titled _That's No Moon_. So let is try `moon` as a password.

```
[moon.zip] flag.txt password: 
extracting: flag.txt
```

Success! The flag is `sun{0kay_it_is_a_m00n}`.
