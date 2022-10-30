# Lab-week-5-report
## Introduction
*Hello! Welcome to this week's lab report. In this lab report, you will learn various uses of the "grep" command through three examples!*

## Part 1: The "-c" command
When you are reading and want to search for useful documentations to support your analysis, you may want to find useful documents faster when you get them. So by using the "-c" option, you can get an idea of does the document contains the word you want, and by how many.

Input1:
```
grep -c "Tuesday" chapter-1.txt
```
Output1:
```
3
```
> By using the command "-c", we can know how many lines matches the pattern we have chosen, which is "Tuesday". This option is pretty useful, because it is always important for people to know the frequency of certain words/pattern's occurence in a file;in this case, Tuesday is the date of the 911, so if a file includes many Tuesday, it may be talking about what happened on that day. So people can quickly understand if their desired "key word" is in this file or not, which could help people to make decision on continue reading the file or not.

Input2:
```
grep -c "studies" 1468-6708-3-1.txt
```
Output2:
```
10
```
> By using the command "-c", people can have an idea of how many times their interested word occurs in the document. In this case, we are searching in the biomed category, so this implies that in this document, the author mentioned studies at least 10 times, so they maybe talking about studies they have done and people who are interested in that can continue reading.

Input3:
```
grep -c "goal" commission_report.txt
```
Output3:
```
2
```
> By using the command "-c", we can know how many lines matches the pattern we have chosen, which is "goal". Based on the observation, we can see that there are only 2 lines that has our targeted word goal. Therefore, people can infer that since the frequency for "goal" is not that high in this document, so maybe the author did not cover the goal of their commission in this report, or only briefly talked about that,

## Part 2: "-n" command
As we may wonder, after I know I want to keep reading the file and know there are a lot of my intersted words in the file, how can I know better and more on what are their contents? Since we were merely making guesses when using the "-c" option in the previous part.

Input1:
```
grep -n "studies" 1468-6708-3-1.txt
```
Output1:
```
9:        Six large controlled population-based studies of
12:        for relevant covariates [ 1 2 3 4 5 6 ] . All studies found
15:        in certain small subsets. A review of 13 studies of older
23:        number of studies of older persons is fairly small, and
24:        because few studies have examined the relation of BMI to
73:          was associated with lower survival in studies cited
87:          of health events in many studies [ 17 ] . Because we are
130:          related to mortality and morbidity in previous studies,
316:          Recent studies have defined obesity without reference
388:          results from many studies. However, health measures
```
> Now we can sort of zoom in to those words and explore whether these information are important for us or not; for example, if I am interested in finding "population-based" studies, I cansee that it is in the 9th line of this document. 
