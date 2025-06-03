75% of cyber attacks are against web-based applications [Acunetix]([https://www.acunetix.com/websitesecurity/web-application-attack/](https://www.acunetix.com/websitesecurity/web-application-attack/))
Attack methods
- SQL Inection
- XSS
- Command Injection
- IDOR
- RFI & LFI
- FIle Upload (Web shell)

##### HTTP Request review example
![](../../../../../../7.%20Images/HTTP-Request.png)
An HTTP request consists of a request line, request headers, and a request message body. The request line consists of the HTTP method and the resource requested from the web server. The request headers contain certain headers that the server will process. The request message body contains the data to be sent to the server.

1. The GET method indicates that the resource "/" is being requested from the server. Because there is no name, a symbol like "/" means that the main page of the web server is being requested.
2. Nowadays there are web applications that belong to more than one domain found on a single web server, so browsers use the "Host" header to identify which domain the requested resource belongs to.
3. When a web application wants to store information on the client's device, it stores it in a "cookie" header. Cookies are typically used to store session information. This saves you from having to re-enter your username and password when you visit a web application that requires you to log in.
4. The “Upgrade-Insecure-Requests” header indicates that the client wants to communicate using encryption (SSL).
5. The “User-Agent” header contains information about the client's browser and operating system. Web servers use this information to send specific HTTP responses to the client. You can find some automated vulnerability scanners by looking under this header.
6. The type of data requested is in the “Accept” header.
7. The type of encoding accepted by the client is found in the “Accept-Encoding” header. You can usually find the names of compression algorithms under this header.
8. The “Accept-Language” header contains the client's language information. The web server uses this information to display the prepared content in the client's language.
9. The “Connection” header shows how the HTTP connection is made. If there is data such as "close", it means that the TCP connection will be closed after receiving the HTTP response. If you see "keep-alive", this means that the connection will be maintained.
10. An empty line is inserted between the HTTP request header and the HTTP request message body to create a partition.
11. Any other data to be sent to the web application is in the Request Message Body. If the HTTP POST method is used, then the POST parameters can be found here.

---
### SQL Injections
3 types
- in-band SQLi (Classic)
	- when an SQL query is sent and responded to on the same channel
	- easier for attackers to exploit than other categories of SQLi
- inferential SQLi (Blind)
	- SQL queries that receive a response that cannot be seen are called inferential SQLi
	- "Blind" because the response cant be seen
- out-of-band SQLi
	- the response to an SQL query is communicated through another channel
	- eg. the attacker receives replies to the SQL queries via DNS

When attackers are successful they obtain/can
- Authentication bypass
- Command execution
- Exfiltration of sensitive data
- Creating/Deleting/Updating database entries

###### How to prevent them
- **Use a framework:** Of course, just using a framework is not enough to prevent a SQL injection attack.
- **Keep your framework up to date**
- **Always sanitize data received from a user:** Never trust data received from a user. In addition, sanitize all data (such as headers, URLs, etc.), not just form data.
- **Avoid the use of raw SQL queries**

###### How to detect them
- When examining a web request, check all areas that come from the user, such as forms and HTTP request headers "User-Agent"
- look for SQL keywords such as "INSERT", "SELECT", "WHERE", in data received from users
- check for any special characters
- familiarise yourself with commonly used SQLi payloads

##### Detecting automated SQLi tools (SQLMap)
- Look at the user-agent
- check the frequency of requests
- look at the content of the payload:
	- an SQLi payload sent by an automated tool might have sqlmap in their requests.
- if the payload is complicated
	- they tend to be more complicated(not always)

**DO NOT UPLOAD ACCESS LOGS TO 3RD PARTY WEB APPS**

You can determine whether a SQL injection attack has been successful by looking at the response size, since we will almost never have access to the response itself, if there is a noticeable difference in response sizes then the attack was probably successful, anyways best to escalate the alert to a senior analyst

---
## Detecting IDOR attacks
**I**nsecure **D**irect **O**bject **R**eference (IDOR) is a vulnerability caused by the absence or improper use of an authorization mechanism. It allows one person to access an object that belongs to another.

IDOR attacks are harder to detect than others because it does not have certain payloads such as SQLi or XSS, HTTP responses would help but they are not logged for several reasons, thus making IDOR attacks harder to identify
A number of methods can be used to identify IDOR attacks. These are:

- **Check all parameters:** An IDOR vulnerability can occur in any parameter. Therefore, do not forget to check all parameters.
- **Look at the number of requests made to the same page:** When attackers discover an IDOR vulnerability, they usually want to access the information of all the other users, so they typically perform a brute-force attack. This is why you may see many requests for the same page from one source.
- **Try to find a pattern:** Attackers will plan a brute-force attack to reach all objects. Since they will be performing the attack on successive and predictable values, such as whole numbers, you can try to find a pattern in the requests you see. For example, if you see requests like id=1, id=2, id=3, you might be suspicious.

---
### Detecting RFI and LFI

Both are ecurity vulns that occur when a file is included without sanitizing the data obtained form a user

##### LFI (Local File Inclusion)
- File is on the same web server that the application is hosted on
##### RFI (Remote File Inclusion)
- File is on another server

How can we detect and prevent LFI and RFI attacks?

- **Look for any special characters:** Within the data received from users, look for notations such as '/', `.`, `\`.
- **Become familiar with files commonly used in LFI attacks:** In an LFI attack, the attacker reads the files on the server. Knowing the critical file names on the server will help us detect LFI attacks.
- **Look for acronyms such as HTTP and HTTPS:** In RFI attacks, the attacker injects the file into their own device and allows the file to run.

---
### Open Redirection Attacks
Web Security vulnerability that occurs when a website redirects users to a different URL without proper validation or sanitization of the target URL.
In this type of attack, an attacker will usually make a legitimate URL hosted on the vulnerable website, but including a malicious URL as a parameter or query string

###### Types or possible vectors
- **URL-based: 
	- Most common type of open redirection
	- Website takes a URL as input with no validation/sanitization
- **Javascript based:
	- Website uses JS to redirect but target URL is obtained from untrusted or user-controlled sources
	- Also no S/V
- **Meta refresh based:
	- "Meta refresh" tag used on headers
	- Meta refresh is a method of **instructing a web browser to automatically refresh the current web page or frame after a given time interval**
- **Header based
	- Such as "Location" header
- **Parameter based
	- Parameter in URL or form submission

NOTE:  Open redirection vulnerabilities can result in legal and regulatory consequences, especially if sensitive user information is compromised. Organizations may face legal liabilities, fines, or other penalties for failing to protect user data and secure their web applications.

###### Prevention methods
- V and S inputs
- Use a whitelist approach when filtering out specific characters
	- Better than blacklist usually
- Avoid using user-controlled data in redirects
- Implement proper authorization and authentication
- Implement secure coding practices
	- Libraries
	- Frameworks
	- Up to date software
	- Regular security reviews

![](../../../../../../7.%20Images/Example+Vulnerable.png)
*Example of vulnerable redirect code*

![](../../../../../../7.%20Images/Example+Fixed.png)
*Fixed version*


##### Detecting the attack
If there is a consecutive requests to query string parameters such as ?next (http://website.com/param.php?next=), or ?url ( http://website.com/…?url=), with payloads like http://attacker.com or attacker.com (URL structure)
    For the WAF or other middleware products, sometimes payloads can have bypass techniques like;
        Localhost
            http://[::]:25/
            http://①②⑦.⓪.⓪.⓪
        CDIR
            http://127.0.0.0
        Decimal Bypass
            http://2130706433/ = http://127.0.0.1
        Hexadecimal Bypass
            http://0x7f000001/ = http://127.0.0.1
    Encoded characters like %2f = /

Of course it’s not possible to detect or analyze web server logs without using automated detection methods. For an easier way, any SOC analyst can use the following regex to detect open redirection attacks. 

/^.*"GET.*\?.*=(https%3a%2f%2f[a-z0-9-]+%2e[a-z]{2,}).+?.*HTTP\/.*".*$/gm

This regex will match any log entry where the HTTP method is GET, the request contains a query parameter with https://x.com, and the request is using HTTP version 1.0 or 1.1. This should match the most common open redirection attack patterns.

You can customize this regex to match specific query parameters or HTTP methods that are relevant to your web application. Remember that this regex is just one part of an overall security monitoring strategy and should be used in conjunction with other security tools and best practices.

### Directory Traversal
Directory traversal is an attack type that the attackers leverage often to access files and directories that are stored outside the web server's root directory. It involves manipulating input to be able to access files on a web server that are actually not intended to be accessible by unauthorized users. This type of attack is also known as the =="dot-dot-slash"== attack, and it can be used to gain unauthorized access to sensitive data or execute arbitrary code on a web server.
At first look, it’s pretty similar to a Local File Inclusion vulnerability. The main difference between the directory traversal and LFI is the source of the input. Directory traversal involves in manipulating the input that is used to access files on a web server, whereas LFI involves in manipulating input that is used to include local files within a web application.

###### Possible Vectors
1. **User input:** Attackers can manipulate user input parameters, such as URLs, file paths, and form fields, to access files outside of the intended directory. This can be done by adding "../" or other special characters to the input.
2. **Cookies:** If a web application stores user data in cookies, attackers can try to manipulate the cookie value to access files outside of the intended directory.
3. **HTTP headers
4. **File upload
5. **Direct requests:**
6. **URL manipulation:**
7. **Malicious links**

###### Prevention methods
Pretty much the same as in Open Redirection attacks

![](../../../../../../7.%20Images/img3.png)
*Vulnerable code*

![](../../../../../../7.%20Images/img4.png)
*Fixed version*

## Brute Force Attacks
Brute forcing is a type of attack that involves attempting to guess a password or authentication token by systematically trying every possible combination of characters until the correct one is found using automated tools, pretty self explanatory.
![](../../../../../../7.%20Images/img1.png)
*code susceptible to brute forcing*
![](../../../../../../7.%20Images/img2.png)
*fixed (prevent unlimited login attempts)*

###### Attack impact
1. **Denial of service:** Brute forcing can consume a significant amount of computing resources, such as CPU cycles and memory, which can lead to system slowdowns or crashes. This can cause a denial of service (DoS) attack, which makes the target system unavailable to legitimate users.
2. **Data leakage
3. **Account takeover
4. **Password reuse
5. **Legal and reputational consequences

##### Prevention methods
**Implement CAPTCHA
- **Limit the rate of login attempts
- **Use multi-factor authentication
- **Monitoring login attempts:** 
	-  This involves monitoring login attempts for signs of suspicious activity, such as multiple failed login attempts from the same IP address, or unusual spikes in traffic or requests. This can help to detect and prevent brute force attacks before they are successful.
- **Using strong passwords and password policies

Here's an example of a regular expression that can be used to detect repeated failed login attempts from the same IP address in an nginx log file:

/^(\S+) \S+ \S+ \[.*?\] "(POST|GET) \/login\.php.*?" (401|403) \d+ ".*?" ".*?"/gm
This regular expression will match any log file entry that includes a failed login attempt **(401 or 403 status code)** to the **/login.php** page. It will capture the IP address of the client making the request in the first capture group **((\S+))**. You can then use a log analysis tool or script to count the number of times each IP address appears in the log file and flag any IP addresses that have a high number of failed login attempts as potential brute force attackers. Also, you can update the regex’s IP address as suspicious IP source.

## XML External Entity
XXE (XML External Entity) vulnerability is a type of security vulnerability that affects applications that parse XML input. In an XXE attack, an attacker injects malicious XML data into an application that uses an XML parser without proper validation, which can result in the application processing external entities that can be controlled by the attacker.
![](../../../../../../7.%20Images/img5.png)
*vulnerable example*

![](../../../../../../7.%20Images/img6.png)
*fixed, disabled external entities using the function **libxml_disable_entity_loader()**, which prevents XXE attacks. We have then validated and sanitized the XML input using a regular expression that only allows alphanumeric and underscore characters. If the input passes validation, we load it into the **DOMDocument** object and output the sanitized XML. If the input fails validation, we output an error message.*

##### Prevention methods
**Disable external entities:** One of the most effective ways to prevent XXE attacks is to disable the processing of external entities in the XML parser configuration. This can be done by setting the appropriate parser configuration or using a secure XML parser that has external entity processing disabled by default.

**Input validation and sanitization:** Always validate and sanitize all XML input before parsing it. This includes checking for malicious input such as nested XML entities, XML injections, and other forms of malicious input.

**Use secure parsers:** Use the latest version of a secure XML parser that has been specifically designed to prevent XXE attacks. These parsers have features that can help detect and prevent XXE attacks.

**Use whitelist filtering:** Implementing a whitelist of allowed entities and DTDs can help reduce the risk of XXE attacks by blocking any input that is not on the whitelist.

**Implement access controls:** Implement proper access controls to restrict access to sensitive data and resources. This can help limit the damage in case an XXE vulnerability is exploited.

##### Example payloads
![](../../../../../../7.%20Images/img7.png)
*Basic XXE Payload*

![](../../../../../../7.%20Images/img8.png)
*Blind XXE Payload*

![](../../../../../../7.%20Images/img9.png)
*XXE Payload with PHP Filter*

  

The most important things to detect XXE attacks on the logs, you should check specific keyword like;

- DOCTYPE
- ELEMENT
- ENTITY

So for the detecting !DOCTYPE keyword in nginx logs, we can use regex like;

^(\S+) - (\S+) \[(.*?)\] "(\S+) (.*?)\?(?=.*?\b21DOCTYPE\b).*? HTTP\/\d\.\d" (\d+) (\d+) "(.*?)" "(.*?)"


