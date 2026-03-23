# cubes_15_1_will.py
import matplotlib.pyplot as plt

# First five cubes
x_values_small = list(range(1, 6))
y_values_small = [x**3 for x in x_values_small]

plt.style.use('seaborn-v0_8')
fig, ax = plt.subplots()
ax.plot(x_values_small, y_values_small, marker='o')

ax.set_title("First Five Cubic Numbers – Will", fontsize=16)
ax.set_xlabel("Value", fontsize=12)
ax.set_ylabel("Cube of Value", fontsize=12)

plt.show()

# First 5,000 cubes
x_values = list(range(1, 5001))
y_values = [x**3 for x in x_values]

plt.style.use('seaborn-v0_8')
fig, ax = plt.subplots()
ax.scatter(x_values, y_values, s=1)

ax.set_title("First 5,000 Cubic Numbers – Will", fontsize=16)
ax.set_xlabel("Value", fontsize=12)
ax.set_ylabel("Cube of Value", fontsize=12)

plt.show()

# cubes_15_2_will.py
import matplotlib.pyplot as plt

x_values = list(range(1, 5001))
y_values = [x**3 for x in x_values]

plt.style.use('seaborn-v0_8')
fig, ax = plt.subplots()

ax.scatter(
    x_values,
    y_values,
    c=y_values,
    cmap=plt.cm.plasma,
    s=3,
)

ax.set_title("Colored Cubes with Colormap – Will", fontsize=16)
ax.set_xlabel("Value", fontsize=12)
ax.set_ylabel("Cube of Value", fontsize=12)

plt.show()


from random import choice

class RandomWalk:
    """A class to generate random walks."""

    def __init__(self, num_points=5000):
        self.num_points = num_points
        self.x_values = [0]
        self.y_values = [0]

    def fill_walk(self):
        """Calculate all the points in the walk."""
        while len(self.x_values) < self.num_points:

            x_direction = choice([1, -1])
            x_distance = choice([0, 1, 2, 3, 4])
            x_step = x_direction * x_distance

            y_direction = choice([1, -1])
            y_distance = choice([0, 1, 2, 3, 4])
            y_step = y_direction * y_distance

            if x_step == 0 and y_step == 0:
                continue

            x = self.x_values[-1] + x_step
            y = self.y_values[-1] + y_step

            self.x_values.append(x)
            self.y_values.append(y)


# rw_visual_15_3_will.py
import matplotlib.pyplot as plt
from random_walk import RandomWalk

# Make a random walk.
rw = RandomWalk(5000)
rw.fill_walk()

plt.style.use('seaborn-v0_8')
fig, ax = plt.subplots(figsize=(10, 6))

# Use plot instead of scatter to show the path.
ax.plot(rw.x_values, rw.y_values, linewidth=1)

ax.set_title("Molecular Motion Path – Will", fontsize=16)
ax.set_xlabel("X", fontsize=12)
ax.set_ylabel("Y", fontsize=12)

# Emphasize start and end points.
ax.scatter(0, 0, c='green', s=50)
ax.scatter(rw.x_values[-1], rw.y_values[-1], c='red', s=50)

ax.get_xaxis().set_visible(False)
ax.get_yaxis().set_visible(False)

plt.show()


# random_walk_15_4_will.py
from random import choice

class RandomWalk:
    """A class to generate random walks."""

    def __init__(self, num_points=5000):
        self.num_points = num_points
        self.x_values = [0]
        self.y_values = [0]

    def fill_walk(self):
        while len(self.x_values) < self.num_points:
            # Try different distance and direction sets
            x_direction = choice([1, -1])          # or [1] to remove -1
            x_distance = choice([0, 1, 2, 3, 4, 5, 6, 7, 8])
            x_step = x_direction * x_distance

            y_direction = choice([1, -1])
            y_distance = choice([0, 1, 2, 3, 4, 5, 6, 7, 8])
            y_step = y_direction * y_distance

            if x_step == 0 and y_step == 0:
                continue

            x = self.x_values[-1] + x_step
            y = self.y_values[-1] + y_step

            self.x_values.append(x)
            self.y_values.append(y)


from random import choice

class RandomWalk:
    """A class to generate random walks with refactored steps."""

    def __init__(self, num_points=5000):
        self.num_points = num_points
        self.x_values = [0]
        self.y_values = [0]

    def get_step(self):
        """Determine direction and distance, then return the step."""
        direction = choice([1, -1])
        distance = choice([0, 1, 2, 3, 4])
        return direction * distance

    def fill_walk(self):
        """Calculate all the points in the walk."""
        while len(self.x_values) < self.num_points:

            x_step = self.get_step()
            y_step = self.get_step()

            if x_step == 0 and y_step == 0:
                continue

            x = self.x_values[-1] + x_step
            y = self.y_values[-1] + y_step

            self.x_values.append(x)
            self.y_values.append(y)

            from random import randint

class Die:
    """A class representing a single die."""

    def __init__(self, num_sides=6):
        self.num_sides = num_sides

    def roll(self):
        return randint(1, self.num_sides)


# two_d8_15_6_will.py
from plotly.graph_objs import Bar, Layout
from plotly import offline

from die import Die  # standard Die class, but with sides=8

die_1 = Die(8)
die_2 = Die(8)

results = [die_1.roll() + die_2.roll() for _ in range(1000)]

max_result = die_1.num_sides + die_2.num_sides
frequencies = [results.count(value) for value in range(2, max_result + 1)]

x_values = list(range(2, max_result + 1))

data = [Bar(x=x_values, y=frequencies)]
x_axis_config = {'title': 'Result', 'dtick': 1}
y_axis_config = {'title': 'Frequency of Result'}

my_layout = Layout(
    title='Rolling Two D8 Dice 1,000 Times – Will',
    xaxis=x_axis_config,
    yaxis=y_axis_config,
)

offline.plot({'data': data, 'layout': my_layout}, filename='two_d8_will.html')

# three_d6_15_7_will.py
from plotly.graph_objs import Bar, Layout
from plotly import offline
from die import Die

die_1 = Die()
die_2 = Die()
die_3 = Die()

results = [die_1.roll() + die_2.roll() + die_3.roll() for _ in range(1000)]

min_result = 3
max_result = 18
frequencies = [results.count(value) for value in range(min_result, max_result + 1)]

x_values = list(range(min_result, max_result + 1))

data = [Bar(x=x_values, y=frequencies)]
x_axis_config = {'title': 'Result', 'dtick': 1}
y_axis_config = {'title': 'Frequency of Result'}

my_layout = Layout(
    title='Rolling Three D6 Dice 1,000 Times – Will',
    xaxis=x_axis_config,
    yaxis=y_axis_config,
)

offline.plot({'data': data, 'layout': my_layout}, filename='three_d6_will.html')


# dice_multiplication_15_8_will.py
from plotly.graph_objs import Bar, Layout
from plotly import offline
from die import Die

die_1 = Die()
die_2 = Die()

results = [die_1.roll() * die_2.roll() for _ in range(1000)]

min_result = 1
max_result = 36
frequencies = [results.count(value) for value in range(min_result, max_result + 1)]

x_values = list(range(min_result, max_result + 1))

data = [Bar(x=x_values, y=frequencies)]
x_axis_config = {'title': 'Product', 'dtick': 1}
y_axis_config = {'title': 'Frequency of Product'}

my_layout = Layout(
    title='Multiplication of Two D6 Dice – Will',
    xaxis=x_axis_config,
    yaxis=y_axis_config,
)

offline.plot({'data': data, 'layout': my_layout}, filename='dice_multiplication_will.html')


# die_comprehensions_15_9_will.py
from plotly.graph_objs import Bar, Layout
from plotly import offline
from die import Die

die_1 = Die()
die_2 = Die()

# List comprehension for results
results = [die_1.roll() + die_2.roll() for _ in range(1000)]

max_result = die_1.num_sides + die_2.num_sides
x_values = list(range(2, max_result + 1))

# List comprehension for frequencies
frequencies = [results.count(value) for value in x_values]

data = [Bar(x=x_values, y=frequencies)]
my_layout = Layout(title='Two D6 with List Comprehensions – Will')

offline.plot({'data': data, 'layout': my_layout}, filename='die_comprehensions_will.html')


# die_comprehensions_15_9_will.py
from plotly.graph_objs import Bar, Layout
from plotly import offline
from die import Die

die_1 = Die()
die_2 = Die()

# List comprehension for results
results = [die_1.roll() + die_2.roll() for _ in range(1000)]

max_result = die_1.num_sides + die_2.num_sides
x_values = list(range(2, max_result + 1))

# List comprehension for frequencies
frequencies = [results.count(value) for value in x_values]

data = [Bar(x=x_values, y=frequencies)]
my_layout = Layout(title='Two D6 with List Comprehensions – Will')

offline.plot({'data': data, 'layout': my_layout}, filename='die_comprehensions_will.html')


import matplotlib.pyplot as plt
from die import Die

# Create two D6 dice.
die_1 = Die()
die_2 = Die()

# Roll the dice 1,000 times and store results.
results = [die_1.roll() + die_2.roll() for _ in range(1000)]

# Analyze the results.
x_values = list(range(2, 13))
frequencies = [results.count(value) for value in x_values]

# Visualize with Matplotlib.
plt.style.use('seaborn-v0_8')
fig, ax = plt.subplots()
ax.bar(x_values, frequencies)

ax.set_title("Two D6 Dice – Matplotlib – Will", fontsize=16)
ax.set_xlabel("Result", fontsize=12)
ax.set_ylabel("Frequency", fontsize=12)

plt.show()

from plotly.graph_objs import Scatter, Layout
from plotly import offline
from random_walk import RandomWalk

# Make a random walk.
rw = RandomWalk(5000)
rw.fill_walk()

# Build the Plotly scatter trace.
data = [Scatter(
    x=rw.x_values,
    y=rw.y_values,
    mode='lines'
)]

my_layout = Layout(
    title='Random Walk with Plotly – Will',
    xaxis={'visible': False},
    yaxis={'visible': False},
)

offline.plot({'data': data, 'layout': my_layout}, filename='random_walk_plotly_will.html')


import csv
from datetime import datetime
import matplotlib.pyplot as plt

filename = 'sitka_weather_2021_full.csv'

dates, prcp = [], []

with open(filename) as f:
    reader = csv.reader(f)
    header_row = next(reader)
    print("Header row:", header_row)

    # Find DATE and PRCP columns
    date_index = None
    prcp_index = None

    for i, col in enumerate(header_row):
        if "DATE" in col:
            date_index = i
        if "PRCP" in col:
            prcp_index = i

    print("DATE index:", date_index)
    print("PRCP index:", prcp_index)

    if date_index is None or prcp_index is None:
        raise ValueError("DATE or PRCP column not found.")

    for row in reader:
        try:
            current_date = datetime.strptime(row[date_index], "%Y-%m-%d")
            rainfall = float(row[prcp_index])
        except:
            continue
        else:
            dates.append(current_date)
            prcp.append(rainfall)

plt.style.use('seaborn-v0_8')
fig, ax = plt.subplots()
ax.plot(dates, prcp, color='blue')

ax.set_title("Daily Rainfall – Sitka 2021 – Will", fontsize=16)
ax.set_xlabel("")
fig.autofmt_xdate()
ax.set_ylabel("Rainfall (inches)", fontsize=12)

plt.show()


import csv
from datetime import datetime
import matplotlib.pyplot as plt

filename = 'sitka_weather_2021_full.csv'

dates, highs = [], []

with open(filename) as f:
    reader = csv.reader(f)
    header_row = next(reader)
    print("Header row:", header_row)

    # Find DATE and TMAX columns
    date_index = None
    tmax_index = None

    for i, col in enumerate(header_row):
        if "DATE" in col:
            date_index = i
        if "TMAX" in col:
            tmax_index = i

    print("DATE index:", date_index)
    print("TMAX index:", tmax_index)

    if date_index is None or tmax_index is None:
        raise ValueError("DATE or TMAX column not found.")

    for row in reader:
        try:
            current_date = datetime.strptime(row[date_index], "%Y-%m-%d")
            high = int(row[tmax_index])
        except:
            continue
        else:
            dates.append(current_date)
            highs.append(high)

plt.style.use('seaborn-v0_8')
fig, ax = plt.subplots()
ax.plot(dates, highs, color='red')

ax.set_title("Daily High Temperatures – Sitka 2021 – Will", fontsize=16)
ax.set_xlabel("")
fig.autofmt_xdate()
ax.set_ylabel("Temperature (F)", fontsize=12)

plt.show()

import csv
from datetime import datetime
import matplotlib.pyplot as plt

filename = 'sitka_weather_2021_full.csv'

dates, highs, lows = [], [], []

with open(filename) as f:
    reader = csv.reader(f)
    header_row = next(reader)
    print("Header row:", header_row)

    # Find DATE, TMAX, TMIN columns
    date_index = None
    tmax_index = None
    tmin_index = None

    for i, col in enumerate(header_row):
        if "DATE" in col:
            date_index = i
        if "TMAX" in col:
            tmax_index = i
        if "TMIN" in col:
            tmin_index = i

    print("DATE index:", date_index)
    print("TMAX index:", tmax_index)
    print("TMIN index:", tmin_index)

    if None in (date_index, tmax_index, tmin_index):
        raise ValueError("DATE, TMAX, or TMIN column not found.")

    for row in reader:
        try:
            current_date = datetime.strptime(row[date_index], "%Y-%m-%d")
            high = int(row[tmax_index])
            low = int(row[tmin_index])
        except:
            continue
        else:
            dates.append(current_date)
            highs.append(high)
            lows.append(low)

plt.style.use('seaborn-v0_8')
fig, ax = plt.subplots()

# Plot highs and lows
ax.plot(dates, highs, color='red', alpha=0.8)
ax.plot(dates, lows, color='blue', alpha=0.8)

# Shade between them
ax.fill_between(dates, highs, lows, facecolor='blue', alpha=0.1)

ax.set_title("Daily Highs & Lows – Sitka 2021 – Will", fontsize=16)
ax.set_xlabel("")
fig.autofmt_xdate()
ax.set_ylabel("Temperature (F)", fontsize=12)

plt.show()


import csv
from datetime import datetime
import matplotlib.pyplot as plt

def load_weather(filename):
    """Load dates, highs, and lows from a weather CSV file."""
    dates, highs, lows = [], [], []

    with open(filename) as f:
        reader = csv.reader(f)
        header_row = next(reader)

        # Find columns
        date_i = None
        tmax_i = None
        tmin_i = None

        for i, col in enumerate(header_row):
            if "DATE" in col:
                date_i = i
            if "TMAX" in col:
                tmax_i = i
            if "TMIN" in col:
                tmin_i = i

        for row in reader:
            try:
                current_date = datetime.strptime(row[date_i], "%Y-%m-%d")
                high = int(row[tmax_i])
                low = int(row[tmin_i])
            except:
                continue
            else:
                dates.append(current_date)
                highs.append(high)
                lows.append(low)

    return dates, highs, lows


# Load Sitka
sitka_dates, sitka_highs, sitka_lows = load_weather("sitka_weather_2021_full.csv")

# Load Death Valley
dv_dates, dv_highs, dv_lows = load_weather("death_valley_2021_full.csv")

plt.style.use('seaborn-v0_8')
fig, ax = plt.subplots()

# Sitka plot
ax.plot(sitka_dates, sitka_highs, color='blue', alpha=0.8, label="Sitka Highs")
ax.plot(sitka_dates, sitka_lows, color='blue', alpha=0.4, label="Sitka Lows")
ax.fill_between(sitka_dates, sitka_highs, sitka_lows, facecolor='blue', alpha=0.1)

# Death Valley plot
ax.plot(dv_dates, dv_highs, color='red', alpha=0.8, label="Death Valley Highs")
ax.plot(dv_dates, dv_lows, color='red', alpha=0.4, label="Death Valley Lows")
ax.fill_between(dv_dates, dv_highs, dv_lows, facecolor='red', alpha=0.1)

ax.set_title("Sitka vs Death Valley – Daily Highs & Lows (2021) – Will", fontsize=16)
ax.set_xlabel("")
fig.autofmt_xdate()
ax.set_ylabel("Temperature (F)", fontsize=12)
ax.legend()

plt.show()


import csv
from datetime import datetime
import matplotlib.pyplot as plt

def load_weather(filename, label):
    """Load dates, highs, and lows from a weather CSV file.
       Print warnings when data is missing."""
    dates, highs, lows = [], [], []

    with open(filename) as f:
        reader = csv.reader(f)
        header_row = next(reader)

        # Find columns
        date_i = None
        tmax_i = None
        tmin_i = None

        for i, col in enumerate(header_row):
            if "DATE" in col:
                date_i = i
            if "TMAX" in col:
                tmax_i = i
            if "TMIN" in col:
                tmin_i = i

        for row in reader:
            try:
                current_date = datetime.strptime(row[date_i], "%Y-%m-%d")
                high = int(row[tmax_i])
                low = int(row[tmin_i])
            except Exception:
                print(f"Missing data for {label} on {row[date_i]}")
                continue
            else:
                dates.append(current_date)
                highs.append(high)
                lows.append(low)

    return dates, highs, lows


# Load Sitka
sitka_dates, sitka_highs, sitka_lows = load_weather(
    "sitka_weather_2021_full.csv", "Sitka"
)

# Load Death Valley
dv_dates, dv_highs, dv_lows = load_weather(
    "death_valley_2021_full.csv", "Death Valley"
)

plt.style.use('seaborn-v0_8')
fig, ax = plt.subplots()

# Sitka plot
ax.plot(sitka_dates, sitka_highs, color='blue', alpha=0.8, label="Sitka Highs")
ax.plot(sitka_dates, sitka_lows, color='blue', alpha=0.4, label="Sitka Lows")
ax.fill_between(sitka_dates, sitka_highs, sitka_lows, facecolor='blue', alpha=0.1)

# Death Valley plot
ax.plot(dv_dates, dv_highs, color='red', alpha=0.8, label="Death Valley Highs")
ax.plot(dv_dates, dv_lows, color='red', alpha=0.4, label="Death Valley Lows")
ax.fill_between(dv_dates, dv_highs, dv_lows, facecolor='red', alpha=0.1)

ax.set_title("Sitka vs Death Valley – Missing Data Handling – Will", fontsize=16)
ax.set_xlabel("")
fig.autofmt_xdate()
ax.set_ylabel("Temperature (F)", fontsize=12)
ax.legend()

plt.show()
