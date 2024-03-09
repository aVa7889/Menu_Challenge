
"Output (the output reads better in edit mode)"

(base) avalee@Avas-MacBook-Air Menu_Challenge % python3 "Menu_Challenge.py"

Welcome to the variety food truck.
From which menu would you like to order? 
1: Snacks
2: Meals
3: Drinks
4: Dessert
------------------------------------------
Type menu number to view or q to quit: 1
You selected Snacks
------------------------------------------
What Snacks item would you like to order?
Item # | Item name                | Price
-------|--------------------------|-------
1      | Cookie                   | $0.99
2      | Banana                   | $0.69
3      | Apple                    | $0.49
4      | Granola bar              | $1.99
Enter your choices in Snacks: 2
------------------------------------------
How many would you like?: 3
Would you like to keep ordering? (Y)es or (N)o y
------------------------------------------
This is what we are preparing for you.

Item name                 | Price  | Quantity
--------------------------|--------|----------
Banana                    | $0.69  |   3
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
From which menu would you like to order? 
1: Snacks
2: Meals
3: Drinks
4: Dessert
------------------------------------------
Type menu number to view or q to quit: 2
You selected Meals
------------------------------------------
What Meals item would you like to order?
Item # | Item name                | Price
-------|--------------------------|-------
1      | Burrito                  | $4.49
2      | Teriyaki Chicken         | $9.99
3      | Sushi                    | $7.49
4      | Pad Thai                 | $6.99
5      | Pizza - Cheese           | $8.99
6      | Pizza - Pepperoni        | $10.99
7      | Pizza - Vegetarian       | $9.99
8      | Burger - Chicken         | $7.49
9      | Burger - Beef            | $8.49
Enter your choices in Meals: 3
------------------------------------------
How many would you like?: 4
Would you like to keep ordering? (Y)es or (N)o y
------------------------------------------
This is what we are preparing for you.

Item name                 | Price  | Quantity
--------------------------|--------|----------
Banana                    | $0.69  |   3
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Sushi                     | $7.49  |   4
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
From which menu would you like to order? 
1: Snacks
2: Meals
3: Drinks
4: Dessert
------------------------------------------
Type menu number to view or q to quit: 3
You selected Drinks
------------------------------------------
What Drinks item would you like to order?
Item # | Item name                | Price
-------|--------------------------|-------
1      | Soda - Small             | $1.99
2      | Soda - Medium            | $2.49
3      | Soda - Large             | $2.99
4      | Tea - Green              | $2.49
5      | Tea - Thai iced          | $3.99
6      | Tea - Irish breakfast    | $2.49
7      | Coffee - Espresso        | $2.99
8      | Coffee - Flat white      | $2.99
9      | Coffee - Iced            | $3.49
Enter your choices in Drinks: 4
------------------------------------------
How many would you like?: 5
Would you like to keep ordering? (Y)es or (N)o n
Thank you for your order.
------------------------------------------
This is what we are preparing for you.

Item name                 | Price  | Quantity
--------------------------|--------|----------
Banana                    | $0.69  |   3
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Sushi                     | $7.49  |   4
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Tea - Green               | $2.49  |   5
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Total cost:  $44.48

(base) avalee@Avas-MacBook-Air Menu_Challenge % 




# Menu_Challenge
menu = {
    "Snacks": {
        "Cookie": .99,
        "Banana": .69,
        "Apple": .49,
        "Granola bar": 1.99
    },
    "Meals": {
        "Burrito": 4.49,
        "Teriyaki Chicken": 9.99,
        "Sushi": 7.49,
        "Pad Thai": 6.99,
        "Pizza": {
            "Cheese": 8.99,
            "Pepperoni": 10.99,
            "Vegetarian": 9.99
        },
        "Burger": {
            "Chicken": 7.49,
            "Beef": 8.49
        }
    },
    "Drinks": {
        "Soda": {
            "Small": 1.99,
            "Medium": 2.49,
            "Large": 2.99
        },
        "Tea": {
            "Green": 2.49,
            "Thai iced": 3.99,
            "Irish breakfast": 2.49
        },
        "Coffee": {
            "Espresso": 2.99,
            "Flat white": 2.99,
            "Iced": 3.49
        }
    },
    "Dessert": {
        "Chocolate lava cake": 10.99,
        "Cheesecake": {
            "New York": 4.99,
            "Strawberry": 6.49
        },
        "Australian Pavlova": 9.99,
        "Rice pudding": 4.99,
        "Fried banana": 4.49
    }
}

menu_dashes = "-" * 42

# 1. Set up order list. Order list will store a list of dictionaries for
# menu item name, item price, and quantity ordered
order_list = []

# Launch the store and present a greeting to the customer
print("Welcome to the variety food truck.")

# Customers may want to order multiple items, so let's create a continuous
# loop
place_order = True
while place_order:
    # Ask the customer from which menu category they want to order
    print("From which menu would you like to order? ")

    # Create a variable for the menu item number
    i = 1
    # Create a dictionary to store the menu for later retrieval
    menu_items = {}

    # Print the options to choose from menu headings (all the first level
    # dictionary items in menu).
    for key in menu.keys():
        print(f"{i}: {key}")
        # Store the menu category associated with its menu item number
        menu_items[i] = key
        # Add 1 to the menu item number
        i += 1

    print(menu_dashes)
    # Get the customer's input
    menu_category = input("Type menu number to view or q to quit: ")
   
    # Exit the loop if the customer types q
    if menu_category == 'q':
            break
    
    # Check if the customer's input is a number
    if menu_category.isdigit():
        # Check if the customer's input is a valid option
        if int(menu_category) in menu_items.keys():
            # Save the menu category name to a variable
            menu_category_name = menu_items[int(menu_category)]
            # Print out the menu category name they selected
            print(f"You selected {menu_category_name}")
            print(menu_dashes)
            # Print out the menu options from the menu_category_name
            print(f"What {menu_category_name} item would you like to order?")
            i = 1
            menu_items = {}
            print("Item # | Item name                | Price")
            print("-------|--------------------------|-------")
            for key, value in menu[menu_category_name].items():
                # Check if the menu item is a dictionary to handle differently
                if type(value) is dict:
                    for key2, value2 in value.items():
                        num_item_spaces = 24 - len(key + key2) - 3
                        item_spaces = " " * num_item_spaces
                        print(f"{i}      | {key} - {key2}{item_spaces} | ${value2}")
                        menu_items[i] = {
                            "Item name": key + " - " + key2,
                            "Price": value2
                        }
                        i += 1
                else:
                    num_item_spaces = 24 - len(key)
                    item_spaces = " " * num_item_spaces
                    print(f"{i}      | {key}{item_spaces} | ${value}")
                    menu_items[i] = {
                        "Item name": key,
                        "Price": value
                    }
                    i += 1
            # 2. Ask customer to input menu item number
            menu_selection = input(f"Enter your choices in {menu_category_name}: ")
            print(menu_dashes)
            # 3. Check if the customer typed a number
            if menu_selection.isdigit():

                # Convert the menu selection to an integer
                menu_selection = int(menu_selection)
                
                # 4. Check if the menu selection is in the menu items
                if menu_selection in menu_items.keys():
                    # Store the item name as a variable
                        item_name = menu_items[menu_selection]["Item name"]
                        price = menu_items[menu_selection]["Price"]

                    # Ask the customer for the quantity of the menu item
                        quantity = input(f"How many would you like?: ")
                    # Check if the quantity is a number, default to 1 if not
                if quantity.isdigit():
                            quantity = int(quantity)
                else:
                            quantity = 1
                            print("The default value is 1")
                    # Add the item name, price, and quantity to the order list
                order_list.append({
                        "Item name": item_name,
                        "Price" : price,
                        "Quantity" : quantity
        })
                    # Tell the customer that their input isn't valid
            else:
                print("Input was not valid.")
# Tell the customer they didn't select a menu option
        else:
            # Tell the customer they didn't select a menu option
                print(f"It was not a menu option.")
    else:
        # Tell the customer they didn't select a number
        print("You didn't select a number.")
        print(menu_dashes)
    while True:
        # Ask the customer if they would like to order anything else
        keep_ordering = input("Would you like to keep ordering? (Y)es or (N)o ")
        # 5. Check the customer's input
                # Keep ordering
                # Check the customer's input
        match keep_ordering.lower():
                # Customer chose yes
            case 'y':
                # keep ordering
                place_order = True
                # Exit the keep ordering question loop
                break
                # Complete the order

                # Since the customer decided to stop ordering, thank them for
                # their order
            case 'n':
                place_order = False
                print("Thank you for your order.")
                # Exit the keep ordering question loop
                break

                # Tell the customer to try again
            case _:   
                print("I didn't understand your response.  Please try again.")
                place_order = False    
                break  
    print(menu_dashes)

        # Print out the customer's order
    print("This is what we are preparing for you.\n")

        # Uncomment the following line to check the structure of the order
        #print(order)

    print("Item name                 | Price  | Quantity")
    print("--------------------------|--------|----------")

        # 6. Loop through the items in the customer's order
    for final_order in order_list:
        
        # 7. Store the dictionary items as variables
            item_name = final_order["Item name"]
            price = final_order["Price"]
            quantity = final_order["Quantity"]

        # 8. Calculate the number of spaces for formatted printing
            num_item_spaces = 24 - len(item_name)
            num_price_spaces = 6 - len(str(price))

        # 9. Create space strings
            item_spaces = " " * num_item_spaces
            price_spaces = " " * num_price_spaces

        # 10. Print the item name, price, and quantity
            print(f"{item_name}{item_spaces}  | ${price}{price_spaces}|   {quantity}")

        # 11. Calculate the cost of the order using list comprehension
        # Multiply the price by quantity for each item in the order list, then sum()
        # and print the prices.
            print ("~" * 46)
total_cost = sum([order_list[i]["Price"] * order_list[i]["Quantity"] for i in range(len(order_list))])
print(f"Total cost:  ${total_cost:.2f}")
