malcolm.barclay2004@gmail.com

# Escaping in Packets

## Flag
Flag: L34v1Ng_tH3_5y5t3M

## Briefing
Dowload the packet capture, find and decode the data being exfiltrated.

By dooby2004.

## Infrastructure
- Host the download file.

## Risks
The packets that are used in the catpure were edited from packets recorded on mt network, so the MAC addresses and IP addresses could be potentially dangerous to give out. I did change the MAC addresses for random ones and canged the 'CF-Connecting-IP' and 'X-Forwarded-For' to something random as well as the 'Host' URL. I didn't change the source and destination IPs as changing them changed the type of packet, however one of them was a private IP that wouldn't be much use to people and the other was the IP of Cloudflare which is most likely public and would know how to handle problems or spam.

## Walkthrough
The student should look thrpugh the packets and see that the subdomains being used in the target URLs are seemingly random. Putting all of them together will give them a string:
MTEwMTAxMTBYT1IxMDAxMDAwMDEwMTExMDEwMTAxMTAxMTExMDExMDAwMTExMTAxMTAwMTExMTAxMTAxMDAxMTAxMDExMTAwMTAxMTExMDAwMTAxMDEwMDAwMDExMTAwMTExMTAwMTEwMDAxMDExMDAwMTEwMDAxMDAxMTAxMDAwMTAxMDAxMTExMDExMTAwMTAxMTAwMDEwMDExMTEwMDAxMTEwMTAxMTExMTExMDAwMTExMDEwMDAxMDExMTAwMTAxMTAwMTEwMTE

The student should then put this through a base 64 decoder to get:
11010110XOR100100001011101010110111101100011110110011110110100110101110010111100010101000001110011110011000101100011000100110100010100111101110010110001001111000111010111111100011101000101110010110011011

Next the student should put the bytes after 'XOR' and the byte before into an XOR decoder/function with the single byte repeated for the length of the the longer number, giving them:
010001100110110001100001011001110011101000100000010011000011001100110100011101100011000101001110011001110101111101110100010010000011001101011111001101010111100100110101011101000011001101001101

Finally, the number should be put into a binary decoder to get the flag.
