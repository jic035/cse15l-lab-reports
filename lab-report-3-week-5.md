# `find` Command Options
> Search for filed modified before x days

Use the command `find / -atime -x`

For example, to find filed modified before 90 days, we can do `find / -atime -90​`.

Here, I tried to find files edited before 90, 8, and 7 days.
Here is what the command lind looks like

```
[cs15lfa22hu@ieng6-201]:technical:138$ find 911report -atime -90
911report
911report/chapter-1.txt
911report/chapter-10.txt
911report/chapter-11.txt
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
911report/chapter-8.txt
911report/chapter-9.txt
911report/preface.txt
[cs15lfa22hu@ieng6-201]:technical:139$ find 911report -atime -8
911report
911report/chapter-1.txt
911report/chapter-10.txt
911report/chapter-11.txt
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
911report/chapter-8.txt
911report/chapter-9.txt
911report/preface.txt
[cs15lfa22hu@ieng6-201]:technical:140$ find 911report -atime -7
911report
```
It turns out that all files in /911reports is modified 7 days ago because when I try `-8`, it prints out all files, meaning that all files are edited 8 days ago. When I tried `-7`, it only prints out the name of this folder, and no file name is printed, meaning that no files are edited within 7 days.

> Search for files via file size

The command `find / -size -20k`, for example, finds files with size smaller than 20KB.
Here, I tried to find files less than 30KB, 100KB, and 200KB in folder 911report.

```
[cs15lfa22hu@ieng6-202]:technical:193$ find 911report -size -30k
911report
911report/preface.txt
[cs15lfa22hu@ieng6-202]:technical:194$ find 911report -size -100k
911report
911report/chapter-10.txt
911report/chapter-11.txt
911report/chapter-13.1.txt
911report/chapter-2.txt
911report/chapter-5.txt
911report/chapter-8.txt
911report/preface.txt
[cs15lfa22hu@ieng6-202]:technical:195$ find 911report -size -200k
911report
911report/chapter-1.txt
911report/chapter-10.txt
911report/chapter-11.txt
911report/chapter-12.txt
911report/chapter-13.1.txt
911report/chapter-13.2.txt
911report/chapter-13.3.txt
911report/chapter-2.txt
911report/chapter-5.txt
911report/chapter-6.txt
911report/chapter-7.txt
911report/chapter-8.txt
911report/chapter-9.txt
911report/preface.txt
```
Looks like only one file preface.txt is less than 30KB. I checked by clicking into the file and found that preface.txt indeed has the least numbers of lines. Some files are less than 100KB, all files are smaller than 300KB.

> Search by name regardless of case sensitive

The command `find somedirectory -iname somestring` looks for files that contains "somestring" in its name in somedirectory. Specifically, this "somestring" that the command is looking for is case insensitive.

Here, I tried to find files that contains `lsc`, `M`, and `OFFICE` in government.

```
[cs15lfa22hu@ieng6-202]:technical:169$ find government -iname *lsc
government/About_LSC
[cs15lfa22hu@ieng6-202]:technical:170$ find government -iname *M  
government/Post_Rate_Comm
[cs15lfa22hu@ieng6-202]:technical:171$ find government -iname *OFFICE
government/Gen_Account_Office
```
The result is indeed case insensitive. For example, when I look for file name that contains `OFFICE`, the terminal returns `government/Gen_Account_Office` even if the "OFFICE" in file name is actually "Office".