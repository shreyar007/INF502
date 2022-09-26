# INF 502 - PA1
Programming Assignment 1 for INF 502.

**DUE DATE:** OCT-13

This assignment will give you some practice with basic Python structures, file input and output, 
and exceptions in the context of writing a basic program. We will deal with two dummy problems, about which you will have to discuss at the end.

## DNA Similarity
Measuring the similarity between different sequences of DNA may tell us how related the owners of those sequences are. 

A molecule of DNA consists of two chains made up of repeating sub-units called nucleotides. There are four different types of nucleotides in DNA: adenine (A), thymine (T), guanine (G), and cytosine (C)[1]. Programmatically, DNA we can have represent it as a string, where each character must be one of A, G, C, or T.

Let's **pretend** that o measure similarity, there are two simple measures:

**NUMBER OF MATCHES:** for the first one, we will compare the alignment between two sequences of DNA checking each position. Most probably there are better ways of assessing DNA similarity, but we will use this as a case for our programming assignment. By aligning the sequences pairwise, we can count the number of matches.

In the case of the figure we have three matches (highlighted in red). The **score is 3**.

However, one thing to have in mind is that each sequence may have insertions or deletions to form a better alignment (but we cannot reorder any sequence). In other words, we can shift nucleotides as long as the order is the same. **For this assignment we will only attempt to shift the complete sequence, without considering insertions or deletions in the middle of the sequence.** By shifting a sequence by one it is possible to verify if we get better results than other previous configurations. The maximum shift (number of insertions in the beginning of a sequence) may be either explicitly set by the user or left to the algorithm to decide when it is not possible to get a better score. 
In this case, as it is possible to see, by shifting the Sequence 2 by 2, we have the highest score (4). And the sequences after shifts are:
```
SEQUENCE 1 -> A  C  T  G  A  T  C  A  C  -  -
SEQUENCE 2 -> -  -  T  T  A  G  C  T  C  G  A
```

**MAXIMUM CONTIGUOUS CHAIN:** In this case, we will analyze the sequences following the same pairwise comparison. However, we will try to search the highest number of contiguous matches. In the example above, one solution could be to shift the sequence 1 by 3, which results in a contiguous chain with 2 matching nucleotides. 

## Assignment: Implementing the similarity algorithm
 
The below souce code demonstrates the working demonstration of the code along with the working mechanisms.

** Source Code: **
```
     #*******************
     #*******************
     #              INF502-- PROGRAMMING ASSIGNMENT 1
     #@sb3292
     #*******************
     #*******************

      # getting user choice       
     def get_method():
         c = 0

         while (c != "cHain_matches" and c != "cHain_contiguous"):
             print ('Your choices are as follows:')
             print ('1. Maximum-Matches\n2. Longest-Continuous-Match \n')
             c = input('Enter your choice from [1 or 2]: ')
             if(c == "1"):
                 c = 'cHain_matches'
             elif(c == "2"):
                 c = 'cHain_contiguous'
             else:
                 print('Enter valid choice!!!')
                 exit

         return c

     #main functions to carry out the operations
     def main():
         chain_one, chain_two = chains_one_two()
         len_oF_chain = len(chain_one)

         c = get_method()

         spaCe_shift = get_maX_shift(len_oF_chain)

         fouNd_matches, optiMal_shift, optiMal_shiFt_one, optiMal_shiFt_two = findMaxMatches(chain_one, chain_two, spaCe_shift, c)
         resulTs(c, fouNd_matches, spaCe_shift, optiMal_shift, optiMal_shiFt_one, optiMal_shiFt_two, chain_one, chain_two)

     # Function that reads the text file containing the ATGC sequence.
     def read_file():
         # Getting the files from the path in my pc
         file_path = '/Users/sb3292/Desktop/INF502/'

         c_list = list()

         #creating a new list to store the sequences
         new_list = ['line_one','line_two']

         #iterating through the list
         for i in new_list:
             flag = False        
             while flag is False:             
                 ff = input('Enter the ' + i + ' of the text file: \n' )

                 # checking whether file exsists
                 try:
                     file = open((file_path + ff),'r')
                     if ff[-4:] != '.txt':
                         raise ValueError
                         print('Invalid file extension. File should be a .txt file!!')

                 except (FileNotFoundError, ValueError):
                     print('File ' + ff + ' does not exist!!')

                 else:
                     file_read = file.read() 
                     file.close()
                     flag2 = False
                     for j in file_read:
                         try:
                             if j not in 'ATGCatgc':
                                 raise ValueError()
                         except ValueError:
                             flag2 = True
                     try:
                         if file_read == "":
                             raise ValueError()
                     except ValueError:
                         print('No contents in file!!')
                         flag2 = True

                     if flag2 is False:
                         flag = True
                         c_list.append(file_read)

         return c_list

     #getting the chains       
     def chains_one_two():
         chain_valid = False
         while chain_valid is False:
             try:
                 c_list = read_file()
                 chain_one,chain_two = c_list[0],c_list[1]
                 if len(chain_one) != len(chain_two):
                     raise ValueError

             except ValueError:
                 print('Chain length not equal!!')

             else:
                 chain_valid = True

         return (chain_one, chain_two)

     # getting the max shift from user for the sequence chain     
     def get_maX_shift(len_oF_chain):
         flag3 = False
         while flag3 == False:
             spaCe_shift = input('Enter the maximum spaces for the Chain shift: ')
             try:
                 spaCe_shift = abs(int(spaCe_shift))
                 if spaCe_shift > (len_oF_chain - 1):
                     spaCe_shift = len_oF_chain - 1
             except ValueError:
                 print('Not an integer!!!')
             else:
                 flag3 = True

         return spaCe_shift

     #comparing the chains for match
     def compares_chain_mAtches(chain_one, chain_two):
         c2 = 0
         for i in range(len(chain_one)):
             if(chain_one[i].upper() == chain_two[i].upper()):
                 c2 = c2 + 1

         return c2

     #comparing the chains for contiguous match
     def compares_chain_cOntiguous(chain_one, chain_two):
         cont_loNg = 0
         contiguous = 0
         for i in range(len(chain_one)):
             if(chain_one[i] == chain_two[i]):
                 contiguous = contiguous + 1
                 if (contiguous > cont_loNg):
                         cont_loNg = contiguous
             else:
                 contiguous = 0

         return cont_loNg

     #chain shifter function to move the sequnece by "n" 
     def shift(chain_one, chain_two, no_shift):
         if no_shift > 0:
             line_one_v2 = '-'*no_shift + chain_one
             line_two_v2 = chain_two + '-'*no_shift

         else:
             line_one_v2 = chain_one + '-'*abs(no_shift)
             line_two_v2 = '-'*abs(no_shift) + chain_two

         return (line_one_v2, line_two_v2)

     #finding the chain matches and contiguous matches
     def findMaxMatches(chain_one, chain_two, spaCe_shift, c):
         fouNd_matches = 0
         optiMal_shift = 'NA'
         if spaCe_shift >0:
             for shiftNum in range(-1*spaCe_shift, spaCe_shift):
                 shiftedA, shiftedB = shift(chain_one, chain_two, shiftNum)
                 if(c == 'cHain_matches'):
                     c2 = compares_chain_mAtches(shiftedA, shiftedB)  

                 elif(c == 'cHain_contiguous'):
                     c2 = compares_chain_cOntiguous(shiftedA, shiftedB)

                 if c2 >= fouNd_matches:
                     fouNd_matches = c2
                     optiMal_shift = shiftNum
                     optiMal_shiFt_one = shiftedA
                     optiMal_shiFt_two = shiftedB
         else:
             if(c == 'cHain_matches'):
                 c2 = compares_chain_mAtches(chain_one, chain_two)  

             elif(c == 'cHain_contiguous'):
                 c2 = compares_chain_cOntiguous(chain_one, chain_two)

             fouNd_matches = c2
             optiMal_shift = 0
             optiMal_shiFt_one, optiMal_shiFt_two = chain_one, chain_two

         return (fouNd_matches, optiMal_shift, optiMal_shiFt_one, optiMal_shiFt_two)

     #printing the results on the output screen
     def resulTs(c, fouNd_matches, spaCe_shift, optiMal_shift, optiMal_shiFt_one, optiMal_shiFt_two, chain_one, chain_two):
         print('\n')
         print ('----- The formulated output is as follows -----')
         print('\nWhen maximum shift is of ' + str(spaCe_shift) + ' spaces.. ')

         if(c == 'cHain_matches'):
             print('The max no. of matches is: ' + str(fouNd_matches))

         elif(c == 'cHain_contiguous'):
             print('\nThe longest contiguous matching chain length is: ' + str(fouNd_matches))

         if (fouNd_matches > 0 and abs(optiMal_shift) > 0):

             if(optiMal_shift >0):
                 print('\n (i.e- This occurs is when the first chain is shifted ' + str(optiMal_shift) + ' spaces to the right. )')

             else:
                 print('\n (i.e- This occurs is when the first chain is shifted ' + str(abs(optiMal_shift)) + ' spaces to the left! )')

             print('\nThe resulting chain combination is as follows: ')
             print(optiMal_shiFt_one)
             print(optiMal_shiFt_two)

         else:
             if(fouNd_matches > 0 and optiMal_shift == 0):
                 print('\n This occurs is when there is no shift!!!')
             print('\nThe original chains are as follows: ')
             print(chain_one)
             print(chain_two)

     #calling main function
     main()
```

## Problem Solution Strategies

1. First step I took towards solving the programming assignment was to break up the problem into smaller subsections. I formulated functions for each of the functionalities. The description for each of the functions is described in the source code.
2. The following outcomes are met in the code;
   (i) start by getting the similarity functions (one at a time) working correctly, and test them using string literals; 
   (ii) add the file input capability; 
   (iii) add the interactive elements, to gather parameters from the user. Finally, add your exception handling using try/except blocks and test your system thoroughly to make sure you're catching all exceptions that can be raised by your code. 
   (iv) Do your best to make the interactive elements of the program look aesthetically pleasing.

## Outputs
```
Chain1 : ACTGATCAC
Chain2 : TTAGCTCGA
```
```
Enter the line_one of the text file: 
chain1.txt
Enter the line_two of the text file: 
chain2.txt
Your choices are as follows:
1. Maximum-Matches
2. Longest-Continuous-Match 

Enter your choice from [1 or 2]: 1
Enter the maximum spaces for the Chain shift: 3


----- The formulated output is as follows -----

When maximum shift is of 3 spaces.. 
The max no. of matches is: 4

 (i.e- This occurs is when the first chain is shifted 2 spaces to the left! )

The resulting chain combination is as follows: 
ACTGATCAC--
--TTAGCTCGA
```

```
Enter the line_one of the text file: 
chain1.txt
Enter the line_two of the text file: 
chain2.txt
Your choices are as follows:
1. Maximum-Matches
2. Longest-Continuous-Match 

Enter your choice from [1 or 2]: 2
Enter the maximum spaces for the Chain shift: 2


----- The formulated output is as follows -----

When maximum shift is of 2 spaces.. 

The longest contiguous matching chain length is: 2

 This occurs is when there is no shift!!!

The original chains are as follows: 
ACTGATCAC
TTAGCTCGA
```

## Hurdles and Benefits
1. Since I had prior experience in working with Python, I found the first part of finding the matches in the code relatively simpler as comapred to the contiguous chain. For the contiguous chain, I made a temporary counter that only counted matches that occurred consecutively (if a match wasn't found, then value=0). I came to the conclusion that using the shift number's sign to denote left/right shifts would make implementation the simplest. The computer code must attempt both left and right shifts if the user enters a maximum shift of 3.nThe chains may be kept at the same length and the shifting procedure could avoid producing any matches by adding "-" to the left and right of the chains. Finding the maximum match was rather easy after I had my two methods for how to count matches and a function for rearranging chains. It just took a loop through all of the potential shifts for me to choose the one that produced the most matches and capture the necessary data from that shift.
2. One of the hurdles that I faced while coding this assignment was to figure out how to keep the code from "exiting" when it came across an error. The error handling approach really helped me handle all the errors effictively.
