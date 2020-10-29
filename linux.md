# Linux

## Unix magic

Find the files accessed by a program   
`strace -fe trace=creat,open,openat,unlink,unlinkat git`

Check which file is taking space   
`du -cha --max-depth=1 ~ | grep -E "M|G"`

