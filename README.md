# SUID-SGID-Finder
Checking if SUID/GUID binaries exists in GTFObins instead of manually check
# How to use
Copy gtfobins.txt on the target machine.

Run this command :

```find / -xdev -type f -a \( -perm -u+s -o -perm -g+s \) -exec ls -l {} \; 2> /dev/null | rev | cut -d'/' -f1 | rev > sample.txt && grep '.' gtfobins.txt | grep SUID | cut -d ' ' -f 1 | grep -x -f - sample.txt```

You can then delete the sample.txt file containing all SUID and SGID binary names (not only the ones on GTFObins list)
