### Stored XSS
- Simplest kind
- XSS payload sent to the database and is calleed every time a page is loaded

![](../../../../../7.%20Images/Pasted%20image%2020250515220717.png)
## Blind XSS
- a type of stored XSS
- You dont see the alert(0) pop up
- it only pops up on a page you can't see (example if the comment had to be approved by an admin, it would still show in the admin control panel server side)
- Instead you use XSS hunter or crafted payloads to check if the XSS ever fires
![](../../../../../7.%20Images/Pasted%20image%2020250515220703.png)


### XSS Hunter

![](../../../../../7.%20Images/Pasted%20image%2020250515220844.png)

## DOM based XSS
- more tricky
- Any page that's using javascript to populate anything in a page
- In vulnerable pages a dev has used something like document.location and then is outputting this in some way
	- Eg populating a nav bar
- But if we could edit document.location we could cause an XSS by interfering with the nav bar and sending an alert(0) instead

![](../../../../../7.%20Images/Pasted%20image%2020250515221049.png)

### Reflected XSS
- In stored XSS our XSS payload is stored by the database
- Reflected is the opposite
- The input is not stored, but just reflected on another page
- An attacker would set up a malicious link which is then sent to a victim
![](../../../../../7.%20Images/Pasted%20image%2020250515222302.png)


### Self XSS
- Out Of Scope
- Requires someone to go into the developers console and run an XSS payload
- Or edit the HTML
- Or include an XSS payload in a form where the results are only visible to them
- Less hacking more social engineering

### Impact
Best one: CSRF
- You can perform actions as the user by sending data to another endpoint in the web app