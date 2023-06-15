## Debugging

Getting access to custom apps means you get the power to deploy whatever you want. This also means you can easily break your bench if things go wrong. But with [ssh access](https://frappecloud.com/docs/benches/ssh) you will also be able to perform some level of debugging to figure out the cause of issues.

> **Note**: Please **ONLY** use SSH for debugging purposes. The bench setup on Frappe Cloud is different from the usual production setup you'll find in self hosted instances. Therefore, you can essentially **break** your bench by running arbitrary bench commands that change configuration. Eg: `bench setup supervisor`

## Reading the logs

After ssh-ing into the bench, you will see certain files in the `logs` directory that are of interest

1.  `web.log` and `web.err.log`. These correspond to the STDOUT and STDERR streams of the web process. These handle the individual web requests to your site.
2.  `worker.log` and `worker.err.log`. These correspond to the STDOUT and STDERR streams of the background workers. These run the background jobs.

These files are usually the areas on interest when you're debugging. But similarly all the files in the `logs` directory correspond to the processes listed when you do `supervisorctl status` in your bench. Different issues will have you looking at different logs in your bench.

Read logs with the `less` command. To start reading from bottom, use `less +G`. Vim keybindings work in `less`. Press `q` to quit.

`tail` is also a similarly useful command. `tail -f` allows you to read output as it is being written to the file.

## Bench

You can use bench commands for debugging. `bench doctor` is a command that shows you the status of background jobs on the machine. When you make code changes to files after ssh, you need to run `bench restart` for the changes to take effect.

### Database Queries

You can access the SQL console with `bench mariadb` command. This console is useful to see current status of the database. Eg: You can see running queries with `SHOW PROCESSLIST` command.

## Supervisor

Supervisor is the process manager within your bench. In a correctly functioning bench, all the processes should be in `RUNNING` state when you run `supervisorctl status`. You can also use `supervisorctl` commands to start and stop the processes listed. `bench restart` uses the same.