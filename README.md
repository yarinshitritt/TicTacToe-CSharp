# TicTacToe-CSharp
using System;
using System.Data;
using System.Reflection.Metadata.Ecma335;

namespace ConsoleApp7
{
    class Program
    {
        static void Main(string[] args)
        {
            game g = new game();
            g.display();
            char p1 = 'X';
            char p2 = 'O';
            
            int player = 1;
            while (g.winner() == false && g.full()==false)
            {

                if (player == 1)
                    g.play( player , p1);

                else
                    g.play( player , p2);
                
                g.display();
                if (g.full()==true && g.winner()==false)
                    Console.WriteLine("game ends with tie");
                if (g.winner() == true)
                {
                    if (player == 1)
                        Console.WriteLine("Player 1 wins");
                    else
                        Console.WriteLine("Player 2 wins");

                }
                if (player == 1)
                    player = 2;
                else
                    player = 1;
             }
           
        }
    }
    class game
    {
        private char[,] board;
        public game()
        {
            this.board = new char[3, 3];
            for (int i = 0; i < board.GetLength(0); i++)
            {
                for (int j  = 0; j  < board.GetLength(1); j ++)
                {
                    this.board[i, j] = ' ';
                }
            }
        }
        public bool winner()
        {
            for (int i = 0; i < board.GetLength(0); i++)
            {
                if (this.board[i, 0] == this.board[i, 1] && this.board[i, 0] == this.board[i, 2]&& this.board[i, 0]!=' ')
                    return true;
                if (this.board[0, i] == this.board[1, i] && this.board[0, i] == this.board[2, i] && this.board[0,i] != ' ')
                    return true;

            }
            if (this.board[0, 0] == this.board[1, 1] && this.board[0, 0] == this.board[2, 2] && this.board[0, 0] != ' ')
                return true;
            if (this.board[0, 2] == this.board[1, 1] && this.board[0, 2] == this.board[2, 0] && this.board[0, 2] != ' ')
                return true;
            return false;
        }   
        public void display ()
        {
            Console.WriteLine(this.board[0,0] + "|" + this.board[0, 1] + "|" + this.board[0, 2]);
            Console.WriteLine("-----");
            Console.WriteLine(this.board[1, 0] + "|" + this.board[1, 1] + "|" + this.board[1, 2]);
            Console.WriteLine("-----");
            Console.WriteLine(this.board[2, 0] + "|" + this.board[2, 1] + "|" + this.board[2, 2]);
        }
        public void play (int player,char ch)
        {
            int row;
            int col;
            Console.WriteLine("player " + player + " enter row (0-2):");
            row = int.Parse(Console.ReadLine());
            Console.WriteLine("player " + player + " enter col (0-2):");
            col = int.Parse(Console.ReadLine());
            while (row<0||row>2||col<0||col>2 || this.board[row, col] != ' ')
            {
                Console.WriteLine("input is invalid, enter again:");
                Console.WriteLine("player " + player + " enter row (0-2):");
                row = int.Parse(Console.ReadLine());
                Console.WriteLine("player " + player + " enter col (0-2):");
                col = int.Parse(Console.ReadLine());
            }
            this.board[row, col] = ch;
            
        }
        public bool full()
        {
            for (int i = 0; i < board.GetLength(0); i++)
            {
                for (int j = 0; j < board.GetLength(1); j++)
                {
                    if (this.board[i, j] == ' ')
                        return false;
                    
                }
                
            }
            return true;
        }
    
    }
}
    
