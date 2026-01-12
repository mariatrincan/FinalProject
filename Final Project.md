# Final Project - MP3 music player with lyrics

This project implements a fully-featured MP3 player using an ESP32 microcontroller with an intuitive menu-driven interface displayed on a small OLED screen. The player offers music playback control, customizable settings, and an enhanced listening experience with synchronized lyrics and visual animations.

## Core Features

### Menu System

Main Menu: Central navigation hub for accessing player controls and settings\
Song Selection Menu: Browse and select tracks from the available music library\
Settings Menu: Adjust screen brightness and audio volume preferences

### Playback Controls

Standard play/pause/resume functionality\
Return to main menu option during playback\
Smooth navigation between menus and playback mode\

### Enhanced Playback Experience

Lyrics Display: Synchronized lyrics shown on screen during vocal sections\
Visual Animations: Dynamic animations displayed during instrumental passages\
Real-time Information: Current track information and playback status

### Hardware Components

ESP32 development board\
0.96" OLED I2C display (white)\
MP3 decoder module with MiniSD card support\
Audio amplifier module with volume control\
3W speaker for audio output\
Joystick

### User Interaction Flow
The interface is designed for intuitive navigation through nested menus, allowing users to easily browse their music collection, adjust preferences, and enjoy an engaging visual experience synchronized with their music.

### BOM - Bill Of Materials

Aprox. 200 lei.

## Answering the questions

### Q1 - What is the system boundary?

What is inside the system:

ESP32 microcontroller \
0.96" OLED display (user interface output)\
MP3 decoder module (WTV020) (audio decoding)\
PAM8403 amplifier module (audio amplification)\
3W speaker (audio output)\
MiniSD card (music file storage)\
Joystick (buttons for navigation)

What is outside the system:

My computer (used only for initial programming and loading music files onto SD card)\
Power supply (USB cable)

Clear System Boundary:
This is a standalone, self-contained embedded system. Everything from user input (joystick) through processing (ESP32), storage (SD card), audio decoding (WTV020), amplification (PAM8403), to output (speaker + OLED) is contained within one physical device. The ESP32's wireless capabilities are not used - it operates purely as a local controller managing the hardware components.

### Q2 - Where Does Intelligence Live?

All decision-making, control logic, and coordination happens exclusively on the ESP32. Everything else is a peripheral that the ESP32 commands.

What the ESP32 handles:

Menu navigation logic - managing main menu, song selection, settings\
Playback control - play, pause, resume commands\
User input processing - joystick detection and response\
Display rendering - drawing menus, lyrics, animations on OLED\
Lyrics synchronization - timing lyrics display with music playback\
Animation control - triggering and managing visual effects during instrumental sections\
Settings management - storing and applying brightness/volume preferences\
Audio module communication - sending commands to WTV020 MP3 decoder\
System state management - tracking current song, menu position, playback status

### Q3 - What is the hardest technical problem?

I think keeping visual content (lyrics/animations) in perfect sync with audio playback from an independent module is the core technical challenge. Everything else is standard embedded programming.

Specific Technical Problems:

No Real-Time Feedback: The WTV020 doesn't provide accurate playback position feedback to the ESP32. 

Synchronization Strategy Required: 

Time-based sync: Starting a timer when play begins, display lyrics based on elapsed time (risks drift if playback varies)\
Pre-processing lyrics files: Creating separate timing files for each song with millisecond markers\
Manual calibration: Testing each song and hardcode timing offsets

Detecting Instrumental vs. Vocal Sections: 

Requires pre-tagged sections or timing data per song

File Format Design: 

Must create and maintain synchronized data files 

### Q4 - What is the minimum demo?

Playing one song with synchronized lyrics appearing on the OLED display at the correct times.

What This Proves:

 Hardware integration works (ESP32 -> WTV020 -> amplifier -> speaker)\
 Display works (OLED showing text)\
 Core technical challenge solved (lyrics synchronization)\
 User can see/hear the system working as intended

Minimum Interaction Flow:

Power on device\
Press button to select pre-loaded song\
Press play\
Song plays from speaker + lyrics appear synchronized on screen

### Q5 - Why is This Not Just a Tutorial?

Hardware is tutorial-level, but the synchronization system is original work

What is Tutorial-Based (Acknowledged):

 Wiring ESP32 to OLED, WTV020, amplifier - all documented\
 Basic menu navigation on OLED - standard patterns\
 Simple play/pause commands to WTV020 - module documentation

What is Not Tutorial-Based:

The Lyrics Synchronization Engine:

WTV020 plays MP3 files independently with no position feedback. You can't ask what second am I at? - yet I need to display the correct lyrics at the correct millisecond.

Custom Solution:

Timer-based sync engine - software timer (millis()) tracks elapsed time\
BUSY pin validation - hardware monitoring to detect errors and drift\
Lyrics parser - reads custom timing files from SD card\
Display coordination - manages text rendering and animations based on timing data\
Drift compensation - manual calibration per song + error recovery

### Do you need an ESP32? 

I want to buy my own ESP32 to have one for myself.
