# Shell Scripting

## Tee

The tee command lets you both save output to a file and display it. Named after a T-splitter in plumbing!

Example:
```shell
wc -l file1.txt | tee file2.txt
```

This outputs the line count in file1.txt to the terminal and saves it in file2.txt.