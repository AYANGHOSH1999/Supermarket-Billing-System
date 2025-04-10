# Define a sample price list for products (case-insensitive keys)
product_prices = {
    "rice": 50, "wheat flour": 40, "dal": 80, "sugar": 45, "salt": 20,
    "milk": 30, "tea": 150, "coffee": 120, "biscuit": 25, "oil": 150,
    "eggs": 6, "bread": 35, "butter": 55, "paneer": 80, "toothpaste": 45,
    "soap": 30, "shampoo": 120, "detergent": 95, "toilet paper": 25, "sanitizer": 70
}

# Get user name and gender-based greeting
name = input("Please enter your name: ")
gender = input("Please enter your gender (M/F): ")

greeting = "Sir" if gender.lower() == 'm' else "Madam"

print(f"\nWelcome {greeting} to 'Apna Dukan' Supermarket!\n")

# Display available products
print("Available products:")
for item, price in product_prices.items():
    print(f"- {item.title()}: ₹{price}")

# Initialize shopping cart
cart = {}

while True:
    product_input = input("\nEnter the product name: ").strip().lower()
    if product_input not in product_prices:
        print("Sorry, we don't have that product. Please choose from available products.")
        continue

    try:
        quantity = int(input(f"Enter quantity for {product_input.title()}: "))
    except ValueError:
        print("Invalid quantity! Please enter a number.")
        continue

    # Add to cart
    if product_input in cart:
        cart[product_input] += quantity
    else:
        cart[product_input] = quantity

    # Ask user if they want to add more items
    more_items = input("Do you want to add more items? (yes/done): ").strip().lower()
    if more_items == "done":
        break

# Generate the bill
print("\n********** BILL **********")
print(f"Customer Name: {name}")
print(f"Thank you {greeting} for shopping at 'Apna Dukan'!\n")

total_amount = 0
for product, quantity in cart.items():
    price = product_prices[product]
    cost = price * quantity
    total_amount += cost
    print(f"{product.title()}: {quantity} x ₹{price} = ₹{cost}")

print(f"\nTotal Amount Payable: ₹{total_amount}")
print("********** THANK YOU FOR SHOPPING **********")
