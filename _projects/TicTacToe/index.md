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
The program was structured into distinct functions such as print board, player input, player move, win check, and more. This was done to ensure that the program was easy to debug.

# Outcome

---
