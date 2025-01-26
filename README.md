import random
import string
# Pre-defined lists of adjectives and nouns
adjectives = ["Cool", "Happy", "Brave", "Mighty", "Shiny", "Fierce", "Witty", "Silent", "Lucky", "Swift"]
nouns = ["Tiger", "Dragon", "Phoenix", "Shark", "Lion", "Wolf", "Eagle", "Falcon", "Bear", "Panther"]
def generate_username(include_numbers=False, include_special_chars=False, length=None):
adjective = random.choice(adjectives)
noun = random.choice(nouns)
username = adjective + noun
if include_numbers:
username += str(random.randint(100, 999))
if include_special_chars:
special_char = random.choice("!@#$%^&*()-_+=<>?") # Exclude problematic characters
username += special_char
if length and len(username) < length:
username += ’’.join(random.choices(string.ascii_letters + string.digits + "!@#$%^&*()-_+=<>?",
k=length - len(username)))
return username
def save_usernames_to_file(usernames, filename="usernames.txt"):
try:
with open(filename, "a") as file:
for username in usernames:
file.write(username + "\n")
print(f,"Usernames saved to {filename}.")
except Exception as e:
print(f"Error saving usernames: {e}")
def main():
print("Welcome to the Random Username Generator!")
try:
num_usernames = int(input("How many usernames would you like to generate? "))
include_numbers = input("Include numbers in usernames? (yes/no): ").strip().lower() == "yes"
include_special_chars = input("Include special characters in usernames? (yes/no): ").strip().lower()
== "yes"
length = None
if input("Would you like to specify a length for the username? (yes/no): ").strip().lower() == "yes":
length = int(input("Enter the desired length (minimum 6): "))
if length < 6:
print("Length too short. Setting to minimum of 6.")
length = 6
except ValueError:
print("Invalid input! Please enter valid numbers and options.")
return
usernames = [generate_username(include_numbers, include_special_chars, length) for _ in
range(num_usernames)]
print("\nGenerated Usernames:")
for username in usernames:
print(f" - {username}")
if input("Would you like to save the usernames to a file? (yes/no): ").strip().lower() == "yes":
filename = input("Enter a filename (default: usernames.txt): ").strip() or "usernames.txt"
save_usernames_to_file(usernames, filename)
if _name_ == "_main_":
main()# Sakshi26
