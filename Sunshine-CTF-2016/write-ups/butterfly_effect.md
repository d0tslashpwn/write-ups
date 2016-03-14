---
title:   "Write-up - Sunshine CTF 2016 - Butterfly Effect"
date:    2016-03-14 00:00:00
tags:    [Write-up, Sunshine CTF 2016]
summary: "Write-up about Sunshine CTF 2016 - Butterfly Effect"
---

After downloading a picture of a beautiful butterfly, we need to find the flag inside the picture. The file is available [here](https://raw.githubusercontent.com/d0tslashpwn/ctf-files/master/Sunshine-CTF-2016/forensics/butterfly.png). We use the application [Steganabara](https://www.wechall.net/downloads/by/user_name/ASC/page-1).

```
% java -jar steganabara-1.1.1.jar
```

We modify a bit the color as shown below.

<p align="center"><img width="15%" src="https://raw.githubusercontent.com/d0tslashpwn/write-ups/master/Sunshine-CTF-2016/assets/steganabara_matrix.jpg"/></p>

We finally find the flag; `sun{READY_THE_4CID_M4GNET!}`.

<p align="center"><img width="45%" src="https://raw.githubusercontent.com/d0tslashpwn/write-ups/master/Sunshine-CTF-2016/assets/butterfly_effect.jpg"/></p>
