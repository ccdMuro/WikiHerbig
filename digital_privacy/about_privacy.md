---
title: About Privacy
description: Why you should bother about privacy.
published: true
date: 2021-01-17T11:41:30.541Z
tags: 
editor: undefined
dateCreated: 2021-01-17T11:10:55.873Z
---

# Privacy is a Right
We are not talking about a minor commodity, but of fundamental human rights. Ever heard of [Secrecy of correspondence](https://en.wikipedia.org/wiki/Secrecy_of_correspondence)? People tend to loose sight of things they can not grasp. So take this as a reminder that E-Mail, Chat or an other form of digital and electronic communication is protected by this very same right. So please, don't treat this right with contempt by voluntarily exposing all your communication to third party.

## OpenPGP
Read about *Pretty Good Privacy* here: [About OpenPGP](https://www.openpgp.org/about/)

Beside message encryption there are other key types to consider.

### Certificate Key
It acts as your *main* key and accommodates your associated identities. Sub keys like the folowing ones can be created and likewise revoked if compromised.

### Encription Key
The reason for encription should be trivial. You want to exchange data with someone and the informations should not be visible to anyone but you and your desired reciepient. 

### Signing Key
You can attach your digital signature to documents, emails and even other keys to verify that the content has been aproved by you.

### Authentikation Key
Is used to prove your identity to someone or a service. It can be used to authenticate over ssh for example.

> Remember that once a key has been created, it is hard to delete it. You can mark it as invalid with a revoke certificate but even a revoked encription key may grand access old messages.
