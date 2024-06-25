```sh
hacker@pwntools~level-0-0:~$ ipython
Python 3.8.10 (default, Nov 22 2023, 10:22:35) 
Type 'copyright', 'credits' or 'license' for more information
IPython 8.12.3 -- An enhanced Interactive Python. Type '?' for help.

In [1]: from pwn import *
   ...: import time
   ...: 
   ...: # Set up the pwntools context
   ...: context(arch="amd64", os="linux", log_level="info")
   ...: 
   ...: # Path to the binary (adjust this path as needed)
   ...: challenge_path = "/challenge/pwntools-tutorials-level0.0"
   ...: 
   ...: # Create a process for the binary
   ...: p = process(challenge_path)
   ...: 
   ...: # The payload to bypass the check
   ...: payload = b'pokemon'
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
[x] Starting local process '/challenge/pwntools-tutorials-level0.0'
[+] Starting local process '/challenge/pwntools-tutorials-level0.0': pid 214
[*] Process '/challenge/pwntools-tutorials-level0.0' stopped with exit code 0 (pid 214)
flag is: b'pwn.college{0UIU9c7v6gqhuDe88CO72_039bW.dlzM5QDLxITOwUzW}\n'
```


```sh

from pwn import *
import time

# Set up the pwntools context
context(arch="amd64", os="linux", log_level="info")

# Path to the binary (adjust this path as needed)
challenge_path = "/challenge/pwntools-tutorials-level0.0"

# Create a process for the binary
p = process(challenge_path)

# The payload to bypass the check
payload = b'pokemon'

# Wait for 1 second before sending the payload
time.sleep(1)

# Send the payload after the specified string is found
p.sendlineafter(b":)\n###\n", payload)

# Receive the output which includes the flag
flag = p.recvline()
print(f"flag is: {flag}")

# Close the process
p.close()

```
