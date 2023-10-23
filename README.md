# CVE-2023-20198
CVE-2023-20198 Checkscript based on: https://blog.talosintelligence.com/active-exploitation-of-cisco-ios-xe-software/
Including the updated where there is an Authorization header to check for the known implant. 

!! Upgraded to look for upgraded implant 



The script checks length of returned response with code 200, and checks if length is shorter then 32 characters. Each IP returning shorter length than 32 chars should be checked to se if device is compromised. This script *only* gives you an indicator, not proof that the device is compromised.

The script also checks if the implant has been upgraded, as dicovered by Fox-IT: https://github.com/fox-it/cisco-ios-xe-implant-detection


Run:

```
python cve-2023-20198.py


and enter you desired subnet to scan. For example:

python CVE-2023-20198


Enter the subnet (CIDR notation): 10.0.0.0/22

IP: 10.0.0.94 - Error: no reply

IP: 10.0.0.94 - Error: no reply

IP: 10.0.0.96 - Status: 200

IP: 10.0.0.96 - Response is a potentially suspicious: 


IPs with status code 200, suspicious length, should be checked:

['10.0.0.96']

IPs with status code 200, but no IOC:

[]
```
