# Lab Report 9
## Introduction
Hello! Welcome to the last lab report of CSE 15L for this quarter. In this lab report, I will show my grade.sh and demonstrate how this grade.sh works with a submission sample.

## Part 1
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
