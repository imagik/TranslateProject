zBackup – A versatile deduplicating backup tool
================================================================================
zbackup is a globally-deduplicating backup tool, based on the ideas found in rsync. Feed a large .tar into it, and it will store duplicate regions of it only once, then compress and optionally encrypt the result. Feed another .tar file, and it will also re-use any data found in any previous backups. This way only new changes are stored, and as long as the files are not very different, the amount of storage required is very low. Any of the backup files stored previously can be read back in full at any time.

### zBackup Features ###

Parallel LZMA or LZO compression of the stored data
Built-in AES encryption of the stored data
Possibility to delete old backup data
Use of a 64-bit rolling hash, keeping the amount of soft collisions to zero
Repository consists of immutable files. No existing files are ever modified
Written in C++ only with only modest library dependencies
Safe to use in production
Possibility to exchange data between repos without recompression

### Install zBackup in ubuntu ###

Open the terminal and run the following command

    sudo apt-get install zbackup

### Using zBackup ###

zbackup init initializes a backup repository for the backup files to be stored.

    zbackup init [--non-encrypted] [--password-file ~/.my_backup_password ] /my/backup/repo

zbackup backup backups a tar file generated by tar c to the repository initialized using zbackup init

    zbackup [--password-file ~/.my_backup_password ] [--threads number_of_threads ] backup /my/backup/repo/backups/backup-`date ‘+%Y-%m-%d'`

zbackup restore restores the backup file to a tar file.

    zbackup [--password-file ~/.my_backup_password [--cache-size cache_size_in_mb restore /my/backup/repo/backups/backup-`date ‘+%Y-%m-%d'` > /my/precious/backup-restored.tar

### Available Options ###

- -non-encrypted -- Do not encrypt the backup repository.
- --password-file ~/.my_backup_password -- Use the password file specified at ~/.my_backup_password to encrypt the repository and backup file, or to decrypt the backup file.
- --threads number_of_threads -- Limit the partial LZMA compression to number_of_threads needed. Recommended for 32-bit architectures.
- --cache-size cache_size_in_mb -- Use the cache size provided by cache_size_in_mb to speed up the restoration process.

### zBackup files ###

~/.my_backup_password Used to encrypt the repository and backup file, or to decrypt the backup file. See zbackup for further details.

/my/backup/repo The directory used to hold the backup repository.

/my/precious/restored-tar The tar used for restoring the backup.

/my/backup/repo/backups/backup-`date ‘+%Y-%m-%d'` Specifies the backup file.

--------------------------------------------------------------------------------

via: http://www.ubuntugeek.com/zbackup-a-versatile-deduplicating-backup-tool.html

作者：[ruchi][a]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创翻译，[Linux中国](http://linux.cn/) 荣誉推出

[a]:http://www.ubuntugeek.com/author/ubuntufix