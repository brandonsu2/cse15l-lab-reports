# Report 5
## Part 1
**The Student Post**

I'm having trouble getting my ArrayExamples class to pass a test care I wrote. I'm not too sure if my test case is wrong or my averageWithoutLowest function is wrong, but I'm leaning towards my function. When passing the double array {1, 1, 5, 6, 7}, I expect the average to be 6.0 as 1 is the minimum value of the array and should be excluded but my actual value is 9.0. This number doesn't make sense as I create a new variable to account for the number of times lowest appears and remove it from the average calculation. Thank you for your help.
Error output:
![symptom](symptom.png)
Test method:
![testmethod](testmethod.png)
My averageWithoutLowest method:
![method](method.png)
My testing bash script in case I am running the wrong commands:
![bash](bash.png)

---
**The TA Response**
Good job in trying eliminate multiple elements that share the value of lowest, but are we counting the number of elements correctly? Try tracing through the iterations when adding to the sum variable and make sure we are incrementing correctly. 

---
**The Bug Fix**
I looked back at my implementation of averageWithoutLowest and traced through the iterati
