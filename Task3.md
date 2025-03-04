**Task 3: File Management**

**1\. Commands**

**Archive and Compress a Directory**

We can use tar to create a compressed archive of the logs directory:

tar –czvf logs logs.tar.gz

- \-c: Create a new archive.
- \-z: Compress using gzip.
- \-v: Verbose output (optional).
- \-f: Specify the archive filename.

1. **Securely Transfer to a Remote Server**

Use scp to transfer the archive to a remote server:

scp logs.tar.gz user@”remote_server”:/”path-to-destination”

- Replace user with your remote server username.
- Replace remote_server with the server's IP or hostname.
- Replace /path-to-destination/ with the target directory on the remote server.

Alternatively, use rsync for more robust transfers:

rsync -avz --progress logs.tar.gz user@”remote_server”:/”path-to-destination”

- \-a: Archive mode (preserves permissions, timestamps, etc.).
- \-v: Verbose output.
- \-z: Compress during transfer.
- \--progress: Show transfer progress.

1. **Uncompress and Extract on the Remote Server**

SSH into the remote server and extract the archive:

ssh user@remote-server then do the below command to extract

tar –xzyf /path-to-destination/logs.tar.gz –C /path/customerlogs

- \-x: Extract the archive.
- \-C: Specify the target directory (customerlogs).

1. **Resuming an Interrupted Transfer**

We can use **rsync** if the transfer is interrupted, rsync can resume from where it left off:

rsync –avz –partial –progress logs.tar.gz user@remote_server:/path-to-destination/

- \--partial: Keeps partially transferred files, allowing resumption.
- \-a: Archive mode (preserves permissions, timestamps, etc.).
- \-v: Verbose output.
- \-z: Compress during transfer.
- \--progress: Show transfer progress.

**Summary**

1. **Compress**: tar -czvf logs.tar.gz logs/
2. **Transfer**: scp logs.tar.gz user@remote_server:/path/to/destination/ or rsync -avz --progress logs.tar.gz user@remote_server:/path/to/destination/
3. **Extract**: tar -xzvf /path/to/destination/logs.tar.gz -C /path/to/customerlogs/
4. **Resume**: Use rsync --partial for resumable transfers.