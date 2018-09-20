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
