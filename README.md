# password-cracker-
Enter password 
from urllib.request import hashlib
import colorama
from colorama import Fore,Style

# some decorations for giving it a good look and feel.
colorama.init()
print(Fore.GREEN + Style.BRIGHT)
print()
print(r".______      ___           _______.     _______.____    __    ____  ______   .______       _______  ")
print (r"|   _  \    /   \         /       |    /       |\   \  /  \  /   / /  __  \  |   _  \     |       \ ")
print (r"|  |_)  |  /  ^  \       |   (----`   |   (----` \   \/    \/   / |  |  |  | |  |_)  |    |  .--.  |")
print(r"|   ___/  /  /_\  \       \   \        \   \      \            /  |  |  |  | |      /     |  |  |  |")
print(r"|  |     /  _____  \  .----)   |   .----)   |      \    /\    /   |  `--'  | |  |\  \----.|  '--'  |")
print(r"| _|    /__/     \__\ |_______/    |_______/        \__/  \__/     \______/  | _| `._____||_______/ ")
print(r"                                                                                                    ")
print(r"              ______ .______          ___       ______  __  ___  _______ .______                    ")
print(r"             /      ||   _  \        /   \     /      ||  |/  / |   ____||   _  \                   ")
print(r"            |  ,----'|  |_)  |      /  ^  \   |  ,----'|  '  /  |  |__   |  |_)  |                  ")
print(r"            |  |     |      /      /  /_\  \  |  |     |    <   |   __|  |      /                   ")
print(r"            |  `----.|  |\  \----./  _____  \ |  `----.|  .  \  |  |____ |  |\  \----.              ")
print(r"             \______|| _| `._____/__/     \__\ \______||__|\__\ |_______|| _| `._____|              ")
print()


while True:
    # We will determine the type of hash to be cracked
    print()
    print ("Enter Type of Hash to be cracked (Select 3 to quit the script)!\n 1. SHA1 Hash \n 2. MD5 Hash \n 3. Quit Script")
    print() 
    k = input(">")

    if (k=="1"):
        passFound = False

        # We'll get the hash from the user to get the sha1 hash to crack

        sha1hash = input("Please input the SH1 hash to crack.\n>")

        # We'll open a file full of password guesses

        with open ("file.txt","r") as file:


        # We'll take a guess from the list of passwords we opened, and split it by line

            for guess in file:

            # We'll hash the guess we took from the password list so we can compare it to the hash the user gave us
                hashedGuess = hashlib.sha1(bytes(guess.strip(), 'utf-8')).hexdigest()

            # We'll compare the hash the user gave us to the hashed version of the password guess and determine if they are equal

                if hashedGuess.upper() == sha1hash.upper():

            # We'll tell the program what to do if the password guess matches, which is to print the current guess and quit the program.
            # We'll also tell the program what to do if the password guess don't match, which is to return to step 3 to get a new password from the list

                    print("The password is ", str(guess))
                    passFound=True
                    break
                elif hashedGuess != sha1hash:
                    print("Password guess ",str(guess)," does not match, trying next...")

        # We'll tell the program what to do if we get all the way through the password list without finding a match.
        if (passFound==False):
            print("Password not in database, we'll get them next time.")

    elif (k=="2"):
        passFound = False
        # We'll get the hash from the user to get the sha1 hash to crack

        md5hash = input("Please input the MD5 hash to crack.\n>")

        # We'll open a file full of password guesses

        with open ("file.txt","r") as file:


        # We'll take a guess from the list of passwords we opened, and split it by line

            for guess in file:

            # We'll hash the guess we took from the password list so we can compare it to the hash the user gave us
                hashedGuess = hashlib.md5(bytes(guess.strip(), 'utf-8')).hexdigest()

            # We'll compare the hash the user gave us to the hashed version of the password guess and determine if they are equal

                if hashedGuess.upper() == md5hash.upper():

            # We'll tell the program what to do if the password guess matches, which is to print the current guess and quit the program.
            # We'll also tell the program what to do if the password guess don't match, which is to return to step 3 to get a new password from the list

                    print("The password is ", str(guess))
                    passFound=True
                    break
                elif hashedGuess != md5hash:
                    print("Password guess ",str(guess)," does not match, trying next...")

        # We'll tell the program what to do if we get all the way through the password list without finding a match.
        if (passFound==False):
            print("Password not in database, we'll get them next time.")

    elif (k=="3"):
        quit()
