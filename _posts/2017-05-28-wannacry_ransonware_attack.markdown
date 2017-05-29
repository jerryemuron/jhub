---
layout: post
title: 'Ransomware Attacks'
date: 2017-05-28 20:39:34 +0300
categories: blog development
tags: cats dogs code
custom_var: 'meow meow meow'
---
{% for post in paginator.posts %}
    {% include tile.html %}
{% endfor %}
<h1>Introduction</h1>
By definition: ransomware is a type of malicious software that blocks access to the victim's data or threatens to publish or delete it until a ransom is paid. Any action is possible once a device or system is infected and there is no guarantee that paying the ransom will return access or not delete the data. 
The more advanced malware uses a technique called cryptoviral extortion, in which it encrypts the victim's files (may also encrypt the master boot file or the entire hard drive), making them inaccessible, and demands a ransom payment to decrypt them, usually the victim is asked to pay the ransom through the digital currency such as bitcoins. 
Ransomware is a denial-of-access attack that prevents computer users from accessing files since it is intractable to decrypt the files without the decryption key. Ransomware attacks are typically carried out using a Trojan that has a payload disguised as a legitimate file.
Payment is virtually always the goal, and the victim is coerced into paying for the ransomware to be removed which may or may not actually occur either by supplying a program that can decrypt the files, or by sending an unlock code that undoes the payload's changes. A key element in making ransomware work for the attacker is a convenient payment system that is hard to trace. 
A range of such payment methods have been used, including wire transfers, premium-rate text messages, pre-paid voucher services such as Paysafecard, and the digital currency Bitcoin. 

<h1>How ransomware attacks are carried out</h1>
Ransomware is also called cryptoviral extortion and is the following three-round protocol carried out between the attacker and the victim.

<OL>
<LI>[attacker_victim] The attacker generates a key pair and places the corresponding public key in the malware. The malware is released.</LI>
<LI>[victim_attacker] To carry out the cryptoviral extortion attack, the malware generates a random symmetric key and encrypts the victim's data with it. It uses the public key in the malware to encrypt the symmetric key. This is known as hybrid encryption and it results in a small asymmetric ciphertext as well as the symmetric ciphertext of the victim's data. It zeroizes the symmetric key and the original plaintext data to prevent recovery. It puts up a message to the user that includes the asymmetric ciphertext and how to pay the ransom. The victim sends the asymmetric ciphertext and e-money to the attacker.</LI>
<LI>[attacker_victim] The attacker receives the payment, deciphers the asymmetric ciphertext with the attacker's private key, and sends the symmetric key to the victim. The victim deciphers the encrypted data with the needed symmetric key thereby completing the cryptovirology attack.</LI>
</OL>

![ransomware_operation1](C:\Jekyll\jerryemuron\_posts\_images/ransomware_operation1.jpg "ransomware_image")

<p>The symmetric key is randomly generated and will not assist other victims. At no point is the attacker's private key exposed to victims and the victim need only send a very small ciphertext (the encrypted symmetric-cipher key) to the attacker.
Ransomware attacks are typically carried out using a Trojan, entering a system through, for example, a downloaded file or a vulnerability in a network service. The program then runs a payload, which locks the system in some fashion, or claims to lock the system but does not. 
Payloads may display a fake warning purportedly by an entity such as a law enforcement agency, falsely claiming that the system has been used for illegal activities, contains content such as pornography and "pirated" media; or the sender email may purport to be from a legitimate source such as a moneypayment agency like Moneygram, Western Union. </p>

<p>Some payloads consist simply of an application designed to lock or restrict the system until payment is made, typically by setting the Windows Shell to itself, or even modifying the master boot record and/or partition table to prevent the operating system from booting until it is repaired. 
The most sophisticated payloads encrypt files, with many using strong encryption to encrypt the victim's files in such a way that only the malware author has the needed decryption key. 
</p>

<h1>Wannacry decryptor ransomware attack</h1>
<p>On the 19th May, 2017 the tech world was shaken by a crytoviral attack called the wannacry.
There was a global attack that affected over 200,000 computers in over 150 countries; many high profile institutions and organizations such as UK’s National Health Services fell victim to this malicious attack.
The "WannaCry" ransomware appears to have used a flaw in Microsoft's software, discovered by the National Security Agency and leaked by hackers, to spread rapidly across networks locking away files.
</p>

<h1>What is wannacry decryptor</h1>
<p>Wanna Decryptor, also known as WannaCry or wcry, is a specific ransomware program that locks all the data on a computer system and leaves the user with only two files: instructions on what to do next and the Wanna Decryptor program itself.
When the software is opened it tells computer users that their files have been encryted, and gives them a few days to pay up, warning that their files will otherwise be deleted. It demands payment in Bitcoin, gives instructions on how to buy it, and provides a Bitcoin address to send it to.</p>

<h1>Wannacry mode of attack</h1>
<p>WannaCry is the ransomware computer worm that targets computers running Microsoft Windows. Initially, the worm uses the EternalBlue exploit to enter a computer, taking advantage of a vulnerability in Microsoft's implementation of the Server Message Block (SMB) protocol. It installs DoublePulsar, a backdoor implant tool, which then transfers and runs the WannaCry ransomware package.</p>

<p>When executed, the malware first checks the "kill switch" domain name; if it is not found, then the ransomware encrypts the computer's data, then attempts to exploit the SMB vulnerability to spread out to random computers on the Internet, and "laterally" to computers on the same network. It is considered a network worm because it also includes a "transport" mechanism to automatically spread itself. This transport code scans for vulnerable systems, then uses the EternalBlue exploit to gain access, and the DoublePulsar tool to install and execute a copy of itself.</p>

<p>As with other modern ransomware, the payload displays a message informing the user that files have been encrypted, and demands a payment of around $300 in bitcoin within three days, or $600 within seven days.</p>

<h1>How wannacry decryptor was combatted</h1>
<ul>
<li>The software contained a URL that, when discovered and registered by a security researcher to track activity from infected machines, was found to act as a "kill switch" that shut down the software before it executed its payload, stopping the spread of the ransomware. 
The researcher speculated that this had been included in the software as a mechanism to prevent it being run on quarantined machines used by anti-virus researchers; he observed that some sandbox environments will respond to all queries with traffic in order to trick the software into thinking that it is still connected to the internet, so the software attempts to contact an address which did not exist, to detect whether it was running in a sandbox, and do nothing if so. 
He also noted that it was not an unprecedented technique, having been observed in the Necurs trojan.
On 19 May it was reported that hackers were trying to use a Mirai botnet variant to effect a distributed attack on WannaCry's kill-switch domain with the intention of knocking it offline. On 22 May @MalwareTechBlog protected the domain by switching to a cached version of the site, capable of dealing with much higher traffic loads than the live site. 
</li>
<li>Microsoft released a statement recommending users install update MS17-010 to protect themselves against the attack.</li>
<li>Microsoft also made security patches available to the general public for several out-of-support versions of Windows, including Windows XP, Windows 8 and Windows Server 2003.</li>
<li>On 16 May 2017, researchers from University College London and Boston University reported that their PayBreak system could defeat WannaCry and several other families of ransomware</li>
<li>On 19 May 2017, a group of French security researchers reported that they had found a way to unlock the program without paying the ransom under some circumstances.
</li>
<li>WannaSmile, a tool that disables the SMBv1 protocol which implementations embed the flaw</li>
<li>WannaPatch, a tool that detects if a system is vulnerable and, if so, automates the downloading of the needed patch.</li>
</ul>

<h1>Protection against ransomware</h1>
<p>It is difficult to prevent determined hackers from launching a ransomware attack, but exercising caution can help. Cyber attackers need to download the malicious software onto a computer, phone or other connected device. The following is advised:</p>
<ul>
<li>Regularly backup your files and servers</li>
<li>Regularly patch up servers and have the computers running on the latest Operating Systems</li>
<li>Regularly pass security awareness tips to the users on the network of the organization</li>
<li>Do not open links or attachments from sources unknown to you, first inquire with your IT Team before you proceed</li>
<li>Organizations are advised not to pay the ransom to the ransomware hackers as this would encourage further development and spread of the malware</li>
<li>Isolate the infected computers off the network to prevent further infections</li>
</ul>