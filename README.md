### FusionPBX & Freeswitch scripts

This repository includes scripts I use for freeswitch and fusionpbx that could be useful for everyone.

- callcenter-announce-position.lua: This is a modified script for FusionPBX callcenters that, unlike the original script, plays the music in the background (and lowers its volume) while it plays the greeting and while it announces the position.   
  This means that your FusionPBX callcenter behaves just like 3CX queues!
  
### based on pbxforum discussion
https://www.pbxforums.com/threads/i-want-to-share-how-to-enable-call-center-position-announcement-feature.8007/

1. copy and replace app_config.php, and call_center_queue_edit.php to /var/www/fusionpbx/app/call_centers/

2. copy callcenter-announce-position.lua to /usr/share/freeswitch/scripts/
  cd /usr/share/freeswitch/scripts
chown www-data:www-data callcenter-announce-position.lua

3. Advanced -> Upgrade -> App Defaults and then Menu Defaults and Permission Defaults.

4. Advanced -> Group Manager -> Superadmin -> Permissions -> Reload.

5. restart freeswitch system and logout and login fusionpbx that's it!! (Optional).

6. Set announce position to true to enable.

7. Set announce frequency to any number in seconds to play the announcement as you like.

8. Add this line into app_languages.php at /var/www/fusionpbx/app/call_centers/

$text['description-queue_announce_position']['en-us'] = "Announce position of caller in the queue.";

Note: Use either Announce Position nor Announce Sound, if use both the call center will play both sound and it will be messy and noisy sound.

![image](https://github.com/user-attachments/assets/f8f1314d-accc-4380-9ed4-0e27c67c57ef)
