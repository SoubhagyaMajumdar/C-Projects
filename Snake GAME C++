#include<iostream>
#include<conio.h>   // Library ---> Console input & output

using namespace std;

bool GameOver;     // Global variable

const int Width = 100;        // 'Width' and 'Height' of the map
const int Height = 30;

int x, y;    // Position of HEAD
int fruitX, fruitY;    // Position of the 'fruit'
int score;
int TailX[100], TailY[100];
int nTail;
enum eDirection {STOP=0, LEFT , RIGHT, UP, DOWN};
enum eDirection  direction;       // This will hold the Direction of the "Snake"


void Setup()
{
    GameOver = false;

    direction = STOP;   // "Snake" will not move, until we move it.
 
    x = Width/2;       // So the "Snake" will be at the 'Center' of the Map
    y = Height/2;

    fruitX = rand() % Width;    // The 'fruit' can be in any random position , But within the 'Map'
    fruitY = rand() % Height;

    score = 0;    // Initially 'Score' = 0

}


void Draw()
{
    system("cls");      // CLEAR the Screen

    for(int i=0; i<Width+2; i++)     // Draw Upper Wall
       cout <<"#";
    cout<<endl;


    for(int i=0; i<Height; i++)
    {
        for(int j=0; j<Width; j++)
        {
            if(j == 0)
                cout <<"#";

                if(i == y && j == x)
                    cout<<"O";

                else if(i == fruitY  &&  j == fruitX)
                    cout<<"F";
    
                else
                {
                    bool Print = false;
                    for(int k=0; k < nTail; k++)
                    {
                        if(TailX[k] == j && TailY[k] == i)
                        {
                            cout<<"o";
                            Print = true;
                        }
                    }
                    if(!Print)
                    {
                        cout <<" ";
                    }
                }
            if(j == (Width-1))
                cout <<"#";
        }
        cout<<endl;
    }


    for(int i=0; i<Width+2; i++)     // Draw Bottom Wall
       cout <<"#";
    cout<<endl;

    cout<<"Score = "<< score <<endl;         // Prints the "Score"
}



void Input()
{
    if( _kbhit() )     // if Keyboard 'key' is hit
    {
        switch( _getch() )
        {
            case 'w':
                direction = UP;
                break;
            case 'a':
                direction = LEFT;
                break;
            case 'd':
                direction = RIGHT;
                break;
            case 's':
                direction = DOWN;
                break;
            case 'x':
                GameOver = true;
                break;

        }
    }
}



void Logic()
{
    int prevX = TailX[0];
    int prevY = TailY[0];
    int prev2X, prev2Y;

    TailX[0] = x;
    TailY[0] = y;

    for (int i = 0; i < nTail; i++)
    {
        prev2X = TailX[i];
        prev2Y = TailY[i];
        TailX[i] = prevX;
        TailY[i] = prevY;
        prevX = prev2X;
        prevY = prev2Y;
    }    
    

    switch (direction)
    {
        case LEFT:
            x--;            
            break;
        case RIGHT:
            x++;            
            break;
        case UP:
            y--;
            break;
        case DOWN:
            y++;
            break;
    
        default:
            break;
    }

    if(x>Width || x<0 || y>Height || y<0)
    {
        GameOver = true;
        cout<<"Game Over"<<endl;
    }

    if(x == fruitX  &&  y == fruitY)
    {
        score += 1;
        fruitX = rand() % Width;    // The 'fruit' can be in any random position , But within the 'Map'
        fruitY = rand() % Height;

        nTail++;
    }
}



int main()
{
    Setup();

    while(!GameOver)
    {
        Draw();
        Input();
        Logic();
    }    

    return 0;
}
