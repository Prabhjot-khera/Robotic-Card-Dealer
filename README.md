# Robotic-Card-Dealer

# Description of the software  

 

# Overall Program 

 

The overall program was broken up into functions that would complete their respective tasks. A lot of functions were included to not only meet the criteria but to make the main code simpler. The tasks that broke up the code are as following. 

Input functions were used to get user input and to be called once in main 

Error functions were used for simplicity in main and to ensure inputs were valid 

Drive functions were used for movement of the robot 

Dispense function was used to dispense cards 

Remainder function was used to ensure correct number of cards were dealt and to calculate the remaining cards 

Rotate function was used to rotate to the person 

A lot of functions were used within other functions as they were built to be used by each other. For example, the input functions being nested in the error functions to ensure valid inputs were given. 

Diagram

Description automatically generated 

Figure 15: Overall flow chart 

 

# Task list 

 

The tasks required from the software to perform during the demo are as follows. 

 
 

Robot starts up  

Robot does test motion (moves forward, backward, spins) 

User enters number of players  

User enters number of cards  

Robot goes to colored tape at table centre 

Deals to the respective number of players 

Robot exits game playing area after dealing  

Robot dumps out remaining cards  

Robot displays number of cards dealt 

Touch sensor to be used as an emergency exit  

 

Throughout the entirety of the project most of the requirements of the robot did not change. However, the task of the robot adjusting itself using an ultrasonic sensor was taken out because it did not improve the accuracy of the dealing by a notable degree. 

 

# Functions 

 

Test_ Function (parameters: none, return type void) 

 

The test function was written by Sachin. This function performs a test motion in the beginning to ensure that the gyro and motors are working correctly while carrying a deck of cards.  

Diagram

Description automatically generated 

Figure 1616: Flowchart for Test Function 

 
 

Drive_ to _Colour (parameters: int colour, return type float) 

 

This function was written by Savyo and takes an input of a number associated with a colour. It then turns the motors on and drives the robot forward until the colour sensor senses the inputted colour as seen in the flow chart.  

Diagram

Description automatically generated 

Figure 1717: Flowchart Color sensor 

 

Rotate _dealer (parameters: int players, return type void): 

 

This function was written by Cheran and takes an input of the number of players in the game and rotates the robot using the gyro sensor. To calculate the angle to rotate a trivial function is called. An example of how the angle is calculated is as follows. If there were 10 players, the function would call the trivial function and divide one rotation (360 degrees) by 10 to rotate the robot by 36 degrees. Note that it rotates clockwise by setting one motor power to a positive value and the other to a negative value. The chronological order of how the function works can be seen in the following flow chart. 

Diagram

Description automatically generated 

Figure 1818: Rotating and deal flow chart 

 
 
 

Number_of_players(parameters: none, return type int)  

 

This function was written by Prabhjot and is used to acquire user input to determine the number of players in the card game. The function requires the user to use the left and right button to increment or decrement the number of players. Each time the right button is clicked the function will increment the counter by 1, when the enter button is clicked the function will return the counter and exit the function. 

 

Diagram

Description automatically generated 

Figure 1919: Number of players flowchart 

 

Input_error(parameters: none, return type int) 

 

This function was written by Savyo and is used to error check the user input of the number of cards. It uses a while loop and within the loop calls the number_of_players functions. Once it gets the input from the user it checks if it meets the condition of less than 12 and greater than 1 player was inputted. If not it will display that there is an invalid input and iterate through the while loop again. Once a valid input is given the while loop will break and will return the number of players. 

 
 

Number_of_cards(parameters: none, return type int):  

 

This function was written by Sachin and is used to acquire user input to determine the number of cards per person in the card game. The function requires the user to use the left and right button to increment or decrement the number of cards. Each time the right button is clicked the function will increment the counter by 1, when the enter button is clicked the function will return the counter and exit the function.  

 
 

Diagram

Description automatically generated 

Figure 2020: number of cards flowchart 

 

Cards_error(parameters: int players, return type int): 

 

This function was written by Cheran and is used to error check the number of cards inputted. It takes in a parameter of the number of players. It then uses a while loop to ensure that the total number of cards does not exceed 52. For example, if there are 10 players, within the while loop it will run the number_of_cards function and then multiply that number of cards per person by 10. If 8 cards were inputted it will multiply it so that 80 cards are needed total. However, 80 cards exceeds the maximum, in this case an error message will be outputted on the EV3 display and iterate through the while loop again. Once a valid input is given the function will return the amount of cards per person. 

 
 

 

Diagram

Description automatically generated 

Figure 21 21: cards error flowchart 

 

Dispense_cards(parameters: int players, return type void): 

This function was written by Prabhjot and is used to dispense 1 round of cards. It uses a for loop for the number of players. Within 1 iteration of the for loop it calls on the rotate_dealer function to rotate the dealer to a person. It then turns on motor to dispense a card. It breaks the for loop once each person gets one card. 

Diagram

Description automatically generated 

Figure 2222: dispense cards flowchart 

 
 

Remainder Dispense(parameters: int players and cards, return type int) 

 

This function was written by Savyo and is used to dispense an equal amount of cards to each player. First it uses the modulus operator to ascertain the amount of remaining cards. For example, with 10 players 52%10 will return 2. Which entails that 50/52 cards should be dealt. Then a while loop is used where it breaks if the number of cards dealt becomes greater than or equal to the maximum amount set beforehand. Within this while loop the dispense_cards function is used. To keep track of how many cards were dealt a counter is used that increments by the number of players each iteration. It increments by the number of players as when the dispense_cards function is called it will deal one card per person. Finally, the function returns the remainder. This can be seen in the flowchart below.  

 

Diagram

Description automatically generated 

 

Figure 2323: Remainder dispense flowchart  

 

Exit_code (parameters: int players, float distance, int remainder, return type void) 

 

This function was written by Sachin and performs a set of tasks to end the function of the robot. The robot reverses out of the playing field (using the inputted distance), deals the remaining card to the side to act as a bank of cards, displays the number of cards dealt and turns off  [3]. This can be seen in the flowchart. 

Diagram

Description automatically generated 

Figure 2424: Exit Code flowchart 

 

# Trade-offs 

The choice of resetting the Gyro after each rotation was an action that resulted in a trade-off. Doing so, made it so that the team did not need to implement the incrementing rotation code. However, it did result in a reoccurring error of a few degrees. Meaning, after many rotations, the robot was off course by a significant angle. Another trade-off resulted due to the choice of not to implement the ultrasonic sensor. This forced the user to direct the robot towards a player rather than enabling it to start from any point on the table's perimeter. 

 

 

 

# Choice of variable type 

 

A vast majority of the variables used in the team's code were in the form of either floats or integers. The code required integers to count objects like cards as they are single entities and cannot be in the form of fractions. Integers were also used in all the for loops in the form of counters. The use of floats can primarily be found using the distance variables. These variables had recorded the value from the motor encoder which was then converted to centimeters using pi. This value will not be an exact integer meaning that it will include a fractional segment as well. 

 

# Testing 

 

In terms of testing the main code, the group decided to take a similar approach to the MTE-121 tutorials where the group would test out functions one at a time. The group initially tested the test motion function to ensure all the motors and sensors were set up properly as well as to check if the robot was driving and rotating properly. In doing so, it also tested out primary functions which included drive and drive all. Next, the group began testing the drive_to_colour function. The group expected this function to stop the robot once it had detected a certain colour. The group had to test this function to ensure the robot did not drive off a table when the program was run. This function would enable the robot to stop at the Centre of a table, denoted by the colour. After doing so, the group tested the robot’s ability to deal a single card at a time by running the dispense card's function. This test was run to ensure that the cards were being dealt one at a time, as otherwise it would defeat the purpose of the robot. The testing purposes had a set number of rotations and cards that the robot would deal with. This function required the most amount of testing and configuring as the timings would need to be changed each day. The group expected this function to have the robot dispense a single card at a time while also rotating a certain angle repeatedly with a certain level of accuracy. 

 

 

# Problems 

 

There were a few problems that occurred with the software. The most prominent issues include the user input double counting and implementing the emergency exit button. 

 

The card dealer requires a user to use the right and left button to increment or decrement the number of players and cards that were needed. At first the function only waited for the button to be clicked. Due to the speed at which the loops were being iterated through the counter would not increase/ decrease by 1. Before the user could lift their finger, it would count it as 2 or even 3 clicks. To overcome this issue, the group added a condition to the function such that it would not go to the next iteration until the button was released. A while loop was used so that the function would not progress while the button was being pressed as seen in the image below. 

 

 

Graphical user interface, text

Description automatically generated with medium confidence 

Figure 2525: input player function 

 

The other issue was the implementation of the emergency exit button. The robot uses the touch sensor to end the program if something were to go wrong. At first the program would not terminate with the touch sensor while the code was within a loop. For example, while the robot was executing the drive_to_colour function it would not stop while it was performing the loop to drive till the colour was sensed. It was also not very practical to add a lot of if statements to check if the touch sensor was clicked. To overcome this, the group used a separate task to perform multitasking within the code. Alongside the main task a separate task was executed in tangent to the main that continuously checked for the condition of the touch sensor being pressed.  

 

Graphical user interface, text

Description automatically generated with medium confidence 

Figure 26 26: emergency touch stop 

 

 

# Verification 

Shape 

Final Constraints List 

 

Below was the final criteria list, and how the group met each criteria during the demo.  

 
 

Completes test motions well 

It did what it was programmed to do. Drove forward, backward, and spun.  

 
 

Detects red and stops  

The color sensor stopped precisely at the red tape the group had laid out for it.  

 
 
 

Invalid inputs for number of players are detected and user is informed (i.e., 25 players) 

After inputting an impractical number of players, the robot told the user this is impossible.  

 
 
 

Deals in general direction to player (distinct piles) 

Although the gyro is inconsistent, the robot was able to deal in 3 distinct piles so that the players were able to tell that a specific pile was theirs.   

 
 
 

Deals to correct number of players 

During the demo the group put 3 players in, and the robot rotated and dealt to the 3 spots.  

 
 
 

Escapes area cleanly 

The program used the number of players to calculate an angle where cards would not be so it could escape. This was done cleanly during the demo as no dealt cards were moved/hit.  

 
 
 

Dumps remainder of cards out 

After escaping it dumped out all excess cards.  

 
 
 

Displays correct number of cards dealt  

The robot displayed 12 cards on the screen (3 players, 4 cards). 
