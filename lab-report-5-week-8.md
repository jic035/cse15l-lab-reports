# Lab Report 5

grade.sh
```
CPATH=".:../lib/hamcrest-core-1.3.jar:../lib/junit-4.13.2.jar"
file="student-submission/ListExamples.java"
totalPoints=2

rm -rf student-submission
git clone $1 student-submission
cp TestListExamples.java student-submission/

if [[ -f $file ]] && [[ -e $file ]]
then
    echo "File exists!"
else
    echo "File not found!"
    echo "Total Points: 0/2"
    exit 1
fi

cd student-submission

javac -cp $CPATH ListExamples.java 2>> errors.txt

javac -target 1.8  -cp $CPATH -Xdiags:verbose TestListExamples.java 2>> errors.txt

java -cp $CPATH  org.junit.runner.JUnitCore TestListExamples > failures.txt

if [[ $(grep -c "error: method filter" errors.txt) -ne 0 ]]
then
    let "totalPoints-=1"
    echo "[EXCEPT 0/1] testFilter"
elif [[ $(grep -c "testFilter(TestListExamples)" failures.txt) -ne 0 ]]
then
    let "totalPoints-=1"
    echo "[FAILED 0/1] testFilter"
else
    echo "[PASSED 1/1] testFilter"
fi

if [[ $(grep -c "error: method merge" errors.txt) -ne 0 ]]
then
    let "totalPoints-=1"
    echo "[EXCEPT 0/1] testMerge"
elif [[ $(grep -c "testMerge(TestListExamples)" failures.txt) -ne 0 ]]
then
    let "totalPoints-=1"
    echo "[FAILED 0/1] testMerge"
else
    echo "[PASSED 1/1] testMerge"
fi

echo "Total Points: $totalPoints/2"
```
Inspired by https://github.com/DaPhysikist/list-examples-grader

Here are the three screenshots.
![image](Week8Screenshots\firstSubmission.png)
![image](Week8Screenshots\secondSubmission.png)
![image](Week8Screenshots\thirdSubmission.png)

>Trace grade.sh

the student submission is passed in as the first argument in the command line, which in this case, passed in by the url input. After cloning, the message of successful cloning is passd into the 'streamToString' method and was printed into the webpage.

Then, grade.sh checks if the ListExamples.java file exists with command '-e'. It then checks if the file compiles by checking the exit code. The grade.sh runs the test in TestListExamples and redirects the standard output into error.txt. I did not separate the standard output and standard error in different files. I check if error.txt contains certain error messages and grade the submission accordingly. 

In my first example, the file ListExamples.java exists, so it echos "File exists!". Then, passing to the second if condition checkpoint, I don't know why the second if statement does not produce any output because I am expecting to see "Compile succeeded" here but see nothing. The submission satisfies the third and forth if condition because it has the expected errors, so it goes to 'then' commands. The totalPoints are deducted twice and echos "[FAILED 0/1] testFilter" and "[FAILED 0/1] testMerge".