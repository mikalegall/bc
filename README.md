# In God We Trust

["ICT Security Basics - from Trust to Blockchain"](https://www.google.com "Blockchain (BitCoin)") assignments from Tero Karvinen's teaching; documented with [MarkDown](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)
(aiheesta suomeksi osoitteessa https://rakenne.wordpress.com/2020/10/29/linux-tuo-windows-kayttajan-morko/#offtopic)
<br />
<br />
<br />
### [H1a (Point out from a real life security incident the concepts of threat actor, exploit, vulnerability, impact and risk) & H1b (Analyzing security incident)](https://terokarvinen.com/2020/ict-security-basics-from-trust-to-blockchain-itc4hm003-3001-2020-spring/#h1): Two databases were copied from online forums. One of these data breach includes a private encryption key allegedly used by administrators. These forums were popular with persons who are willing to take a risks with law (experienced cybercriminals). There was also an attempt to dump all network traffic from third [cracker](https://securitytrails.com/blog/hacker-vs-cracker) forum.

So in these cases [threat actor](https://www.beyondtrust.com/blog/entry/difference-between-a-threat-actor-hacker-attacker/) may or may not have technical skills to break in and therefore it is possible that behind these actions is a group (like interest group of "law-abiding" people) which practice "break down and control" method through the tech guys who perform the actual ICT work.

Evil program code ([exploit](https://www.trendmicro.com/vinfo/us/security/definition/exploit)) or possibly unrepaired backdoor ([vulnerability](https://www.rapid7.com/fundamentals/vulnerabilities-exploits-threats/)) did not appear in the news, so exploit method was not identified so far on those DataBase cases. How ever the attempt to dump all network traffic was somehow exploited to achieve unauthorized secure shell access to the server.

<img alt="Risk matrix" src="https://www.pratum.com/images/content/RiskMatrix_Pratum_20200422_PXX.jpg" />

<br />

It is possible that the [risk](https://www.forbes.com/sites/theyec/2019/10/01/10-data-security-risks-that-could-impact-your-company-in-2020/) of getting compromised was low because assumed administrators could have been experienced Russian cybercriminals but [impact](https://www.cisa.gov/blog/2021/01/14/risk-based-approach-national-cybersecurity) in these cases were high because it is possible that real people behind nicknames can be traced (thanks to individual information that has been stored in those breached DataBases).

I don't know if it would have been possible to avoid private key leak by

1) creating separate Admin user and removing the Root/Superuser keys as well as storing Root/Superuser credentials in a safe place (only the new Admin account is used to create services or perform other administrative tasks)

2) using some kind of Bastion jump box 🤔

Or clean up the database from ip addresses of the first registrations and cookies etc. in the spirit of GDPR (MyData readiness for "right to be forgotten").

News source: [Three Top Russian Cybercrime Forums Hacked](https://krebsonsecurity.com/2021/03/three-top-russian-cybercrime-forums-hacked/)

<br />
<br />
<br />

### [H1b (Analyzing security incident)](https://terokarvinen.com/2020/ict-security-basics-from-trust-to-blockchain-itc4hm003-3001-2020-spring/#h1): The world's first Bitcoin exchange, [Magic the Gathering Online Exchange](https://www.mtgox.com/ "Mt. Gox") aka Mt. Gox (launched in 2010 by Jed McCaleb and afterwards managed by Mark Karpelès), was compromised several times. Methods where like manipulating API calls into third party destination, privilege escalation for allowed account and so on. One of the abuse case was to compromise the "wallet.dat" file so the cybercriminal could foward total of 650.000 Bitcoins during almost two years period. 

<img alt=" Cyber Kill Chain" src="https://www.lockheedmartin.com/content/dam/lockheed-martin/rms/photo/cyber/THE-CYBER-KILL-CHAIN-body.png.pc-adaptive.1920.medium.png" />

<br />

Reconnaissance: ?

Weaponization: ?

Delivery: ?

Exploitation: ?

Installation: Maybe some malware had been left on this Mt. Gox´s Bitcoin exchange server or the attacker must otherwise have made the intrusion each time again for a couple of years.

Command and Control: Definedly there has been some kind of connection pipe for remote manipulation of victim because the abuse lasted couple of years.

Actions on Objectives: Obviously there has also been "Hands on keyboard" access because intruder was able to perform tasks to achieve the goal many times.

<br />

News source: [https://darknetdiaries.com/transcript/9/](https://darknetdiaries.com/transcript/9/ "Darknet Diaries")

<br />
<br />
<br />

### [H1c (Attack tree analysis of the target)](https://terokarvinen.com/2020/ict-security-basics-from-trust-to-blockchain-itc4hm003-3001-2020-spring/#h1): Persistent data


[Attack tree](https://www.schneier.com/academic/archives/1999/12/attack_trees.html) GOAL: Manipulate persistent data (like Bitcoin´s "wallet.dat" file) or copy all of it 
<br />
<br />
(Those [DevSecOps](https://docs.microsoft.com/en-us/azure/architecture/solution-ideas/articles/devsecops-in-github) guys can [seek best practises)](https://attack.mitre.org/mitigations/M1013/)
<img alt="Multi tier architecture" src="https://rakenne.files.wordpress.com/2021/04/scalable_architecture.jpg" />

<br />
Rough draft (was left unfinished):
<br />

1 Exploit possible input fields of web page

1.1. Injection

1.2. Cross-site scripting --> Broken Authentication

1.3. Renaming input fields

2 Exploit browser address bar (or use Postman, Fidler etc)

2.?

3 Privilege escalation by adding your connection to specific security policy group

3.? "Lateral movement" (jump on to next hop)

3.? Reconnaissance: Information gathering of structure 

3.? Break in to jumper

3.? Reconnaissance: Information gathering of structure (for example public IP-addresses)

was left unfinished...

<br />
<br />
<br />

### [H1d (MITRE: Give example of tactics, techniques and procedures from the ATT&CK framework)](https://terokarvinen.com/2020/ict-security-basics-from-trust-to-blockchain-itc4hm003-3001-2020-spring/#h1): Privilege Escalation - Sudo Caching - Proton

[Tactic](https://attack.mitre.org/tactics/enterprise/): [Privilege Escalation](https://attack.mitre.org/tactics/TA0004/) consists of techniques that criminals use to gain higher-level permission.

* [Technique](https://attack.mitre.org/techniques/enterprise/): Within Linux and MacOS systems ["SuperUser do" (sudo) credentials caching](https://attack.mitre.org/techniques/T1548/003/) allows users to perform commands with elevated privileges and it has some amount of time ("timestamp_timeout" range) in minutes when it won´t prompt for a password. Variable "tty_tickets" isolates open terminal sessions. If "tty_tickets" is disabled and sudo credentials caching is valid then attacker can execute commands with elevated privileges without password from any new terminal.

    * [Procedure](https://attack.mitre.org/software/S0279/): Backdoor malware for macOS (called [Proton](https://www.cybereason.com/blog/labs-proton-b-what-this-mac-malware-actually-does)) cheat user to enter their password on some believable dialog prompt and then use it to modifiy the tty_tickets line in the sudoers file:

        sudo -S sh -c "echo \'Defaults !tty_tickets\' >> /etc/sudoers";

Proton does what it wants and then erase logs

        sudo -S rm -rf /var/log/* /Library/Logs/*
