class Restaurant:
    def __init__(self, restaurant_name, cuisine_type):
        self.restaurant_name = restaurant_name
        self.cuisine_type = cuisine_type

    def describe_restaurant(self):
        print(f"{self.restaurant_name} serves {self.cuisine_type} cuisine.")

    def open_restaurant(self):
        print(f"{self.restaurant_name} is now open!")

restaurant = Restaurant("Will’s Grill", "American")
print(restaurant.restaurant_name)
print(restaurant.cuisine_type)
restaurant.describe_restaurant()
restaurant.open_restaurant()


class Restaurant:
    def __init__(self, restaurant_name, cuisine_type):
        self.restaurant_name = restaurant_name
        self.cuisine_type = cuisine_type

    def describe_restaurant(self):
        print(f"{self.restaurant_name} serves {self.cuisine_type} cuisine.")

    def open_restaurant(self):
        print(f"{self.restaurant_name} is now open!")

restaurant = Restaurant("Will’s Grill", "American")
print(restaurant.restaurant_name)
print(restaurant.cuisine_type)
restaurant.describe_restaurant()
restaurant.open_restaurant()


restaurant1 = Restaurant("Mama Mia", "Italian")
restaurant2 = Restaurant("Dragon House", "Chinese")
restaurant3 = Restaurant("Taco Spot", "Mexican")

restaurant1.describe_restaurant()
restaurant2.describe_restaurant()
restaurant3.describe_restaurant()


class User:
    def __init__(self, first_name, last_name, age, email):
        self.first_name = first_name
        self.last_name = last_name
        self.age = age
        self.email = email

    def describe_user(self):
        print(f"User: {self.first_name} {self.last_name}, Age: {self.age}, Email: {self.email}")

    def greet_user(self):
        print(f"Welcome back, {self.first_name}!")

user1 = User("Will", "Wright", 20, "will@example.com")
user2 = User("Sarah", "Jones", 22, "sj@example.com")

user1.describe_user()
user1.greet_user()
user2.describe_user()
user2.greet_user()


class Restaurant:
    def __init__(self, restaurant_name, cuisine_type):
        self.restaurant_name = restaurant_name
        self.cuisine_type = cuisine_type
        self.number_served = 0

    def describe_restaurant(self):
        print(f"{self.restaurant_name} serves {self.cuisine_type} cuisine.")

    def open_restaurant(self):
        print(f"{self.restaurant_name} is now open!")

restaurant = Restaurant("Will’s Grill", "American")
print(restaurant.number_served)

restaurant.number_served = 25
print(restaurant.number_served)

class User:
    def __init__(self, first_name, last_name):
        self.first_name = first_name
        self.last_name = last_name
        self.login_attempts = 0

    def increment_login_attempts(self):
        self.login_attempts += 1

    def reset_login_attempts(self):
        self.login_attempts = 0

user = User("Will", "Wright")

for _ in range(5):
    user.increment_login_attempts()

print(user.login_attempts)

user.reset_login_attempts()
print(user.login_attempts)


class IceCreamStand(Restaurant):
    def __init__(self, restaurant_name, cuisine_type, flavors):
        super().__init__(restaurant_name, cuisine_type)
        self.flavors = flavors

    def show_flavors(self):
        print("Available flavors:")
        for flavor in self.flavors:
            print(f"- {flavor}")

stand = IceCreamStand("Will’s Ice Cream", "Dessert", ["Vanilla", "Chocolate", "Strawberry"])
stand.show_flavors()


class Admin(User):
    def __init__(self, first_name, last_name):
        super().__init__(first_name, last_name)
        self.privileges = ["can add post", "can delete post", "can ban user"]

    def show_privileges(self):
        print("Privileges:")
        for p in self.privileges:
            print(f"- {p}")

admin = Admin("Will", "Wright")
admin.show_privileges()


class Battery:
    def __init__(self, size=40):
        self.size = size

    def get_range(self):
        if self.size == 40:
            print("Range: 150 miles")
        elif self.size == 65:
            print("Range: 225 miles")

    def upgrade_battery(self):
        if self.size < 65:
            self.size = 65

class ElectricCar:
    def __init__(self):
        self.battery = Battery()

car = ElectricCar()
car.battery.get_range()

car.battery.upgrade_battery()
car.battery.get_range()

class Restaurant:
    def __init__(self, name, cuisine):
        self.name = name
        self.cuisine = cuisine

    def describe_restaurant(self):
        print(f"{self.name} serves {self.cuisine}.")

from restaurant import Restaurant

r = Restaurant("Will’s Grill", "American")
r.describe_restaurant()


class User:
    def __init__(self, first, last):
        self.first = first
        self.last = last

class Privileges:
    def __init__(self, privileges):
        self.privileges = privileges

    def show_privileges(self):
        for p in self.privileges:
            print(f"- {p}")

class Admin(User):
    def __init__(self, first, last):
        super().__init__(first, last)
        self.privileges = Privileges(
            ["can add post", "can delete post", "can ban user"]
        )
from users import Admin

admin = Admin("Will", "Wright")
admin.privileges.show_privileges()


class User:
    def __init__(self, first, last):
        self.first = first
        self.last = last

class Privileges:
    def __init__(self, privileges):
        self.privileges = privileges

    def show_privileges(self):
        for p in self.privileges:
            print(f"- {p}")

class Admin:
    def __init__(self, first, last):
        self.user = f"{first} {last}"
        self.privileges = Privileges(
            ["can add post", "can delete post", "can ban user"]
        )


from admin_privileges import Admin

admin = Admin("Will", "Wright")
admin.privileges.show_privileges()


import random

class Die:
    def __init__(self, sides=6):
        self.sides = sides

    def roll_die(self):
        print(random.randint(1, self.sides))

die6 = Die()
for _ in range(10):
    die6.roll_die()

die10 = Die(10)
die20 = Die(20)

for _ in range(10):
    die10.roll_die()

for _ in range(10):
    die20.roll_die()


import random

items = [1,2,3,4,5,6,7,8,9,10,'A','B','C','D','E']
winners = random.sample(items, 4)
print(f"Winning ticket: {winners}")


import random

items = [1,2,3,4,5,6,7,8,9,10,'A','B','C','D','E']
my_ticket = [1, 'A', 5, 'C']

count = 0
while True:
    count += 1
    draw = random.sample(items, 4)
    if draw == my_ticket:
        break

print(f"It took {count} tries to win.")

text = [
    "In Python you can work with files.\n",
    "In Python you can write clean, readable code.\n",
    "In Python you can automate boring tasks.\n",
]

with open("learning_python.txt", "w") as file:
    file.writelines(text)

# read entire file
with open("learning_python.txt") as file:
    contents = file.read()
    print("=== full read ===")
    print(contents)

# read line by line using a list
with open("learning_python.txt") as file:
    lines = file.readlines()

print("=== line by line ===")
for line in lines:
    print(line.rstrip())

    with open("learning_python.txt") as file:
    contents = file.read()

for line in contents.splitlines():
    print(line)


    name = input("What is your name? ")

with open("guest.txt", "w") as file:
    file.write(name)

    with open("guest_book.txt", "a") as file:
    while True:
        name = input("Enter your name (or 'quit' to stop): ")
        if name.lower() == "quit":
            break
        file.write(name + "\n")
        print(f"Welcome, {name}")

        try:
    a = int(input("First number: "))
    b = int(input("Second number: "))
    print(a + b)
except ValueError:
    print("Please enter valid numbers.")

    while True:
    try:
        a = int(input("First number: "))
        b = int(input("Second number: "))
    except ValueError:
        print("Please enter valid numbers.")
    else:
        print(a + b)


filenames = ["cats.txt", "dogs.txt"]

for file in filenames:
    try:
        with open(file) as f:
            print(f.read())
    except FileNotFoundError:
        print(f"{file} is missing.")

        filenames = ["cats.txt", "dogs.txt"]

for file in filenames:
    try:
        with open(file) as f:
            print(f.read())
    except FileNotFoundError:
        pass


import json

num = input("Your favorite number: ")

with open("favorite.json", "w") as file:
    json.dump(num, file)

import json

with open("favorite.json") as file:
    num = json.load(file)

print(f"I know your favorite number! It's {num}.")


import json

filename = "favorite.json"

try:
    with open(filename) as file:
        num = json.load(file)
except FileNotFoundError:
    num = input("Your favorite number: ")
    with open(filename, "w") as file:
        json.dump(num, file)
    print("Got it. I'll remember that.")
else:
    print(f"I know your favorite number! It's {num}.")


import json

info = {
    "name": input("Name: "),
    "age": input("Age: "),
    "city": input("City: ")
}

with open("user.json", "w") as file:
    json.dump(info, file)

with open("user.json") as file:
    data = json.load(file)

print("Stored info:")
for key, value in data.items():
    print(f"{key}: {value}")


import json

filename = "username.json"

def get_new_username():
    username = input("What is your name? ")
    with open(filename, "w") as file:
        json.dump(username, file)
    return username

def greet_user():
    try:
        with open(filename) as file:
            username = json.load(file)
    except FileNotFoundError:
        username = get_new_username()
    else:
        correct = input(f"Are you {username}? (y/n): ")
        if correct.lower() != "y":
            username = get_new_username()

    print(f"Welcome back, {username}!")

greet_user()

def city_country(city, country, population=None):
    if population:
        return f"{city.title()}, {country.title()} - population {population}"
    return f"{city.title()}, {country.title()}"

from city_functions import city_country

def test_city_country():
    result = city_country("santiago", "chile")
    assert result == "Santiago, Chile"


def city_country(city, country, population):
    return f"{city.title()}, {country.title()} - population {population}"
def city_country(city, country, population=None):
    if population:
        return f"{city.title()}, {country.title()} - population {population}"
    return f"{city.title()}, {country.title()}"
from city_functions import city_country

def test_city_country():
    result = city_country("santiago", "chile")
    assert result == "Santiago, Chile"

def test_city_country_population():
    result = city_country("santiago", "chile", 5000000)
    assert result == "Santiago, Chile - population 5000000"
