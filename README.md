//C++ code to play guessing a number game
//You only can play it using terminal(console)
//created by Snowfall2279.. 06/05/2020

#include <iostream>
#include <cmath>
#include <string>
#include <cstdlib>
#include <ctime>
#include <vector>
#include <array>
#include <fstream>

using std::cout;
using std::cin;
using std::string;
using std::endl;
using std::hex;
using std::vector;
using std::ifstream;
using std::ofstream;

void print_vector(vector<int> nums)
{
    for(int i = 0; i < nums.size(); i++)
    {
        cout << nums[i] << "\t";
    }
    cout << endl;
    cout << "You tried " << nums.size() << " times" << endl;
    cout << endl;
    cout << " if you want to Play again please enter 1" << endl;
    cout << endl;
}

void play_game()
{
    vector <int> guesses;
    int count = 0;
    
    int random = rand()%300;
    cout << "Please guess a number\n" << endl;

    while(true)
    {

        int guess;
        cin >> guess;
        count++;

        guesses.push_back(guess);

        if(guess == random)
        {
            cout << " You Win  \n";
            break;
        }
        else if (guess < random)
        {
            cout << "Guess is lower than the number. Try Again\n";
        }
        else
        {
            cout << " Guess is higher than the number. Try again\n";
        }
        
    }
    ifstream input("Best_score.txt");

    int Best_score;
    input >> Best_score;

    ofstream output("Best_score.txt");
    if(count < Best_score)
    {
        output << count;
        cout << "BEST SCORE " << count << "    Congratulations!!!!" << endl;
    }
    else 
    {
        output << Best_score;
    }
    print_vector(guesses);

    cout << "your Best Score Was " << Best_score << endl;
}

int main()
{
    srand(time(NULL));
    int choice;
    do
    {
        cout << "0. Quit\n1. Play games\n";
        cin >> choice;

        switch(choice)
        {
            case 0:
                    cout << " Thank you. Come again later\n";
                    break;
            case 1:
                    play_game();
                    break;
        }
    
    } while(choice != 0);
    
} 

