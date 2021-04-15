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

### [H1b (Analyzing security incident)](https://terokarvinen.com/2020/ict-security-basics-from-trust-to-blockchain-itc4hm003-3001-2020-spring/#h1): The world's first Bitcoin exchange, [Magic the Gathering Online Exchange](https://www.mtgox.com/ "Mt. Gox") aka Mt. Gox (launched in 2010 by Jed McCaleb and afterwards managed by Mark Karpelès), was compromised several times. Methods where like manipulating API calls into third party destination, privilege escalation for allowed account and so on. One of the abuse case was to compromise the "wallet.dat" file so the cybercriminal could foward total of 650.000 Bitcoins during almost two years period. 

<img alt="Cyber Kill Chain" src="https://www.lockheedmartin.com/content/dam/lockheed-martin/rms/photo/cyber/THE-CYBER-KILL-CHAIN-body.png.pc-adaptive.1920.medium.png" />

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

### [H1d (MITRE: Give example of tactics, techniques and procedures from the ATT&CK framework)](https://terokarvinen.com/2020/ict-security-basics-from-trust-to-blockchain-itc4hm003-3001-2020-spring/#h1): Privilege Escalation - Sudo Caching - Proton

[Tactic](https://attack.mitre.org/tactics/enterprise/): [Privilege Escalation](https://attack.mitre.org/tactics/TA0004/) consists of techniques that criminals use to gain higher-level permission.

* [Technique](https://attack.mitre.org/techniques/enterprise/): Within Linux and MacOS systems ["SuperUser do" (sudo) credentials caching](https://attack.mitre.org/techniques/T1548/003/) allows users to perform commands with elevated privileges and it has some amount of time ("timestamp_timeout" range) in minutes when it won´t prompt for a password. Variable "tty_tickets" isolates open terminal sessions. If "tty_tickets" is disabled and sudo credentials caching is valid then attacker can execute commands with elevated privileges without password from any new terminal.

    * [Procedure](https://attack.mitre.org/software/S0279/): Backdoor malware for macOS (called [Proton](https://www.cybereason.com/blog/labs-proton-b-what-this-mac-malware-actually-does)) cheat user to enter their password on some believable dialog prompt and then use it to modifiy the tty_tickets line in the sudoers file:

        sudo -S sh -c "echo \'Defaults !tty_tickets\' >> /etc/sudoers";

Proton does what it wants and then erase logs

        sudo -S rm -rf /var/log/* /Library/Logs/*


<br />
<br />

### [H2a (Explain how BitCoin uses . . .)](https://terokarvinen.com/2021/trust-to-blockchain-spring-2021/#h2-blockchain-and-cryptocurrency): Satoshi Nakamoto's original paper is available in [many languages](https://bitcoin.org/en/bitcoin-paper)
* Hashes:
<br/>
The current case will be hashed by mathematical [sha256sum](https://emn178.github.io/online-tools/sha256.html) function
* Signatures:
<br/>
Seller signes digitally previously mentioned hash and buyer's public key. Buyer verify seller's signature and earlier happened signatures.

* Blockchain:
<br/>
By signing the previous transactions it will form a link in the chain which contains blocks of 256 bit long hashes

* Proof of work:
<br/>
After signing the next case should that mathematical sha256sum function output start with zeros (eg. 007etc). The more zeros required at the beginning, the longer it takes to form a next valid link in chain. Who ever demonstrates that "gibberish-nonsense" input (which met the criteria with required zeros) proves at the same time that this actor has worked to solve the set target. 

* Concensus:
<br/>
Nodes in peer-to-peer network receives someone's sent proof of work and then the nodes calculates all links in blockchain and if everything is valid. If there are branches on that same chain then the longest chain with most links is valid.  

* Incentive:
<br/>
Reward which will be granted for actor whos proof of work has been validated. That happens to issue brand new bitcoins for actor who's proof of work has been validated.

<br />
<br />


### [H2b (Summarize each video)](https://terokarvinen.com/2021/trust-to-blockchain-spring-2021/#h2-blockchain-and-cryptocurrency): Felten et al 2015: Bitcoin and Cryptocurrency Technologies: [Week 1](https://www.coursera.org/learn/cryptocurrency/home/week/1)

Lecture: Cryptographic Hash Functions
https://www.coursera.org/learn/cryptocurrency/lecture/gFEJL/cryptographic-hash-functions
* Mathematical sha256sum function can take any string as input and it produces a fixed-size output (Bitcoin uses this)
* While using hash in cryptocurrency it has to be collision-free, hiding and also puzzle-friendly


	  Collision-free = In a reasonable time no one can find which existing different inputs produces the same fixed-size output, not even with supercomputers

	  Hiding = previous hash + information to be hidden concatenated to a chain and then hashed again leads to the end result where you can not reverse and reveal information which wanted to be hidden

	  Puzzle-friendly = Any mathematical approach to reveal information which where hidden are not much better than just try to guess 
* No collision of SHA-256 has ever been found

Lecture: Hash Pointers and Data Structures
https://www.coursera.org/learn/cryptocurrency/lecture/EYEAo/hash-pointers-and-data-structures
* Result of hiding can also been seen as a pointer to a previous phase (maps where the hidden information lays) that is how the chain has been made in blockchain

Lecture: Digital Signatures
https://www.coursera.org/learn/cryptocurrency/lecture/bx6si/digital-signatures
* A key ring can be use to form so called secret key pair and public key pair (secret you hide and public you show publicly)
* Only specific secret key pair can produce a certain kind of signature (which is not possible to forge) and public key pair releated to that secret key pair can validate that certain signature to be authentic

Lecture: Public Keys as Identities
https://www.coursera.org/learn/cryptocurrency/lecture/HvhIA/public-keys-as-identities
* When public key pair validate certain signature to be authentic it also says that who ever is behind that secret key pair which can produce validateable things for this public key it also forms identity for the actor behind that secret key pair. So then a public key becomes identity because no one else can manage that
* Anyone can make new key rings (with secret key pair and based on that formulate public key pair that correspond only that secret key pair) anytime and so many as they wants
* Nobody needs to now who is behind certain public key ring
* In context of Bitcoin these public key identities are called addresses and actors can generate them indefinitely. If wanted those can be stored in one centralized place a.k.a. wallet


Lecture: A Simple Cryptocurrency ([In Laa-laa land all well](https://youtu.be/pdAMfkHp4aM?t=632); "Hipiecoin")
https://www.coursera.org/learn/cryptocurrency/lecture/rJ8KJ/a-simple-cryptocurrency
* Anyone can announce that I have imagined some commodity (goods, service, etc.) and now I issue that intangible material or that intellectual property rights by using that commodity as an input for mathematical hash function and then digitally sign it. It is almost like the [smallest Russian doll](https://www.istockphoto.com/vector/russian-matryoshka-babushka-dolls-gm1179776503-330258673) inside another doll except that in Blockchain those "dolls" are almost always fixed-size (remember that previously mentoned "mathematical [sha256sum](https://emn178.github.io/online-tools/sha256.html) function can take any string as input and it produces a fixed-size output") because I assume that keyring length can vary by service provider and then the "doll" size can vary
* The transfer of ownership takes place by encrypting pointer (in this first link of chain it would be digitally signed hash of the announcement) by receiver's aka buyer's public key and then that hash will be confirmed by sender's aka seller's public key
* Problem with this kind of "no one never suspect anything" Hippiecoin-blockchain is that owner can sell it twice ([double-spending attack](https://en.wikipedia.org/wiki/Double-spending)) becouse there is no prevent mechanism
* You can't solve Hippiecoin problem by authorization every transaction over third party because that's not a new "anyone can announce that I have imagined some commodity" -blockchain. It's like banking system without national licensure and supervision. And that centralized third party can on any impulse decide to do just about anything like steal all the money

<img alt="Decentralization" src="src/centralized_decentralized.jpg" />

<br />
<br />

### [H2c (Explain parts of BitCoin's public ledger)](https://terokarvinen.com/2021/trust-to-blockchain-spring-2021/#h2-blockchain-and-cryptocurrency): Blockchain(dot)com is a place where wallets can be managed by using eg. Ethereum-cryptocurrency or Bitcoin-cryptocurrency (there exist many different types of [cryptocurrency](https://duckduckgo.com/?q=cryptocurrency))
URL https://www.blockchain.com/btc/address/1KvfTBcQuhTLjwyQdrDyTgJ6C4LDyFuiw maintains an address "1KvfTBcQuhTLjwyQdrDyTgJ6C4LDyFuiw" (public key). It shows that this address had some kind of balance before transaction and because transactions can't be reversed there has been made two forwarding transactions afterwards so that total outgoing sum equals start balance.

<img alt="Address in blockchain" src="src/transaction.jpg" />
<br />

Red icon nearby address "39uVwQEJC2Hp3N6H99zwqnwz4TwoRaMKmw" shows how much (0.00606637 BTC aka [mBTC](https://developer.bitcoin.org/devguide/payment_processing.html)) has been sended away and

Green icon nearby address "1D5nc1Xcg5zPgdEeDAXWG4hExfZbjVJnCS" shows how much (0.00374275 BTC) has been sended to new public key address (with secret keys of the original owner) "inside the same wallet" for remaining balance.

The exercise was done in ninja-mode (I took a photo of my son)

<img alt="Automated Teller Machine for cryptocurrency (ATM for Bitcoin)" src="src/eastside_bitcoins_to_cash.jpg" />
<br />

but actually [Prasos Ltd](https://coinmotion.com/) which holds the [Bittimaatti](https://bittimaatti.fi/en/locations-status/itis/) requires identification when you cash out your bitcoins.

<img alt="Can't be anonymous" src="src/identification.jpg" />
<br />

Also blockchain.com requires identification at the time of purchase. Of course you can just make a anonymous wallet and some "middleman" / "random anonymous nick name guy" from the [Tor](https://en.wikipedia.org/wiki/Tor_(anonymity_network))-network can send the assets to your anonymous wallet. Maybe only truly anonymous can be the original coin owners like the miners who gets a rewarded with brand new coins to their anonymous mining wallet (I don't know do they have to identify themselves somehow at some point) but it is still a mystery how to cash out anonymously.
<br />
<br />

### [H2c (Create your own blockchain)](https://terokarvinen.com/2021/trust-to-blockchain-spring-2021/#h2-blockchain-and-cryptocurrency):

Auto Hash
https://emn178.github.io/online-tools/sha256.html

1. A valuable product from my imagination. Would you like to buy this?
--> sha256
--> 9a39326358c7bca31e72cc6b55010e2d6324f5c392363e0de6d34888eeba81bc

2. Seller's (Mika) digital signature for buyer's (Patricia) public key and signature for previous hash
--> 9a39326358c7bca31e72cc6b55010e2d6324f5c392363e0de6d34888eeba81bcSeller's (Mika) digital signature for buyer's (Patricia) public key and signature for previous hash
--> sha256
--> df2798d71afec5d6e2f76399eb9ea0387de526821fc34aba2e7916b927546501

3. Seller's (Patricia) digital signature for buyer's (Roberto) public key and signature for previous hash
--> df2798d71afec5d6e2f76399eb9ea0387de526821fc34aba2e7916b927546501Seller's (Patricia) digital signature for buyer's (Roberto) public key and signature for previous hash
--> sha256
--> 3dd6a9231540678a48f0d6e7834c2f238e76159076e1dace8005f5f9e97d2240

4. Seller's (Roberto) digital signature for buyer's (Venla) public key and signature for previous hash
--> 3dd6a9231540678a48f0d6e7834c2f238e76159076e1dace8005f5f9e97d2240Seller's (Roberto) digital signature for buyer's (Venla) public key and signature for previous hash
--> sha256
--> 459ec3ad671c579067bf22e596c84d1c0e30701421a209351671b655fb3b695f


### Verifying the chain

Latest block (number 4) owner is Venla. Previous block's hash was signed by Roberto's private key and the current block is owned by Venla's public key (aka adress). So that information "Seller's (Roberto) digital signature for buyer's (Venla) public key and signature for previous hash" has to be glued (concatenate) to previous hash:

        3dd6a9231540678a48f0d6e7834c2f238e76159076e1dace8005f5f9e97d2240Seller's (Roberto) digital signature for buyer's (Venla) public key and signature for previous hash
and then run through to mathematical sha256sum function. If the output
https://emn178.github.io/online-tools/sha256.html

        459ec3ad671c579067bf22e596c84d1c0e30701421a209351671b655fb3b695f
matches with information stored on ledger then the ownership has been confirmed. When block number 3 hash

         3dd6a9231540678a48f0d6e7834c2f238e76159076e1dace8005f5f9e97d2240

with signatures has been proved to be correct it is possible to check that's genuine also the same manner.

Block number 3 owner has been Roberto's public key (aka address). Block number 2 hash was signed by Patricia's private key. So that information "Seller's (Patricia) digital signature for buyer's (Roberto) public key and signature for previous hash" has to be glued (concatenate) to previous hash:

        df2798d71afec5d6e2f76399eb9ea0387de526821fc34aba2e7916b927546501Seller's (Patricia) digital signature for buyer's (Roberto) public key and signature for previous hash
and then run through to mathematical sha256sum function. If the output
https://emn178.github.io/online-tools/sha256.html

        3dd6a9231540678a48f0d6e7834c2f238e76159076e1dace8005f5f9e97d2240
matches with information stored on ledger (block number 3) then the ownership and actually also block number 2 hash has been confirmed.

Block number 2 owner has been Patricia's public key (aka address). Block number 1 hash was signed by Mika's private key. So that information "Seller's (Mika) digital signature for buyer's (Patricia) public key and signature for previous hash" has to be glued (concatenate) to previous hash:

        9a39326358c7bca31e72cc6b55010e2d6324f5c392363e0de6d34888eeba81bcSeller's (Mika) digital signature for buyer's (Patricia) public key and signature for previous hash
and then run through to mathematical sha256sum function. If the output
https://emn178.github.io/online-tools/sha256.html

        df2798d71afec5d6e2f76399eb9ea0387de526821fc34aba2e7916b927546501
matches with information stored on ledger (block number 2) then the ownership and actually also block number 1 hash has been confirmed.

Only the issuer can know what kind of "gibberish-nonsense" was the original input in the beginning and by signing that with the first buyer's public key the result should be like registered in the ledger.

If a malicious attacker had manipulated the content like changed ownership (Patricia --> Oscar) then the chain won't be harmonious anymore and anyone can notice it from the public ledger. And the reason is that different inputs produce different outputs like

        9a39326358c7bca31e72cc6b55010e2d6324f5c392363e0de6d34888eeba81bcSeller's (Mika) digital signature for buyer's (Patricia) public key and signature for previous hash

produce --> sha256 --> df2798d71afec5d6e2f76399eb9ea0387de526821fc34aba2e7916b927546501

and

        9a39326358c7bca31e72cc6b55010e2d6324f5c392363e0de6d34888eeba81bcSeller's (Mika) digital signature for buyer's (Oscar) public key and signature for previous hash

produce --> sha256 --> e4559ef01468985b64db97cb20ae3a141bacb78b93ad2761e5f99a840144e44b

<br />
<br />

