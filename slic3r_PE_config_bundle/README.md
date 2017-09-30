# Config Bundle
Slic3r Prusa Edition Config Bundle for Nova i3 printer

#Notes
Configured with Slic3r PE [v1.37.1](https://github.com/prusa3d/Slic3r/releases/).  It should be more or less fully forwards compatible and reasonably backwards compatible depending on the features and configuration variables supported by that version.

This configuration started off as the stock [Prusa Slic3r Settings](https://github.com/prusa3d/Slic3r-settings) imported in a blank Slic3r PE.  I left in the stock settings I either wanted to keep as examples or didn't immediately need.  They start with "~", which you can delete if you want.

You will *lose* features and settings if you try to import it using the regular version of Slic3r.

#Use 
* Download the file somewhere and note where you stored it
* Open Slic3r PE
* Export your existing configuration via **File**->**Export Config Bundle** (optional)
* Remove all other settings (optional, but the next steps will overwrite anything with the same name)
* **File**->**Load Config Bundle**
* Select the downloaded file
