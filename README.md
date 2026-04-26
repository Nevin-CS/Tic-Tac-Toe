[Tic Tac Toe AI Game for C++ Project Report.pdf](https://github.com/user-attachments/files/27105123/Tic.Tac.Toe.AI.Game.for.C%2B%2B.Project.Report.pdf)

[Day 1 Idea Submission on Tic Tac Toe - Nevin.docx](https://github.com/user-attachments/files/27105114/Day.1.Idea.Submission.on.Tic.Tac.Toe.-.Nevin.docx)
<img width="1051" height="667" alt="C++ Project on Tic Tac Toe" src="https://github.com/user-attachments/assets/9dd94223-fb88-4d32-b2b0-82482697dba6" />
<img width="332" height="213" alt="image" src="https://github.com/user-attachments/assets/e584eb6f-a8f1-4700-9cec-0bf3a6ae3ff9" 
  #include <iostream>
#include <cstdlib>
#include <ctime>
using namespace std;

void displayBoard(char board[3][3]) {
    cout << "\n";
    for (int i = 0; i < 3; i++) {
        cout << " ";
        for (int j = 0; j < 3; j++) {
            cout << board[i][j];
            if (j < 2) cout << " | ";
        }
        cout << "\n";
        if (i < 2) cout << "---|---|---\n";
    }
    cout << "\n";
}

bool checkWin(char board[3][3], char player) {
    for (int i = 0; i < 3; i++) {
        if (board[i][0] == player && board[i][1] == player && board[i][2] == player)
            return true;
        if (board[0][i] == player && board[1][i] == player && board[2][i] == player)
            return true;
    }
    if (board[0][0] == player && board[1][1] == player && board[2][2] == player)
        return true;
    if (board[0][2] == player && board[1][1] == player && board[2][0] == player)
        return true;
    return false;
}

bool checkDraw(char board[3][3]) {
    for (int i = 0; i < 3; i++)
        for (int j = 0; j < 3; j++)
            if (board[i][j] != 'X' && board[i][j] != 'O')
                return false;
    return true;
}

bool findBestMove(char board[3][3], char player, int &row, int &col) {
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) {
            if (board[i][j] != 'X' && board[i][j] != 'O') {
                char temp = board[i][j];
                board[i][j] = player;
                if (checkWin(board, player)) {
                    row = i;
                    col = j;
                    return true;
                }
                board[i][j] = temp;
            }
        }
    }
    return false;
}

void computerMove(char board[3][3]) {
    int row, col;
    if (findBestMove(board, 'O', row, col)) {
        board[row][col] = 'O';
        return;
    }
    if (findBestMove(board, 'X', row, col)) {
        board[row][col] = 'O';
        return;
    }
    if (board[1][1] != 'X' && board[1][1] != 'O') {
        board[1][1] = 'O';
        return;
    }
    srand(time(0));
    while (true) {
        int choice = rand() % 9;
        row = choice / 3;
        col = choice % 3;
        if (board[row][col] != 'X' && board[row][col] != 'O') {
            board[row][col] = 'O';
            return;
        }
    }
}

int main() {
    char board[3][3] = {
        {'1','2','3'},
        {'4','5','6'},
        {'7','8','9'}
    };

    int choice, row, col;

    cout << "Tic Tac Toe (Player vs Computer)\n";

    while (true) {
        displayBoard(board);

        cout << "Enter position (1-9): ";
        cin >> choice;

        row = (choice - 1) / 3;
        col = (choice - 1) % 3;

        if (choice < 1 || choice > 9 || board[row][col]=='X' || board[row][col]=='O') {
            cout << "Invalid move!\n";
            continue;
        }

        board[row][col] = 'X';

        if (checkWin(board, 'X')) {
            displayBoard(board);
            cout << "You win!\n";
            break;
        }

        if (checkDraw(board)) {
            displayBoard(board);
            cout << "Draw!\n";
            break;
        }

        computerMove(board);

        if (checkWin(board, 'O')) {
            displayBoard(board);
            cout << "Computer wins!\n";
            break;
        }

        if (checkDraw(board)) {
            displayBoard(board);
            cout << "Draw!\n";
            break;
        }
    }

    return 0;
}
<img width="636" height="786" alt="C++ Project on Tic Tac Toe Report" src="https://github.com/user-attachments/assets/45afc5a4-42b6-4c02-84fa-fadf9651b516" />
/>
