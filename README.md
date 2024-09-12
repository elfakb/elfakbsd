# elfakbsd
Python password generator
import random 
import string

#password generator using boolean data type 

def generate_password(min_length , numbers = True,special_char=True):

    letters = string.ascii_letters
    digits = string.digits
    special = string.punctuation

    characters = letters
    if numbers:
        characters += digits
    if special_char:
        characters += special

    passw = ""
    criteria = False
    has_numb = False
    has_special = False

    while not criteria or len(passw) < min_length:
        new_char = random.choice(characters)

        passw += new_char

        if new_char in digits:
            has_numb = True
        elif new_char in special:
            has_special = True

        criteria = True
        if numbers:
            criteria = has_numb
        if special_char:
            criteria = criteria and has_special
    return passw


min_lenght = int(input("Enter the minimum lenght: "))
has_numb =  input("Do you want to have numbers (y/n)?").lower() == "y"
has_special = input("Do you want to have special characters(y/n)?").lower()== "y"

pwd= generate_password(min_lenght,has_numb,has_special)    
print("The generated password is: "+ pwd)



