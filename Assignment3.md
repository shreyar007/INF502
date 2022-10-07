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
          abbr = input('Enter the abbreviation of the element to change: ')
          name = input('Enter the name of the element to change: ')
          value = input('Enter the updated value for ' + name + "-- ")
          periodic_table_ele[abbr][name] = value

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
  Enter the element's atomic no: 600
  Enter the element's row no: 2
  Enter the new element's column no: 5


   ----------	PERIODIC TABLE OPERATIONS	----------

  1. Search the element by symbol
  2. Search by a property (name, number, row, column) and see the values for that property for all the elements in the table
  3. Enter a new element manually (type the information for each property) 
  4. Change the properties of an element (by symbol)
  5. Export periodic table as a JSON file 
  6. Load periodic table from JSON file
  7. Exit the program 
  4
  Enter the abbreviation of the element to change: Shr
  Enter the name of the element to change: Shreya
  Enter the updated value for Shreya-- 560


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
  name
  The name of H is Hydrogen
  The name of He is Helium
  The name of Li is Lithium
  The name of Be is Beryllium
  The name of B is Boron
  The name of C is Carbon
  The name of N is Nitrogen
  The name of O is Oxygen
  The name of F is Fluorine
  The name of Ne is Neon
  The name of Na is Sodium
  The name of Mg is Magnesium
  The name of Al is Aluminum
  The name of Si is Silicon
  The name of P is Phosphorus
  The name of S is Sulfur
  The name of Cl is Chlorine
  The name of Ar is Argon
  The name of K is Potassium
  The name of Ca is Calcium
  The name of Sc is Scandium
  The name of Ti is Titanium
  The name of V is Vanadium
  The name of Cr is Chromium
  The name of Mn is Manganese
  The name of Fe is Iron
  The name of Co is Cobalt
  The name of Ni is Nickel
  The name of Cu is Copper
  The name of Zn is Zinc
  The name of Ga is Gallium
  The name of Ge is Germanium
  The name of As is Arsenic
  The name of Se is Selenium
  The name of Br is Bromine
  The name of Kr is Krypton
  The name of Rb is Rubidium
  The name of Sr is Strontium
  The name of Y is Yttrium
  The name of Zr is Zirconium
  The name of Nb is Niobium
  The name of Mo is Molybdenum
  The name of Tc is Technetium
  The name of Ru is Ruthenium
  The name of Rh is Rhodium
  The name of Pd is Palladium
  The name of Ag is Silver
  The name of Cd is Cadmium
  The name of In is Indium
  The name of Sn is Tin
  The name of Sb is Antimony
  The name of Te is Tellurium
  The name of I is Iodine
  The name of Xe is Xenon
  The name of Cs is Cesium
  The name of Ba is Barium
  The name of La is Lanthanum
  The name of Ce is Cerium
  The name of Pr is Praseodymium
  The name of Nd is Neodymium
  The name of Pm is Promethium
  The name of Sm is Samarium
  The name of Eu is Europium
  The name of Gd is Gadolinium
  The name of Tb is Terbium
  The name of Dy is Dysprosium
  The name of Ho is Holmium
  The name of Er is Erbium
  The name of Tm is Thulium
  The name of Yb is Ytterbium
  The name of Lu is Lutetium
  The name of Hf is Hafnium
  The name of Ta is Tantalum
  The name of W is Wolfram
  The name of Re is Rhenium
  The name of Os is Osmium
  The name of Ir is Iridium
  The name of Pt is Platinum
  The name of Au is Gold
  The name of Hg is Mercury
  The name of Tl is Thallium
  The name of Pb is Lead
  The name of Bi is Bismuth
  The name of Po is Polonium
  The name of At is Astatine
  The name of Rn is Radon
  The name of Fr is Francium
  The name of Ra is Radium
  The name of Ac is Actinium
  The name of Th is Thorium
  The name of Pa is Protactinium
  The name of U is Uranium
  The name of Np is Neptunium
  The name of Pu is Plutonium
  The name of Am is Americium
  The name of Cm is Curium
  The name of Bk is Berkelium
  The name of Cf is Californium
  The name of Es is Einsteinium
  The name of Fm is Fermium
  The name of Md is Mendelevium
  The name of No is Nobelium
  The name of Lr is Lawrencium
  The name of Rf is Rutherfordium
  The name of Db is Dubnium
  The name of Sg is Seaborgium
  The name of Bh is Bohrium
  The name of Hs is Hassium
  The name of Mt is Meitnerium
  The name of Ds is Darmstadtium
  The name of Rg is Roentgenium
  The name of Cn is Copernicium
  The name of Uut is Ununtrium
  The name of Uuq is Ununquadium
  The name of Uup is Ununpentium
  The name of Uuh is Ununhexium
  The name of Uus is Ununseptium
  The name of Uuo is Ununoctium
  The name of Shr is Shreya


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
  number 600
  row 2
  column 5
  Shreya 560


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
