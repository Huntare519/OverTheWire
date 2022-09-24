ssh cmd: `ssh bandit@bandit.labs.overthewire.org -p 2220`

**Level 1 --> 2**

`find . -type f -exec file {} + | grep ASCII`

`.` means search the current working directory (can leave out)

`-type f` means the type is file

`-exec file {} + | grep ASCII` means execute the cmd `file {name}` and then pipe that through to match only when ASCII is returned.

**Level 2 --> 3**

`cd "spaces in this filename"`

**Level 3 --> 4**

`cd inhere`

`ls -la` is a command to return the long list, which has (from left to right)

- filetype
- file permissions
- number of links
- owner name
- owner group
- file size
- time of last modification
- the name of the file / dir

**Level 4 --> 5**

`find . -type f -exec file {} + | grep ASCII`
Outputs File7
`cat ./-file07`

**Level 5 --> 6**

1. human readable
2. 1033 bytes in size
3. not executable

`find . -size 1033c ! -executable`

By adding the `!` to the command, we are looking for a file that is not executable.

**Level 6 --> 7**

`find / -group bandit6 -user bandit7 -size 33c 2>/dev/null`

`2>/dev/null` makes it so the permission denied error doesn't output

**Level 7-->8**

`cat data.txt | grep millionth`

**Level 8-->9**

`sort data.txt | uniq -u`

sort will sort the data lexographically (i.e. alphabetically)

piping the data into uniq with -u will only consider unique lines

**Level 9-->10**

`strings data.txt | grep -E "==+"`

`-E` is the option to allow for complex regex pattern matching. + is 1 or more matches
