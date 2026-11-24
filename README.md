# Personal backup tools

Small Python scripts for:

- **Backup**: incremental backup of folders to an external drive (Windows / WSL).
- **Folder analyzer**: find out which folders use the most disk space. Used to find relevant folders to backup.

## Requirements

- Python 3.10 or newer

## Setup: fill in the blanks

`backup.py` has a **SETUP block** at the top, marked with
`# ===== SETUP =====`. Fill in the blanks there before the first run. The
script stop with a clear message if a needed value is still empty.

| `backup.py` | `SOURCE_A`, `BACKUP_A` | List of folders backed up with `--setA`, and the folder their backups go into. |
| | `SOURCE_B`, `BACKUP_B` | The same for `--setB`. `BACKUP_B` is also used for folders given on the command line. |
| | `WSL_DISTRO` | Name of your WSL distribution (default `"Ubuntu"`, check with `wsl -l`). Only matters when running on Windows. |

## Backup

```bash
python3 backup.py --setA --dry-run   # show what would be copied
python3 backup.py --setA --setB      # back up both sets
python3 backup.py /path/to/folder    # back up one folder into BACKUP_B
```

New and changed files are copied; nothing is ever deleted from the backup.
On Windows drives, running it with Windows Python (`py backup.py ...`) is much
faster than from WSL.

## Folder analyzer

```bash
python folder_analyzer.py /path/to/folder
```

Shows the subfolders sorted by size; type a number to open one, `b` to go back.