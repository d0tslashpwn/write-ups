---
title:   "Write-up - Sunshine CTF 2016 - Randy"
date:    2016-03-14 00:00:00
tags:    [Write-up, Sunshine CTF 2016]
summary: "Write-up about Sunshine CTF 2016 - Randy"
---

```
import telnetlib
import struct

x = lambda a: struct.pack('I', a)

def fukmin(x):
    return hex((int(x, 16) - 0x41) & 0xff)

host = "4.31.182.242"
port = "9002"

s = telnetlib.Telnet(host, port)

welcome = s.read_until(b"\n")
(a, b, c, d) = (welcome[41:42].encode("hex"),
                welcome[42:43].encode("hex"),
                welcome[43:44].encode("hex"),
                welcome[44:45].encode("hex"))

debuginfo = a + b + c + d
print "debuginfo = 0x" + debuginfo
print " - - - - - "

magic = fukmin(a) +\
        fukmin(b)[2:]+\
        fukmin(c)[2:]+\
        fukmin(d)[2:]
print "magic = " + magic
print " - - - - - "

s.write(x(int(magic, 16)))
print s.read_all()

''' OUTPUT:
debuginfo = 0x6ba9580a
 - - - - - 
magic = 0x2a6817c9
 - - - - - 

We've dealt you your hand face down, please enter it:
You guessed that hand perfectly! Here's your prize: sun{c4rds_in_th3_tr4p}
'''

''' BONUS:
   <encoding function>
   0x8048608 <main+120>:    sar    ecx,0x18
   0x804860b <main+123>:    and    ecx,0xff
   0x8048611 <main+129>:    add    ecx,eax
   ...
   0x8048625 <main+149>:    sar    ecx,0x10
   0x8048628 <main+152>:    and    ecx,0xff
   0x804862e <main+158>:    add    ecx,eax
   ...
   0x8048642 <main+178>:    sar    ecx,0x8
   0x8048645 <main+181>:    and    ecx,0xff
   0x804864b <main+187>:    add    ecx,eax
   ...
   0x804865f <main+207>:    and    ecx,0xff
   0x8048665 <main+213>:    add    ecx,eax
'''
def saradd(e):
    a=hex((((e >> 0x18) & 0xff) + 0x41 ) & 0xff)
    b=hex((((e >> 0x10) & 0xff) + 0x41 ) & 0xff)
    c=hex((((e >> 0x8) & 0xff) + 0x41 ) & 0xff)
    d=hex((e & 0xff) + 0x41)
    return a + b[2:] + c[2:] + d[2:]
```
