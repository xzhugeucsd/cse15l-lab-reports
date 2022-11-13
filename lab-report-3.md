# Grep Command-line Options

# The -l option

grep -l, which seems to work well, because when a match is found, the return contains the name of the matching file.

## Example1

code:

``` 
grep "United 175 was hijacked" 911report/*.txt -l
```
result:

``` 
911report/chapter-1.txt
```

The output shows which txt files in /911report contain "United 175 was hijacked," with only /chapter-1.txt containing the string I'm looking for in this case.


## Example2

code:
```
grep  "dance" 911report/*.txt -l 
```

result:
```
911report/chapter-1.txt
911report/chapter-10.txt
911report/chapter-12.txt
911report/chapter-13.1.txt
911report/chapter-13.2.txt
911report/chapter-13.3.txt
911report/chapter-13.4.txt
911report/chapter-13.5.txt
911report/chapter-2.txt
911report/chapter-3.txt
911report/chapter-5.txt
911report/chapter-6.txt
911report/chapter-7.txt
911report/chapter-9.txt
911report/preface.txt
```
This grep -l command searches all files in the technical/911report/ directory for the keyword "dance" and prints out the files that contain that word.

## Example3

code:
```
grep -l "baby" plos/* 
```
result:
```
plos/journal.pbio.0030056.txt
```
The word "baby" was searched for in all the files in the plos/ directory, but only one file was printed because only one diary contained the word "baby."

# The -n option

-n: Show line numbers

It's useful because it clearly tells us how many lines there are.

## Example 1

code:
``` 
grep -n "one" 911report/preface.txt  
```
result:
```
7:                people for their consideration. Ten Commissioners-five Republicans and five
59:                Commissioners, whose dedication to this task has been profound. We have reasoned
83:            We want to note what we have done, and not done. We have endeavored to provide the
85:                This final report is only a summary of what we have done, citing only a fraction of
96:                enormous sympathy for the victims and their loved ones, and with enhanced respect
```
This is useful when you want to find not only rows that match a specific pattern, but also what that row is and where it is.

## Example 2

code:
```
grep -n -o "is" 911report/preface.txt
```
result:
```
5:is
7:is
9:is
9:is
9:is
9:is
11:is
...
```
-o will shorten the number of lines and give only the string as the result. It can help you to find the corresponding line number quickly.

## Example 3

code:
```
grep -n -w "WE HAVE SOME PLANES" 911report/chapter-1.txt 
```

result:
```
4:"WE HAVE SOME PLANES"
```
-n -w helps to print lines only if the entire string matches.

# The -V option

-v: reverse selection, i.e. show the line without the 'search string' content!

It helps to find lines that do not contain the specified content.

## Example1

code:

``` 
grep -v "the " 911report/*
```

result:

``` 
...

911report/preface.txt:            As we complete our final report, we want to begin by thanking our fellow
911report/preface.txt:                Commissioners, whose dedication to this task has been profound. We have reasoned
911report/preface.txt:                of our colleagues, as well as our great affection for them.
911report/preface.txt:                setting aside other important endeavors to take on this all-consuming assignment.
911report/preface.txt:                built. They have given good advice, and faithfully carried out our guidance. They
911report/preface.txt:                have searched records and produced a multitude of documents for us. We thank
911report/preface.txt:                officials, past and present, who were generous with their time and provided us with
911report/preface.txt:                assistance. We owe a huge debt to their investigative labors, painstaking attention
911report/preface.txt:            We want to note what we have done, and not done. We have endeavored to provide the
911report/preface.txt:                This final report is only a summary of what we have done, citing only a fraction of
911report/preface.txt:                issues and organizations, we are conscious of our limits. We have not interviewed
911report/preface.txt:                every knowledgeable person or found every relevant piece of paper. New information
911report/preface.txt:                inevitably will come to light. We present this report as a foundation for a better
911report/preface.txt:            We have listened to scores of overwhelming personal tragedies and astounding acts of
911report/preface.txt:                have admired their determination to do their best to prevent another tragedy while
911report/preface.txt:                preparing to respond if it becomes necessary. We emerge from this investigation with
911report/preface.txt:                number of them. We decided consciously to focus on recommendations we believe to be
911report/preface.txt:                this process with strong opinions about what would work. All of us have had to
911report/preface.txt:                pause, reflect, and sometimes change our minds as we studied these problems and
911report/preface.txt:                citizens to study, reflect-and act.
911report/preface.txt:            Thomas H. Kean, chair
911report/preface.txt:            Lee H. Hamilton, vice chair
911report/preface.txt:   

...
```
It returns all lines in the specific file that do not include "the".

## Example2

code:

``` 
grep -v "baby" plos/*

```

result:

``` 
...
plos/pmed.0020281.txt:        Whistleblowers serve no function if they cannot tell their stories. The present story of
plos/pmed.0020281.txt:        whistleblowing—as discussed, in part, in 
plos/pmed.0020281.txt:        PLoS Medicine —that involves the pharmaceutical industry, pharmaceutical
plos/pmed.0020281.txt:        benefit management corporations, the managed care industry, and the political and lobbying
plos/pmed.0020281.txt:        forces that zealously guard their secrets could not have been told without the help of
plos/pmed.0020281.txt:        courageous men and women [1, 2] For that reason, those of us who congregated in Washington,
plos/pmed.0020281.txt:        D.C., on May 15th, 2005, at the invitation and support of the Public Library of Science and
plos/pmed.0020281.txt:        the Government Accountability Project feel particularly humbled and grateful to these two
plos/pmed.0020281.txt:        sponsors. Our convictions could not have been aired were it not for the essential First
plos/pmed.0020281.txt:        Amendment work of responsible journalists, who exemplify the best in investigatory
plos/pmed.0020281.txt:        research.
plos/pmed.0020281.txt:        For me, whistleblowing is not a theoretical exercise. It has a human face and tangible
plos/pmed.0020281.txt:        features. It is the face of children and adults who have been injured or killed by
plos/pmed.0020281.txt:        misrepresented pharmaceuticals; clinical research trial results that have been sequestered
plos/pmed.0020281.txt:        from the scientific community and whose incomplete findings cause injury; and
plos/pmed.0020281.txt:        pharmaceuticals that are detailed to physicians, not to save lives or necessarily improve
plos/pmed.0020281.txt:        the health or welfare of the recipients, but to make money.
plos/pmed.0020281.txt:        In the lonely and, at times, discouraging world of whistleblowing, we whistleblowers are
plos/pmed.0020281.txt:        passionate, and often successful, because our efforts have a different goal than the
plos/pmed.0020281.txt:        corporations and political interests whose operations we occasionally challenge. Our goal
plos/pmed.0020281.txt:        is to tell the truth. That honest effort is the source of any ethical difference we can or
plos/pmed.0020281.txt:        might make. Truth is the basis for the power of a whistleblower, one that can withstand the
plos/pmed.0020281.txt:        assault of unprecedented odds against being heard put forth by that sum of political power,
plos/pmed.0020281.txt:        expediency, and money.
plos/pmed.0020281.txt:        A whistleblower's success depends upon competent and articulate media. The debate to
plos/pmed.0020281.txt:        improve the status quo—be it in pharmaceutical marketing or managed-care decision
plos/pmed.0020281.txt:        making—cannot proceed or flourish without it.
plos/pmed.0020281.txt:        Ralph Waldo Emerson, American essayist and philosopher (1803–1882), commented about
plos/pmed.0020281.txt:        success (I have adapted his comments for all of us who gathered in Washington in mid-May
plos/pmed.0020281.txt:        2005): “To leave the world a bit better, whether by a healthy child, a garden patch or a
plos/pmed.0020281.txt:        redeemed social condition; to know even one life breathed easier because you have lived;
plos/pmed.0020281.txt:        this is to have succeeded [as a whistleblower].”

...
```
Since only one plos file contain "baby", it returns the rest of the lines in the plos file.

## Example3

code:

``` 
grep -v "We" 911report/preface.txt
```

result:

``` 
...

PREFACE
                the President of the United States, the United States Congress, and the American
                people for their consideration. Ten Commissioners-five Republicans and five
                Democrats chosen by elected leaders from our nation's capital at a time of great
                partisan division-have come together to present this report without dissent.
                September 11, 2001, was a day of unprecedented shock and suffering in the history of
                the United States. The nation was unprepared. How did this happen, and how can we
                avoid such tragedy again?
            To answer these questions, the Congress and the President created the National
                Commission on Terrorist Attacks Upon the United States (Public Law 107-306, November
                27, 2002).
            Our mandate was sweeping. The law directed us to investigate "facts and circumstances
                relating to the terrorist attacks of September 11, 2001," including those relating
                to intelligence agencies, law enforcement agencies, diplomacy, immigration issues
                and border control, the flow of assets to terrorist organizations, commercial
                aviation, the role of congressional oversight and resource allocation, and other
                areas determined relevant by the Commission. In pursuing our mandate, we have
                reviewed more than 2.5 million pages of documents and interviewed more than 1,200
                individuals in ten countries. This included nearly every senior official from the
                current and previous administrations who had responsibility for topics covered in
                From the outset, we have been committed to share as much of our investigation as we
                can with the American people. To that end, we held 19 days of hearings and took
                public testimony from 160 witnesses.
            Our aim has not been to assign individual blame. Our aim has been to provide the
                fullest possible account of the events surrounding 9/11 and to identify lessons
                learned.
                
...
```
Use -v to return files and lines in preface.txt that do not have "We" in them. (Case Matters)



