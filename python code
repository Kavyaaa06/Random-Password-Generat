import random
import string

def generatePassword(length, special_count, number_count, alphabet_count):
    lowercase_letters = string.ascii_lowercase
    uppercase_letters = string.ascii_uppercase
    digits = string.digits
    special_chars = "&@!#$%^*"  

    password = []
    password.append(random.choice(uppercase_letters))  
    password.extend(random.choices(special_chars, k=special_count))
    password.extend(random.choices(digits, k=number_count))
    password.extend(random.choices(lowercase_letters, k=alphabet_count))  

    random.shuffle(password)

    if not password[0].isalpha():
        for idx, char in enumerate(password):
            if char.isalpha():
                password[0], password[idx] = password[idx], password[0]
                break

    if not (password[-1].isalpha() or password[-1].isdigit()):
        for idx in range(len(password) - 1, -1, -1):
            if password[idx].isalpha() or password[idx].isdigit():
                password[-1], password[idx] = password[idx], password[-1]
                break

    return "".join(password)

def main():
    print("HI! THIS IS A RANDOM PASSWORD GENERATOR!")

    while True:
        length = int(input("\nHow much length of password do you want? : "))

        if length < 10:
            print("\nAbove entered length of password is a weak password."
                  "\nYour security is our main priority. We recommend a minimum length of password as 10")
        else:
            break  
            
    numPasswords = int(input("How many passwords should be generated? "))

    while True:
        special_count = int(input("How many special characters do you want? "))
        number_count = int(input("How many numbers (1-3 ALLOWED) do you want? "))

        if number_count not in [1, 2, 3]:
            print("Please enter 1, 2, or 3 for numbers.")
            continue  

        alphabet_count = length - (special_count + number_count + 1)  # Adjusting for one uppercase letter
        if alphabet_count < 1:
            print("TOTAL CHARACTERS EXCEEDED. PLEASE ENTER VALID COUNTS.")
            continue  

        break  

    print("\nGENERATED PASSWORDS:")
    generated_passwords = []
    for i in range(numPasswords):
        password = generatePassword(length, special_count, number_count, alphabet_count)
        generated_passwords.append(password)
        print(f"PASSWORD #{i+1}: {password}")

    while True:
        chosen_index = int(input("\nChoose one number from above choices (1 - " + str(numPasswords) + "): "))
        if 1 <= chosen_index <= numPasswords:
            print("\nYOUR SELECTED PASSWORD IS:", generated_passwords[chosen_index - 1])
            break
        else:
            print("INVALID CHOICE. PLEASE CHOOSE A VALID PASSWORD NUMBER.")

    print("\nTHANK YOU! VISIT AGAIN!")

main()
