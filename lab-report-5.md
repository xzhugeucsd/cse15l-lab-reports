## Lab Report 5
**Bash File:**
```
rm -rf student-submission
git clone $1 student-submission
 
score=0
 
# check if files exist 1 point
FILE=student-submission/ListExamples.java
SUBMISSION=ListExamples.java
if [[ -f "$FILE" ]]
then
   echo "$SUBMISSION is submitted successfully. [1 piont]"
   ((score+1))
else
   echo "$SUBMISSION is not found."
   echo "Grade: [$score/3]"
   exit
fi
 
cp TestListExamples.java student-submission
cp -rf lib student-submission
cd student-submission
CPATH=".:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar"
 
# check if files compile 1 point
javac -cp $CPATH *.java 2> compile_error.txt

if [[ $? -eq 0 ]]; then
    echo "$SUBMISSION compiled succssfully. [1 point]"
    ((score+=1))
 
else
    echo "File cannot be compiled"
    cat compile_error.txt
    echo "Grade: [$score/3]"
    exit
fi

# check the tests 1 point
java -cp $CPATH org.junit.runner.JUnitCore TestListExamples > test_result.txt
if [[ $? -eq 0 ]];then
   echo "All tests passed. [1 point]"
   ((score+=1))
else
   echo "Tests failed."
   grep "Tests run" test_result.txt
fi
echo "Grade: [$score/3]"
```

**Student Submission Examples**


![First](lab8/compile error)


![Second](lab8/)


![Third](lab8/)


**Tracing the code**

Let’s trace the code with the first student example, which is a compile error.
1. The ``rm -rf`` command deletes any folders left over from running the grading script on a student submission previously. There is no stderr or stdout, and the return code is 0.
2. The ``git clone`` command clones the student submission into the folder. The return code is 0 and there is no stderr. The stdout is ``Cloning into 'student-submission'...``
3. The if statement ``if [[ -f "$FILE" ]]`` evaluates to true, because the file “ListExamples.java” exist in the given path and then we echo stdout that "The file is submitted successfully. [1 piont]". It has no standard error, and its return code is 0.
4. Next, We then hit the ``cp``. The cp has no standard output, no standard error, and its return code is 0.
5. We hit our second if statement which checks whether the file is compiled or not. Then it evaluates to false that throw/echo any error message to  ``compile_error.txt`` as stderr.
6. Finally, the command ``exit`` has not stderr or stdout. The exit code is 1.