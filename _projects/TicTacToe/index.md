---
layout: post
title: C-Based Tic-Tac-Toe Engine
description: To advance my skills in programming and C language - a core skill applied in microcontroller-involved projects - I designed and developed a fully functional command-line version of Tic-Tac-Toe. This project was focused on array manipulation and developing a robust game loop. 
skills: 
- C Programming
- Automatic algorithm
main-image: /mainimg.png
---

---
# The Challenge
The challenge of this project was creating an efficient system of functions to implement the game rules, allow the creation of a simple interface that is user friendly, and the creation of a computer for the player to play against.

# Technical Implementation

### **Game Logic:**
The main game was built on a _while loop_ structure to manage game information (player turn, computer turn, win check, and draw check). This mirrors the state machine logic used in embedded systems.

### **Data Structures:**
Since Tic-Tac-Toe is a game on a 3x3 grid, 2D arrays were used to represent the game board. Algorithms were developed to iterate through row, columns, and diagonals to detect conditions for win check as well as computer response.

### **Input and Validation:**
A simple function to take player input was implemented within the game loop, along with an error-handling function to make sure the program does not crash if user inputted an invalid data.

### **Modular Design:**
The program was structured into distinct functions such as print board, player input, player move, win check, and more. This was done to ensure that the program was easy to debug. <br>

Upon starting the game, the player will be given the option to play against another in a pass and play manner or play against the computer. The figure below shows the starting message of the game.<br>

{% include image-gallery.html images="intro.png" height="300" %} <br>

One notable function is the function to take the player input. In this function, there are embedded error checking system that simply uses three if functions, to make sure that the player input is valid. Finally, the program outputs the position that the player wants to put their marks on, as seen on the code snippet below.<br>

```C
void input(int *m, int *n, char *p, char a[3][3])
{
    char y1;
    int x,y;
    do 
    {
        y=0;
        printf("\n%c to move, enter coordinate: ", *p);
        scanf(" %C%d", &y1, &x);
        if(y1 == 'A' || y1 == 'a') y=1;
        if(y1 == 'B' || y1 == 'b') y=2;
        if(y1 == 'C' || y1 == 'c') y=3;

        if(x < 1 || x > 3 || y==0 || a[x-1][y-1]!=' ') printf("Invalid move!\n\n");
    }   while(x < 1 || x > 3 || y==0 || a[x-1][y-1]!=' ');
    
    *m = x;
    *n = y;
    
    printf("\n");
}
```
<br>
One important function is a function to check for wins and draws. The code scans for all horizontal, vertical, and diagonal part of the board and checks if there are filled with the same marks. The code snippet below shows the if functions that are used to check for wins. <br>

```C
int wincheck(char a[3][3], char *p)     // function to check for wins
{
    int i;
    for(i=0; i<3; i++) // row check
        if(a[i][0] == *p && a[i][1] == *p && a[i][2] == *p) return 1;

    for(i=0; i<3; i++) // col check
        if(a[0][i] == *p && a[1][i] == *p && a[2][i] == *p) return 1;

    // diagonal check
    if((a[0][0] == *p && a[1][1] == *p && a[2][2] == *p) || (a[0][2] == *p && a[1][1] == *p && a[2][0] == *p)) return 1;
    return 0;
}
```
<br>

If a win is detected, a message will be displayed, as seen in the figure below. <br>

{% include image-gallery.html images="win.png" height="200" %} <br>

There are two categories of compouter opponent that was programmed into the game, normal mode and hard mode. On the easy mode, the computer does random moves and only prevents wins if the player is one move away from winning by blocking; like a very reasonable average player would do. This function is built on an _if loop_ to make sure that it checks for every row, column, and diagonal. The code snippet below shows the random comoputer move function, which includes the process of checking if the field is already filled. <br>

```C
void randommove(char a[3][3], char *p)
{
    srand(time(NULL));
    int m,n;
    while(1)
    {
        m = rand() % 3 + 1;     // selects a random integer from 1 to 3
        n = rand() % 3 + 1;
        if(a[m-1][n-1] == ' ') break;   // to prevent choosing an already filled 
    }
    move(a, &m, &n, p);
}
```
<br>

For the hard computer opponent, the computer responds differently if the player starts first or if the computer starts first. If the computer starts first, it would place a mark on the corner, and place another one on the opposite corner to prepare for a strategic win. If the player starts first, the computer has a specific respond to different player strategies to prevent the player from winning. If played correctly, the player would always draw the computer. The computer would also block the player from winning, and always seek a move to win. The code below shows the computer code in placing the marks on the corners, where c is the number of turns passed. <br>

```C
    if(*c == 0) // Starts with corner 1 1
    {
        m = 1; n = 1;
        move(a, &m, &n, p); return;
    }
    
    if(*c == 1) 
    {
        if(a[0][0]!=' ' || a[2][2]!=' ' || a[2][0]!=' ' || a[0][2]!=' ' || a[0][1]!=' ' || a[1][2]!=' ' || a[2][1]!=' ' || a[1][0]!=' ')
        {
            m = 2; n = 2;
            move(a, &m, &n, p); return;
        }

        if(a[1][1] != ' ')
        {
            m = 1; n = 1;
            move(a, &m, &n, p); return;
        }
    }
```
<br>

# Outcome
The final application is a fully-functional Tic-Tac-Toe game that succesfully manages the flow of game between player and player or player and computer. It accurately detects all possible win and draw conditions, and handles any invalid user input. The computer opponent succesfully implemented a proven and tested strategy to win or draw against the player. <br>

Through this project, I gained a deeper understanding of _loop_ functions and conditional statements, which are important in most programming problem in microcontrollers. Furthermore, I learned to break a complex problem into smaller managable functions through the modular design of the code. Not only does the modular approach made the program easier to debug, but also is a standard practice in engineering design.<br>

---
