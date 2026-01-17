# 1. Program intro
print("Welcome to Will's Toyota Inventory & Payment Assistant!")

# 2. Favorite brand
brand = 'Toyota'

# 3. 5 models from cheapest to most expensive
models = ['Corolla', 'Camry', 'RAV4', 'Highlander', 'Land Cruiser']

# 4. Append a 6th model
models.append('Sequoia')

# 5. 5 standard colors
colors = ['White', 'Black', 'Silver', 'Blue', 'Red']

# 6. Replace last color
colors[-1] = 'Purple'

# 7. Current year
YEAR = 2026

# 8. MSRP constants
MSRP_Corolla = 21000
MSRP_Camry = 25000
MSRP_RAV4 = 28000
MSRP_Highlander = 36000
MSRP_LandCruiser = 87000
MSRP_Sequoia = 62000

# 9. Loan terms
fouryr = 48
fiveyr = 60
sixyr = 72

# 10. Guest name
guest_name = 'Bobby'

# 11. Welcome message
message = f"Hello {guest_name}, welcome to the best Toyota dealership known to mankind!"

# 12. Awesome banner
banner = f"""
===============================
 :) {brand.upper()} DEALERSHIP - {YEAR} :)
===============================
"""

# 13. Print banner and welcome
print(banner)
print(message)

# 14. Alphabetical vehicles with year and colors
print("\nAvailable Vehicles:")
for model in sorted(models):
    print(f"{YEAR} {model.title()} - Colors: {', '.join(colors)}")

# 15. Monthly payment for Corolla (5yr)
monthly_corolla = round(MSRP_Corolla / fiveyr, 2)
print(f"\nFor the {models[0]}, your 5-year monthly payment is: ${monthly_corolla}")

# 16. Kind message
print(f"Thanks for checking out the {models[0]}, Bobby. No pressure — just great cars and great deals.")

# 17. 4yr and 6yr options for Corolla
monthly_4yr = round(MSRP_Corolla / fouryr, 2)
monthly_6yr = round(MSRP_Corolla / sixyr, 2)
print(f"\nOther options for the {models[0]}:")
print(f"4-year plan: ${monthly_4yr}/month")
print(f"6-year plan: ${monthly_6yr}/month")

# 18. 5yr options for other vehicles
print("\nHere are 5-year monthly payments for other models:")
for model, price in zip(models[1:], [MSRP_Camry, MSRP_RAV4, MSRP_Highlander, MSRP_LandCruiser, MSRP_Sequoia]):
    monthly = round(price / fiveyr, 2)
    print(f"{model}: ${monthly}/month")
# 19. cash discount
    cash_price = round(MSRP_Corolla * 0.95, 2)
    print(f"\nIf you pay cash for the Corolla, your price is: ${cash_price}")
# 20. Extra loan Option
seven_year = 84
corolla_7yr = round(MSRP_Corolla / seven_year, 2)
print(f"7-year option for the Corolla: ${corolla_7yr}/month")
# 21. List of Models Under $30K
under_30k = [model for model, price in zip(models, [MSRP_Corolla, MSRP_Camry, MSRP_RAV4, MSRP_Highlander, MSRP_LandCruiser, MSRP_Sequoia]) if price < 30000]
print(f"\nModels under $30,000: {under_30k}") 
