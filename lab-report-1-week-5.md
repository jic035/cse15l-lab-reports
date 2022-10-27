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