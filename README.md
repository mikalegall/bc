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
The current case will be hashed by mathematical [sha256sum](https://emn178.github.io/online-tools/sha256.html) function

* Signatures: 
Seller signes digitally previously mentioned hash and buyer's public key. Buyer verify seller's signature and earlier happened signatures.

* Blockchain: 
By signing the previous transactions it will form a link in the chain which contains blocks of 256 bit long hashes

* Proof of work: 
After signing the next case should that mathematical sha256sum function output start with zeros (eg. 007etc). The more zeros required at the beginning, the longer it takes to form a next valid link in chain. Who ever demonstrates that "gibberish-nonsense" input (which met the criteria with required zeros) proves at the same time that this actor has worked to solve the set target. 

* Consensus: 
When someone sends proof of work to peer-to-peer network and part of the nodes calculates all links in blockchain by verifying it to be valid then the consensus has been made. If there are branches on that same chain then the longest chain with most links is valid.  

* Incentive: 
Reward which will be granted for actor whos proof of work has been validated. That happens by issuing brand new bitcoins for actor who's proof of work has been validated.

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

### [H2f ("Brute force" 6b88c087247aa2f07ee1c5956b8e1a9f4c7f892a70e324f1bb3d161e05ca107b)](https://terokarvinen.com/2021/trust-to-blockchain-spring-2021/#h2-blockchain-and-cryptocurrency): Hint, it is an sha256 hash of a single lower case word

https://emn178.github.io/online-tools/sha256.html

input: bitcoin

output: 6b88c087247aa2f07ee1c5956b8e1a9f4c7f892a70e324f1bb3d161e05ca107b
<br />
<br />

### [H3a (Summarize . . . )](https://terokarvinen.com/2021/trust-to-blockchain-spring-2021/#h3-public-key-encryption-and-pgp): Schneier 2015: [Applied Cryptography](https://www.oreilly.com/library/view/applied-cryptography-protocols/9781119096726/08_chap01.html#chap01) Chapter 1: Foundations
* In modern times digitally encrypted messages usually also fulfill the requirements of authentication (who encrypted message), integrity like consistency (the message has not changed between encryption and decryption) and nonrepudiation (once encrypted message has been delivered available the one who has made it cannot deny that s/he did it)
* On "key" (large number) based cryptography algorithms the algorithm itself can be published becouse the game changer is the hidden (secret) large number (key)
* In asymmetric algorithms like "public-key algorithm" the key used for encryption is different from the key used for decryption. And even when you know the encryption key (public key) you can not calculate decryption key (secret private key) out of it in any reasonable amount of time  
* Rivest, Shamir, Adleman (RSA)) is the most popular public-key algorithm which can be used to digital signatures
<br />
<br />

### [H3b & H3c (Public key example: Encrypt and sign a message)](https://terokarvinen.com/2021/trust-to-blockchain-spring-2021/#h3-public-key-encryption-and-pgp): Singh, Simon. [The code book](https://books.google.fi/books?hl=fi&id=skt7TrLK5uYC&dq=editions%3AcR-CAJ7P0pIC&focus=searchwithinvolume&q=prime): the science of secrecy from ancient Egypt to quantum cryptography ([in Finnish](https://haku.helmet.fi/iii/encore/record/C__Rb1515358))

Alice need to change confidentially information with Bob. First Bob pics some [prime numbers](https://en.wikipedia.org/wiki/Prime_number) e.g. 7, 11, 17 which can be used in RSA public key system as follows:

<font color="lightblue"><i>7</i></font>, 11(q) ja 17(p)

11 x 17 = <b>187</b>

Bob's public-keyring key-pair is <font color="lightblue"><i>7</i></font>(e) and <b>187</b>(N). That is the key (public pair) what Alice uses to encrypt her message.

Bob's so called secret key-ring pair (private key) is 11 and 17. The first prime number <font color="lightblue"><i>7</i></font> was already published with [product](https://en.wikipedia.org/wiki/Product_(mathematics)) of private key. Because these three key components (7, 11, 17) are all prime numbers it has been so far that not yet any algorithm has invented to reverse product <b>187</b> back to its factors (multiplicand and multiplier). 

So that Bob can decrypt Alice's message he has to fabricate decryption key:

Factors of <b>187</b>(N) are 11(q) ja 17(p). Those should be minus with one:

10 and 16

10 x 16 = 160

160 + 1 = 161(G)

161 ÷ 7(e) = decryption key <b><font color="red">23</font></b>(d)
<br />
<br />

[REMAINDER OF THE MODULO OPERATION](https://en.wikipedia.org/wiki/Modulo_operation)
<br />

<img alt="RSA: remainder of the modulo operation" src="src/rsa.JPG" />
<br />
<br />

### Pretty Good Privacy (PGP) in practice:
Download [Thunderbird](https://www.thunderbird.net/en-US/)-email software (and ProtonMail [Bridge](https://protonmail.com/bridge/thunderbird) if needed). After 
[configuration](https://support.mozilla.org/en-US/kb/openpgp-thunderbird-howto-and-faq#w_i-have-never-used-openpgp-with-thunderbird-before-how-do-i-setup-openpgp) there is two [Elliptic-curve cryptography](https://en.wikipedia.org/wiki/Elliptic-curve_cryptography) (ECC) key files:

<img alt="Thunderbird configuration" src="src/Thunderbird.jpg" />
<br />
<br />

alice-example-(0xEF46BB2E0691BB72)-public.asc

        -----BEGIN PGP PUBLIC KEY BLOCK-----
        xjMEYIcVdhYJKwYBBAHaRw8BAQdAqK8HLeHYPCj3ZddWciHzQBSfrOd5WcbVkFxU3+vbti3NJE1pa2EgTGUgR2FsbCA8bGFyZS5sZWdhbGxAZ21haWwuY29tPsKRBBMWCAA5FiEEBiJLE+Q1qiOsp5cE70a7LgaRu3IFAmCHFXYFCQHhM4ACGwMFCwkIBwIGFQgJCgsCBRYCAwEAAAoJEO9Guy4Gkbty0l0BALW3pBCReQh+Z7cUWe+iZqwnZ9P//DjFsPJATk+68Yh1AQDZAal54X7MN9dbqfq1v0SB/sKUbfsCIBYB2oe+6aH/Cs44BGCHFXYSCisGAQQBl1UBBQEBB0B0WENXR+igmumtdaK7QR0bBnz5q9mVp1uq1keiFrWqKAMBCAfCfgQYFggAJhYhBAYiSxPkNaojrKeXBO9Guy4GkbtyBQJghxV2BQkB4TOAAhsMAAoJEO9Guy4Gkbty1k8A/2O9f6gINYOsssl/1VGo6pH8qqX+Gv95EAM5E6tqGu/EAQC1ajKiQdmEK3CttmF29JpdCZViUFxdDPGBvSaj0KLvDA===qOQT
        -----END PGP PUBLIC KEY BLOCK-----

alice-example-(0xEF46BB2E0691BB72)-secret.asc

        -----BEGIN PGP PRIVATE KEY BLOCK-----
        xYYEYIcVdhYJKwYBBAHaRw8BAQdAqK8HLeHYPCj3ZddWciHzQBSfrOd5WcbVkFxU3+vbti3+CQMI25jdS8KcUTbEuGKZUrEHPmd3HHqONfiSGR0BEYoTDncHUgouwK3a91LVbwrYMXue+74lZTEwDxP1tYESKv8cNg62YMOLTI7Oq09ab/RxJc0kTWlrYSBMZSBHYWxsIDxsYXJlLmxlZ2FsbEBnbWFpbC5jb20+wpEEExYIADkWIQQGIksT5DWqI6ynlwTvRrsuBpG7cgUCYIcVdgUJAeEzgAIbAwULCQgHAgYVCAkKCwIFFgIDAQAACgkQ70a7LgaRu3LSXQEAtbekEJF5CH5ntxRZ76JmrCdn0//8OMWw8kBOT7rxiHUBANkBqXnhfsw311up+rW/RIH+wpRt+wIgFgHah77pof8Kx4sEYIcVdhIKKwYBBAGXVQEFAQEHQHRYQ1dH6KCa6a11ortBHRsGfPmr2ZWnW6rWR6IWtaooAwEIB/4JAwjFKejiDFGIitQeTHZoTV5cZtSy1oaIJ7vUwhl9AXM5OV+KSbyX/l/2TDkBKj0rb4J8tWQy391MuO2d1VpVoUbnd5MjBy3t15sMNmpQwGLIwn4EGBYIACYWIQQGIksT5DWqI6ynlwTvRrsuBpG7cgUCYIcVdgUJAeEzgAIbDAAKCRDvRrsuBpG7ctZPAP9jvX+oCDWDrLLJf9VRqOqR/Kql/hr/eRADOROrahrvxAEAtWoyokHZhCtwrbZhdvSaXQmVYlBcXQzxgb0mo9Ci7ww==k9Xn
        -----END PGP PRIVATE KEY BLOCK-----

Alice uses Bob's public key to encrypt the email.
Bob uses old school [Rivest–Shamir–Adleman](https://en.wikipedia.org/wiki/RSA_(cryptosystem)) (RSA 4096) which is longer key.

bob-example-(0x56EDB674B0788552)-public.asc

        -----BEGIN PGP PUBLIC KEY BLOCK-----
        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ore8
        -----END PGP PUBLIC KEY BLOCK-----

bob-example-(0x56EDB674B0788552)-secret.asc

        -----BEGIN PGP PRIVATE KEY BLOCK-----

        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yAsv
        -----END PGP PRIVATE KEY BLOCK-----

The encrypted message is attached in email and looks like this

        encrypted.asc

        -----BEGIN PGP MESSAGE-----
        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ITpc
        -----END PGP MESSAGE-----
