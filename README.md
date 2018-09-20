Problem Description  
Find the product of two non-negative integers up to 200 bits.  
  
Input data  
There are two lines, each line is a non-negative integer of no more than 200 bits, and there is no extra leading 0.  
  
Output requirements  
One line, the result of multiplication. There can be no extra leading 0 in the result, ie if the result is 342, then it can't
The output is 0342.  
  
Input sample  
12345678900  
98765432100  
  
Output sample  
1219326311126352690000  
  
Problem solving  
In the following example program, unsigned an1[200] and unsigned an2[200] are used to store two multipliers respectively, and aResult[400] is used to store the product. The intermediate results of the calculation are also present in aResult. The length of aResult is 400 because two 200-bit numbers are multiplied, and the product has a maximum of 400 bits. An1[0], an2[0], aResult[0] all represent ones. The calculation process is basically the same as the primary school multiplication. For the convenience of programming, it is not eager to handle the carry, but leave the carry problem to be finally unified. Now take 835×49 as an example to illustrate the calculation process of the program.

First calculate 835 × 9. 5 × 9 to get 45 1, 3 × 9 to get 27 10, 8 × 9 to get 72 100. Because there is no hurry
After processing the carry, so after 835×9 is finished, the aResult is as follows:  
![](https://github.com/reignsocket/Large-integer-multiplication/blob/master/1.png)  
Next count 4 × 5. Here the result of 4×5 represents 20 10, so to aResult[1]+=20, it becomes:  
![](https://github.com/reignsocket/Large-integer-multiplication/blob/master/2.png)  
Then count down 4×3. Here, the result of 4×3 represents 12 100, so to aResult[2]+= 12, it becomes:  
![](https://github.com/reignsocket/Large-integer-multiplication/blob/master/3.png)     
Finally count 4 × 8. Here the result of 4×8 represents 32 1000, so to aResult[3]+= 32, it becomes:  
![](https://github.com/reignsocket/Large-integer-multiplication/blob/master/4.png)    
The multiplication process is complete. Next, from aResult[0], the carry problem is processed bit by bit from the high bit. aResult[0] leaves 5, adds 4 to aResult[1], after aResult[1] becomes 51, it should leave 1 and add 5 to aResult[2]... eventually make each in aResult The elements are all 1 digit and the result is calculated:  
![](https://github.com/reignsocket/Large-integer-multiplication/blob/master/5.png)    
Summarize a rule that the number of the ith bit of one number multiplied by the jth bit of another number must be added
The i+j bit of the result. Here i, j are all from right to left, starting from 0.  
  
Implementation skills  
It is not necessary to deal with the carry-in immediately, but to wait for all the results to be calculated and then process the carry-in. Sometimes it will be convenient.



