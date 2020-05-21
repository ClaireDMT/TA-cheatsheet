# PostgreSQL

## Error to connect to the DB

### Error message: "pg connectionbad could not connect to server no such file or directory"

### Solution
Some old PID (process id) file to remove. 
Your computer didn't complete the shutdown process completely which means postgres didn't delete the PID (process id) file. 

[solution](https://stackoverflow.com/questions/19828385/pgconnectionbad-could-not-connect-to-server-connection-refused)

## Error to connect to the DB on MAC
### Error message: "could not connect to server: No such file or directory"

### Solution

Uninstall postgres
brew uninstall postgresql
2. Reinstall postgres
brew install postgresql
3. Check that postgress was installed
psql -d postgres
This command should take you to a irb like interface inside your terminal 
If you get no errors and you are in that interface run step 4
4. Exit postgress interface
\q
5. Go up one folder to your /code/GITHUBUSERNAME, and delete your previous mr cocktail
cd ..
rm -rf rails-mister-cocktail
6. Make sure you go into your github account and delete the old repository of mister cocktail
7. Start the challenge again 
11:58
Specifically for OSX users

## Localhost never loading

### Rendering for ages or port already in use or temp/83668.pid to remove

### Solution
Some old PID (process id) file to remove. You can delete the server.pid file.
rm /your_project_path/tmp/pids/server.pid
[solution](https://stackoverflow.com/questions/24627701/a-server-is-already-running-check-tmp-pids-server-pid-exiting-rails)

### Solution
Kill whatever is on port 3000 (which is what webrick normally uses), type in your terminal to find out the PID of the process:
$ lsof -wni tcp:3000

Then, use the number in the PID column to kill the process:
$ kill -9 PID

