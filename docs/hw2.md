  <a name=top><p>&nbsp;<hr>
  <p align=center>
  &nbsp;<a href="/README.md#top">home</a> &nbsp; | &nbsp;
  <a href="/docs/syllabus.md#top">syllabus</a> &nbsp; | &nbsp;
  <a href="https://docs.google.com/spreadsheets/d/1KuW-SH46KmFW0grEX2wT01jicUSew_5sr1QdGuSrweU/edit#gid=0">groups</a> &nbsp; | &nbsp;
  <a href="https://moodle-courses2223.wolfware.ncsu.edu/course/view.php?id=1771">moodle</a> &nbsp; | &nbsp;
  <a href="https://ncsu.hosted.panopto.com/Panopto/Pages/Sessions/List.aspx#folderID=%22389b8ebf-2f29-4c15-8231-aee9000e3f05%22">video</a> &nbsp; | &nbsp;
  <a href="/docs/review.md">review</a> &nbsp; | &nbsp;
  <a href="/LICENSE.md#top">&copy; 2022</a></p>
  <hr>
  <p align=center><a href="/README.md#top"><img  width=700 src="/etc/img/banner.png"></a></p>
  

# Homework 2

Write some code to read a CSV file and generate summaries of columns (medians and standard
deviation for numerics; mode and entropy for symbolic columns).

The task is very simple. The real goal here is to get your group to practice working together.
- This a small task with lots of even smaller moving parts.
- So your first step must be to
  - Find some way to divide this work across may small files
  - Write a test suite that checks if code from personA works wouth code form PersonB.:wq
  - :
  (so that different people can each work sperately on their own work);
- As a side goal, one lesson here is you'll have to work in languages you've never seen
  before. Get used to it.

Internal to your code you must have different obejcts for `Num`eric and `Sym`olic columns.
THese are stored in a `Data` object which stores `Row` objects, which are summarizes in
`Num`s or `Sym`s. So to make the sumamries:

- Load in the csv into a `Data`
- The ask each `Num` and `Sym` for their central tendancy and diversity aroun that center.

## Resources

- [Source code](https://github.com/txt/se22/blob/main/etc/pdf/csv.pdf). Written in LUA.
  **Your must not write in LUA.**

## What to hand-in

Paste your github repo into Moodle.

Include in the repo all the code and the output of six test cases:

1. `the`: show you can print the settings (magic variables) inside the code.

```txt
-----------------------------------
{:eg ALL :file ../data/auto93.csv :help false :nums 512 :seed 10019}
```

2. `ent`: code that prints summaries of a stream of symbols. e.g. the
   entropy of  {"a","a","a","a","b","b","c"} is

```txt
1.3787834934862	a
```

3. `num`: code that prints summaries of a stream of numbers. eg.  the
median and standard devation of the first 100 integet is something line

```txt
0<= med and med<= 52 and 30.5 <ent and ent <32 e
```

4. `bignum`: code that demonstrates your `Num`s object is a reservour sampler;
             i.e. it keeps N numbers and if you see more than N, 
             some old number is replaced at randaom. E.g. if you read 1000
             numbers for 1,1000, and you are only keeping 32, then this test
             case would print something lineL

```
{1 28 49 50 56 85 86 156 208 237 294 327 444 459 461 485 490 
503 546 618 653 712 723 727 770 801 849 915 928 941 967 987}
```

5. `record`: code that shows you can simply read each row of the csv, then print it
             (no sumamrization required). This is a stepping stone test before
             the next test. 
6. `stats`: Code that reports the median/mode of each column.

```
-----------------------------------
{1 28 49 50 56 85 86 156 208 237 294 327 444 459 461 
485 490 503 546 618 653 712 723 727 770 801 849 915 928 941 967 987}

!!!!!!	bignum	PASS

-----------------------------------
!!!!!!	ent	PASS

-----------------------------------
50	31.007751937984
!!!!!!	num	PASS

-----------------------------------
{
Nums{:at 4 :hi 5140 :isNum true :isSorted false :lo 1613 :n 398 :name Lbs- :w -1} 
Nums{:at 5 :hi 24.8 :isNum true :isSorted false :lo 8    :n 398 :name Acc+ :w 1} 
Nums{:at 8 :hi 50   :isNum true :isSorted false :lo 10   :n 398 :name Mpg+ :w 1}}
!!!!!!	records	PASS

-----------------------------------
{:Acc+ 15.5 :Lbs- 2800 :Mpg+ 20}
!!!!!!	stats	PASS

!!!!!!	ALL	PASS
```    


