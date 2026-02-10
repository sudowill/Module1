def make_shirt(size, message):
    print(f"Creating a {size}-sized shirt with the message: '{message}'")

# Call the function using positional arguments
make_shirt("Medium", "Hello World!")

# Call the function using keyword arguments
make_shirt(size="Large", message="Python is Fun")

def make_shirt(size="large", message="I love Python"):
    print(f"Making a {size} shirt with the message: '{message}'")

# Large shirt with default message
make_shirt()

# Medium shirt with default message
make_shirt(size="medium")

# Custom shirt
make_shirt(size="small", message="Keep Grinding!")

def describe_city(city, country="Iceland"):
    print(f"{city} is in {country}.")

# Three calls
describe_city("Reykjavik")
describe_city("Akureyri")
describe_city("Tokyo", "Japan")

def city_country(city, country):
    return f"{city}, {country}"

print(city_country("Santiago", "Chile"))
print(city_country("Tokyo", "Japan"))
print(city_country("Charlotte", "USA"))

def make_album(artist, title, songs=None):
    album = {"artist": artist, "title": title}
    if songs is not None:
        album["songs"] = songs
    return album

# Three albums
print(make_album("Drake", "Views"))
print(make_album("Kendrick Lamar", "DAMN"))
print(make_album("J. Cole", "2014 Forest Hills Drive", songs=13))


def make_album(artist, title, songs=None):
    album = {"artist": artist, "title": title}
    if songs is not None:
        album["songs"] = songs
    return album

print("Enter 'q' at any time to quit.")

while True:
    artist = input("Artist name: ")
    if artist == "q":
        break

    title = input("Album title: ")
    if title == "q":
        break

    album = make_album(artist, title)
    print(album)

    messages = ["Yo", "Call me", "Practice at 6", "Study tonight"]

def show_messages(msgs):
    for msg in msgs:
        print(msg)

show_messages(messages)


messages = ["Yo", "Call me", "Practice at 6", "Study tonight"]
sent_messages = []

def send_messages(msgs, sent):
    while msgs:
        current = msgs.pop(0)
        print(current)
        sent.append(current)

send_messages(messages, sent_messages)

print("Original list:", messages)
print("Sent messages:", sent_messages)


def make_sandwich(*items):
    print("Making a sandwich with:")
    for item in items:
        print(f"- {item}")
    print()

make_sandwich("turkey", "cheese")
make_sandwich("ham", "lettuce", "tomato")
make_sandwich("steak", "onions", "peppers", "mayo")


def build_profile(first, last, **info):
    profile = {"first": first, "last": last}
    for key, value in info.items():
        profile[key] = value
    return profile

my_profile = build_profile(
    "William",
    "Wright",
    sport="Track",
    major="Cybersecurity",
    goal="Incident Response Analyst"
)

print(my_profile)


def make_car(manufacturer, model, **options):
    car = {"manufacturer": manufacturer, "model": model}
    for key, value in options.items():
        car[key] = value
    return car

car = make_car("subaru", "outback", color="blue", tow_package=True)
print(car)

def print_models(unprinted_designs, completed_models):
    while unprinted_designs:
        current = unprinted_designs.pop(0)
        print(f"Printing model: {current}")
        completed_models.append(current)

def show_completed_models(completed_models):
    print("The following models have been printed:")
    for model in completed_models:
        print(model)


import printing_functions

unprinted = ["phone case", "robot", "drone"]
completed = []

printing_functions.print_models(unprinted, completed)
printing_functions.show_completed_models(completed)


def greet_user(name):
    print(f"Hello, {name}!")

    # 1. import module_name
import greet
greet.greet_user("Will")

# 2. from module_name import function_name
from greet import greet_user
greet_user("Will")

# 3. from module_name import function_name as fn
from greet import greet_user as gu
gu("Will")

# 4. import module_name as mn
import greet as g
g.greet_user("Will")

# 5. from module_name import *
from greet import *
greet_user("Will")


def make_album(artist, title, songs=None):
    """Return a dictionary describing a music album."""
    album = {"artist": artist, "title": title}
    if songs is not None:
        album["songs"] = songs
    return album


def city_country(city, country):
    """Return a formatted city-country string."""
    return f"{city}, {country}"


def make_sandwich(*items):
    """Print a summary of the sandwich being made."""
    print("Making a sandwich with:")
    for item in items:
        print(f"- {item}")
    print()


print(make_album("Drake", "Views"))
print(city_country("Tokyo", "Japan"))
make_sandwich("turkey", "cheese")


import easygui as eg

# 1. msgbox – Welcome message
eg.msgbox("Welcome to the Track Athlete Performance Manager!", "Track Manager")

# 2. enterbox – Athlete name
athlete_name = eg.enterbox("Enter the athlete's name:", "Athlete Info")

# 3. integerbox – Athlete age
age = eg.integerbox("Enter athlete's age:", "Athlete Info", lowerbound=10, upperbound=60)

# 4. choicebox – Athlete event
event = eg.choicebox(
    "Select the athlete's main event:",
    "Event Selection",
    ["100m", "200m", "400m", "800m", "Long Jump", "High Jump"]
)

# 5. multenterbox – Enter multiple performance stats
fields = ["Best Time/Distance", "Season Best", "Personal Best"]
stats = eg.multenterbox("Enter performance stats:", "Performance Stats", fields)

# 6. ynbox – Ask if user wants to upload an image
upload_image = eg.ynbox("Do you want to load an athlete image?", "Image Option")

# 7. fileopenbox – Choose an image file to open
if upload_image:
    image_path = eg.fileopenbox("Choose an athlete image:", "Open Image", filetypes=["*.png", "*.jpg", "*.jpeg"])

    # 8. buttonbox – Display the image
    if image_path:
        eg.buttonbox("Athlete Image Loaded Successfully!", "Image Viewer", image=image_path, choices=["Continue"])

# 9. multchoicebox – Select training focuses
training_focus = eg.multchoicebox(
    "Select training focuses for the athlete:",
    "Training Plan",
    ["Speed", "Endurance", "Strength", "Flexibility", "Recovery"]
)

# 10. textbox – Show summary of athlete info
summary = f"""
Athlete Summary
-------------------------
Name: {athlete_name}
Age: {age}
Event: {event}

Performance Stats:
- Best: {stats[0]}
- Season Best: {stats[1]}
- Personal Best: {stats[2]}

Training Focus:
{training_focus}
"""

eg.textbox("Athlete Summary", "Summary", summary)

# 11. filesavebox – Choose where to save the summary
save_path = eg.filesavebox("Choose where to save the athlete summary:", "Save File")

# 12. msgbox – Final confirmation
eg.msgbox("Summary saved successfully! Thank you for using the Track Athlete Performance Manager.", "Done")
