# CS:GO Bomb Game with Chrome Dino

## Introduction 

Welcome to the CS:GO Bomb Game, an interactive embedded systems project developed using ESP32. This project recreates the iconic bomb defusal experience from Counter-Strike: Global Offensive, combined with a Chrome Dino mini-game for an alternative defusal method. During the development of this project, I encountered various challenges including LCD character customization, precise timing mechanisms, keypad debouncing issues, and state machine management for seamless gameplay transitions.

The idea for this game came from my love for CS:GO and the tension-filled moments when you have to defuse a bomb under time pressure. I wanted to recreate that adrenaline rush in a physical, tangible form. Initially, I planned to make just a simple code-input bomb, but then I thought—why not add a fun twist? That's when I decided to include the Chrome Dino game as an alternative defusal method, giving players two ways to save the day. The 3-attempt limit for the code adds extra pressure, making every decision count!

## Game Description 

The CS:GO Bomb Game is a portable interactive device where you can test your skills in two challenging scenarios: code-breaking and reflex gaming. Your goal is to defuse the armed bomb either by entering the correct code within 3 attempts or by successfully completing the Chrome Dino mini-game—all before time runs out!

In short, once the bomb is armed with a custom code, you have 45 seconds to defuse it. You can choose to enter the defusal code directly (but you only get 3 attempts!), or you can play the Chrome Dino game where you must dodge 7 obstacles to automatically defuse the bomb. The beeping gets faster as time runs out, creating an authentic CS:GO atmosphere. One wrong move in the Dino game or the third failed code attempt, and BOOM—it's game over!

## How to Play 

To play the CS:GO Bomb Game, follow these steps:

### 1. Setup:

When you turn on the device, you'll see the "READY" screen with a green LED indicator. Press * to start setting up the bomb code.

### 2. Arming the Bomb:

- Enter your desired code using the keypad (maximum 7 digits)
- Press # to delete the last digit if you make a mistake
- Press * again to confirm and arm the bomb
- The red LED will start blinking, and the countdown begins!

### 3. Game Rules:

Your goal is to defuse the bomb before the 45-second timer runs out. You have two options:

*Option 1: Code Defusal*\
Press # when the bomb is armed to enter defusal mode\
Enter the correct code\
 You have *3 attempts only*—the third wrong attempt causes immediate detonation!\
Press # to delete digits, * to cancel and return to armed state

*Option 2: Chrome Dino Game*\
  Press * when the bomb is armed to start the Dino game\
  Use *any number key (0-9)* to jump over obstacles\
  Press 8 for an *extended jump* (4 seconds vs normal 400ms)\
  Successfully dodge *7 obstacles* to defuse the bomb\
  Hit any obstacle and the bomb explodes!\
  Press # to exit back to armed state

### 4. Objective:

Defuse the bomb using either method before time expires. The beeping accelerates as time runs out:\
  0-10 seconds: Rapid beeping (100ms intervals)\
  10-20 seconds: Fast beeping (300ms intervals)\
  20-30 seconds: Medium beeping (500ms intervals)\
  30-45 seconds: Slow beeping (1000ms intervals)

### 5. Winning:

You successfully defuse the bomb when:\
  You enter the correct code within 3 attempts, or you complete the Dino game by dodging 7 obstacles

The green LED will flash, and you'll hear a victory melody!

### 6. Losing:

The bomb explodes if:\
  The 45-second timer runs out\
  You fail to enter the correct code after 3 attempts\
  You hit an obstacle in the Dino game

The red LED will flash rapidly, and you'll hear the explosion sound!

## Used Components 

The CS:GO Bomb Game incorporates the following components:

  ESP32 development board - main microcontroller\
  4×3 Matrix Keypad - for code input and game controls\
  16×2 I2C LCD Display - shows game information and animations\
  Green LED - indicates ready/defused state\
  Red LED - indicates armed/explosion state\
  Passive Buzzer- for sound effects and countdown beeps\
  Resistors and wires as needed

  ## Set-up Picture
  ![CS-GO-BOMB](https://github.com/user-attachments/assets/32babf2a-b12c-4af2-8cbd-35250c428dec)

## Video Showcasing

[![CS:GO Bomb Game](https://img.youtube.com/vi/2S69-Q-V2Vc/0.jpg)](https://www.youtube.com/watch?v=2S69-Q-V2Vc)

[CS:GO Bomb Game ](https://www.youtube.com/watch?v=2S69-Q-V2Vc)
  
