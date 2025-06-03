**Swiss Army knife** for data, these tasks range from simple encodings like **XOR** or **Base64** to complex operations like **AES encryption** or **RSA decryption**. CyberChef operates on **recipes**.

|Operations|Description|Examples|
|---|---|---|
|From Morse Code|Translates Morse Code into (upper case) alphanumeric characters.|`- .... .-. . .- - ...` becomes `THREATS` when used with default parameters|
|URL Encode|Encodes problematic characters into percent-encoding, a format supported by URIs/URLs.|`https://tryhackme.com/r/room/cyberchefbasics` becomes `https%3A%2F%2Ftryhackme%2Ecom%2Fr%2Froom%2Fcyberchefbasics` when used with the parameter “Encode all special chars”|
|To Base64|This operation encodes raw data into an ASCII Base64 string.|`This is fun!` becomes `VGhpcyBpcyBmdW4h`|
|To Hex|Converts the input string to hexadecimal bytes separated by the specified delimiter.|`This Hex conversion is awesome!` becomes `54 68 69 73 20 48 65 78 20 63 6f 6e 76 65 72 73 69 6f 6e 20 69 73 20 61 77 65 73 6f 6d 65 21`|
|To Decimal|Converts the input data to an ordinal integer array.|`This Decimal conversion is awesome!` becomes `84 104 105 115 32 68 101 99 105 109 97 108 32 99 111 110 118 101 114 115 105 111 110 32 105 115 32 97 119 101 115 111 109 101 33`|
|ROT13|A simple Caesar substitution cipher which rotates alphabet characters by the specified amount (default 13).|`Digital Forensics and Incident Response` becomes `Qvtvgny Sberafvpf naq Vapvqrag Erfcbafr`|

Most used operations
## Extract

| Specific                | Description                                                                                                                                                 |
| ----------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Extract IP addresses    | Extracts all IPv4 and IPv6 addresses.                                                                                                                       |
| Extract URLs            | Extracts Uniform Resource Locators (URLs) from the input. The protocol (HTTP, FTP, etc.) is required, otherwise there will be far too many false positives. |
| Extract email addresses | Extracts all email addresses from the input.                                                                                                                |
|                         |                                                                                                                                                             |

## Date and Time
|Specific|Description|
|---|---|
|From UNIX Timestamp|Converts a UNIX timestamp to a datetime string.|
|To UNIX Timestamp|Parses a datetime string in UTC and returns the corresponding UNIX timestamp.|

## Data Format
|Operations|Description|Examples|
|---|---|---|
|From Base64|This operation decodes data from an ASCII Base64 string back into its raw format.|`V2VsY29tZSB0byB0cnloYWNrbWUh` becomes `Welcome to tryhackme!`|
|URL Decode|Converts URI/URL percent-encoded characters back to their raw values.|`https%3A%2F%2Fgchq%2Egithub%2Eio%2FCyberChef%2F` becomes `https://gchq.github.io/CyberChef/`|
|From Base85|notation for encoding arbitrary byte data. It is usually more efficient than Base64. This operation decodes data from an ASCII string (with an alphabet of your choosing, presets included).|`BOu!rD]j7BEbo7` becomes `hello world`|
|From Base58|is a notation for encoding arbitrary byte data. It differs from Base64 by removing efficiently misread characters (i.e. l, I, 0, and O) to improve human readability.|`AXLU7qR` becomes`Thm58`|
|To Base62|is a notation for encoding arbitrary byte data using a restricted set of symbols that humans can conveniently use and process by computers. The high number base results in shorter strings than with the decimal or hexadecimal system|`Thm62` becomes`6NiRkOY`|

[ASCII Table](https://en.wikipedia.org/wiki/ASCII)

