# Linux Terminal — Essential Commands

Core Linux terminal commands for everyday use, plus basic networking and system administration.

## Section Map

| File | Topics |
|------|--------|
| [01 — Navigation, Files & Shell Basics](./01-navigation-files.md) | `man`, bash shortcuts, `pwd`, `ls`, `cd`, `mkdir`, `cp`, `mv`, `rm`, `cat`, `less`, `chmod`, `tar`, env vars |
| [02 — Search, Pipes & Text Processing](./02-search-text-processing.md) | `find`, `locate`, `grep`, `rg`, pipes, redirects, `&&`/`||`, `sed`, `sort`, `uniq`, `wc` |
| [03 — Processes & System Monitoring](./03-processes-system-monitoring.md) | `ps`, `top`, `kill`, `pkill`, `watch`, jobs, `systemctl`, `journalctl`, `free`, `df`, `du` |
| [04 — Network Basics](./04-network-ssh-downloads.md) | `ip`, `ss`, `ping`, `curl`, `wget`, `ssh`, `scp`, troubleshooting checklist |

## Quick Start

```bash
man ls               # get help
pwd                  # where am I?
ls -lah              # list files (detailed)
cd /path/to/dir      # change directory
mkdir -p docs/notes  # create nested dirs
cp file.txt backup/  # copy file
mv old.txt new.txt   # rename/move file
rm -i temp.txt       # delete with confirmation
```

## Safety Rules

1. Start with read-only commands (`ls`, `cat`, `less`, `df`).
2. Use interactive mode when unsure (`rm -i`, `cp -i`, `mv -i`).
3. Verify paths before delete/move operations.
4. Keep commands simple and test on one file first.
