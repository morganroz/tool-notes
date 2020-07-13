# Shell Scripting

## Tee

The tee command lets you both save output to a file and display it. Named after a T-splitter in plumbing!

Example:
```shell
wc -l file1.txt | tee file2.txt
```

This outputs the line count in file1.txt to the terminal and saves it in file2.txt.

## crontab

To schedule a cron job, I use the crontab

to edit the cron jobs:
crontab -e

format:

```* * * * * * <command here>```

The asterisks represent: minute (0-59), hour (0-23), day of the month (1-31), month (1-12), day of the week (1-7). The command can be stored in a .sh file to make it easy.