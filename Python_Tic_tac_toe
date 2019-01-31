"""Tic_tac_toe
A program to play a game of tic-tac-toe


Quick run by copying and pasting into
https://www.onlinegdb.com/online_python_compiler

...


Functions
-------
getValue(key)
    gets the value to be displayed on the gameboard

displayCurrentBoard()
    Displays the current gameboard

makeMove(piece)
    Validates user input and stores the move of the piece in a list

checkWin(currentMoves, piece)
    Checks if a piece has won
"""

import sys

def getValue(key):
    """Gets the value to be displayed on the gameboard to the user
    
    If the value is empty in the dictionary, the key name, representing a 
    space on the board will be displayed,so the user knows how what 
    to type in to choose a space
    
    Parameters
    ----------
    
    key : str
        the key, representing a position on the board, to be looked up
    """
    
    return key if gameBoard.get(key) == ' ' else gameBoard.get(key) 


def displayCurrentBoard():
    """Displays the current moves on gameboard
        
    Displays the current moves made and the names of the spaces that 
    can be chosen  
    """
    
    print() 
    print(getValue('top_l') + ' | ' + getValue('top_m') + ' | ' 
            + getValue('top_r'))
    print('----------------')
    print(getValue('mid_l') + ' | ' + getValue('mid_m') + ' | ' 
            + getValue('mid_r'))
    print('----------------')
    print(getValue('bot_l') + ' | ' + getValue('bot_m') + ' | ' 
            + getValue('bot_r'))
    print()


def makeMove(piece):
    """Validates user input and stores the move of the piece in a list
    
    Checks the input of the user to make sure the move is valid.
    Will then make the move by adding the space to the appropiate
    pieces list, so that the piece list can be checked for a winning 
    set of moves.
    
    Parameters
    ----------
    
    piece : str
        'X' or 'O' represents what piece is taking a turn
    """
    displayCurrentBoard()
    
    #check input
    print('Enter the move for \'' + piece + ('\''))
    userInput = input()
    
    while acceptedMoves.count(userInput) == 0: 
        print('Please enter a valid move for \'' + piece + ('\''))
        userInput = input()
    
    #make move
    userMove = acceptedMoves.pop(acceptedMoves.index(userInput))
    gameBoard[userMove] = piece #updates dictionary item as userMove:piece 

    if piece == 'X':
        xMoves.append(userMove)
        checkWin(xMoves, piece)
    else:
        oMoves.append(userMove)
        checkWin(oMoves, piece)



def checkWin(currentMoves, piece): 
    """Checks to see if a piece has won 
    
    Holds all eight winning combinations. This function will check if a 
    winning combination is held within a pieces list of moves made
    (currentmoves)
    
    Parameters
    ----------
    currentMoves : list 
        all current moves of the piece 
    
    piece : str
        'X' or 'O', piece that is currently making a move 
    """
    
    winList = []
    winList.append(['top_l', 'mid_l', 'bot_l']) #leftWin
    winList.append(['top_m', 'mid_m', 'bot_m']) #middle verticle win 
    winList.append(['top_r', 'mid_r', 'bot_r']) #rightWin
    winList.append(['top_l', 'top_m', 'top_r']) #top win
    winList.append(['mid_l', 'mid_m', 'mid_r']) #middle horizontal win
    winList.append(['bot_l', 'bot_m', 'bot_r']) #bottom win 
    winList.append(['bot_l', 'mid_m', 'top_r']) #ascending diagional win
    winList.append(['top_l', 'mid_m', 'bot_r']) #descending diagional win
    
    if (len(currentMoves) > 2):
        for winOption in winList:
            if(all(elem in currentMoves for elem in winOption)):
                displayCurrentBoard()
                print(piece + ' has won! Play again soon')
                sys.exit(0)

"""Code below displays the welcome screen and runs each turn
This is the main() of the program. 

Attributes
----------

gameBoard : dictionary
    set of items representing the spaces and the piece in a space

acceptedMoves : list
    set of moves valid for a turn

xMoves : list
    all current positions of the 'X' piece

oMoves : list   
    all current positions of the 'O' piece

totMoveCnt : int
    keeps track of the number of moves made
"""

gameBoard = {'top_l': ' ', 'top_m': ' ', 'top_r': ' ',
    'mid_l': ' ', 'mid_m': ' ', 'mid_r': ' ',
    'bot_l': ' ', 'bot_m':' ', 'bot_r': ' '}
acceptedMoves = list(gameBoard.keys())
acceptedMoves.sort()
xMoves = []
oMoves = []
totMoveCnt = 0 

print('Welcome, Welcome, This is Tic-Tac-Toe')
print('Please type in the names as you see them on the board')
print('The available moves are: ')

while totMoveCnt <=9: 
    makeMove('X') if totMoveCnt % 2 == 0 else makeMove('O')
    totMoveCnt += 1
