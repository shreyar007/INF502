# Assignment 3: Python Basics

* **INDIVIDUAL ASSIGNMENT**
* **Deadline**: Oct-11th 11:59PM
* **Value**: 100 points counted towards Homework category
* **Link to the code run on Jupyter Notebook(.py file) for the answers below**: [click here]()

**How to submit**: In your GitHub repository called *INF502* (same used for the HW assignments 1 and 2), create a file called *"Assignment3.md"* with the following content:
  1. The problem's specification (as provided below in this file);
  2. A brief textual explanation of you approach to solve the problem. Use the tag ```code``` if you need to show snippets of code along with the explanation (not required though).
  3. A link to the file with the solution. Add the `.py` file to the `code` folder (create one if you don't have it already!).
  
  Please remember to check if you invited me to see your repository (do so if you did not do for previous assignments). I will evaluate the latest commit before 11:59PM (Oct-11th)

## Problem 1: Wallets

Write a Python program that request a user to provide numbers representing the value in cash for different wallets. Your program should store these values in a list. The user should be able to add as many values as they want. One example of a filled `wallets` list (in this example, with 5 wallets) would be:

```
print(wallets)

Output: [1023, 984, 192, 1842, 12]
```

After the user adds the values for the wallets, your application should provide the following information:
* The fattest wallet has `$value` in it.
* The skinniest wallet has `$value` in it.
* All together, these wallets have `$value` in them.
* All together, the total value of these wallets is worth `$value` dimes.

## Source Code
```
  # the below function defines the user input of the amount and its value amount
  def inp():
      wallets = []

      #getting the number of amount values to enter
      user_int = int(input('Enter the no.of amount you want to enter: '))
      for i in range(user_int):

          # entering the amount values
          amount = float(input('Enter the amount of money: '))

          #adding these user entered amounts to the list
          wallets.append(amount)        
      return wallets

  # the below function outputs the result of the program
  def main(wallets):

      # getting the minimun value element from the list
      min_val = min(wallets)

      # getting the maximum value element from the list
      max_val = max(wallets)

      # getting the sum from the list
      sum_val = sum(wallets)

      # getting the dime equivalent ( $1 = 10 dimes)
      dimes_val = sum_val*10

      # printing the output
      print ("----------  Your wallet stats are as follows... ----------")
      print("The fattest wallets has $"+str(max_val)+" in it.")
      print("The skinniest wallets has $"+str(min_val)+" in it.")
      print("All together, these wallets have $"+str(sum_val)+" in them.")
      print("All together, the total amount of these wallets is worth $"+ str(dimes_val) +" dimes")

  # calling the functions
  wallet = inp()
  main(wallet)
```
## Outputs
```
  Enter the no.of amount you want to enter: 5
  Enter the amount of money: 1023
  Enter the amount of money: 984
  Enter the amount of money: 192
  Enter the amount of money: 1842
  Enter the amount of money: 12
  ----------  Your wallet stats are as follows... ----------
  The fattest wallets has $1842.0 in it.
  The skinniest wallets has $12.0 in it.
  All together, these wallets have $4053.0 in them.
  All together, the total amount of these wallets is worth $40530.0 dimes
  Please try to think about different functions to complete your work.
```

## Periodic Table 

The Periodic Table of the Elements was developed to organize information about the elements that make up the Universe.
Write a terminal application that lets you enter information about each element in the periodic table.
Make sure you include the following information:
* symbol, name, atomic number, row, and column

You must save the elements in a dictionary where the `symbol` is the key and the other attributes are nested inside `symbol`. The nested keys are `name`, `number`, `row`, `column`.

To populate your dictionary with data, provide a menu of options to the users:

1. Search the element by symbol (see all the details).
2. Search by a property (`name`, `number`, `row`, `column`) and see the values for that property for all the elements in the table.
3. Enter a new element manually (type the information for each property)
4. Change the properties of an element (by symbol)
5. Export periodic table as a JSON file
6. Load periodic table from JSON file
7. Exit the program

Make sure you do the appropriate communication with the user to get the necessary information to complete each step.
