A collection of scripts I am using with Knulli.

Create the `services` folder if needed and add files to `/userdata/system/services`.

You can then toggle the scripts on/off in Knulli by pressing Start --> SYSTEM SETTINGS --> SERVICES

You will need to reboot before any of the settings take effect.

1. fast_shutdown changes the shutdown time from 2 to 1 second.
2. instant_shutdown effectively disables suspend and shutting down now only requires a tap.
3. random_boot_logo will randomise your boot logo with correctly formatted images. Create the folder and place your `.bmp` files in `/userdata/bootlogos`. Try to keep names without spaces or special characters, the script is untested for those conditions.

TRY THESE AT YOUR OWN RISK
I'm running them daily and haven't seen an issue, but ymmv. (Also I have no idea what happens if you enable scripts 1 and 2 at the same time.)
