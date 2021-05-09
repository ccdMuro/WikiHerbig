---
title: YubiKey 5 NFC
description: Add personal credentials ans set a pin.
published: true
date: 2021-05-09T20:41:25.757Z
tags: nfc, yubikey
editor: markdown
dateCreated: 2021-05-08T05:56:40.042Z
---

# Yubikey

In this guide I will be referring to the **YubiKey 5 NFC** as card. Also you will need the `pcscd` (*PC/SC Smart Card Daemon*) package installed on your system.

Make sure the card has been recognised correctly with `gpg --card-status`. You should see some basic card informations. If not, check on `pcscd` with `systemctl status pcscd`.


# Initialise Card
```
gpg --card-edit
admin
```

## Key size
```
key-attr
(RSA) 1
4096
```

## PIN and Password


# Personalise

## name

## Language

## Public Key URL

## Login Data


# Generate keys

Instructions how to create keys can be found here: [PGP](/digital_privacy/pgp#create-keys)


# Move keys to card


With the card stuck and recognised, let's edit the key you want to move to the card.

```
$ gpg --edit-key C153F8B2CC34081E9091C71B195E33D069143FE5

...

Secret key is available

sec  rsa4096/195E33D069143FE5
     created: 2021-01-05  expires: 2022-01-05  usage: C   
     trust: ultimate      validity: ultimate
ssb  rsa4096/8E15AB3040140A61
     created: 2021-01-16  expires: 2022-01-16  usage: A   
ssb  rsa4096/620EE3F18E5C933B
     created: 2021-01-16  expires: 2022-01-16  usage: S   
ssb  rsa4096/1B4B84BB9AF3677E
     created: 2021-01-16  expires: 2022-01-16  usage: E
[ultimate] (1). Your Name (work) <your.name@company.email>
[ultimate] (2)  Your Name <you.other@email.address
```

With the `key #` command you can **toggle/select** the key you want to move with `keytocard`. An asterisk (`*`) will mark your selection.

Let's start with moving the `[A]uthentication` key. When prompted where to store the key, select the *Authentication key* slot (`3`).

**Type:**
`key 1` :arrow_right: `Return` :arrow_right:
`keytocard` :arrow_right: `Return` :arrow_right:
`3` :arrow_right: `Return`
```
gpg> key 1
...
ssb* rsa4096/8E15AB3040140A61
     created: 2021-01-16  expires: 2022-01-16  usage: A
...
gpg> keytocard
Please select where to store the key:
   (3) Authentication key
Your selection? 3
```

Good, now switch to the `[S]ignature` key. Remember to **toggle** the selection for `key 1` to deselect it. When prompted where to store the key, select the *Signature key* slot (`1`).

**Type:**
`key 2`:arrow_right: `Return` :arrow_right:
`key 1` :arrow_right: `Return` :arrow_right:
`keytocard` :arrow_right: `Return` :arrow_right:
`1` :arrow_right: `Return`

```
gpg> key 2
...
ssb* rsa4096/8E15AB3040140A61
     created: 2021-01-16  expires: 2022-01-16  usage: A   
ssb* rsa4096/620EE3F18E5C933B
     created: 2021-01-16  expires: 2022-01-16  usage: S
...
gpg> key 1
...
ssb* rsa4096/620EE3F18E5C933B
     created: 2021-01-16  expires: 2022-01-16  usage: S
...
gpg> keytocard
Please select where to store the key:
   (1) Signature key
Your selection? 1
```

Repeat for the `[E]ncryption` Key. When prompted where to store the key, select the *Encryption key* slot (`2`).

**Type:**
`key 3`:arrow_right: `Return` :arrow_right:
`key 2` :arrow_right: `Return` :arrow_right:
`keytocard` :arrow_right: `Return` :arrow_right:
`2` :arrow_right: `Return`

```
gpg> key 3
...
ssb* rsa4096/620EE3F18E5C933B
     created: 2021-01-16  expires: 2022-01-16  usage: S   
ssb* rsa4096/1B4B84BB9AF3677E
     created: 2021-01-16  expires: 2022-01-16  usage: E
...
gpg> key 2
...
ssb* rsa4096/1B4B84BB9AF3677E
     created: 2021-01-16  expires: 2022-01-16  usage: E
...
gpg> keytocard
Please select where to store the key:
   (2) Encryption key
Your selection? 2
```

> Don't forget to save your changes.
{.is-success}

```
gpg> save
```

The `[C]ertify` key will not be moved to the card. Thus, someone who gets access to the card, even with the passphrase, will not be able to extend the expiration time of the key, sign other keys or create a revocation certificate. This is the last stronghold against card theft.

Finally check on your key with `gpg -K`. A right angle bracket (`>`) will mark the sub keys which are stored on the card.

```
$ gpg -K

sec   rsa4096 2021-01-05 [C] [expires: 2022-01-05]
      C153F8B2CC34081E9091C71B195E33D069143FE5
uid           [ultimate] Your Name (work) <your.name@company.email>
uid           [ultimate] Your Name <you.other@email.address>
ssb>  rsa4096 2021-01-16 [A] [expires: 2022-01-16]
ssb>  rsa4096 2021-01-16 [S] [expires: 2022-01-16]
ssb>  rsa4096 2021-01-16 [E] [expires: 2022-01-16]
```


# Unblock PIN


# Factory reset

# Problems I encountered


## YubiKey and Snap (Thunderbird)
I started out using Thunderbird from the snap repository. I got in to trouble forwarding access to the YubiKey through the snap environment.

> This Problem is still unresolved.
{.is-warning}