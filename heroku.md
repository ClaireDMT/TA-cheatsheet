# HEROKU

## **When pushing to Heroku, error when Puma is launching**

### Error Message
bundler: failed to load command: puma (/app/vendor/bundle/ruby/2.6.0/bin/puma)
2019-08-20T12:46:08.770272+00:00 app[web.1]: Errno::ENOENT: No such file or directory @ rb_sysopen - tmp/pids/server.pid

### Solution
removing the line `pidfile ENV.fetch("PIDFILE") { "tmp/pids/server.pid" }` from the `config/puma.rb` 

[stackoverflow thread](https://stackoverflow.com/questions/57574694/why-does-the-heroku-rails-app-crash-after-upgrading-rails-to-6-0-0)
