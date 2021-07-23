---
templateKey: blog-post
title: This is a nice little test.
date: 2021-07-23T09:01:22.639Z
description: Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam
  nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed
  diam voluptua. At vero e
featuredpost: true
featuredimage: /img/coffee.png
tags: []
---
Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam voluptua. At vero eos et accusam et justo duo dolores et ea rebum. Stet clita kasd gubergren, no sea takimata sanctus est Lorem ipsum dolor sit amet. Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam voluptua. At vero eos et accusam et justo [duo dolores](www.google.com)

![a cup](/img/safari-pinned-tab.svg)

 et ea rebum. Stet clita kasd gubergren, no sea takimata sanctus est Lorem ipsum dolor sit amet.

Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam voluptua. At vero eos et accusam et justo duo dolores et ea rebum. Stet clita kasd gubergren, no sea takimata sanctus est Lorem ipsum dolor sit amet. Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam voluptua. At vero eos et accusam et justo duo dolores et ea rebum. Stet clita kasd gubergren, no sea takimata sanctus est Lorem ipsum dolor sit amet.

Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam voluptua. At vero eos et accusam et justo duo dolores et ea rebum. Stet clita kasd gubergren, no sea takimata sanctus est Lorem ipsum dolor sit amet. Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam voluptua. At vero eos et accusam et justo duo dolores et ea rebum. Stet clita kasd gubergren, no sea takimata sanctus est Lorem ipsum dolor sit amet.

Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam voluptua. At vero eos et accusam et justo duo dolores et ea rebum. Stet clita kasd gubergren, no sea takimata sanctus est Lorem ipsum dolor sit amet. Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam voluptua. At vero eos et accusam et justo duo dolores et ea rebum. Stet clita kasd gubergren, no sea takimata sanctus est Lorem ipsum dolor sit amet.

```
from hashlib import pbkdf2_hmac

lower_case = list("abcdefghijklmnopqrstuvwxyz")
upper_case = list("ABCDEFGHJKLMNOPQRTUVWXYZ")
numbers = list("0123456789")
special_char = list("!§$%&/()=?[],.-")
password_chars = lower_case + upper_case + numbers + special_char
salt = "pepper"

def convert_bytes_to_password(hashed_bytes, length):
    number = int.from_bytes(hashed_bytes, byteorder="big")
    password = ""
    while number > 0 and len(password) < length:
        password = password + password_chars[number % len(password_chars)]
        number = number // len(password_chars)
    return password

master_password = input("Master Password: ")
domain = input("Website: ")

while len(domain) < 1:
    print("Enter a Website you want to generate the password for: ")
    domain = input("Website: ")

hash_string = domain + master_password

hashed_bytes = pbkdf2_hmac("sha512",
                            hash_string.encode("utf-8"),
                            salt.encode("utf-8"),
                            4096)

print("Passwort: " + convert_bytes_to_password(hashed_bytes, 10))
```