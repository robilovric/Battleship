# Battleship

A fully functional Battleship game built in C# with Windows Forms, designed for
single-player gameplay against an AI opponent.

## Overview

This project implements the classic Battleship board game as a desktop application.
The player places their fleet on a grid, then takes turns exchanging fire with a
computer opponent that uses a multi-phase intelligent guessing algorithm to locate
and sink player ships. The project follows a clean Model-GUI separation, and
includes a full unit test suite covering core game behaviour and ship operations.

## Features

- Interactive ship placement UI — position and orient your entire fleet before battle
- Turn-based gameplay against an AI opponent
- Multi-phase AI algorithm: Hunt, Target, and Direction modes
- Visual game board rendered in Windows Forms with hit and miss tracking
- Full unit test coverage of game model, ship creation, placement validation,
  and game operations

## Project Structure

Battleship/
├── Model/          # Core game logic — board, ships, game state, AI algorithm
├── GUI/            # Windows Forms presentation layer — forms, controls, events
├── UnitTests/      # Unit tests covering ship creation, behaviour, and operations
└── Battleship.sln  # Visual Studio solution file

## Tech Stack

- Language: C# (.NET Framework)
- UI Framework: Windows Forms
- Testing: Unit tests covering ship creation, placement validation, and game operations
- IDE: Visual Studio

## Getting Started

### Prerequisites

- Visual Studio 2019 or later
- .NET Framework installed

### Running the application

1. Clone the repository

git clone https://github.com/robilovric/Battleship.git

2. Open Battleship.sln in Visual Studio
3. Build the solution (Ctrl+Shift+B)
4. Run the project (F5)

### Running the tests

Open Test Explorer in Visual Studio (Test > Test Explorer) and run all tests.

## Gameplay

1. Setup phase: Place your ships on the grid by selecting orientation and position
2. Battle phase: Click cells on the enemy grid to fire — hits and misses are
   tracked visually
3. AI turn: The computer fires back using an intelligent targeting algorithm
4. Victory: The first player to sink all opponent ships wins

## AI Algorithm

The computer opponent uses a three-phase Hunt and Target algorithm:

- Hunt mode: Randomly selects unvisited cells until a hit is scored
- Target mode: After a hit, fires at adjacent cells (up, down, left, right)
  to determine ship orientation
- Direction mode: Once a second consecutive hit confirms the ship axis, the
  algorithm locks direction and fires along that line to sink the remaining hull
- On sink: Resets to Hunt mode, excluding all previously visited cells from
  future random selection

This approach ensures the AI plays logically and efficiently without resorting
to brute force, while remaining beatable by a human player.

## Architecture

The project follows a strict Model-GUI separation. All game rules, ship management,
board state, and AI logic live in the Model layer and are fully independent of the
presentation. The GUI layer handles only user interaction and visual rendering.
This separation made the codebase clean to unit test and straightforward to extend.
