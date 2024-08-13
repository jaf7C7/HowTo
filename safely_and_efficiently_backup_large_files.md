# How To Safely And Efficiently Backup Large Files

You want to back up a large amount of data, (e.g. to a network share) and you want to only copy things if the source file has changed.

Use [`rsync(1)`](https://www.samba.org/ftp/rsync/rsync.html), e.g.:
```
$ rsync --checksum --recursive --compress --verbose ~/Data /mnt/network/Data_$(date -I)
```
