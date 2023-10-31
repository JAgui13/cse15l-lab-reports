# Lab 3 Report

## **Part 1 - Bugs**
* Failure inducing input for buggy program
```
@Test
  public void testReversedMultiple() {
    int[] input1 = { 1,2,3 };
    assertArrayEquals(new int[]{3,2,1 }, ArrayExamples.reversed(input1));
```

---
* Input that does not induce failure
```
@Test
  public void testReversed() {
    int[] input1 = { };
    assertArrayEquals(new int[]{ }, ArrayExamples.reversed(input1));
```

---
* Symptom of bug from inputs

![Symptoms](Photos/LabRep3/Lab4Symptoms.png)

---
* Code before and after fixing the bug

**Before**
```
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1];
    }
    return arr;
  }
```
**After**
```
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      newArray[i] = arr[arr.length - i - 1]; // Changed Line
    }
    return newArray;
  }
```

---
**Reason for Change:**\
The given code before change had a write up explaining that the method must return a **new** array, but when the for loop iterates instead of adding the numbers into the new array it replaces the current array with the reversed numbers. The change was that the new list of numbers are put into the newly created array. This also solves the problem where when simlpy replacing the nubmers in the list the first number will be overwritten making so the last int in the list will not be replaced properly.

## **Part 2 - Researching Commands**

**Comman Chosen: "grep"**

---

**-r (lowercase R)**
* -r makes it so that when grep runs it recursivly runs through all files within the given path. Shown below when looking for the string "base pair" it outputs every line within /technical/* containg the string "base pair". This command line option is very useful by itself being able to find every specified string, but shines when uitilzed with other command line options. Recursevly looking through every file with the attatched command line options makes it so that the additional option is applied to every file. Useful for running a specifed command for every file within a directory.
```
grep -r "base pair" technical/plos
```
![plos -r](Photos/LabRep3/Lab5Rep3grep_plos_r.png)
```
grep -r "base pair" technical/biomed
```
![biomed -r](Photos/LabRep3/Lab5Rep3grep_biomed_r.png)

---

**-c (lowercase C)**
* -c outputs the amount of times the specified string appears in a file. When paired with the -r option I was able to count the amount of times base pair occoured in each file. This command line is useful for trying to find the amount of times a word is used, without showing the entire line. Simply counting the occurnces within the file.
```
grep -r -c "base pair" technical/plos
```
![plos -r -c](Photos/LabRep3/Lab5Rep3grep_plos_r_c.png)
```
grep -r -c "base pair" technical/biomed
```
![biomed -r -c](Photos/LabRep3/Lab5Rep3grep_biomed_r_c.png)

---

**-l (lowercase L)**
* -l suppresses normal output and makes it so that when scanning each text file it will stop/continue search upon first match. When paired with the -r option the code outputted the amount of text files the specified string occurs in. This command is useful for freeing up visual clutter on ones device, and only filtering the amount of time the string uniquely occours. Being able to hide duplicates in files, and only finding the first occurnce within each file. 
```
grep -r -l "base pair" technical/plos
```
![plos -r -l](Photos/LabRep3/Lab5Rep3grep_plos_r_l.png)
```
grep -r -l "base pair" technical/biomed
```
![biomed -r -l](Photos/LabRep3/Lab5Rep3grep_biomed_r_l.png)

---

**-v (lowercase V)**
* -v is able to invert the match parameter. In other words does the oppisite of the command line options fuinction. When paired with -r and -c the code recursevly counts the amount of non-specifed strings. Counting every word that isn't "base pair". This command is useful for trying to find the reverse of something, effectly finding the command output excluding the specified string given.
```
grep -r -c -v "base pair" technical/plos
```
![plos -r -c -v](Photos/LabRep3/Lab5Rep3grep_plos_r_c_v.png)
```
grep -r -c -v "base pair" technical/biomed
```
![biomed -r -c -v](Photos/LabRep3/Lab5Rep3grep_biomed_r_c_v.png)

---

[Grep Documentation](https://github.com/ucsd-cse15l-s23/docsearch) - Has the documentation for a lot grep expression and options
