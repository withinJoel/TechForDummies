* Install Github Desktop
* Go and clone the repo that you want.
* Then Find the repository/open in the command prompt menu from the status bar(The file, edit .. section)
* Type "git lfs install". (This is a one-time process)
* type "git lfs track "path/to/your/large/file".
* Type "git add .".
* Type "git commit -m "//your comments".
* Type "git push origin main".
* Volia the large file has been uploaded

* (If in case you get an error during the upload only then try this, Be very cateful with these codes)
* Type "git clean -fdX"
* Type "git reset --hard"
* Type "git reset --hard HEAD"
* Type "git push --force origin main"
* And if all these steps are successful then go back to the "git lfs track "path/to/your/large/file". and continue the upload procedure from the beginning.
