# windows_icon_cache_delete
delete the cache of thumbnails, icons, start-menu jump lists, and the tray icons, after a reboot it will build itself correctly. uses K-Lite tiny application, few registry cleanups and a batch-file to manage it all and delete some files. you should run it as admin, then clear the icon cache in the application that will pop-up, then reboot (yourself).


<details><summary>more information</summary>  

0. backup files yourself, backup registry before you apply reg-file by exporting just the two keys. <br/>
everything here is somewhat risky! <strong>BACKUP stuff first\!\!\!</strong>

1. delete:
1.1     <code>C:\Users\\%UserName%\AppData\Local\IconCache.db</code>
1.2     <strong>multiple files:</strong>  <code>C:\Users\\%UserName%\AppData\Local\Microsoft\Windows\Explorer\iconcache_\*.db</code>
1.3     <code>C:\Users\\%UserName%\AppData\Local\Microsoft\Windows\Explorer\ExplorerStartupLog.etl</code>
1.4     <code>C:\Users\\%UserName%\AppData\Local\Microsoft\Windows\Explorer\ExplorerStartupLog_RunOnce.etl</code>
1.5     <code>C:\Users\\%UserName%\AppData\Local\Microsoft\Windows\Explorer\NotifyIcon\\\*.\*</code> (keep folder\!)
1.6     <code>C:\Users\\%UserName%\AppData\Local\Microsoft\Windows\Explorer\IconCacheToDelete\\\*.\*</code> (keep folder\!)

2. copy this to a new text-file, name it whatever, just have it with <code>.reg</code> extension, you can use notepad++ for that.
```reg
Windows Registry Editor Version 5.00

; 1. delete:
; 1.1     C:\Users\%UserName%\AppData\Local\IconCache.db
; 1.2     multiple files:  C:\Users\%UserName%\AppData\Local\Microsoft\Windows\Explorer\iconcache_*.db
; 1.3     C:\Users\%UserName%\AppData\Local\Microsoft\Windows\Explorer\ExplorerStartupLog.etl
; 1.4     C:\Users\%UserName%\AppData\Local\Microsoft\Windows\Explorer\ExplorerStartupLog_RunOnce.etl
; 1.5     C:\Users\%UserName%\AppData\Local\Microsoft\Windows\Explorer\NotifyIcon\*.*
; 1.6     C:\Users\%UserName%\AppData\Local\Microsoft\Windows\Explorer\IconCacheToDelete\*.*
;
; 2. run this reg-file to remove registry cache.
;
; 3. run 'CodecTweakTool.exe' (taken from K-Lite Codec pack), click 'Fixes', select JUST(!) 'Clear Windows icon cache', press 'Apply &amp; Close'. it will finish after one second, just close it.
;
; 4. restart your computer, the registry values will be updated after a full restart.
;
; 5. done. notes: iconcache_* files will be regenerated, and 'IconStreams' and 'PastIconsStream' will be filled with new values, you can not just kill and re-open explorer.exe .
;

[HKEY_CURRENT_USER\SOFTWARE\Classes\Local Settings\Software\Microsoft\Windows\CurrentVersion\TrayNotify]
"IconStreams"=-
"PastIconsStream"=-
```

3. download 'CodecTweakTool_for_cleaning_cache.zip' from above, extract and run 'CodecTweakTool.exe' (taken from K-Lite Codec pack), click 'Fixes', select JUST(!) 'Clear Windows icon cache', press 'Apply &amp; Close'. it will finish after one second, just close it. if you have K-Lite Codec pack installed you can use your-own exe file, it's the same. don't run anything else there.

4. restart your computer, the registry values will be updated after a full restart.

5. done. notes: iconcache_* files will be regenerated, and 'IconStreams' and 'PastIconsStream' will be filled with new values, you can not just kill and re-open explorer.exe .

</details>

