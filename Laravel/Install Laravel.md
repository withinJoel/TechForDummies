# Installation of Laravel

1. Download these required ones (If you have already have skip it else download it)
  *Download PHP from https://www.techspot.com/downloads/5680-php.html
  *Download Git from https://git-scm.com/downloads
  *Download 7zip from https://www.7-zip.org/download.html
  *Download Composer from https://getcomposer.org/download/ (Download the .exe file)
2. Find the php.ini file (If it's a fresh install there will php.ini.development and php.ini.production), Just take the php.ini.development and rename it as php.ini
3. In the php.ini file find this line `;extension=fileinfo` and remove the semicolan.
4. Create a project using this line of code to be executed in the cmd window `composer create-project --prefer-dist --ignore-platform-reqs laravel/laravel hello`
5. Hurray, You have successfully installed laravel.
