Варіант A (backup.sh):

#!/bin/bash

if [ "$#" -ne 2 ]; then
    echo "Usage: ./backup.sh <log_dir> <backup_dir>"
    exit 1
fi

LOG_DIR="$1"
BACKUP_DIR="$2"

if [ ! -d "$LOG_DIR" ] || [ ! -d "$BACKUP_DIR" ]; then
    echo "Usage: ./backup.sh <log_dir> <backup_dir>"
    exit 1
fi

LOCKFILE="/tmp/backup.lock"

if [ -e "$LOCKFILE" ]; then
    echo "Backup already running"
    exit 1
fi

touch "$LOCKFILE"
trap 'rm -f "$LOCKFILE"' EXIT

TIMESTAMP=$(date +"%Y-%m-%d_%H-%M")
ARCHIVE_NAME="logs_backup_${TIMESTAMP}.tar.gz"
BACKUP_PATH="${BACKUP_DIR}/${ARCHIVE_NAME}"

tar -czf "$BACKUP_PATH" -C "$LOG_DIR" . 2>/dev/null

if [ $? -eq 0 ]; then
    echo "Backup created: $(realpath "$BACKUP_PATH")"
else
    echo "Backup failed"
    exit 2
fi

Термінал:

ddminkov@ddminkov-virtual-machine:~$ cd Desktop
ddminkov@ddminkov-virtual-machine:~/Desktop$ chmod +x backup.sh
ddminkov@ddminkov-virtual-machine:~/Desktop$ ./backup.sh /bad/path_example/source_logs /bad/path_example/backup_folder
Usage: ./backup.sh <log_dir> <backup_dir>
ddminkov@ddminkov-virtual-machine:~/Desktop$ echo "Testing log data" > ~/Desktop/source_logs/app.log
ddminkov@ddminkov-virtual-machine:~/Desktop$ ./backup.sh ~/Desktop/source_logs ~/Desktop/backup_folder
Backup created: /home/ddminkov/Desktop/backup_folder/logs_backup_2026-06-17_14-16.tar.gz
ddminkov@ddminkov-virtual-machine:~/Desktop$ ls ~/Desktop/backup_folder
logs_backup_2026-06-17_14-16.tar.gz
