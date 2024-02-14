
# **Lab Report 2**

## 1. Bugs

### averageWithoutLowest(doube[] arr)
```
static double averageWithoutLowest(double[] arr) {
    if(arr.length < 2) { return 0.0; }
    double lowest = arr[0];
    for(double num: arr) {
      if(num < lowest) { lowest = num; }
    }
    double sum = 0;
    for(double num: arr) {
      if(num != lowest) { sum += num; }
    }
    return sum / (arr.length - 1);
}
```
#### **Failure Inducing**
Input: {5, 5, 5}
```
@Test
public void testAverageWithoutLowest(){
    double[] input2 = {5, 5, 5};
    assertEquals("Testing same number", 5, ArrayExamples.averageWithoutLowest(input2), 0.001);
}
```
Expect: 5, Output: 0


#### **Non-Failure Inducing**
Input: {1, 2, 3}
```
@Test
public void testAverageWithoutLowest(){
    double[] input1 = {1, 2, 3};
    assertEquals(3, ArrayExamples.averageWithoutLowest(input1), 0.001);
}
```
Expect: 2.5, Output: 2.5

#### **Symptom**
![Image](JUnit1.png)
> The test with input {1, 2, 3} passes and is the first "." in the terminal output
> 
> The test with input {5, 5, 5} is the failure, resulting in the "E" and the rest of the terminal output

#### **Fixing the Bug**

Bug: Does not check for a null array input

Bug: Input being of all same number
```
static double averageWithoutLowest(double[] arr) {
    if(arr.length < 2) { return 0.0; }
    double lowest = arr[0];
    for(double num: arr) {
      if(num < lowest) { lowest = num; }
    }
    double sum = 0;
    for(double num: arr) {
      if(num != lowest) { sum += num; }
    }
    return sum / (arr.length - 1);
  }
```
Fix
```
static double averageWithoutLowest(double[] arr) {
    if(arr == null || arr.length < 2) { return 0.0; }
    
    boolean same = true;
    double firstElement = arr[0]; // Get the first element
    
    for (double num : arr) {
        if (num != firstElement) {
            same = false; // Found an element different from the first one
        }
    }
    
    if(same)return arr[0];

    double lowest = arr[0];
    for(double num: arr) {
      if(num < lowest) { lowest = num; }
    }
    double sum = 0;
    for(double num: arr) {
      if(num != lowest) { sum += num; }
    }
    return sum / (arr.length - 1);
}
```
## Researching Commands: find

### -iname
> Calling `-iname` after `$find` will search for files by an aproximate name
#### Example 1
```
hpajo@HP-Envy MINGW64 ~/OneDrive/Documents/Desktop/CSE/15L/Lab5/docsearch (main)
$ find -iname "*plos*.txt"
./plos+-sizes.txt
./plos-bp-lines.txt
./plos-bp.txt
./plos-sizes.txt
```
> If your files all follow a certain naming convention (such as using "plos" for file output", it can be convinient to separate them by searching the keyword desired contained in all of them

#### Example 2
```
hpajo@HP-Envy MINGW64 ~/OneDrive/Documents/Desktop/CSE/15L/Lab5/docsearch/technical (main)
$ find -iname "*bi*.txt"
./government/Env_Prot_Agen/bill.txt
./government/Media/Bias_on_the_Job.txt
./government/Media/The_Columbian.txt
./plos/journal.pbio.0020001.txt
./plos/journal.pbio.0020010.txt
./plos/journal.pbio.0020012.txt
./plos/journal.pbio.0020013.txt
./plos/journal.pbio.0020019.txt
./plos/journal.pbio.0020028.txt
./plos/journal.pbio.0020035.txt
./plos/journal.pbio.0020040.txt
./plos/journal.pbio.0020042.txt
./plos/journal.pbio.0020043.txt
./plos/journal.pbio.0020046.txt
...
```
> This is an example of a worse application as the search term was way too broad to properly locate anything

### -type
> Used to search for all files of a certain type, each type has its matching letter for its reference

### Example 1
```
hpajo@HP-Envy MINGW64 ~/OneDrive/Documents/Desktop/CSE/15L/Lab5/docsearch/technical (main)
$ find  -type d
.
./911report
./biomed
./government
./government/About_LSC
./government/Alcohol_Problems
./government/Env_Prot_Agen
./government/Gen_Account_Office
./government/Media
./government/Post_Rate_Comm
./plos
```
> Using `-type d` will search for all the directories

### Exmaple 2
```
hpajo@HP-Envy MINGW64 ~/OneDrive/Documents/Desktop/CSE/15L/Lab5/docsearch/technical (main)
$ find  -type f
./911report/chapter-1.txt
./911report/chapter-10.txt
./911report/chapter-11.txt
./911report/chapter-12.txt
./911report/chapter-13.1.txt
./911report/chapter-13.2.txt
./911report/chapter-13.3.txt
./911report/chapter-13.4.txt
./911report/chapter-13.5.txt
./911report/chapter-2.txt
./911report/chapter-3.txt
...
```
> Using `-type f` will return all the regular files

## -maxdepth
> Limits the depth of searches within the directory

### Exmaple 1
```
hpajo@HP-Envy MINGW64 ~/OneDrive/Documents/Desktop/CSE/15L/Lab5/docsearch/technical (main)
$ find -maxdepth 1 -type d
.
./911report
./biomed
./government
./plos
```
> A depth of 1 means it will only produce the directories directly under our current one

### Example 2
```
hpajo@HP-Envy MINGW64 ~/OneDrive/Documents/Desktop/CSE/15L/Lab5/docsearch/technical (main)
$ find -maxdepth 2 -type d
.
./911report
./biomed
./government
./government/About_LSC
./government/Alcohol_Problems
./government/Env_Prot_Agen
./government/Gen_Account_Office
./government/Media
./government/Post_Rate_Comm
./plos
```
> Coincidentally, a depth of 2 results in looking into our directories' directory for more files of type d

Reference: https://www.redhat.com/sysadmin/linux-find-command
