

```python
from __future__ import print_function
```


```python
print("hello")
```


```python
from IPython.display import clear_output
def display_board(board):
    clear_output()
    print('  |   |  ')
    print(''+board[7]+' | '+board[8] +' | '+board[9])
    print('  |   |  ')
    print('---------')
    print('  |   |  ')
    print(''+ board[4]+ ' | '+ board[5] + ' | '+ board[6])
    print('  |   |  ')
    print('---------')
    print('  |   |  ')
    print(''+ board[1]+ ' | '+ board[2] + ' | '+ board[3])
    print('  |   |  ')
```


```python
board = ['Z','O', 'X', 'O', 'X', 'O','O', 'X', 'O', 'X']
display_board(board)
```


```python
def player_input():
    marker = ''
    while not (marker == 'O' or marker == 'X'):
        marker = raw_input('Player 1: Do you want to be X or O? ').upper()
        if marker =='X':
            return ('X', 'O')
        else:
            return ('O', 'X')
```


```python
player_input()
```


```python
def place_marker(board, marker, position):
    board[position] = marker
```


```python
def win_check(board, mark):
    return ((board[7] == mark and board[8] == mark and board[9] == mark)
           (board[4] == mark and board[5] == mark and board[6] == mark)
           (board[1] == mark and board[2] == mark and board[3] == mark)
           (board[7] == mark and board[4] == mark and board[1] == mark)
           (board[8] == mark and board[5] == mark and board[2] == mark)
           (board[9] == mark and board[6] == mark and board[3] == mark)
           (board[7] == mark and board[5] == mark and board[3] == mark)
           (board[9] == mark and board[5] == mark and board[1] == mark))
```


```python
import random
def choose_first():
    if random.randint(0,1) == 0:
        return 'Player 1'
    else:
        return 'Player 2'
```


```python
def space_check(board, position):
    return board[position] == ' '
```


```python
def full_board_check(board):
    for i in range(1, 10):
        if space_check(board, i):
            return False
    return true
```


```python
def player_choice(board):
    position = ' '
    while position not in '1 2 3 4 5 6 7 8 9'.split() or not space-check(board, int(position)):
        position = raw_input('Choose your next position: (1-9)')
    return int(position)
        
```


```python
def replay():
    return raw_input('Do you want to play again? Enter Yes or no').lower().startswith('y')
```


```python
print('Welcome to Tic Toe Tac')
while True:
    theBoard = [' ']*10
    player1_marker, player2_marker = player_input()
    turn = choose_first()
    print(turn  + 'will go first')
        
    game = True
    while game :
        
        if turn == "Player 1":
            display_board(theBoard)
            position = player_choice(theBoard)
            place_marker(theBoard, player1_marker,position)
            if win_check(theBoard, player1_marker):
                display_board(theBoard)
                print('Congratulations1')
                game = False
            else:
                if full_board_check(theBoard):
                    display_board(theBoard)
                    print('the game is a draw!')
                    break
                else:
                    turn = 'Player 2'
        else:
            display_board(theBoard)
            position = player_choice(theBoard)
            place_marker(theboard, player2_marker,position)
                    
            if win_check(theBoard, player2_marker):
                display_board(theBoard)
                print('Congratulations2')
                game = False
            else:
                if full_board_check(theBoard):
                    display_board(theBoard)
                    print('the game is a draw!')
                    break
                else:
                    turn = 'Player 1'
    if not replay():
        break
        
```
