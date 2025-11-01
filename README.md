# 🐍 Snake Water Gun Game (Python)

A fun and simple **Python-based console game** inspired by Rock-Paper-Scissors!  
Challenge the computer in multiple rounds of **Snake 🐍, Water 💧, and Gun 🔫** — and see who wins more.

---

## 🎮 How to Play
- Type:
  - `s` for **Snake**
  - `w` for **Water**
  - `g` for **Gun**
- The rules are simple:
  - Snake drinks Water → **Snake wins**
  - Gun kills Snake → **Gun wins**
  - Water douses Gun → **Water wins**
  - Same choices → **Draw**

---

## 🧠 Features
- Choose the number of rounds to play  
- Tracks wins, losses, and draws  
- Option to **play again**  
- Prevents invalid inputs  
- Random computer choices using `random` module  

---

## 🚀 Run the Game
Make sure you have Python installed.  
Then run:
```bash

import random

computer = None
youstr = None
youDict = {"s":1, "w":-1, "g":0}
revDict = {1:"Snake", -1:"Water", 0:"Gun"}

def play():
    numRound = int(input("Number of rounds to play: "))
    wins = 0
    losses = 0
    draws = 0

    for i in range(numRound):
        print(f"\nRound {i+1}")
        computer = random.choice([1, -1, 0])
        youstr = input("Enter your choice: ").lower()

        if  youstr == "s" or youstr == "w" or youstr == "g":
            youkey = youDict[youstr]
            if computer == youkey:
                print(f"Computer chose: {revDict[computer]}\nIts a draw!")
                draws += 1
            elif (computer == -1 and youkey == 1) or (computer == 1 and youkey == 0) or (computer == 0 and youkey == -1):
                print(f"Computer chose: {revDict[computer]}\nYou win!")
                wins += 1 
            elif (computer == -1 and youkey == 0) or (computer == 1 and youkey == -1) or (computer == 0 and youkey == 1):
                print(f"Computer chose: {revDict[computer]}\nYou lose!")
                losses += 1

        else: 
            print("Thats inavlid. Choose between s, w, g.\n")
            play()

    print(f"\nNumber of wins: {wins}\nNumber of losses: {losses}\nNumber of draws: {draws}")

play()

while True:
    plAg = input("\nPlay again Y/n: ").lower()

    if plAg == "y":
        play()
    else: 
        print("\nThanks for playing!")
        quit()
