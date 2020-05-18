# PostgreSQL

## Error to connect to the DB

### Error message: "pg connectionbad could not connect to server no such file or directory"

### Solution
Some old PID (process id) file to remove. 
Your computer didn't complete the shutdown process completely which means postgres didn't delete the PID (process id) file. 

[solution](https://stackoverflow.com/questions/19828385/pgconnectionbad-could-not-connect-to-server-connection-refused)

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

