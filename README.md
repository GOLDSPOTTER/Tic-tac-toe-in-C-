using System;

public class Program
{
    public static void Main()
	{
		//game layout 0|1|2  
			//		  0|1|2	
			//		  0|1|2
		
		
        string[,] letters = {{"_","_","_"},{"_","_","_"},{"_","_","_"}};
        int Playerturn = 2; 
        bool gameover = false;
		int spotsleft = 9;
		//game welcome
		bool ready = false;
		Console.Write("Hello, welcome to tic tac toe!"); 
		while (!ready)
		{
		Console.WriteLine(" Click E to play");
		string ans = Console.ReadLine();
			if (ans == "e" || ans == "E"){ 
				ready = true;
			}
		}

		Console.WriteLine("Player 1 is X, player 2 is O. Press enter when your ready");
		Console.ReadLine();
        while(!gameover)
        { 
			Console.Clear();
			//draws the board for the game
            for (int i = 0; i < 3; i++)
            {
                for (int j = 0; j < 3; j++)
                {
                    Console.Write(letters[i, j]);
                }
                Console.WriteLine();
            }

            bool ask = true;

            while (ask && !gameover && spotsleft > 0)
            { 
				if (Playerturn == 1){
					Playerturn = 2;
				}else{ 
					Playerturn = 1;
				}
                Console.WriteLine("Player " + Playerturn + ", Write your first dim: "); //asks for column 
                int num1 = Convert.ToInt32(Console.ReadLine());
                Console.WriteLine("Player " + Playerturn + ", Write your second dim: "); //asks for row
                int num2 = Convert.ToInt32(Console.ReadLine());

                if (num1 < 0 || num1 >= 3 || num2 < 0 || num2 >= 3) //Checks if the number is valid
                {
                    Console.WriteLine("Invalid input. Please enter numbers between 0 and 2."); //Message if the number is invalid
                }
                else if (letters[num1, num2]  == "X" || letters[num1, num2] == "O") //Checks if the spot isn't already taken
                {
                    Console.WriteLine("This position is already taken. Try again"); //Message if the spot is already taken
                }
                else
                {
                    if (Playerturn == 1)
                    {
                        letters[num1, num2] = "X";
						spotsleft = spotsleft - 1;
                    }
                    else
                    {
                        letters[num1, num2] = "O";
						spotsleft = spotsleft - 1; 
                    }

                    ask = false;

					
					for(int i = 0; i < 3; i++){
						if(letters[0, i] == letters[1, i] && letters[1, i] == letters[2, i] && letters[0, i] != "_"){
							Console.WriteLine("Player {0} won!", Playerturn);
							// to do: swap number and i below!
						} else if(letters[i, 0] == letters[i, 1] && letters[i, 1] == letters[i, 2] && letters[i, 0] != "_"){
							
						}
					}
					
                    if (
                        (letters[0, 0] == letters[1, 1] && letters[1, 1] == letters[2, 2] && letters[1, 1] != "_") || //Winning diagonally right
                        (letters[0, 2] == letters[1, 1] && letters[1,1] == letters[2, 0] && letters[1, 1] != "_"))   //Winning diagonally left
                    {
                        gameover = true;
                        Console.WriteLine("Player {0} won!", Playerturn);
                    }
					/*
                    else if ((letters[0, 0] == "O" && letters[0, 1] == "O" && letters[0, 2] == "O") || //Winning horizonatlly top
                             (letters[1, 0] == "O" && letters[1, 1] == "O" && letters[1, 2] == "O") || //Winning horizonatlly middle
                             (letters[2, 0] == "O" && letters[2, 1] == "O" && letters[2, 2] == "O") || //Winning horizonatlly bottom
                             (letters[0, 0] == "O" && letters[1, 0] == "O" && letters[2, 0] == "O") || //Winning vertically left
                             (letters[0, 1] == "O" && letters[1, 1] == "O" && letters[2, 1] == "O") || //Winning vertically middle
                             (letters[0, 2] == "O" && letters[1, 2] == "O" && letters[2, 2] == "O") || //Winning vertically right
                             (letters[0, 0] == "O" && letters[1, 1] == "O" && letters[2, 2] == "O") || //Winning diagonally right
                             (letters[0, 2] == "O" && letters[1, 1] == "O" && letters[2, 0] == "O"))   //Winning diagonally left
                    {
                        gameover = true;
                        Console.WriteLine("Player 2 won!");
					
                    }*/
                }
            }
			
			//draw check
			if (spotsleft == 0)
			{
				gameover = true;
				Console.WriteLine("All positions taken. It's a draw!");
			}
        }				
    }				
}						
