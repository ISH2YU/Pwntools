```
In [2]: from pwn import *
   ...: import time
   ...: 
   ...: # Set up the pwntools context
   ...: context(arch="amd64", os="linux", log_level="info")
   ...: 
   ...: # Path to the binary (adjust this path as needed)
   ...: challenge_path = "/challenge/pwntools-tutorials-level1.0"
   ...: 
   ...: # Create a process for the binary
   ...: p = process(challenge_path)
   ...: 
   ...: # The payload to bypass the check
   ...: payload =  p32(0xdeadbeef)
   ...: 
   ...: # Wait for 1 second before sending the payload
   ...: time.sleep(1)
   ...: 
   ...: # Send the payload after the specified string is found
   ...: p.sendlineafter(b":)\n###\n", payload)
   ...: 
   ...: # Receive the output which includes the flag
   ...: flag = p.recvline()
   ...: print(f"flag is: {flag}")
   ...: 
   ...: # Close the process
   ...: p.close()
   ...: 
[x] Starting local process '/challenge/pwntools-tutorials-level1.0'
[+] Starting local process '/challenge/pwntools-tutorials-level1.0': pid 166
[*] Process '/challenge/pwntools-tutorials-level1.0' stopped with exit code 0 (pid 166)
flag is: b'pwn.college{UuBQJGSsmIvBNH72Nth8dVRa88C.dBDN5QDLxITOwUzW}\n'
```


