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

## Source-Code
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
## Output
```
  Enter the no.of amount you want to enter: 4
  Enter the amount of money: 125
  Enter the amount of money: 657
  Enter the amount of money: 14
  Enter the amount of money: 78
  ----------  Your wallet stats are as follows... ----------
  The fattest wallets has $657.0 in it.
  The skinniest wallets has $14.0 in it.
  All together, these wallets have $874.0 in them.
  All together, the total amount of these wallets is worth $8740.0 dimes
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

## Source-Code
```
  import json

  # storing the periodic table elements in the form of a dictionary
  periodic_table_ele = {"H":{"row":1,"column":1,"number":1,"name":"Hydrogen"}, "He":{"row":1,"column":18,"number":2,"name":"Helium"}, "Li":{"row":2,"column":1,"number":3,"name":"Lithium"}, "Be":{"row":2,"column":2,"number":4,"name":"Beryllium"}, "B":{"row":2,"column":13,"number":5,"name":"Boron"}, "C":{"row":2,"column":14,"number":6,"name":"Carbon"}, "N":{"row":2,"column":15,"number":7,"name":"Nitrogen"}, "O":{"row":2,"column":16,"number":8,"name":"Oxygen"}, "F":{"row":2,"column":17,"number":9,"name":"Fluorine"}, "Ne":{"row":2,"column":18,"number":10,"name":"Neon"}, "Na":{"row":3,"column":1,"number":11,"name":"Sodium"}, "Mg":{"row":3,"column":2,"number":12,"name":"Magnesium"}, "Al":{"row":3,"column":13,"number":13,"name":"Aluminum"}, "Si":{"row":3,"column":14,"number":14,"name":"Silicon"}, "P":{"row":3,"column":15,"number":15,"name":"Phosphorus"}, "S":{"row":3,"column":16,"number":16,"name":"Sulfur"}, "Cl":{"row":3,"column":17,"number":17,"name":"Chlorine"}, "Ar":{"row":3,"column":18,"number":18,"name":"Argon"}, "K":{"row":4,"column":1,"number":19,"name":"Potassium"}, "Ca":{"row":4,"column":2,"number":20,"name":"Calcium"}, "Sc":{"row":4,"column":3,"number":21,"name":"Scandium"}, "Ti":{"row":4,"column":4,"number":22,"name":"Titanium"}, "V":{"row":4,"column":5,"number":23,"name":"Vanadium"}, "Cr":{"row":4,"column":6,"number":24,"name":"Chromium"}, "Mn":{"row":4,"column":7,"number":25,"name":"Manganese"}, "Fe":{"row":4,"column":8,"number":26,"name":"Iron"}, "Co":{"row":4,"column":9,"number":27,"name":"Cobalt"}, "Ni":{"row":4,"column":10,"number":28,"name":"Nickel"}, "Cu":{"row":4,"column":11,"number":29,"name":"Copper"}, "Zn":{"row":4,"column":12,"number":30,"name":"Zinc"}, "Ga":{"row":4,"column":13,"number":31,"name":"Gallium"}, "Ge":{"row":4,"column":14,"number":32,"name":"Germanium"}, "As":{"row":4,"column":15,"number":33,"name":"Arsenic"}, "Se":{"row":4,"column":16,"number":34,"name":"Selenium"}, "Br":{"row":4,"column":17,"number":35,"name":"Bromine"}, "Kr":{"row":4,"column":18,"number":36,"name":"Krypton"}, "Rb":{"row":5,"column":1,"number":37,"name":"Rubidium"}, "Sr":{"row":5,"column":2,"number":38,"name":"Strontium"}, "Y":{"row":5,"column":3,"number":39,"name":"Yttrium"}, "Zr":{"row":5,"column":4,"number":40,"name":"Zirconium"}, "Nb":{"row":5,"column":5,"number":41,"name":"Niobium"}, "Mo":{"row":5,"column":6,"number":42,"name":"Molybdenum"}, "Tc":{"row":5,"column":7,"number":43,"name":"Technetium"}, "Ru":{"row":5,"column":8,"number":44,"name":"Ruthenium"}, "Rh":{"row":5,"column":9,"number":45,"name":"Rhodium"}, "Pd":{"row":5,"column":10,"number":46,"name":"Palladium"}, "Ag":{"row":5,"column":11,"number":47,"name":"Silver"}, "Cd":{"row":5,"column":12,"number":48,"name":"Cadmium"}, "In":{"row":5,"column":13,"number":49,"name":"Indium"}, "Sn":{"row":5,"column":14,"number":50,"name":"Tin"}, "Sb":{"row":5,"column":15,"number":51,"name":"Antimony"}, "Te":{"row":5,"column":16,"number":52,"name":"Tellurium"}, "I":{"row":5,"column":17,"number":53,"name":"Iodine"}, "Xe":{"row":5,"column":18,"number":54,"name":"Xenon"}, "Cs":{"row":6,"column":1,"number":55,"name":"Cesium"}, "Ba":{"row":6,"column":2,"number":56,"name":"Barium"}, "La":{"row":8,"column":3,"number":57,"name":"Lanthanum"}, "Ce":{"row":8,"column":4,"number":58,"name":"Cerium"}, "Pr":{"row":8,"column":5,"number":59,"name":"Praseodymium"}, "Nd":{"row":8,"column":6,"number":60,"name":"Neodymium"}, "Pm":{"row":8,"column":7,"number":61,"name":"Promethium"}, "Sm":{"row":8,"column":8,"number":62,"name":"Samarium"}, "Eu":{"row":8,"column":9,"number":63,"name":"Europium"}, "Gd":{"row":8,"column":10,"number":64,"name":"Gadolinium"}, "Tb":{"row":8,"column":11,"number":65,"name":"Terbium"}, "Dy":{"row":8,"column":12,"number":66,"name":"Dysprosium"}, "Ho":{"row":8,"column":13,"number":67,"name":"Holmium"}, "Er":{"row":8,"column":14,"number":68,"name":"Erbium"}, "Tm":{"row":8,"column":15,"number":69,"name":"Thulium"}, "Yb":{"row":8,"column":16,"number":70,"name":"Ytterbium"}, "Lu":{"row":8,"column":17,"number":71,"name":"Lutetium"}, "Hf":{"row":6,"column":4,"number":72,"name":"Hafnium"}, "Ta":{"row":6,"column":5,"number":73,"name":"Tantalum"}, "W":{"row":6,"column":6,"number":74,"name":"Wolfram"}, "Re":{"row":6,"column":7,"number":75,"name":"Rhenium"}, "Os":{"row":6,"column":8,"number":76,"name":"Osmium"}, "Ir":{"row":6,"column":9,"number":77,"name":"Iridium"}, "Pt":{"row":6,"column":10,"number":78,"name":"Platinum"}, "Au":{"row":6,"column":11,"number":79,"name":"Gold"}, "Hg":{"row":6,"column":12,"number":80,"name":"Mercury"}, "Tl":{"row":6,"column":13,"number":81,"name":"Thallium"}, "Pb":{"row":6,"column":14,"number":82,"name":"Lead"}, "Bi":{"row":6,"column":15,"number":83,"name":"Bismuth"}, "Po":{"row":6,"column":16,"number":84,"name":"Polonium"}, "At":{"row":6,"column":17,"number":85,"name":"Astatine"}, "Rn":{"row":6,"column":18,"number":86,"name":"Radon"}, "Fr":{"row":7,"column":1,"number":87,"name":"Francium"}, "Ra":{"row":7,"column":2,"number":88,"name":"Radium"}, "Ac":{"row":9,"column":3,"number":89,"name":"Actinium"}, "Th":{"row":9,"column":4,"number":90,"name":"Thorium"}, "Pa":{"row":9,"column":5,"number":91,"name":"Protactinium"}, "U":{"row":9,"column":6,"number":92,"name":"Uranium"}, "Np":{"row":9,"column":7,"number":93,"name":"Neptunium"}, "Pu":{"row":9,"column":8,"number":94,"name":"Plutonium"}, "Am":{"row":9,"column":9,"number":95,"name":"Americium"}, "Cm":{"row":9,"column":10,"number":96,"name":"Curium"}, "Bk":{"row":9,"column":11,"number":97,"name":"Berkelium"}, "Cf":{"row":9,"column":12,"number":98,"name":"Californium"}, "Es":{"row":9,"column":13,"number":99,"name":"Einsteinium"}, "Fm":{"row":9,"column":14,"number":100,"name":"Fermium"}, "Md":{"row":9,"column":15,"number":101,"name":"Mendelevium"}, "No":{"row":9,"column":16,"number":102,"name":"Nobelium"}, "Lr":{"row":9,"column":17,"number":103,"name":"Lawrencium"}, "Rf":{"row":7,"column":4,"number":104,"name":"Rutherfordium"}, "Db":{"row":7,"column":5,"number":105,"name":"Dubnium"}, "Sg":{"row":7,"column":6,"number":106,"name":"Seaborgium"}, "Bh":{"row":7,"column":7,"number":107,"name":"Bohrium"}, "Hs":{"row":7,"column":8,"number":108,"name":"Hassium"}, "Mt":{"row":7,"column":9,"number":109,"name":"Meitnerium"}, "Ds""":{"row":7,"column":10,"number":110,"name":"Darmstadtium"}, "Rg""":{"row":7,"column":11,"number":111,"name":"Roentgenium"}, "Cn""":{"row":7,"column":12,"number":112,"name":"Copernicium"}, "Uut""":{"row":7,"column":13,"number":113,"name":"Ununtrium"}, "Uuq""":{"row":7,"column":14,"number":114,"name":"Ununquadium"}, "Uup""":{"row":7,"column":15,"number":115,"name":"Ununpentium"}, "Uuh""":{"row":7,"column":16,"number":116,"name":"Ununhexium"}, "Uus""":{"row":7,"column":17,"number":117,"name":"Ununseptium"}, "Uuo""":{"row":7,"column":18,"number":118,"name":"Ununoctium"}}

  # keeping the loop going continuously
  flAg = True

  # running the code
  while flAg == True:

    # getting the user input for the various operations
      user_input = input('\n\n ----------	PERIODIC TABLE OPERATIONS	----------\n'
        '\n1. Search the element by symbol\n'
          '2. Search by a property (name, number, row, column) and see the values for that property for all the elements in the table\n'
          '3. Enter a new element manually (type the information for each property) \n'
          '4. Change the properties of an element (by symbol)\n'
          '5. Export periodic table as a JSON file \n'
          '6. Load periodic table from JSON file\n'
          '7. Exit the program \n')

      # if user input value is '1' then the below code is executed..   
      if user_input == "1":

        # getting the elements abbreviatin from user
          ele = input("Enter the element's abbreviation: ")

          # getting the value of that particuar ele from the periodic table
          result = periodic_table_ele[ele]

          # printing out the results obtained
          print ("-----	ELEMENT DETAILS	-----")
          print("\n\nName: " + str(result["name"]))
          print("Atomic number: " + str(result["number"]))
          print("Row: " + str(result["row"]))
          print("Column: " + str(result["column"]))

      # if user input value is '2' then the below code is executed..  
      elif user_input == "2":

        # getting the property to search by
          prop = input('Enter the property name: (name, number, row, column)\n')

          # printing the based on property chosen
        for i in periodic_table_ele:    
              print("The " + str(prop) + " of " + str(i) + " is " + str(periodic_table_ele[i][prop]))

      # if user input value is '3' then the below code is executed..    
      elif user_input == "3":

        # getting user input for new element entry
          abbR = input("Enter the element's abbreviated name: ")
          namE = input("Enter the element's name: ")
          no = input("Enter the element's atomic no: ")
          row = input("Enter the element's row no: ")
          colUmn = input("Enter the new element's column no: ")
          periodic_table_ele[abbR] = {"name": namE, "number": no, "row": row, "column": colUmn}

      # if user input value is '4' then the below code is executed..      
      elif user_input == "4":

          # getting user input for updated element entry
          symbol=input("Enter the symbol of the element to make chnages:")
          while(True):
          attribute=input("Which attribute do you want to change - 'name', 'number', 'row' or 'column'\nIf you don't wish to change anything enter 'EXIT'\n")
          if attribute=="name":
            periodic_table_ele[symbol][attribute]=input("Enter new name:  ")
          elif attribute=="number":
            periodic_table_ele[symbol][attribute]=input("Enter new atomic number: ")
          elif attribute=="row":
            periodic_table_ele[symbol][attribute]=input("Enter new row no:  ")
          elif attribute== "column":
            periodic_table_ele[symbol][attribute]=input("Enter new column no: ")
          elif attribute=="EXIT":
              break
          print("Attributes for the element "+symbol+" are changed and is as follows:",periodic_table_ele[symbol])

      # if user input value is '5' then the below code is executed..      
      elif user_input == "5":

        #exporting dict to json file
        with open("dict.json", "w") as op_file:
          json.dump(periodic_table_ele, op_file)
        print ('Successfully exported dictionary to Json File!!')

      # if user input value is '6' then the below code is executed..      
      elif user_input == "6":

        # Opening JSON file
      file = open('dict.json')

      # returning JSON object as a dictionary
      data = json.load(file)

      # Iterating through the json file
          for n, values in data.items():
              print(f"------------\n{n}\n------------")
              for k, v in values.items():
                  print(k, v)

      # Closing file
      file.close()

    # if user input value is '7' then the below code is executed.. 
      elif user_input == "7":

        print ('\n-----	BYE BYE... -----\n\n')

        # setting the flag value to 0 and exiting from program
          flAg = False
          break

      else:
        print ('Enter valid choice!!')
        continue
``` 
## Output
```
   ----------	PERIODIC TABLE OPERATIONS	----------

  1. Search the element by symbol
  2. Search by a property (name, number, row, column) and see the values for that property for all the elements in the table
  3. Enter a new element manually (type the information for each property) 
  4. Change the properties of an element (by symbol)
  5. Export periodic table as a JSON file 
  6. Load periodic table from JSON file
  7. Exit the program 
  1
  Enter the element's abbreviation: He
  -----	ELEMENT DETAILS	-----


  Name: Helium
  Atomic number: 2
  Row: 1
  Column: 18


   ----------	PERIODIC TABLE OPERATIONS	----------

  1. Search the element by symbol
  2. Search by a property (name, number, row, column) and see the values for that property for all the elements in the table
  3. Enter a new element manually (type the information for each property) 
  4. Change the properties of an element (by symbol)
  5. Export periodic table as a JSON file 
  6. Load periodic table from JSON file
  7. Exit the program 
  3
  Enter the element's abbreviated name: Shr
  Enter the element's name: Shreya
  Enter the element's atomic no: 680
  Enter the element's row no: 3
  Enter the new element's column no: 6


   ----------	PERIODIC TABLE OPERATIONS	----------

  1. Search the element by symbol
  2. Search by a property (name, number, row, column) and see the values for that property for all the elements in the table
  3. Enter a new element manually (type the information for each property) 
  4. Change the properties of an element (by symbol)
  5. Export periodic table as a JSON file 
  6. Load periodic table from JSON file
  7. Exit the program 
  4
  Enter the symbol of the element to make chnages:Shr
  Which attribute do you want to change - 'Name', 'number', 'row' or 'column'
  If you don't wish to change anything enter 'EXIT'number
  Enter new atomic number: 730
  Attributes for the element Shr are changed and is as follows: {'name': 'Shreya', 'number': '730', 'row': '3', 'column': '6'}
  Which attribute do you want to change - 'Name', 'number', 'row' or 'column'
  If you don't wish to change anything enter 'EXIT'EXIT


   ----------	PERIODIC TABLE OPERATIONS	----------

  1. Search the element by symbol
  2. Search by a property (name, number, row, column) and see the values for that property for all the elements in the table
  3. Enter a new element manually (type the information for each property) 
  4. Change the properties of an element (by symbol)
  5. Export periodic table as a JSON file 
  6. Load periodic table from JSON file
  7. Exit the program 
  2
  Enter the property name: (name, number, row, column)
  row
  The row of H is 1
  The row of He is 1
  The row of Li is 2
  The row of Be is 2
  The row of B is 2
  The row of C is 2
  The row of N is 2
  The row of O is 2
  The row of F is 2
  The row of Ne is 2
  The row of Na is 3
  The row of Mg is 3
  The row of Al is 3
  The row of Si is 3
  The row of P is 3
  The row of S is 3
  The row of Cl is 3
  The row of Ar is 3
  The row of K is 4
  The row of Ca is 4
  The row of Sc is 4
  The row of Ti is 4
  The row of V is 4
  The row of Cr is 4
  The row of Mn is 4
  The row of Fe is 4
  The row of Co is 4
  The row of Ni is 4
  The row of Cu is 4
  The row of Zn is 4
  The row of Ga is 4
  The row of Ge is 4
  The row of As is 4
  The row of Se is 4
  The row of Br is 4
  The row of Kr is 4
  The row of Rb is 5
  The row of Sr is 5
  The row of Y is 5
  The row of Zr is 5
  The row of Nb is 5
  The row of Mo is 5
  The row of Tc is 5
  The row of Ru is 5
  The row of Rh is 5
  The row of Pd is 5
  The row of Ag is 5
  The row of Cd is 5
  The row of In is 5
  The row of Sn is 5
  The row of Sb is 5
  The row of Te is 5
  The row of I is 5
  The row of Xe is 5
  The row of Cs is 6
  The row of Ba is 6
  The row of La is 8
  The row of Ce is 8
  The row of Pr is 8
  The row of Nd is 8
  The row of Pm is 8
  The row of Sm is 8
  The row of Eu is 8
  The row of Gd is 8
  The row of Tb is 8
  The row of Dy is 8
  The row of Ho is 8
  The row of Er is 8
  The row of Tm is 8
  The row of Yb is 8
  The row of Lu is 8
  The row of Hf is 6
  The row of Ta is 6
  The row of W is 6
  The row of Re is 6
  The row of Os is 6
  The row of Ir is 6
  The row of Pt is 6
  The row of Au is 6
  The row of Hg is 6
  The row of Tl is 6
  The row of Pb is 6
  The row of Bi is 6
  The row of Po is 6
  The row of At is 6
  The row of Rn is 6
  The row of Fr is 7
  The row of Ra is 7
  The row of Ac is 9
  The row of Th is 9
  The row of Pa is 9
  The row of U is 9
  The row of Np is 9
  The row of Pu is 9
  The row of Am is 9
  The row of Cm is 9
  The row of Bk is 9
  The row of Cf is 9
  The row of Es is 9
  The row of Fm is 9
  The row of Md is 9
  The row of No is 9
  The row of Lr is 9
  The row of Rf is 7
  The row of Db is 7
  The row of Sg is 7
  The row of Bh is 7
  The row of Hs is 7
  The row of Mt is 7
  The row of Ds is 7
  The row of Rg is 7
  The row of Cn is 7
  The row of Uut is 7
  The row of Uuq is 7
  The row of Uup is 7
  The row of Uuh is 7
  The row of Uus is 7
  The row of Uuo is 7
  The row of Shr is 3


   ----------	PERIODIC TABLE OPERATIONS	----------

  1. Search the element by symbol
  2. Search by a property (name, number, row, column) and see the values for that property for all the elements in the table
  3. Enter a new element manually (type the information for each property) 
  4. Change the properties of an element (by symbol)
  5. Export periodic table as a JSON file 
  6. Load periodic table from JSON file
  7. Exit the program 
  5
  Successfully exported dictionary to Json File!!


   ----------	PERIODIC TABLE OPERATIONS	----------

  1. Search the element by symbol
  2. Search by a property (name, number, row, column) and see the values for that property for all the elements in the table
  3. Enter a new element manually (type the information for each property) 
  4. Change the properties of an element (by symbol)
  5. Export periodic table as a JSON file 
  6. Load periodic table from JSON file
  7. Exit the program 
  6
  ------------
  H
  ------------
  row 1
  column 1
  number 1
  name Hydrogen
  ------------
  He
  ------------
  row 1
  column 18
  number 2
  name Helium
  ------------
  Li
  ------------
  row 2
  column 1
  number 3
  name Lithium
  ------------
  Be
  ------------
  row 2
  column 2
  number 4
  name Beryllium
  ------------
  B
  ------------
  row 2
  column 13
  number 5
  name Boron
  ------------
  C
  ------------
  row 2
  column 14
  number 6
  name Carbon
  ------------
  N
  ------------
  row 2
  column 15
  number 7
  name Nitrogen
  ------------
  O
  ------------
  row 2
  column 16
  number 8
  name Oxygen
  ------------
  F
  ------------
  row 2
  column 17
  number 9
  name Fluorine
  ------------
  Ne
  ------------
  row 2
  column 18
  number 10
  name Neon
  ------------
  Na
  ------------
  row 3
  column 1
  number 11
  name Sodium
  ------------
  Mg
  ------------
  row 3
  column 2
  number 12
  name Magnesium
  ------------
  Al
  ------------
  row 3
  column 13
  number 13
  name Aluminum
  ------------
  Si
  ------------
  row 3
  column 14
  number 14
  name Silicon
  ------------
  P
  ------------
  row 3
  column 15
  number 15
  name Phosphorus
  ------------
  S
  ------------
  row 3
  column 16
  number 16
  name Sulfur
  ------------
  Cl
  ------------
  row 3
  column 17
  number 17
  name Chlorine
  ------------
  Ar
  ------------
  row 3
  column 18
  number 18
  name Argon
  ------------
  K
  ------------
  row 4
  column 1
  number 19
  name Potassium
  ------------
  Ca
  ------------
  row 4
  column 2
  number 20
  name Calcium
  ------------
  Sc
  ------------
  row 4
  column 3
  number 21
  name Scandium
  ------------
  Ti
  ------------
  row 4
  column 4
  number 22
  name Titanium
  ------------
  V
  ------------
  row 4
  column 5
  number 23
  name Vanadium
  ------------
  Cr
  ------------
  row 4
  column 6
  number 24
  name Chromium
  ------------
  Mn
  ------------
  row 4
  column 7
  number 25
  name Manganese
  ------------
  Fe
  ------------
  row 4
  column 8
  number 26
  name Iron
  ------------
  Co
  ------------
  row 4
  column 9
  number 27
  name Cobalt
  ------------
  Ni
  ------------
  row 4
  column 10
  number 28
  name Nickel
  ------------
  Cu
  ------------
  row 4
  column 11
  number 29
  name Copper
  ------------
  Zn
  ------------
  row 4
  column 12
  number 30
  name Zinc
  ------------
  Ga
  ------------
  row 4
  column 13
  number 31
  name Gallium
  ------------
  Ge
  ------------
  row 4
  column 14
  number 32
  name Germanium
  ------------
  As
  ------------
  row 4
  column 15
  number 33
  name Arsenic
  ------------
  Se
  ------------
  row 4
  column 16
  number 34
  name Selenium
  ------------
  Br
  ------------
  row 4
  column 17
  number 35
  name Bromine
  ------------
  Kr
  ------------
  row 4
  column 18
  number 36
  name Krypton
  ------------
  Rb
  ------------
  row 5
  column 1
  number 37
  name Rubidium
  ------------
  Sr
  ------------
  row 5
  column 2
  number 38
  name Strontium
  ------------
  Y
  ------------
  row 5
  column 3
  number 39
  name Yttrium
  ------------
  Zr
  ------------
  row 5
  column 4
  number 40
  name Zirconium
  ------------
  Nb
  ------------
  row 5
  column 5
  number 41
  name Niobium
  ------------
  Mo
  ------------
  row 5
  column 6
  number 42
  name Molybdenum
  ------------
  Tc
  ------------
  row 5
  column 7
  number 43
  name Technetium
  ------------
  Ru
  ------------
  row 5
  column 8
  number 44
  name Ruthenium
  ------------
  Rh
  ------------
  row 5
  column 9
  number 45
  name Rhodium
  ------------
  Pd
  ------------
  row 5
  column 10
  number 46
  name Palladium
  ------------
  Ag
  ------------
  row 5
  column 11
  number 47
  name Silver
  ------------
  Cd
  ------------
  row 5
  column 12
  number 48
  name Cadmium
  ------------
  In
  ------------
  row 5
  column 13
  number 49
  name Indium
  ------------
  Sn
  ------------
  row 5
  column 14
  number 50
  name Tin
  ------------
  Sb
  ------------
  row 5
  column 15
  number 51
  name Antimony
  ------------
  Te
  ------------
  row 5
  column 16
  number 52
  name Tellurium
  ------------
  I
  ------------
  row 5
  column 17
  number 53
  name Iodine
  ------------
  Xe
  ------------
  row 5
  column 18
  number 54
  name Xenon
  ------------
  Cs
  ------------
  row 6
  column 1
  number 55
  name Cesium
  ------------
  Ba
  ------------
  row 6
  column 2
  number 56
  name Barium
  ------------
  La
  ------------
  row 8
  column 3
  number 57
  name Lanthanum
  ------------
  Ce
  ------------
  row 8
  column 4
  number 58
  name Cerium
  ------------
  Pr
  ------------
  row 8
  column 5
  number 59
  name Praseodymium
  ------------
  Nd
  ------------
  row 8
  column 6
  number 60
  name Neodymium
  ------------
  Pm
  ------------
  row 8
  column 7
  number 61
  name Promethium
  ------------
  Sm
  ------------
  row 8
  column 8
  number 62
  name Samarium
  ------------
  Eu
  ------------
  row 8
  column 9
  number 63
  name Europium
  ------------
  Gd
  ------------
  row 8
  column 10
  number 64
  name Gadolinium
  ------------
  Tb
  ------------
  row 8
  column 11
  number 65
  name Terbium
  ------------
  Dy
  ------------
  row 8
  column 12
  number 66
  name Dysprosium
  ------------
  Ho
  ------------
  row 8
  column 13
  number 67
  name Holmium
  ------------
  Er
  ------------
  row 8
  column 14
  number 68
  name Erbium
  ------------
  Tm
  ------------
  row 8
  column 15
  number 69
  name Thulium
  ------------
  Yb
  ------------
  row 8
  column 16
  number 70
  name Ytterbium
  ------------
  Lu
  ------------
  row 8
  column 17
  number 71
  name Lutetium
  ------------
  Hf
  ------------
  row 6
  column 4
  number 72
  name Hafnium
  ------------
  Ta
  ------------
  row 6
  column 5
  number 73
  name Tantalum
  ------------
  W
  ------------
  row 6
  column 6
  number 74
  name Wolfram
  ------------
  Re
  ------------
  row 6
  column 7
  number 75
  name Rhenium
  ------------
  Os
  ------------
  row 6
  column 8
  number 76
  name Osmium
  ------------
  Ir
  ------------
  row 6
  column 9
  number 77
  name Iridium
  ------------
  Pt
  ------------
  row 6
  column 10
  number 78
  name Platinum
  ------------
  Au
  ------------
  row 6
  column 11
  number 79
  name Gold
  ------------
  Hg
  ------------
  row 6
  column 12
  number 80
  name Mercury
  ------------
  Tl
  ------------
  row 6
  column 13
  number 81
  name Thallium
  ------------
  Pb
  ------------
  row 6
  column 14
  number 82
  name Lead
  ------------
  Bi
  ------------
  row 6
  column 15
  number 83
  name Bismuth
  ------------
  Po
  ------------
  row 6
  column 16
  number 84
  name Polonium
  ------------
  At
  ------------
  row 6
  column 17
  number 85
  name Astatine
  ------------
  Rn
  ------------
  row 6
  column 18
  number 86
  name Radon
  ------------
  Fr
  ------------
  row 7
  column 1
  number 87
  name Francium
  ------------
  Ra
  ------------
  row 7
  column 2
  number 88
  name Radium
  ------------
  Ac
  ------------
  row 9
  column 3
  number 89
  name Actinium
  ------------
  Th
  ------------
  row 9
  column 4
  number 90
  name Thorium
  ------------
  Pa
  ------------
  row 9
  column 5
  number 91
  name Protactinium
  ------------
  U
  ------------
  row 9
  column 6
  number 92
  name Uranium
  ------------
  Np
  ------------
  row 9
  column 7
  number 93
  name Neptunium
  ------------
  Pu
  ------------
  row 9
  column 8
  number 94
  name Plutonium
  ------------
  Am
  ------------
  row 9
  column 9
  number 95
  name Americium
  ------------
  Cm
  ------------
  row 9
  column 10
  number 96
  name Curium
  ------------
  Bk
  ------------
  row 9
  column 11
  number 97
  name Berkelium
  ------------
  Cf
  ------------
  row 9
  column 12
  number 98
  name Californium
  ------------
  Es
  ------------
  row 9
  column 13
  number 99
  name Einsteinium
  ------------
  Fm
  ------------
  row 9
  column 14
  number 100
  name Fermium
  ------------
  Md
  ------------
  row 9
  column 15
  number 101
  name Mendelevium
  ------------
  No
  ------------
  row 9
  column 16
  number 102
  name Nobelium
  ------------
  Lr
  ------------
  row 9
  column 17
  number 103
  name Lawrencium
  ------------
  Rf
  ------------
  row 7
  column 4
  number 104
  name Rutherfordium
  ------------
  Db
  ------------
  row 7
  column 5
  number 105
  name Dubnium
  ------------
  Sg
  ------------
  row 7
  column 6
  number 106
  name Seaborgium
  ------------
  Bh
  ------------
  row 7
  column 7
  number 107
  name Bohrium
  ------------
  Hs
  ------------
  row 7
  column 8
  number 108
  name Hassium
  ------------
  Mt
  ------------
  row 7
  column 9
  number 109
  name Meitnerium
  ------------
  Ds
  ------------
  row 7
  column 10
  number 110
  name Darmstadtium
  ------------
  Rg
  ------------
  row 7
  column 11
  number 111
  name Roentgenium
  ------------
  Cn
  ------------
  row 7
  column 12
  number 112
  name Copernicium
  ------------
  Uut
  ------------
  row 7
  column 13
  number 113
  name Ununtrium
  ------------
  Uuq
  ------------
  row 7
  column 14
  number 114
  name Ununquadium
  ------------
  Uup
  ------------
  row 7
  column 15
  number 115
  name Ununpentium
  ------------
  Uuh
  ------------
  row 7
  column 16
  number 116
  name Ununhexium
  ------------
  Uus
  ------------
  row 7
  column 17
  number 117
  name Ununseptium
  ------------
  Uuo
  ------------
  row 7
  column 18
  number 118
  name Ununoctium
  ------------
  Shr
  ------------
  name Shreya
  number 730
  row 3
  column 6


   ----------	PERIODIC TABLE OPERATIONS	----------

  1. Search the element by symbol
  2. Search by a property (name, number, row, column) and see the values for that property for all the elements in the table
  3. Enter a new element manually (type the information for each property) 
  4. Change the properties of an element (by symbol)
  5. Export periodic table as a JSON file 
  6. Load periodic table from JSON file
  7. Exit the program 
  9
  Enter valid choice!!


   ----------	PERIODIC TABLE OPERATIONS	----------

  1. Search the element by symbol
  2. Search by a property (name, number, row, column) and see the values for that property for all the elements in the table
  3. Enter a new element manually (type the information for each property) 
  4. Change the properties of an element (by symbol)
  5. Export periodic table as a JSON file 
  6. Load periodic table from JSON file
  7. Exit the program 
  7

  -----	BYE BYE... -----
```
