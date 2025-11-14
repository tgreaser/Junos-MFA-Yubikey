# Junos-MFA-Yubikey AAL2 maybe even AAL3
DRAFT MFA to Junos
AAL2 A standard for authentication assurance that requires the claimant to control two different authentication factors.
5.2.2 Rate Limiting/Throttling using Junos OS. <br>
Day off so putting in a bummper crop to document howto.(remove when I have worked out with tac the feature requests)<br>

This is a day 0 on how to start on getting NIST Authenticator Assurance Level 2 (AAL2). Once I have some stuff better honed in I will updated .<br>
**ER in to Juniper on getting this docmuented . If like normal the request goes to /dev/null.. This is my way. <br>

Im waiting to see if I can get some  on some gear from account team :) ...  Qfx 5120s, MX301*wish list <br>

My home lab has SRX340, EX4100 and EX4400 <br>
Model: ex4400-24mp  Junos: 25.2R1-S1.4 <br>
Model: ex4100-f-24t Junos: 25.2R1-S1.4 <br>
Model: ex9214     Junos: 25.2R1-9 <br>
Model: ex4600 **waiting on getting one to finish this and other evpn vxlan labs  <br>

Fedora 42 workstaiton x86 <br>
Yubico  Multi-factor authentication (MFA) Security Key, Connect via USB-A FIDO Certified <br>
## Goal meet or exceed AAL2 requirements 
Requirements: You must prove control of two factors, such as a physical authenticator (like a hardware token YubiKey )and a memorized secret (like a password PIN for ED25519-SK key and maybe the passphrase ), or a physical authenticator and a biometric factor.I dont have a biometric reader and honestly as oftern as I mess up my fingers it would not work for me and my lifestyle.<br>
Purpose: To provide a high level of confidence in the control of user accounts by preventing single points of failure from compromised passwords<br>

## URLs
https://pages.nist.gov/800-63-3/sp800-63b.html#63bSec4-Table1<br>
https://pages.nist.gov/800-63-3/sp800-63b.html#t10-1<br>

##  5.1.9.1 and 5.2.2

5.1.9.1 Multi-Factor Cryptographic Device Authenticators<br>
authenticator for activation SHALL be a randomly-chosen numeric value at least 6 decimal digits in length or other memorized secret meeting the requirements of Section 5.1.1.2 and SHALL be rate limited as specified in Section 5.2.2. A biometric activation factor SHALL meet the requirements of Section 5.2.3, including limits on the number of consecutive authentication failures.<br>

https://pages.nist.gov/800-63-3/sp800-63b.html#63bSec4-Table1<br>
https://pages.nist.gov/800-63-3/sp800-63b.html#t10-1<br>
NIST Authenticator Assurance Level 2 (AAL2)<br>
   What it is: A standard for authentication assurance that requires the claimant to control two different authentication factors.<br>
    Requirements: You must prove control of two factors, such as a physical authenticator (like a hardware token) and a memorized secret (like a password), or a physical authenticator and a biometric factor.<br>
    Purpose: To provide a high level of confidence in the control of user accounts by preventing single points of failure from compromised passwords<br>

5.2.2<br>
reauthentication do to user inactivity    "set system login class super-user-local idle-timeout 10"<br>
fixed perodic reauthetication . IIRC that was just checking tacacs if the user account was still in good standings still matched current passwd.<br>
"set system tacplus-options authorization-time interval 10"<br>
"set system login retry-options lockout-period 10"<br>
provsion for tech assiistance. For now.. thinking of is access-ing a on prem linux jump box via say Cockpit using OTP from my own google authenticaor  :)   <br>



## Yubico Linux setup. 
They have other os howtos. 
