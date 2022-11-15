## Collection of utils for Unix-like systems.

### 1. pass-check-health

Util to run some tests against your ~/password-store folder for passwordstore util pass.

Example:
```
$ pass-check-health
No key found for my-password.gpg
Problems found: 1
```

### 2. ram-by-proc

Example:
```
$ ram-by-proc firefox-bin
4.4G
```

### 3. sandbox

Run it with `sandbox`. The idea is that you may need to work with files that you want to erase once finished (e. g. you got a encrypted picture, you need to decrypt it, do something, and erase/shred). There could be multiple files and all.

So this util creates a folder, runs bash inside, you do all kinds of things, then when you `exit`, it runs secure-delete on this folder.
