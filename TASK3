#include <iostream>
#include <vector>

using namespace std;

void init(vector<vector<char>> &board)
{
    for (int i = 0; i < 3; i++)
    {
        vector<char> row(3, ' ');
        board.push_back(row);
    }
}

void viewBoard(const vector<vector<char>> &board)
{
    cout << "  1 2 3" << endl;
    for (int i = 0; i < 3; i++)
    {
        cout << i + 1 << " ";
        for (int j = 0; j < 3; j++)
        {
            cout << board[i][j];
            if (j < 2)
                cout << "|";
        }
        cout << endl;
        if (i < 2)
            cout << "  -+-+-" << endl;
    }
}

bool checkwin(const vector<vector<char>> &board, char player)
{
    for (int i = 0; i < 3; i++)
    {
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

bool checkDraw(const vector<vector<char>> &board)
{
    for (int i = 0; i < 3; i++)
    {
        for (int j = 0; j < 3; j++)
        {
            if (board[i][j] == ' ')
                return false;
        }
    }
    return true;
}

int main()
{
    vector<vector<char>> board;
    init(board);

    vector<char> players = {'X', 'O'};
    int currentPlayerIndex = 0;

    bool gameWon = false;
    bool gameDraw = false;

    cout << "TIC-TAC-TOE GAME" << endl;

    while (!gameWon && !gameDraw)
    {
        viewBoard(board);

        int row, col;
        char currentPlayer = players[currentPlayerIndex];
        cout << "Player " << currentPlayer << ", enter your move (row and column): ";
        cin >> row >> col;

        if (row < 1 || row > 3 || col < 1 || col > 3 || board[row - 1][col - 1] != ' ')
        {
            cout << "Invalid move. Try again." << endl;
            continue;
        }

        board[row - 1][col - 1] = currentPlayer;

        if (checkwin(board, currentPlayer))
        {
            viewBoard(board);
            cout << "Player " << currentPlayer << " wins!" << endl;
            gameWon = true;
        }
        else if (checkDraw(board))
        {
            viewBoard(board);
            cout << "It's a draw!" << endl;
            gameDraw = true;
        }
        else
        {
            currentPlayerIndex = (currentPlayerIndex + 1) % players.size();
        }
    }

    cout << "Do you want to play again? (yes/no): ";
    string playAgain;
    cin >> playAgain;

    if (playAgain == "yes" || playAgain == "y")
    {
        init(board);
        main();
    }
    else
    {
        cout << "Thanks for playing!" << endl;
    }

    return 0;
}
