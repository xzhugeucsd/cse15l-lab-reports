

# Grep Command-line Options
``` 
grep ".txt" find-results.txt -v
```
-v: reverse selection, i.e. show the line without the 'search string' content!

It helps to find lines that do not contain the specified content.


``` 
grep ".txt" find-results.txt --color
```

--color: highlight the matched content

It has the ability to highlight matched strings in color in its output.



``` 
grep ".txt" find-results.txt -n
```
-n: Show line numbers

It's useful because it clearly tells us how many lines there are.


