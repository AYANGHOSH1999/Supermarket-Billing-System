# Define a sample price list for products
product_prices = {
    "Rice": 50, "Wheat Flour": 40, "Dal": 80, "Sugar": 45, "Salt": 20,
    "Milk": 30, "Tea": 150, "Coffee": 120, "Biscuit": 25, "Oil": 150,
}

# Get user name and gender-based greeting
name = input("Please enter your name: ")
gender = input("Please enter your gender (M/F): ")

if gender.lower() == 'm':
    greeting = "Sir"
else:
    greeting = "Madam"

print(f"Welcome {greeting}  'Apna Dukan' Supermarket!\n")

# Initialize shopping cart
cart = {}

while True:
    product_name = input("Enter the product name: ").strip()
    if product_name not in product_prices:
        print("Sorry, we don't have that product. Please choose from available products.")
        continue

    try:
        quantity = int(input(f"Enter quantity for {product_name}: "))
    except ValueError:
        print("Invalid quantity! Please enter a number.")
        continue

    # Add to cart
    if product_name in cart:
        cart[product_name] += quantity
    else:
        cart[product_name] = quantity

    # Ask user if they want to add more items
    more_items = input("Do you want to add more items? (yes/done): ").strip().lower()
    if more_items == "done":
        break

# Generate the bill
print("\n********** BILL **********")
print(f"Customer Name: {name}")
print(f"Welcome {greeting}  'Apna Dukan' Supermarket!\n")
total_amount = 0

for product, quantity in cart.items():
    price = product_prices[product]
    cost = price * quantity
    total_amount += cost
    print(f"{product}: {quantity} x ₹{price} = ₹{cost}")

print(f"\nTotal Amount Payable: ₹{total_amount}")
print("********** THANK YOU FOR SHOPPING **********")
