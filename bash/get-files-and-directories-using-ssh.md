You can copy files from a remote host via ssh using scp.
To do so, you can use the following command:

```bash
$ scp user@remotehost:/path/to/file /path/to/local/destination
```

Also, you can copy directories as well using the `-r` flag.

```bash
$ scp -r /path/to/local/destination user@remotehost:/path/to/dir
```

- [Source 1](http://unix.stackexchange.com/questions/106480/how-to-copy-files-from-one-machine-to-another-using-ssh)
- [Source 2](http://askubuntu.com/questions/446724/copy-folders-not-one-file-using-ssh-ubuntu)
