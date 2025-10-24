# Minimax TicTacToe

In this project, we utilized concepts about adversarial search, minimax algorithm, and alpha-beta pruning. 

![Screenshot](https://github.com/UPHSL-CCS-J3A/build-a-minimax-tic-tac-toe-ttetromino/blob/70a09b9392bf7fa42d9aa1915186fa8940d9b4cf/TicTacToe%20Game%20Screenshot.png)

## Minimax Algorithm Implementation

Adversarial search is a concept on game theory where we create agents with strategic-thinking, enabling them to function in a competitive environment against players. The minimax algorithm is an algorithm that allows the program to select the best possible move against the player. In the code, these are the values that track the game state:

- **MAX player** (AI - 'O'): Aims to maximize the score
- **MIN player** (Human - 'X'): Aims to minimize the score

## Alpha-beta Pruning Implementation

We can actually run the game without implementing pruning, but it will really slow the game. Without pruning the tree, the program would need to evaluate all possible combinations and moves every step. Though it won't change how optimally it plays the game, the program would be able to run efficiently.

1. Set up function where the board represents the current game state and alpha-beta pruning is bounded to -2 and 2)
```
def alphabeta(board, player, alpha=-2, beta=2, me='O', opp='X'):
    if terminal(board):
        return utility(board, me, opp), None
```

For the following implementation, we'll be looking at the MAX part which is similar to the MIN.

2. MAX starts with the worst possible score (-2), explores opponent's responses with current alpha/beta bounds and then update the game if they found a better score.
```
if player == me:
        best = (-2, None)  # MAX
        for m in moves(board):
            b2 = board[:]; b2[m] = player
            val, _ = alphabeta(b2, opp, alpha, beta, me, opp)
            if val > best[0]:
                best = (val, m)
```

3. Prune if the program found an optimal move. Return the best move to the play_game() loop.
```
                alpha = max(alpha, val)
                      if alpha >= beta:  # prune
                          break
        return best
```

## Reflection

Personally, a challenge that I faced was thinking about how I would manipulate it. I originally wanted to add some other features to the program, but due to external factors, I wasn't able to do it in the time I have. I think I wasted a lot of time trying other things than just understanding the concepts and the code more. 

[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=21272943&assignment_repo_type=AssignmentRepo)
