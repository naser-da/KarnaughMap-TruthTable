/*
 Karnaugh Map of 3 variables
 by: Naser Dakhel
** Date: 13/12/2019
*/
#include <bits/stdc++.h>
using namespace std;

int kmap[2][4] = {0};
int kmap_mod[2][6]; //a copy of kmap (the addition is size is to avoid getting out of bound)
int kmap_s[2][4];   //same size as kmap
bool x, y, z;
bool truth[8][4] =
    {
        {0, 0, 0, 0}, {0, 1, 0, 0}, {1, 1, 0, 0}, {1, 0, 0, 0}, {0, 0, 1, 0}, {0, 1, 1, 0}, {1, 1, 1, 0}, {1, 0, 1, 0}}; //initiate the truth table {x,y,z,f}

void truthCalc() //this function calculates and prints the truth table
{
    for (int i = 0; i < 8; i++)
    {
        x = truth[i][0];
        y = truth[i][1];
        z = truth[i][2];
        //the boolean equation
        bool eq = (x && !y) || (y && z);
        //f(x,y,z)=(x.y')+(y.z)
        truth[i][3] = eq;
    }

    //this code prints out the truth table of the boolean equation
    cout << "x|y|z|f" << endl;
    for (int i = 0; i < 8; i++)
    {

        for (int j = 0; j < 4; j++)
        {
            cout << truth[i][j] << " ";
        }
        cout << endl;
    }
    cout << endl;
}

void kmapCalc() //to store karnaugh map into kmap array
{
    for (int i = 0, k = 0; i < 2; i++, k += 4)
    {
        for (int j = 0; j < 4; j++)
        {
            kmap[i][j] = truth[j + k][3];
            kmap_mod[i][j + 1] = truth[j + k][3];
        }
    }
    //this piece of code is to prevent getting out of bound
    kmap_mod[0][0] = kmap[0][3];
    kmap_mod[0][5] = kmap[0][0];
    kmap_mod[1][0] = kmap[1][3];
    kmap_mod[1][5] = kmap[1][0];

    //prints the kmap
    cout << "Kmap" << endl;
    for (int i = 0; i < 2; i++)
    {
        for (int j = 0; j < 4; j++)
            cout << kmap[i][j] << " ";
        cout << endl;
    }

    /* for(int i=0; i<2; i++) //prints the kmap_mod
    {
        for(int j=0; j<6; j++)
            cout<<kmap_mod[i][j]<<" ";
        cout<<endl;
    }*/
}

void findgroup2()
{
    for (int i = 0; i < 2; i++)
    {
        for (int j = 1; j < 5; j++)
        {
            if (kmap_mod[i][j] == 1)
            {
                bool up;
                int left = 0; //left = 1 (the cell is on the upper left corner)
                if (i == 0)
                    up = true;
                else
                    up = false;
                if (j == 1)
                    left = 1;
                kmap_s[i][j] = 1;

                if (up) //if the cell is in the first line
                {
                    if (kmap_mod[i + 1][j] == 1) //checking the cell below
                    {
                        kmap_s[i + 1][j] = -2;
                        kmap_mod[i][j] = 0;
                    }
                    if (left = 1) //cell is in the upper left corner
                    {
                        if (kmap_mod[i][j + 1] == 1) //checking the cell on the right
                        {
                            kmap_s[i][j + 1] = -2;
                            kmap_mod[i][j + 1] = 0;
                        }
                        if (kmap_mod[i][j - 1] == 1) //checking the cell on the left
                        {
                            kmap_s[i][j + 3] = -2;
                        }
                    }

                    else
                    {
                        if (kmap_mod[i][j + 1] == 1) //checking the cell on the right
                        {
                            kmap_s[i][j] = -2;
                        }
                    }
                }

                else if (!up) //if the cell is in the second line
                {
                    if (kmap_mod[i - 1][j] == 1) //checking the cell above
                    {
                        kmap_s[i - 1][j] = -2;
                    }
                    if (kmap_mod[i][j + 1] == 1) //checking the cell on the right
                    {
                        kmap_s[i][j + 1] = -2;
                    }
                    if (kmap_mod[i][j - 1] == 1) //checking the cell on the left
                    {
                        kmap_s[i][j - 1] = -2;
                    }
                }
            }

            else if (kmap_mod[i][j] == 0) //if the kmap cell is equal to zero set the kmap_s responding cell to '-1'
            {
                kmap_s[i][j - 1] = -1;
            }
        }
    }

    //    for (int i = 0; i <)

    for (int i = 0; i < 2; i++) //prints the kmap_mod
    {
        for (int j = 0; j < 6; j++)
            cout << kmap_s[i][j] << " ";
        cout << endl;
    }
}

int main()
{
    truthCalc();
    kmapCalc();

    return 0;
}
