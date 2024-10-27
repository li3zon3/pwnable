pwnable notes

# chroot
https://github.com/earthquake/chw00t
```console
- wrong setup (chroot without chdir)
    -> open("../../flag")

- can open a directory befor chroot + chdir
    -> 1. use openat then read target file
    -> 2. use linkat
    -> 3. use fchdir
    -> 4. re chroot again to escapse the old chroot
    -> 5. if no opened file? let open once then pass through pipe (check pipe trick)
```

# pipe trick
```console
- you can open a file and pass to the fd you want like this
/challenge/babyjail_level8 0 < shellcode-raw 3</
```