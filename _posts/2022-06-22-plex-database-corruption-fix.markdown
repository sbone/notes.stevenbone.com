---
layout: post
title: "Plex Media Server 'Database Corrupted' fix"
---

https://support.plex.tv/articles/repair-a-corrupted-database/

https://old.reddit.com/r/PleX/comments/eszfm2/corrupted_database_how_i_fixed_it/

Didn't have a backup DB file... despite having the option checked. Maybe because the folder's on an external? 
Anyways, couldn't follow the Reddit post because of no recent backup.

`cd /Volumes/SSD\ 850/Plex\ Media\ Server/Plug-in\ Support/Databases/`

`cp com.plexapp.plugins.library.db com.plexapp.plugins.library.db.original`

`"/Applications/Plex Media Server.app/Contents/MacOS/Plex SQLite" com.plexapp.plugins.library.db "PRAGMA integrity_check"`

Returned: `wrong # of entries in index index_statistics_bandwidth_on_account_id_and_timespan_and_at
wrong # of entries in index index_statistics_bandwidth_on_at`

Tried repair:
`"/Applications/Plex Media Server.app/Contents/MacOS/Plex SQLite" com.plexapp.plugins.library.db ".output recover.out" ".recover"`

But, `"/Applications/Plex Media Server.app/Contents/MacOS/Plex SQLite" com.plexapp.plugins.library.db "PRAGMA integrity_check"` still returned: 
`wrong # of entries in index index_statistics_bandwidth_on_account_id_and_timespan_and_at
wrong # of entries in index index_statistics_bandwidth_on_at`

Performed a database export and import
`"/Applications/Plex Media Server.app/Contents/MacOS/Plex SQLite" com.plexapp.plugins.library.db ".output dump.sql" ".dump"`

Delete/move the DB
`mv com.plexapp.plugins.library.db ~/Desktop/com.plexapp.plugins.library.db`

Rebuild
`"/Applications/Plex Media Server.app/Contents/MacOS/Plex SQLite" com==> "/Applications/Plex Media Server.app/Contents/MacOS/Plex SQLite" com.plexapp.plugins.library.db ".read dump.sql"`

No `com.plexapp.plugins.library.db-shm` nor `db-wal` file.

Running check `"/Applications/Plex Media Server.app/Contents/MacOS/Plex SQLite" com.plexapp.plugins.library.db "PRAGMA integrity_check"` now returns `ok`. 

**PHEW!**

