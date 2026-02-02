# Create a dictionary describing a person
person = {
    "f_name": "Serena",
    "l_name": "Williams",
    "age": 42,
    "hometown": "Saginaw",
    "current_city": "Palm Beach Gardens",
    "username": "serena_smashes42"
}

# Print the entire dictionary
print(person)

# Print each key individually
print("First name:", person["f_name"])
print("Last name:", person["l_name"])
print("Age:", person["age"])
print("Hometown:", person["hometown"])
print("Current city:", person["current_city"])
print("Username:", person["username"])


# Create a dictionary describing a person
person = {
    "f_name": "Serena",
    "l_name": "Williams",
    "age": 42,
    "hometown": "Saginaw",
    "current_city": "Palm Beach Gardens",
    "username": "serena_smashes42"
}

# Use f-strings to print clean, formatted statements
print(f"This person's first name is {person['f_name']}, last name is {person['l_name']}, "
      f"and their username is {person['username']}.")

print(f"For security reasons, we might ask them for their hometown, which is {person['hometown']}.")


# Create a dictionary of programming definitions
definitions = {
    "python": "A high-level programming language used for general-purpose coding.",
    "variable": "A named storage location that holds a value.",
    "list": "An ordered collection of items stored in a single variable.",
    "method": "A function that belongs to an object and performs an action on that object.",
    "if statement": "A conditional structure that runs code only when a condition is true.",
    "dictionary": "A collection of key-value pairs used to store related data.",
    "function": "A reusable block of code designed to perform a specific task."
}

# Print each word and its meaning with clean formatting
for word, meaning in definitions.items():
    print(f"{word}:\n  {meaning}\n")


# Dictionary of programming definitions
definitions = {
    "python": "A high-level programming language used for general-purpose coding.",
    "variable": "A named storage location that holds a value.",
    "list": "An ordered collection of items stored in a single variable.",
    "method": "A function that belongs to an object and performs an action on that object.",
    "if statement": "A conditional structure that runs code only when a condition is true.",
    "dictionary": "A collection of key-value pairs used to store related data.",
    "function": "A reusable block of code designed to perform a specific task."
}

# Loop through keys and values to print formatted output
for word, meaning in definitions.items():
    print(f"{word}:\n  {meaning}\n")


# Dictionary of South Carolina counties and their county seats
sc_counties = {
    "Anderson": "Anderson",
    "Greenville": "Greenville",
    "Spartanburg": "Spartanburg",
    "Richland": "Columbia",
    "Charleston": "Charleston",
    "Horry": "Conway"
}

# Print each county and its seat
for county, seat in sc_counties.items():
    print(f"{county}: {seat}")


# Dictionary of South Carolina counties and their county seats
sc_counties = {
    "Anderson": "Anderson",
    "Greenville": "Greenville",
    "Spartanburg": "Spartanburg",
    "Richland": "Columbia",
    "Charleston": "Charleston",
    "Horry": "Conway"
}

# List of 10 counties (same 6 + 4 new ones)
county_list = [
    "Anderson", "Greenville", "Spartanburg", "Richland",
    "Charleston", "Horry",
    "Lexington", "Pickens", "York", "Oconee"
]

# Loop through the list and check membership in the dictionary
for county in county_list:
    if county in sc_counties:
        print(f"{county} is in our dictionary, and the capital/seat is {sc_counties[county]}.")
    else:
        print(f"{county} is not in our dictionary. We will add this county shortly. Thanks!")


        # Five South Carolina county dictionaries, each with 5 cities and populations
anderson_county = {
    "anderson": 29000,
    "belton": 4500,
    "honea path": 3800,
    "ivory": 1200,
    "pendleton": 3200
}

greenville_county = {
    "greenville": 72000,
    "mauldin": 25000,
    "simpsonville": 25000,
    "taylors": 23000,
    "greer": 35000
}

spartanburg_county = {
    "spartanburg": 38000,
    "boiling springs": 10000,
    "chesnee": 900,
    "woodruff": 4300,
    "duncan": 3500
}

richland_county = {
    "columbia": 136000,
    "irmo": 12000,
    "forest acres": 10000,
    "eastover": 800,
    "arcadia lakes": 900
}

charleston_county = {
    "charleston": 150000,
    "mount pleasant": 94000,
    "north charleston": 115000,
    "isle of palms": 4300,
    "sullivans island": 2000
}

# List containing all county dictionaries
county_list = [
    anderson_county,
    greenville_county,
    spartanburg_county,
    richland_county,
    charleston_county
]

# Loop through each dictionary and print formatted statements
for county in county_list:
    for city, population in county.items():
        print(f"In {city.title()}, the current population is {population}.")


# Dictionary of SC counties with their three largest cities
sc_counties = {
    "Anderson": ["Anderson", "Belton", "Powdersville"],
    "Greenville": ["Greenville", "Greer", "Mauldin"],
    "Spartanburg": ["Spartanburg", "Boiling Springs", "Duncan"],
    "Richland": ["Columbia", "Forest Acres", "Irmo"],
    "Charleston": ["Charleston", "North Charleston", "Mount Pleasant"]
}

# Loop through the dictionary and print formatted output
for county, cities in sc_counties.items():
    print(f"In {county}, the largest cities are {cities[0]}, {cities[1]}, and {cities[2]}.")


name = input("What is your name? ")
print(f"Welcome to Anderson University, {name}!")


# Ask the user how much money they have
money = float(input("How much money do you have? $"))

# Processor prices (realistic estimates)
i3_price = 120
i5_price = 200
i7_price = 320
i9_price = 500

# Determine what they can afford
if money >= i9_price:
    print("You can afford an Intel i3, i5, i7, or even an i9 processor!")
elif money >= i7_price:
    print("You can afford an Intel i3, i5, or i7 processor.")
elif money >= i5_price:
    print("You can afford an Intel i3 or i5 processor.")
elif money >= i3_price:
    print("You can afford an Intel i3 processor.")
else:
    print("You cannot afford a processor at this time. Save up a little more!")


    # This program keeps running until the user types "stop"

while True:
    user_input = input("Enter an integer (or type 'stop' to end): ")

    # Check if the user wants to end the program
    if user_input.lower() == "stop":
        print("Program ended. Goodbye!")
        break

    # Convert input to an integer and check even/odd
    number = int(user_input)

    if number % 2 == 0:
        print(f"{number} is even.\n")
    else:
        print(f"{number} is odd.\n")


# Active variable to control the loop
active = True

# Loop runs as long as 'active' is True
while active:
    user_input = input("Type anything (or 'quit' to stop): ")

    # Break statement to exit immediately when user types 'quit'
    if user_input.lower() == "quit":
        print("Exiting program. Goodbye!")
        break

    # Conditional test inside the loop
    if user_input == "":
        print("You entered nothing. Try again.\n")
    else:
        print(f"You typed: {user_input}\n")

    # Conditional test in the while statement (example):
    # If the user types 'stop', the loop ends by changing the active variable
    if user_input.lower() == "stop":
        active = False
        print("Loop ended using the active variable method.")


# Valid Ubuntu flavours
valid_flavours = [
    "ubuntu", "kubuntu", "lubuntu", "xubuntu",
    "ubuntu mate", "ubuntu budgie", "ubuntu studio",
    "ubuntu kylin", "edubuntu"
]

# Dictionary to store username : favourite flavour
poll_results = {}

# Poll loop
while True:
    username = input("Enter your username (or type 'quit' to stop): ")

    if username.lower() == "quit":
        print("Polling ended.")
        break

    flavour = input("What is your favorite Ubuntu flavour? ").lower()

    if flavour in valid_flavours:
        poll_results[username] = flavour
        print(f"Thanks {username}, your favourite flavour '{flavour}' has been recorded.\n")
    else:
        print("\nYou entered a non-legitimate Ubuntu flavour.")
        print("Valid options are:")
        for f in valid_flavours:
            print(f" - {f.title()}")
        print()  # blank line for spacing

# Final results (optional)
print("Poll results:", poll_results)
