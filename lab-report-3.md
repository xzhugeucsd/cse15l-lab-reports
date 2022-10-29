# Find Command-line Options

``` 

``` 
-mtime -n Files modified within n days. 
+n Files modified outside of n days. 
n Files modified in exactly n days

It's useful becuase it helps to query recently modified files

![]()
``` 

``` 

-iname Find all files in the current directory with the file name aa, the file name is not case sensitive, for example: find . -name aa

It can help search for specific file names.
![]()

``` 

``` 
-empty : empty files -gid n or -group name : gid is n or group name is name

It helps to search for empty files.
![]()

# Less Command-line Options
``` 

``` 
-l: ignore case difference when searching
It helps to reduce search errors.

``` 

```
-e: Automatically exit when the contents of the file are displayed

It helps to auto-quit and saves time.

``` 

```
-f: force files to be displayed

You can force special files to open, such as peripheral designations, directories, and binary files.

# Grep Command-line Options
``` 

```
-v: reverse selection, i.e. show the line without the 'search string' content!

Find lines that do not contain the specified content.

``` 

```

--color: highlight the matched content

The ability to highlight matched strings in color in its output.

``` 

```
-n: Show line numbers
Clearly tell us how many lines there are.