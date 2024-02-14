# Cash-register-app-draft
takes users input and displays output using a few functions
class Retailitem():
    def __init__(self, description, units, price):
        self.description = description
        self.units = units
        self.price = price

    def __str__(self):
        return f'Retailitem(Description: {self.description}, Units in inventory: {self.units}, Price: {self.price})'

    def get_description(self):
        return self.description
    
    def set_description(self, description):
        self.description = description

    def get_units(self):
        return self.units
    
    def set_units(self, units):
        self.units = units

    def get_price(self):
        return self.price
    
    def set_price(self, price):
        self.price = price


class CashRegister:
    def __init__(self):
        self.item_list = []
        self.total_price = 0
    
    def purchase_item(self, item: Retailitem):
        self.item_list.append(item)
        self.total_price += item.price  

    def get_total(self):
        total_price = sum(item.price for item in self.item_list)
        return total_price
    
    def show_items(self):
        for item in self.item_list:
            print(item)
    
    def clear(self):
        self.item_list = []


def main():
    item1 = Retailitem("Jacket", 12, 59.95)
    item2 = Retailitem("Designer Jeans", 40, 34.95)
    item3 = Retailitem("Shirt", 20, 24.95)
    item4 = Retailitem("Socks", 10, 4.99)
    item5 = Retailitem("Gloves", 100, 2.99)
    item6 = Retailitem("Ski Mask", 10, 500)
    item7 = Retailitem("Gucci flipflops", 32, 69999)

    register = CashRegister()

    while True:
        print("\nSelect an item to add to the cart:")
        print("1. Jacket")
        print("2. Designer Jeans")
        print("3. Shirt")
        print("4. Socks")
        print("5. Gloves")
        print("6. Ski Mask")
        print("7. Gucci Flip flops")
        print("8. Show selected items")
        print("9. Checkout and Exit")
        print("10. Clear Cart")
        choice = input("Enter your choice (1-10): ")

        if choice == '1':
            register.purchase_item(item1)
        elif choice == '2':
            register.purchase_item(item2)
        elif choice == '3':
            register.purchase_item(item3)
        elif choice == '4':
            register.purchase_item(item4)
        elif choice == '5':
            register.purchase_item(item5)
        elif choice == '6':
            register.purchase_item(item6)
        elif choice == '7':
            register.purchase_item(item7)
        elif choice == '8':
            print("\nSelected items:")
            register.show_items()
            total_price = register.get_total()
            print(f"Total Price: ${total_price:.2f}")
        elif choice == '9':
            print("\nCheckout Summary:")
            register.show_items()
            total_price = register.get_total()
            print(f"Total Price: ${total_price:.2f}")
            print("Thank you for shopping! Have a nice day")
            break
        
        elif choice == '10':
            print("Clear cart:")
            register.clear()
            print("Your cart is now empty")
            
        else:
            print("Invalid Choice, Please enter a number from 1-9")


if __name__ == "__main__":
    main()

