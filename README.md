pwnable notes

# chroot
- wrong setup (chroot without chdir)
    -> open("../../flag")

- can open a directory befor chroot + chdir
    -> 1. use openat then read target file
    -> 2. use linkat
    -> 3. use fchdir
    -> 4. re chroot again to escapse the old chroot

test