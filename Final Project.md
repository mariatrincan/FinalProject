# Final Project - CS:GO Defusal Bomb Replica

This project implements a highly realistic CS:GO bomb replica using an ESP32 microcontroller with an authentic game-inspired interface. The device simulates the iconic defusal bomb from Counter-Strike: Global Offensive, complete with arming sequences, countdown timers, authentic sound effects, and multiple defusal methods that mirror the in-game experience.

## Core Features

### Bomb States & Interaction

Idle State: Bomb awaiting arming code input via numeric keypad\
Arming Sequence: Multi-digit code entry with visual/audio feedback mimicking game mechanics\
Armed State: Active countdown with escalating beep patterns and LED indicators\
Defusal Modes: 
Code-based defusal (enter the same arming code)\
 Mini-game defusal challenge on LCD using keypad navigation

Detonation/Success: Explosion sound effects or successful defusal celebration

### Visual & Audio Feedback

LCD Display: Real-time countdown timer, code entry interface, defusal mini-game graphics\
RGB LED: Color-coded status\
Sound Effects: MP3 module plays authentic CS:GO sounds\
Buzzer: Escalating beep frequency as countdown progresses, arming beep, countdown beeps

### Hardware Components

ESP32 development board\
LCD 16x2 with I2C module (timer and interface display)\
4x3 numeric keypad (12 buttons for code entry and mini-game controls)\
WTV020 MP3 decoder module with MiniSD card (sound effects)\
40mm 3W speaker (sound output)\
RGB LED (status indicator)\
Passive buzzer (countdown beeps)

### BOM - Bill Of Materials

Aprox 200 lei

## Answering the Questions

### Q1 - What is the system boundary?

What is inside the system:

ESP32 microcontroller (central intelligence)\
LCD 16x2 display with I2C (visual output)\
4x3 numeric keypad (user input - code entry and game controls)\
WTV020 MP3 decoder module (audio playback)\
40mm 3W speaker (sound effects output)\
RGB LED (visual status indicator)\
Passive buzzer (countdown beeper)\
MiniSD card (sound effects storage)

What is outside the system:

Computer (initial programming and loading sound files only)\
Power supply (USB)

Clear System Boundary:

This is a fully self-contained interactive embedded system. All inputs (keypad), processing (ESP32), storage (SD card), audio (MP3 module + speaker), and visual feedback (LCD + RGB LED + buzzer) exist within one cohesive physical device. The ESP32 orchestrates all components.

### Q2 - Where Does Intelligence Live?

All game logic, state management, timing, and synchronization happen exclusively on the ESP32. Every other component is a peripheral controlled by the ESP32.

What the ESP32 handles:

State machine management - tracking bomb states\
Keypad input processing - reading numeric codes, validating entries, managing input buffers, interpreting directional navigation for mini-game\
Dual-mode input interpretation - same keypad buttons serve different functions: digits for code entry, navigation controls for mini-game\
Code verification logic - storing arming code, comparing with defusal attempts\
Countdown timer control - precise millisecond timing for bomb countdown\
Audio synchronization - triggering appropriate sound effects at exact moments (arming beep, countdown ticks, explosion)\
LCD rendering - displaying timer, code entry interface, mini-game graphics\
Mini-game logic - cursor movement, win/lose conditions\
LED control - RGB color sequences synchronized with bomb states\
Buzzer patterns - escalating beep frequency based on remaining time\
MP3 module communication - sending playback commands\
Safety interlocks - ensuring proper state transitions and preventing illegal operations

### Q3 - What is the hardest technical problem?

Implementing dual-mode keypad functionality while synchronizing multiple timed audio/visual elements and maintaining precise countdown accuracy.

Specific Technical Problems:

#### Dual-Mode Keypad Interpretation:

 Same physical buttons must function differently based on context:
   Code mode\
   Game mode

 #### Mini-Game Graphics on 16x2 LCD

 Must show cursor position clearly\
 Must update display without interfering with timer precision\


### Q4 - What is the minimum demo?

Arming the bomb with a code, watching a countdown with escalating beeps and synchronized LED, then defusing via the mini-game using keypad navigation.

What This Proves:

Hardware integration works\
Dual-mode keypad functionality (digits for arming, navigation for game)\
Core state machine functions\
Timing precision (accurate countdown continues during mini-game)\
Audio/visual synchronization (beeps + LED match countdown state)\
Mini-game logic works

### Q5 - Why is This Not Just a Tutorial?

Hardware wiring is standard, but the dual-mode keypad system, integrated timing engine, and mini-game mechanics are original implementations.

What is Tutorial-Based (Acknowledged):

Wiring ESP32 to LCD I2C, keypad, buzzer - all documented\
Basic keypad input reading - standard keypad library exists\
Simple MP3 playback commands - module documentation available\
RGB LED color control - common patterns

What is Not Tutorial-Based:

#### Dual-Mode Keypad System:

 Context-aware input handler that changes button meaning based on state\
 Preventing input errors during mode transitions


#### CS:GO-Authentic State Machine

Replicating game behavior requires careful design:
 Exact beep patterns matching in-game bomb\
 Realistic arming/defusal timing windows\
 Sound effect triggering at precise moments 


### Do you need an ESP32?

Yes, I want to purchase my own ESP32 to have one for personal projects.
