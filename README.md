# Dice-Game
import time, random#imports time and ramndom into the program.

    




def Scores():#a section for scores
    file = open("scores.txt", "r")#opens scores.txt so i can use the data inside.
    print (file.read())#reads the data inside the scores.txt so i can see the soreboard.
    Enter()






#Decides who is the winner by looking at who scored most, if the scores draw they play a death-match. Deadth-Match contiunes until someone scores more then other.
def Winner():
    file = open("scores.txt", "r+")#opens the file to edit.
    text = file.read().strip().split()
    if PlayerOnescore > PlayerTwoscore:#checks if player1's score higher than player2's score.
        print (username1+" has won the game with", PlayerOnescore ,"scores!")#tells to players that player1 won.
        file.write(username1+"'s points: " + str(PlayerOnescore) + "\n")#saves player1's score to a text file.
        file.write(username2+"'s points: " + str(PlayerTwoscore) + "\n")#saves player2's score to a text file.
        Enter()#goes back to entarance at the end of the game.
    elif PlayerTwoscore > PlayerOnescore:#checks if player2's score is higher than player1's score.
        print (username2+" has won the game with", PlayerTwoscore ,"scores!")#tells to players that player2 won.
        file.write(username1+"'s points: " + str(PlayerOnescore) + "\n")#saves player1's score to a text file.
        file.write(username2+"'s points: " + str(PlayerTwoscore) + "\n")#saves player2's score to a text file.
        Enter()#goes back to entarance at the end of the game.
    elif PlayerOnescore == PlayerTwoscore:#checks if both players scores are equal.
        print ("Its A Death-Match!")#goes to one more round so we an decide who won.
        Game()#goes back to game.
    else:
        print ("A error has occured!")#if in case a error occures, well reports to the player.
        Enter()#goes back to enterance.
    



def Rounds():#THIS SECTION IS NOT READY YET AND HAS SYNTAX/LOGIC ERRORS.
    if index <= 5:
        index = index + 1
        Game()
    elif index >= 5:
        Winner()
    else:
        print ("An unknown error has occured.")
        Enter()




#Most important bit of the program
def Game():
    global index
    global PlayerOnescore#Globalizes the variable so we can call it after to count scores and see who won or save the scores.
    index = 1
    P1score1 = random.randint(1,6)#reandomly rolls a number between 1 and 6
    P1score2 = random.randint(1,6)#randomly rolls a number between 1 and 6
    PlayerOnescore = P1score1 + P1score2#adds both rolled numbers to have a total score.
    print ("--------------------------------------------------------------------------------")
    print ("Round ", index)#Adds 1 to index so Rounds() can count how many rounds have been played
    print (username1+"'s first turn.")#informs that is player1's turn.
    print ("--------------------------------------------------------------------------------")#some good looking feature.
    print ("To roll your dice press enter :  ")#informs player to roll.
    playerOnefirst = input("Press Enter ")#inputs the command.
    while playerOnefirst is not "":
        playerOnefirst = input("Press Enter ")#inputs the command.
    if playerOnefirst == "":
        print ("Rolling.")
        time.sleep(0.5)#waits for 0.5 seconds loading.
        print ("Rolling..")
        time.sleep(0.5)#waits for 0.5 seconds loading.
        print ("Rolling...")
        time.sleep(0.5)#waits for 0.5 seconds loading.
        print ("You have scored ", P1score1, "!")#prints the rolled score.
        print ("--------------------------------------------------------------------------------")
        print (username1+"'s second turn.")#informs that is player1's turn.
        print ("--------------------------------------------------------------------------------")
        print ("To roll your dice press enter :  ")#informs player to roll
        playerOnesecond = input("Press Enter ")#inputs the command.
        while playerOnesecond is not "":
            playerOnesecond = input("Press Enter ")#inputs the command.
        if playerOnesecond == "":
            print ("Rolling.")
            time.sleep(0.5)#waits for 0.5 second loading.
            print ("Rolling..")
            time.sleep(0.5)#waits for 0.5 second loading.
            print ("Rolling...")
            time.sleep(0.5)#waits for 0.5 second loading.
            print ("You have scored ", P1score2, "!")
            if PlayerOnescore % 2 == 0:#checks if the score is even number or odd number because of even number.
                print ("--------------------------------------------------------------------------------")
                PlayerOnescore = PlayerOnescore + 10#extra 10 points to total score.
                print (username1+"'s total score is even number so it gets extra 10 points!")#informs player1 that he/she get a extra 10 points.
                print (PlayerOnescore)#prints to screen player 1 score for this round.
                print ("--------------------------------------------------------------------------------")
            else:#if the player 1 score is a odd number, goes to this part to take away 5 points from the score.
                print ("--------------------------------------------------------------------------------")
                PlayerOnescore = PlayerOnescore - 5#extra -5 points to total score because of odd number.
                print (username1+"'s score is odd number so it loses extra 5 points!")#informs player 1 that he/she lost 5 points.
                print (PlayerOnescore)#prints to screen player 1 score for this round.
                print ("--------------------------------------------------------------------------------")
                if PlayerOnescore < 0:#if players score is lower than 0,
                    PlayerOnescore = 0#sets the players score to 0.
                    print ("The score cannot be lower than 0 so ",username1,"'s score setted to 0.")#informs player 1 about his new score 0.
#samething above for player 2.
    global PlayerTwoscore
    P2score1 = random.randint(1,6)
    P2score2 = random.randint(1,6)
    PlayerTwoscore = P2score1 + P2score2
    print ("--------------------------------------------------------------------------------")
    print (username2+"'s first turn.")
    print ("--------------------------------------------------------------------------------")
    print ("To roll your dice press enter :  ")
    playerTwofirst = input("Press Enter ")
    while playerTwofirst is not "":
        playerTwofirst = input("Press Enter ")#inputs the command.
    if playerTwofirst == "":
        print ("Rolling.")
        time.sleep(0.5)
        print ("Rolling..")
        time.sleep(0.5)
        print ("Rolling...")
        time.sleep(0.5)
        print ("You have scored ", P2score1, "!")
        print ("--------------------------------------------------------------------------------")
        print (username2+"'s second turn.")
        print ("--------------------------------------------------------------------------------")
        print ("To roll your dice press enter :  ")
        playerTwosecond = input("Press Enter ")
        while playerTwosecond is not "":
            playerTwosecond = input("Press Enter ")#inputs the command.
        if playerTwosecond == "":
            print ("Rolling.")
            time.sleep(0.5)
            print ("Rolling..")
            time.sleep(0.5)
            print ("Rolling...")
            time.sleep(0.5)
            print ("You have scored ", P2score2, "!")
            if PlayerTwoscore % 2 == 0:
                print ("--------------------------------------------------------------------------------")
                PlayerTwoscore = PlayerTwoscore + 10
                print (username2+"'s total score is even number so it gets extra 10 points!")
                print (PlayerTwoscore)
                print ("--------------------------------------------------------------------------------")
                Winner()#loops for Rounds().
            else:
                print ("--------------------------------------------------------------------------------")
                PlayerTwoscore = PlayerTwoscore - 5
                print (username2+"'s score is odd number so it loses extra 5 points!")
                print (PlayerTwoscore)
                print ("--------------------------------------------------------------------------------")
                if PlayerTwoscore < 0:
                    PlayerTwoscore = 0
                    print ("The score cannot be lower than 0 so ",username2,"'s score setted to 0.")
                    Winner()#end of the round goes to Rounds() for loop.
                else:
                    Winner()#loop for Rounds()
    





def Register():
    print ("-----------------------------------")
    print ("|Please Dont Forget Your Password!|")
    print ("-----------------------------------")
    file = open("users.txt", "r+")# opens the file to edit
    text = file.read().strip().split()#i dont know whats this
    check = True#beginning of the loop.
    while check:# loop
        username=input("Create a username: ") #Takes input of a username from user
        if username == "": #if the answer is nothing it loops until it gets a valid username.
            continue#continues
        if username in text: #username in present in the text file
            print("Username is already exists. Try again.")#informs players that the username already used/exists.
        else: #username is absent in the text file
            print("Username has been created")#informs players about that the username has been created.
            check = False#end if the loop
            check = True#begining of the loop.
            password1=input("Create a password: ")#asks for a password
            password2=input("Re-enter the password: ")#asks again to be sure
            while check:#loop
                if password1 == password2:#checks if the passwords match each other
                    print("You have succesfully registered.")
                    file.write("Username: " + username + " Password: " + password2 + "\n")#writes the username and password in text file
                    check = False#end of the loop.
                else:
                    print ("-------------------------------------------")
                    print ("|Passwords do not match, please try again.|")
                    print ("-------------------------------------------")
                    password1=input("Create a password: ")#asks for a password
                    password2=input("Re-enter the password: ")#asks again to be sure
                    if password1 == password2:#checks if the passwords match each other
                        print("You have succesfully registered.")
                        file.write("Username: " + username + " Password: " + password2 + "\n")#writes the username and password in text file
                        check = False#end of the loop.
                    
    file.close()#closes the file to save data
    Enter()#goes back to enterance


def Login():#a section for login
    global username1#global variable to call it later
    global username2#global variable to call it later
    check_failed = True#beginning of the loop.
    while check_failed:#loop
        print ("---------------")
        print ("|Please Log-In|")
        print ("---------------")
        username1=input("Player 1's Username: ")#input a existing username
        password=input("Player 1's Password: ")#input a existing password
        with open("users.txt","r") as UserFinder:#opens the text file
            for line in UserFinder:#looks into the text file for user data
                if ("Username: " + username1 + " Password: " + password) == line.strip(): #checks if data is correct
                    print(username1+" is logged in.")#logged in
                    check_failed = False#end of the loop.
                    check_failed = True#begining of the loop
                    while check_failed:#all same with the upper part of the comments for player 2
                        username2=input("Player 2's Username: ")#asks for 2nd players username.
                        password=input("Player 2's Password: ")#asks for 2nd players password.
                        with open("users.txt","r") as UserFinder:#opens the users file to check if user exists.
                            for line in UserFinder:#checks inside the user file for valid data.
                                if ("Username: " + username2 + " Password: " + password) == line.strip():#if the data inputted by the player 2 is correct, then log in.
                                    print(username2+" is logged in.")#informs player 2 that he/she is logged in.
                                    check_failed = False#end of the loop.
                                    Game()#goes to game section to play game



def Enter():#enterance for different options.
    
    print ("Welcome to dice game!")#welcomes to players.
    print ("----------------------------------------------------------------------------------------------------------------------------------------------------------------")
    print ("If you dont have an account yet and want to register, then please type in 'register' below,")#asks for a decision
    print ("If you already have an account and want to sign in, then please type in 'login' below,")
    print ("If you just want to see the scoreboard, then please type in 'score' or 'scores' below.")
    decision = input(">>> ").lower()#input the decision
    print ("----------------------------------------------------------------------------------------------------------------------------------------------------------------")
    if decision == "register":#if decision is register,
        Register()#goes to register section.
    elif decision == "login":#if the decision is login,
        Login()#goes to login section.
    elif decision == "scores":#if decision is scores,
        Scores()#goes to scores section.
    elif decision == "score":
            Scores()
    while decision not in ("login", "register", "score", "scores"):#loops if player give an unavailable input.
        #samething that is upwards only to loop.
        print ("Error, please answer correctly")
        print ("----------------------------------------------------------------------------------------------------------------------------------------------------------------")
        print ("If you dont have an account yet and want to register, then please type in 'register' below,")#asks for a decision
        print ("If you already have an account and want to sign in, then please type in 'login' below,")
        print ("If you just want to see the scoreboard, then please type in 'score' or 'scores' below.")
        decision = input(">>> ").lower()
        print ("----------------------------------------------------------------------------------------------------------------------------------------------------------------")
        if decision == "register":
            Register()
        elif decision == "login":
            Login()
        elif decision == "scores":
            Scores()
        elif decision == "score":
            Scores()
        
Enter()#a starter so as we open the program the code sends user to the entarance to make a decision.





                                
