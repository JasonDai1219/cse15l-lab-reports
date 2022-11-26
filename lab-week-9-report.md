# Lab Report 5
## Introduction
Hello! Welcome to the last lab report of CSE 15L for this quarter. In this lab report, I will show my grade.sh and demonstrate how this grade.sh works with a submission sample.

## Part 1 - The Code and Examples
In the first part, let me show you the code and some examples of using the grade.sh with different submissions.

```
rm -rf student-submission
git clone $1 student-submission
cd student-submission

if [ -e "ListExamples.java" ]
then 
    echo "The file ListExamples.java exists [+2 point]"
    ((score+=2))
else 
    echo "The file ListExamples.java does not exist [+0 point]"
    echo "Final Grade: [0/10]"
    exit
fi
cp ../TestListExamples.java ./

javac -cp .:../lib/hamcrest-core-1.3.jar:../lib/junit-4.13.2.jar *.java 2> compile-error.txt
if [[ $? -eq 0 ]]
then
    echo "compiled successfully [+3 point]"
    ((score+=3))
else
    echo "compile error[+0 point]"
    echo ""
    cat compile-error.txt
    echo "Final Grade: [$score/10]"
    exit
fi

java -cp .:../lib/hamcrest-core-1.3.jar:../lib/junit-4.13.2.jar org.junit.runner.JUnitCore TestListExamples > test-error.txt
if [[ $? -eq 0 ]]
then
    echo "tests passed [+5 point]"
    ((score += 5))
else
    echo "some tests did not pass[+0 point]"
    echo ""
    cat test-error.txt
fi
echo "Final Grade: [$score/10]"
```


**Examples of running the grade.sh on various student submission examples**

*1. Some test error*

https://github.com/ucsd-cse15l-f22/list-methods-lab3

![Image](Test-error.png)

*2. All correct*

https://github.com/ucsd-cse15l-f22/list-methods-corrected

![Image](Corrected.png)

*3. Compile error*

https://github.com/ucsd-cse15l-f22/list-methods-compile-error

![Image](Compile-error.png)

## Part 2 - Trace of the code
In this part, let me show you how does the grade.sh produce its result by using the "All correct" example.

```
rm -rf student-submission
git clone $1 student-submission
cd student-submission
```
In this part, since we are just creating and cloning the student-submission that we want to give a grade for, we are not doing any test or comparisons, so their stdout and stderr would have no thing, and these lines' return codes would all be 0, because there is no error in these lines.


```
if [ -e "ListExamples.java" ]
then 
    echo "The file ListExamples.java exists [+2 point]"
    ((score+=2))
else 
    echo "The file ListExamples.java does not exist [+0 point]"
    echo "Final Grade: [0/10]"
    exit
fi
```
In this part, we are trying to see whether the file, ListExamples.java" exist or not, if the student submission does not contain this file, or the file is saved in a wrong name, then these lines would be able to detect it and directly give the 0/10 score for this submission. However, in our example, the submission contains the wanted file name, so the if statement would be true, and the stdout of our example would be "The file ListExamples.java exists [+2 point]", and at the same time the score would be added by 2; the stderr would be empty, and the return codes would all be 0 because there is no error. The else part would not be activated because the file exists.


```
cp ../TestListExamples.java ./
```
In this part, we are trying to get our tests for the submission into the same directory with the student's submission. The stdout and the stderr would all be empty, since we are just moving files, and the return code would be 0, because there is no error.


```
javac -cp .:../lib/hamcrest-core-1.3.jar:../lib/junit-4.13.2.jar *.java 2> compile-error.txt
```
In this part, we are doing the compile test on the student's submission. The stdout and stderr would all be empty again, because we are just compiling files, and the return code would be 0, because there is no error occured.


```
if [[ $? -eq 0 ]]
then
    echo "compiled successfully [+3 point]"
    ((score+=3))
else
    echo "compile error[+0 point]"
    echo ""
    cat compile-error.txt
    echo "Final Grade: [$score/10]"
    exit
fi
```
In this part, we are trying to see that if there are any compile error in the student's submission or not. In our example, we have successfully done the compilation on the file, so the if statement would be true, because the last exit code is indeed 0. Then the "compiled successfully [+3 point]" would be echoed, so the stdout would the thing got echoed, and the stderr would be nothing, and at the same time, the score would be added by 3. The return code for the echo would be 0. The else statement will not run, because we ran the if statement.


```
java -cp .:../lib/hamcrest-core-1.3.jar:../lib/junit-4.13.2.jar org.junit.runner.JUnitCore TestListExamples > test-error.txt
```
In this part, the java command will apply JUnit test on the student's submission, and we are also redirecting the error message(if any) to the test-error.txt, and the contents of the test-error.txt will be casted to the screen once we run the bash command. In our example, even though there is no error, it will still send the empty error message(stdout) to the test-error.txt, and the stderr is empty. The return code would be 0 in this case, since there is no error.


```
if [[ $? -eq 0 ]]
then
    echo "tests passed [+5 point]"
    ((score += 5))
else
    echo "some tests did not pass[+0 point]"
    echo ""
    cat test-error.txt
fi
```
In this part, it is similar to the compile test we did above. We first look at whether there is any test error from the student's submission using the if statement. If it contains error, then the "$?" would not equal to 0, so the then block will not run, and the else part would be activated to print necessary messages and show the errors, vice versa. In our example, the file does not contain errors, so the "$?" is equal to 0, and the "tests passed [+5 point]" would be printed as the stdout, the stderr would be empty and the return code is 0, because there is no error. At the same time, the score will be added by 5.


```
echo "Final Grade: [$score/10]"
```
In this part, we are trying to give the final grade for the student's submission, and we can do that simply by echoing how many point the student has gained after going through the testing process. The if statement would be true, because there is no error detected in the student submission. The stdout would be "Final Grade: [$score/10]", which the $score is the score that has been cumulated, the stderr would be empty, and the return code would be 0, since there is no error in this line. Because we have ran the if statement in our example, we will not run the else block.

## Conclusion
All in all, this is how my grade.sh give tests on the student submission, and output some feedback and the final score. Thanks for your time and patience for reviewing this lab report, have a great rest of your day. 
