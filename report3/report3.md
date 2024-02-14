# Lab 3
## Part 1
**Failure Inducing Output**
```
@Test
public void testReversed1() {
    int[] integers = new int[]{1, 2, 3, 4, 5};
    int[] expectedArr = new int[]{5, 4, 3, 2, 1};
    assertArrayEquals(expectedArr, reversed(integers));
}
```
**Non-failure Inducing Output**
```
@Test
public void testReversed2() {
    int[] integers = new int[]{1};
    int[] expectedArr = new int[]{1};
    assertArrayEquals(expectedArr, reversed(integers));
}
```
**Symptom of Tests**
![Image](report3symptom.png)
**Before-and-After Code Changes**
Before
```
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1];
    }
    return arr;
  }
```
After
```
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      newArray[i] = arr[arr.length - i - 1];
    }
    return newArray;
  }
```
The problem with the code before the change was the for loop was assigning values form the argument array with the values from the newly created array and returning the argument array. In order to fix this, we switch the assignment in the for loop so the newArray array is recieving values from the argument array and change the return statement so newArray is returned.

## Part 2
**Command `grep`**
**`-n` Line Number**
ChatGPT prompt: "example of -n for grep"
Output: 
The -n option in grep is used to prefix each line of output with the line number within its input file. Here's an example of how you can use it:

Let's say you have a text file named example.txt with the following contents:

kotlin
Copy code
This is the first line
This is the second line
And this is the third line
Now, if you want to search for the word "line" in this file and display the line numbers along with the matching lines, you can use grep with the -n option like this:

perl
Copy code
grep -n "line" example.txt
The output will be:

kotlin
Copy code
1:This is the first line
2:This is the second line
3:And this is the third line
As you can see, each line of output is prefixed with the line number within the file where the match occurred. This is particularly useful when dealing with large files or when you need to reference specific line numbers containing matches.

**Example 1**
```
Brandon-6:biomed brandonsu$ grep -n "age" 1468-6708-3-1.txt
8:        associated with increased mortality in those over age 65.
20:        most robust health as we age. It has been suggested that
21:        weight standards be adjusted upwards for age [ 8 ] . Such
50:          population-based longitudinal study of 5,888 adults aged
69:          classifies normal weight (without reference to age) as a
113:          YHL from their age, sex, and health at the end of 3
132:          include age, gender, smoking (never or former), history
152:          follows. We regressed YOL and YHL first on age, age
181:        and race. Mean age at baseline was 73.1 and about two
195:        to age 73. For example, black women averaged 6.3 YOL, but
210:        loss and weight loss since age 50. Among males, there were
215:        income and education, as well as age and former smoking,
218:        significantly on BMI, BMI>30, weight loss since age 50,
221:        in weight loss since age 50 was no longer significant.
223:        after adjustment for age, but the difference disappeared
228:        for age, race, and previous smoking (columns 1 and 3), and
230:        and 4). For example, YOL for women, adjusted for age, race,
231:        and smoking, averaged 6.0 years for women with a baseline
232:        BMI below 18.5, but averaged 6.6 years for women with a BMI
238:        and 4). Subsequent analyses are adjusted only for age,
252:        YOL for women (the uppermost curve on Figure 1) averaged
255:        averaged about .25 fewer YOL than other women (p < .05
262:        women and men. Women who were normal or overweight averaged
275:        being compared. For example, underweight women averaged
317:          to age [ 6 13 30 ] . Andres 
319:          24-30 for persons aged 60 to 69 [ 8 ] . Allison 
367:          average older adult; however, adjustment for detailed
384:          person who is depressed because of a poor self-image
```
**Example 2**
```
Brandon-6:biomed brandonsu$ grep -n "similar" 1471-230X-2-21.txt
186:        findings are strikingly similar in patients with liver
230:        autoimmune and similar to that of primary biliary cirrhosis
232:        lymphocytic infiltration similar to that found in stage I
```
The option `-n` is used to search for a keyword within a specific file and returns the line along with the line number that contains the specified keyword. The command follows the format of `grep -n (keyword) (file to search)`. This is useful for finding the frequency of the specified keyword and can also be used to find the location of a word, like how we search for keyword "similar" in example 2 and `grep -n` returned the specific line numbers which contained out word.
---
**`-l` Finding Files**
ChatGPT prompt: -l option grep
Output: 
The -l option in grep is used to suppress normal output and instead print the names of files that contain matches. This is particularly useful when you want to know which files contain a certain pattern without seeing the actual matching lines. Here's how you can use it:

bash
Copy code
grep -l "pattern" file1.txt file2.txt file3.txt
This command will search for the pattern in file1.txt, file2.txt, and file3.txt, and it will only output the names of the files that contain the pattern.

You can also use it with other commands to search within a directory:

bash
Copy code
grep -l "pattern" /path/to/directory/*
This command will search for the pattern in all files within the /path/to/directory directory and its subdirectories, and it will only output the names of the files that contain the pattern.

For example, if you want to find all files containing the word "error" in the current directory and its subdirectories, you can use:

bash
Copy code
grep -l "error" ./*
This command will list all files in the current directory and its subdirectories that contain the word "error".

**Example 1**
```
Brandon-6:biomed brandonsu$ grep -l "Darwin" ./*
./1471-2105-3-2.txt
```
**Example 2**
```
Brandon-6:biomed brandonsu$ grep -l "subspecies" ./*
./1471-2180-2-2.txt
./1471-2180-3-10.txt
```
The option `-l` is used to search for files with the specified keyword and returns a list of the files that contain the keyword. The command follows the format of `grep -l (keyword) (directory to search)`. This is useful for finding files that contain specific keywords that we want to prompt for. For example, in example 1, we look for the keyword "Darwin" and `grep -l` returns the only file that contains "Darwin" in the working directory.
---
**'-i' Case-Insensitive Search**
ChatGPT prompt: grep -i example
Output:
The grep -i command is used to perform a case-insensitive search for the specified pattern. It will match lines containing the pattern regardless of case. Here's how you can use it:

bash
Copy code
grep -i "example"
This command will read from standard input and print all lines that contain the pattern "example", ignoring case. For example, it will match lines containing "example", "Example", "EXAMPLE", etc.

You can also specify a file to search within:

bash
Copy code
grep -i "example" file.txt
This command will search within file.txt and print all lines that contain the pattern "example", ignoring case.

If you want to search within a directory and its subdirectories:

bash
Copy code
grep -ri "example" /path/to/directory
This command recursively searches within /path/to/directory and its subdirectories, printing all lines that contain the pattern "example", ignoring case.

**Example 1**
```
Brandon-6:biomed brandonsu$ grep -i "darwin" 1471-2105-3-2.txt
        In the 1830's, Charles Darwin's investigation of the
        In the 1970's, Woese and Fox revisited Darwinian
```
**Example 2**
```
Brandon-6:biomed brandonsu$ grep -i "subspecies" 1471-2180-2-2.txt
        Mycobacterium avium subspecies 
```
The option `-i` is used on files for a case-insensitive search for a specified keyword. The command follows the format of `grep -i (keyword) (file to search)`. This option is useful for searching for looking for words which are not proper nouns. For example, searching for "the" within a file would be inconvenient to search for with a case-sensitive search as "the" is commonly used as the first word of a sentence and can be capitalized.
---
**`-v` Invert Matches**
ChatGPT prompt: grep -v
Output:
The grep -v command is used to invert the matching, meaning it selects only lines that do not match the specified pattern. Here's how you can use it:

bash
Copy code
grep -v "pattern"
This command will read from standard input and print all lines that do not contain the specified pattern.

You can also specify a file to search within:

bash
Copy code
grep -v "pattern" file.txt
This command will search within file.txt and print all lines that do not contain the specified pattern.

If you want to search within a directory and its subdirectories:

bash
Copy code
grep -rv "pattern" /path/to/directory
This command recursively searches within /path/to/directory and its subdirectories, printing all lines that do not contain the specified pattern.

**Example 1**
```
Brandon-6:biomed brandonsu$ grep -v "s" 1471-2288-3-8.txt

  
    
      
        Background
        arm [ 8 9 ] , ( 
        method ( 
        Prevention Trial (PPT) in which 2079 men and women with
        recently removed colorectal adenoma were randomized to
        in the probability of adenoma recurrence between the
        reduced the probability of adenoma recurrence. An important
```
**Example 2**
```
Brandon-6:biomed brandonsu$ grep -v "t" 1471-2288-3-8.txt

  
    
      
        Background
        arm [ 8 9 ] , ( 
      
      
        
          missing depends on 
          Z and 
          Y , namely,
          
          pr ( 
          R = 1| 
          z, s, Y = 1) = 
          pr ( 
          R = 1 | 
          z, s ). (1)
```
The option `-v` is used to recieve the inverse match of the `grep` command, meaning the lines returned are the lines that do not contain the keyword. The command follows the format `grep -v (keyword) (file or directory to search)`. This command is useful for niche cases where finding lines where you want to exclude the keyword. For example, my specified keyword for example 2 was the letter "t" and `grep -v` returned all the lines which did not include "t".
