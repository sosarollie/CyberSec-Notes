The help page contains multiple sections:

- **Usage:** Shows the syntax on how to use the command.
- **Available Commands:** Multiple commands are available to aid us in enumerating directories, files, DNS subdomains, Google Cloud Storage buckets, and Amazon AWS S3 buckets. Throughout this room, we will focus on the `dir`, `dns`, and `vhost` commands. We will cover each of them in the following tasks.
- **Flags:** These are specific options we can configure to customize our commands. Let’s look at the flags we will often use throughout this room:

|Short Flag|Long Flag|Description|
|---|---|---|
|`-t`|`--threads`|This flag configures the number of threads to use for the scan. Each of these threads sends out requests with a slight delay. The default number of threads is 10. This number may be slow when using large wordlists. You can increase or decrease the number of threads depending on the available system resources.|
|`-w`|`--wordlist`|The flag configures a wordlist to use for iterating. Each wordlist entry is attached to the URL you included in the command.|
||`--delay`|This flag defines the amount of time to wait between sending requests. Some web servers include mechanisms to detect enumeration by looking at how many requests are received in a certain period of time. We can increase the delay between subsequent requests to make it look like normal web traffic.|
||`--debug`|This flag helps us to troubleshoot when our command gives unexpected errors.|
|`-o`|`--output`|This flag writes the enumeration results to a file we choose.|

## Example

Let us look at an example of how we would use these commands and flags together to enumerate a web directory:

```
gobuster dir -u "http://www.example.thm/" -w /usr/share/wordlists/dirb/small.txt -t 64
```

- `gobuster dir` indicates that we will use the directory and file enumeration mode.
- `-u "http://www.example.thm/"` tells Gobuster that the target URL is http://example.thm/.
- `-w /usr/share/wordlists/dirb/small.txt` directs Gobuster to use the _small.txt_ wordlist to brute force the web directories. Gobuster will use each entry in the wordlist to form a new URL and send a GET request to that URL. If the first entry of the wordlist were images, Gobuster would send a GET request to [http://example.thm/images/.](http://example.thm/images/.)
- `-t 64` sets the number of threads Gobuster will use to 64. This improves the performance drastically.


## How To Use dir Mode

To run Gobuster in `dir` mode, use the following command format:

```
gobuster dir -u "http://www.example.thm" -w /path/to/wordlist
```

  
Notice that the command also includes the flags `-u` and `-w`, in addition to the `dir` keyword. These two flags are required for the Gobuster directory enumeration to work. Let us look at a practical example of how to enumerate directories and files with Gobuster `dir` mode:

```
gobuster dir -u "http://www.example.thm" -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -r
```

  
This command scans all the directories located at _www.example.thm_ using the wordlist _directory-list-2.3-medium.txt_. Let’s look a bit closer at each part of the command:

- `gobuster dir`: Configures Gobuster to use the directory and file enumeration mode.
- `-u http://www.example.thm`:

- The URL will be the base path where Gobuster starts looking. So, the URL  above is using the root web directory. For example, in a typical Apache installation on Linux, this is `/var/www/html`. So if you have a “resources” directory and you want to enumerate that directory, you’d set the URL as `http://www.example.thm/resources`. You can also think of this like `http://www.example.thm/path/to/folder`.
- The URL must contain the protocol used, in this case, HTTP. This is important and required. If you pass the wrong protocol, the scan will fail.
- In the host part of the URL, you can either fill in the IP or the HOSTNAME. However, it is important to mention that when using the IP, you may target a different website than intended. A web server can host multiple websites using one IP (this technique is also called virtual hosting). Use the HOSTNAME if you want to be sure.
- Gobuster does not enumerate recursively. So, if the results show a directory path you are interested in, you will have to enumerate that specific directory.

- `-w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt` configures Gobuster to use the _directory-list-2.3-medium.txt_ wordlist to enumerate. Each entry of the wordlist is appended to the configured URL.
- `-r` configures Gobuster to follow the redirect responses received from the sent requests. If a status code 301 was received, Gobuster will navigate to the redirect URL that is included in the response.  
    

Let’s look at a second example where we use the `-x` flag to specify what type of files we want to enumerate:

```
gobuster dir -u "http://www.example.thm" -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -x .php,.js
```

### How to Use dns Mode

To run Gobuster in dns mode, use the following command syntax:  
`gobuster dns -d example.thm -w /path/to/wordlist`  

Notice that the command also includes the flags `-d` and `-w`, in addition to the `dns` keyword. These two flags are required for the Gobuster subdomain enumeration to work. Let us look at an example of how to enumerate  subdomains with Gobuster dns mode:

`gobuster dns -d example.thm -w /usr/share/wordlists/SecLists/Discovery/DNS/subdomains-top1million-5000.txt`

- `gobuster dns` enumerates subdomains on the configured domain.  
    
- `-d example.thm` sets the target to the _example.thm_ domain.  
    
- `-w /usr/share/wordlists/SecLists/Discovery/DNS/subdomains-top1million-5000.txt` sets the wordlist to s_ubdomains-top1million-5000.txt_. Gobuster uses each entry of this list to construct a new DNS query. If the first entry of this list is 'all', the query would be _all.example.thm._

## How To Use vhost Mode

To run Gobuster in `vhost` mode, type the following command:

```
gobuster vhost -u "http://example.thm" -w /path/to/wordlist
```

