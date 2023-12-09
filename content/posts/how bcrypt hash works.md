---
title: "How bcrypt hashing works?"
date: "2023-11-22"
draft: true
tags: ["bcrypt"]
---

- idea is to create interactive guide who is new to this

rough notes:
- common keywords, password, salt, rounds, hashing algo/function, sha256, decryption, how much time it takes to decrypt the password
- interactive of salt generator, hashing function, time it takes to decrypt the password
- what is the worst to best of storing passwords, basic to secure
- basic:
    - direct storing the plain text data into the storage
    - storing encrypted passwords and using some kind of decryption key to get the plain text password and someone from insider who has the decryption key access can mis use it
    - hashing, comparing hash to hash, so that way no one can get direct access to the password other than user, hashing function required
        - https://gist.github.com/epixoip/a83d38f412b4737e99bbef804a270c40
        - (md5 hash function sucks) https://github.com/corkami/collisions#fastcoll-md5
        - how does hashing prevent someone from turning hash into password ?
        - can two string have same hash ?
        - collision resistance
        - demo of how same hash can't be generated even only if one single character is changed the entire hash changes
        - dictionary attacks, how hashing passwords are attacked, rainbow tables
    - salting with hashing is more secure compare to just hashing
        - gpu are guessing billions hash per second
    - slow hashing functions

normal hash algorithm: MD5, SHA-1, SHA-256
password hash algorithm(with inbuilt salt): argon, bcrypt

- this password hash algorithm slows the hashing guess to very low, it is known as work factor