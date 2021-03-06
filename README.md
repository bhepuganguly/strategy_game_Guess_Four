# strategy_game_Guess_Four
In this game, each of two players sets up a secret sequence of four decimal digits, where each digit is not repeated.
For instance, 2017 is a legal sequence, but 2012 is not because the digit 2 is repeated. The two players take turns guessing
the sequence of digits of their opponent. Each guess consists of a 4 digit number, without repeated digits. A player responds 
to an opponents guess by specifying the number of digits that were successfully guessed in the correct position and the number
of digits that were successfully guessed but in the wrong positions. Thus, if a players chosen number is 2017 and the opponent
guesses 1089, the opponent would be told that one digit was guessed correctly in the correct position (i.e., the 0), and
another digit was guessed in the wrong position, (i.e., the 1). This application has two background threads playing against
each other while also updating the user interface with their moves. The first thread to correctly guess the opposing thread’s 
number wins the game.
My implementation has two Java worker threads play against each other. The UI thread is responsible for creating and starting the two worker threads and for maintaining and updating the display. Each worker thread will take turns taking the following actions:
1. Waiting for a short time (1-2 seconds) in order for a human viewer to take note of the previous move on the display.
2. Figuring out the next guess of this thread.
3. Communicating this guess to the opponent thread.
4. Waiting for a response from the opponent thread.
5. Communicating both the guess and the response from the opposite thread to the UI thread.
While carrying out the above steps each worker thread must also be able to respond to guesses from the opponent thread. Whenever a guess from the opponent thread is received, a worker thread must respond by communicating the number of correctly positioned and incorrectly positioned digits contained in the guess to the opponent thread.
Furthermore, the game must proceed in lockstep between the two threads. A thread is not allowed to make two consecutive guesses without handling an intervening guess from the opponent thread.
The UI thread is specifically responsible for the following functionality:
1. Showing the two initial numbers chosen by the worker threads.
2. Receiving notifications of guesses and their outcomes by the worker threads.
3. Displaying the guesses and responses of each worker thread in an appropriate format as each worker thread communicates this information to the UI thead.
4. Displaying a button to start the game. Pressing this button while a game is in progress will void the current game and start a new game from scratch.
5. Checking on the status of the game, by determining whether one thread has won or the game needs to continue.
6. Halting the game after each thread has made 20 guesses without identifying the opponent’s number.
7. Signaling the two worker threads that the game is over; the two threads should stop their execution as a result of this action. Displaying the outcome of the game in the UI.
