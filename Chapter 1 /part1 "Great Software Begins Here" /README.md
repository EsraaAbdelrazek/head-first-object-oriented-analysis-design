
## Initial Implementation  

### **Guitar Class**  
The `Guitar` class encapsulates the key attributes of a guitar, such as serial number, price, builder, model, type, back wood, and top wood.  

```python
class Guitar:
    def __init__(self, serial_number, price, builder, model, type, back_wood, top_wood):
        self.serial_number = serial_number
        self.price = price
        self.builder = builder
        self.model = model
        self.type = type
        self.back_wood = back_wood
        self.top_wood = top_wood

    # Getter methods for each attribute
    def get_serial_number(self):
        return self.serial_number
    def get_price(self):
        return self.price
    def get_builder(self):
        return self.builder
    def get_model(self):
        return self.model
    def get_type(self):
        return self.type
    def get_back_wood(self):
        return self.back_wood
    def get_top_wood(self):
        return self.top_wood
```

---

### **Inventory Class**  
The `Inventory` class manages Rick's collection of guitars and provides methods for adding and searching guitars.  

```python
class Inventory:
    def __init__(self):
        self.guitars = []

    def add_guitar(self, serial_number, price, builder, model, type, back_wood, top_wood):
        guitar = Guitar(serial_number, price, builder, model, type, back_wood, top_wood)
        self.guitars.append(guitar)

    def search(self, search_guitar):
        for guitar in self.guitars:
            if (
                (search_guitar.builder == "" or guitar.get_builder() == search_guitar.builder) and
                (search_guitar.model == "" or guitar.get_model() == search_guitar.model) and
                (search_guitar.type == "" or guitar.get_type() == search_guitar.type) and
                (search_guitar.back_wood == "" or guitar.get_back_wood() == search_guitar.back_wood) and
                (search_guitar.top_wood == "" or guitar.get_top_wood() == search_guitar.top_wood)
            ):
                return guitar
        return None
```

---

### **FindGuitarTester**  
Simulates a scenario where Rick uses his system to search for a guitar based on a customer’s preferences.  

```python
def initialize_inventory(inventory):
    inventory.add_guitar("001", 1500.0, "Fender", "Stratocastor", "electric", "Alder", "Alder")
    inventory.add_guitar("002", 1200.0, "Gibson", "Les Paul", "electric", "Mahogany", "Maple")
    inventory.add_guitar("003", 2000.0, "Martin", "D-28", "acoustic", "Rosewood", "Spruce")

def find_guitar_tester():
    inventory = Inventory()
    initialize_inventory(inventory)

    # Guitar Erin is looking for
    what_erin_likes = Guitar("", 0, "Fender", "Stratocastor", "electric", "Alder", "Alder")

    guitar = inventory.search(what_erin_likes)
    if guitar:
        print(f"Erin, you might like this {guitar.get_builder()} {guitar.get_model()} "
              f"{guitar.get_type()} guitar:\n"
              f"{guitar.get_back_wood()} back and sides, "
              f"{guitar.get_top_wood()} top.\n"
              f"You can have it for only ${guitar.get_price()}!")
    else:
        print("Sorry, Erin, we have nothing for you.")

find_guitar_tester()
```

---

## Problems with the Initial Design  
1. **Rigid Search**: Required exact matches for every attribute.  
2. **Poor Scalability**: Adding new guitar attributes required modifying multiple parts of the code.  
3. **Lack of Flexibility**: Could not handle partial matches or advanced customer preferences.  


