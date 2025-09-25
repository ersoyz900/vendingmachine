Vending Machine Program

This Java program simulates a simple vending machine that sells drinks.

Features

Reads available drinks, their quantities, and prices from a file (Prices.txt).

Allows the user to insert coins of various denominations.

Lets the user select a drink to purchase if sufficient funds are inserted.

Returns the remaining balance after the purchase.

Displays error messages for invalid coins or insufficient balance.

How It Works

Reading Prices: The program reads drink data from Prices.txt. Each line should have the format:

DrinkName,Quantity,Price


Example:

Coke,10,$1.25
Pepsi,5,$1.00


Listing Drinks: Shows all available drinks with their prices and quantities.

Inserting Coins: Accepts coins like 1$, 50c, 25c, 10c, 5c, and 1c. Type tamam to finish inserting money.

Selecting Drink: User types the name of the drink they want to buy. If the balance is sufficient, the drink is dispensed and quantity decreased.

Supported Coins

1 Dollar (1$)

50 cents (50c)

25 cents (25c)

10 cents (10c)

5 cents (5c)

1 cent (1c)

Usage

Make sure you have a Prices.txt file in the program directory.

Run the program.

Insert coins until you have enough money.

Select your drink by typing its name.

Enjoy!

Example
--- Available Drinks ---
Coke - $1.25 (10 available)
Pepsi - $1.00 (5 available)

Insert coins ('tamam' to finish):
1$
50c
tamam

Select a drink:
Coke

Coke dispensed. Remaining balance: $0.25


