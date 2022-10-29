# Find Command-line Options

``` 
find technical/ -mtime -1
``` 
-mtime -n Files modified within n days. 
+n Files modified outside of n days. 
n Files modified in exactly n days

It's useful becuase it helps to query recently modified files

![](lab5/find%20-mtime.png)
``` 
find technical/ -iname XXXXXX.txt
``` 

-iname Find all files in the current directory with the file name aa, the file name is not case sensitive, for example: find . -name aa

It can help search for specific file names.
![](lab5/find%20-iname.png)

``` 
find technical/ -empty
``` 
-empty : empty files -gid n or -group name : gid is n or group name is name

It helps to search for empty files.

![](lab5/find%20-empty.png)

# Less Command-line Options
``` 
less GREP-RESULTS.txt -i
``` 
-l: ignore case difference when searching

It helps to reduce search errors.

![](lab5/less%20-i.png)

![](lab5/less%20-i2.png)

``` 
less xxxxx.txt -e
```
-e: Automatically exit when the contents of the file are displayed

It helps to auto-quit and saves time.

![](lab5/less%20-e.png)

``` 
less README.md -f
```
-f: force files to be displayed

You can force special files to open, such as peripheral designations, directories, and binary files.

![](lab5/less%20-f.png)

![](lab5/less%20-f2.png)

# Grep Command-line Options
``` 
grep ".txt" find-results.txt -v
```
-v: reverse selection, i.e. show the line without the 'search string' content!

Find lines that do not contain the specified content.

![](lab5/less%20-v.png)

``` 
grep ".txt" find-results.txt --color
```

--color: highlight the matched content

The ability to highlight matched strings in color in its output.

![](lab5/grep%20--color.png)

![](lab5/less%20--color2.png)

``` 
grep ".txt" find-results.txt -n
```
-n: Show line numbers
Clearly tell us how many lines there are.

![](lab5/less%20-n.png)

![](lab5/less%20-n2.png)
