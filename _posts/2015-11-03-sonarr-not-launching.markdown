---
layout: post
title: "Sonarr Not Launching on OSX"
---

### Problem

Sonarr wasn’t starting, regardless of how I tried to launch it.

### Solution

Checked Sonarr log: `~/.config/NzbDrone/logs/nzbdrone.txt`

Found scary message: `System.Data.SQLite.SQLiteException: database disk image is malformed`

Fixed it:

1. Go to Sonarr config directory: `cd ~/.config/NzbDrone`

2. Backup Sonarr DB: `mv nzbdrone.db nzbdrone.bkp.db`

3. Create new Sonarr DB: `touch nzbdrone.db`

4. Dump backup DB contents into new DB: `sqlite3 nzbdrone.bkp.dp “.dump" | sqlite3 nzbdrone.db` [source](http://stackoverflow.com/a/18260642)

5. Remove backup: `rm nzbdrone.bkp.db`

