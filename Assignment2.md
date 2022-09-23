# Assignment 2: Python Basics

* **INDIVIDUAL ASSIGNMENT**
* **Deadline**: Sept-27th 11:59PM
* **Value**: 100 points counted towards Homework category

## Problems

**1. Write a function with the following signature:** `pythagoreanTheorem(length_a, length_b)`.

The function returns the length of the hypotenuse assuming that `length_a` and `length_b` are the lengths of the two legs of a right triangle (the legs that form the triangle's right angle). Hint: the `math` module might have useful functions to use.

For example:
```python
print(pythagoreanTheorem(2, 2))
2.8284271247461903
```
## *Source-Code*

     def pythagoreanTheorem(length_a, length_b):
       hypotenuse = (length_a**2 + length_b**2)**(1/2)
       return hypotenuse
    
## *Output*

     >>> pythagoreanTheorem(2,2)
     2.8284271247461903
     
     >>> pythagoreanTheorem(5,4) 
     6.4031242374328485

     >>> pythagoreanTheorem(12,16)
     20
     

**2. Write a function with the following signature:** `list_mangler(list_in)`.

The function assumes that `list_in` is a list of integers, and returns a new list containing transformed elements of `list_in`. If the element is even, it's doubled. If the element is odd, it's tripled.

For example:

```python
print(list_mangler([1, 2, 3, 4]))
[3, 4, 9, 8]
```
## *Source-Code*
         
      def list_mangler(inp_list):
          new_l = list()
          for no in inp_list:
              if type(no) == int:
                  if no % 2 == 0:
                      new_inp = no * 2
                  else:
                      new_inp = no* 3
                  new_l.append(new_inp)
          return new_l
 
 ## *Output*  

     >>> list_mangler([1,2,3,4])
     [3, 4, 9, 8]

     >>> list_mangler([5,7,1,9])
     [15, 21, 3, 27]

     >>> ist_mangler([15,3,-19,6])
     [45, 9, -57, 12]

**3. Write a function with the following signature:** `grade_calc(grades_in, to_drop)`.

The function accepts a list `grades_in` containing integer grades, drops the `to_drop` lowest grades (so, for `to_drop` equal to 2, the function should drop the 2 lowest grades), calculates the average of the grades left, and returns the letter grade this average corresponds to according to the letter grade scale for this course.

For example:

```
print(grade_calc([100, 90, 80, 95], 2)) # drops the 2 lowest grades (80 and 90)
'A'
```
## *Source-Code*
         
     def grade_calc(grades_in, to_drop):
        grades_in.sort(reverse = True)
        not_dropped = grades_in[:len(grades_in)-to_drop]
        final = statistics.mean(not_dropped)

        if (final >= 90):
            letter_grade = 'A'
        elif (final >= 80):
            letter_grade = 'B'
        elif (final >= 70):
            letter_grade = 'C'
        elif (final >= 60):
            letter_grade = 'D'
        else:
            letter_grade = 'F'

        return letter_grade
        
## *Output*  

     >>> grade_calc([100,90,80,95],2)
     'A'

     >>> grade_calc([78,30,12,8],0)
     'F'

     >>> grade_calc([78,90,52,89],1)
     'B'


**4. Write a function with the following signature:** `odd_even_filter(numbers)`.

The function accepts an input list of integers and returns a list with two sublists. The first sublist contains all even numbers in the input list and the second sublist contains all odd numbers.

For example:
```
print(odd_even_filter([1, 2, 3, 4, 5, 6, 7, 8, 9]))
[[2, 4, 6, 8], [1, 3, 5, 7, 9]]
print(odd_even_filter([3, 9, 43, 7]))
[[], [3, 9, 43, 7]]
print(odd_even_filter([71, 39, 98, 79, 5, 89, 50, 90, 2, 56]))
[[98, 50, 90, 2, 56], [71, 39, 79, 5, 89]]
```
## *Source-Code*

      def odd_even_filter(numbers):
          even_list = []
          odd_list = []
          for i in numbers:
              if type(i) == int:
                  if i % 2 == 0:
                      even_list.append(i)
                  else:
                      odd_list.append(i)

           return(even_list, odd_list)
 
 ## *Output*  

     >>> odd_even_filter([1, 2, 3, 4, 5, 6, 7, 8, 9])
     ([2, 4, 6, 8], [1, 3, 5, 7, 9])

     >>> odd_even_filter([3, 9, 43, 7])
     ([], [3, 9, 43, 7])

     >>> dd_even_filter([71, 39, 98, 79, 5, 89, 50, 90, 2, 56])
     ([98, 50, 90, 2, 56], [71, 39, 79, 5, 89])