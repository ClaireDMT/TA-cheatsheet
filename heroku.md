# HEROKU

## **Installing Heroku on Ubuntu**

### Error Message
Cannot accept the Microsoft EULA agreement for ttf-mscorefonts-installer.

### Solution
1. first loook at process running: `ps aux | grep -i apt`
2. Kill them `sudo kill -9 <process_id>`
3. Run in terminal:  `echo ttf-mscorefonts-installer msttcorefonts/accepted-mscorefonts-eula select true | sudo debconf-set-selections`
4. Run in terminal: `sudo apt-get install ttf-mscorefonts-installer`
5. launch the configuration of the package  `sudo dpkg --configure -a`
6. And launch Heroku install

[stackoverflow thread](https://askubuntu.com/questions/16225/how-can-i-accept-the-microsoft-eula-agreement-for-ttf-mscorefonts-installer)

## **Installing Heroku on Mac**

### Error Message
The zip is downloading the zip for the installation but then installation is never starting and no error message from the terminal.

### Solution
Run`Brew doctor` to repair whatever is broken or `update brew` or `upgrade brew`
Eventually try `type -a heroku`




## **When pushing to Heroku, error when Puma is launching**

### Error Message
bundler: failed to load command: puma (/app/vendor/bundle/ruby/2.6.0/bin/puma)
2019-08-20T12:46:08.770272+00:00 app[web.1]: Errno::ENOENT: No such file or directory @ rb_sysopen - tmp/pids/server.pid

### Solution
removing the line `pidfile ENV.fetch("PIDFILE") { "tmp/pids/server.pid" }` from the `config/puma.rb` 

[stackoverflow thread](https://stackoverflow.com/questions/57574694/why-does-the-heroku-rails-app-crash-after-upgrading-rails-to-6-0-0)

## **Images show on local but no production (wrong img url built)**

### Error Message
No error message, instance have the photo and the key but the path to the cloudinary image is wrong

### Solution
Check if the student forgot to:
1.) add or duplicate with :local
 in config/environments/production.rb,  add `config.active_storage.service = :cloudinary`
2.) delete the default values in config/storage.yml, 
   ` cloudinary:
      service: Cloudinary `
      
     
