# Password_Strength
import re

# Function to check the length of the password
def check_length(password):
    return len(password) >= 8

# Function to check for digits in the password
def check_digits(password):
    return bool(re.search(r"\d", password))

# Function to check for uppercase letters in the password
def check_uppercase(password):
    return bool(re.search(r"[A-Z]", password))

# Function to check for lowercase letters in the password
def check_lowercase(password):
    return bool(re.search(r"[a-z]", password))

# Function to check for special symbols in the password
def check_symbols(password):
    return bool(re.search(r"[!@#$%^&*(),.?\":{}|<>]", password))

# Main function to check password strength
def check_password_strength(password):
    checks = [
        check_length,
        check_digits,
        check_uppercase,
        check_lowercase,
        check_symbols
]
    
    score = sum(check(password) for check in checks)
    
    if score == 5:
        return "Very Strong"
    elif score >= 3:
        return "Strong"
    else:
        return "Weak"

# User input and output
if __name__ == "__main__":
    user_password = input("Enter a password to check its strength: ")
    strength = check_password_strength(user_password)
    print(f"Your password is: {strength}")
