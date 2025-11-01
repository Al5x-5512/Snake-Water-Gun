# Snake-Water-Gun
# Its like rock, paper scissors but with snake water and gun!
    import random
    
    computer = None
    youstr = None
    youDict = {"s":1, "w":-1, "g":0}
    revDict = {1:"snake", -1:"water", 0:"gun"}
    
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
            younum = youDict[youstr]
            if computer == younum:
                print(f"Computer chose: {revDict[computer]}\nIts a draw!")
                draws += 1
            elif (computer == -1 and younum == 1) or (computer == 1 and younum == 0) or (computer == 0 and younum == -1):
                print(f"Computer chose: {revDict[computer]}\nYou win!")
                wins += 1 
            elif (computer == -1 and younum == 0) or (computer == 1 and younum == -1) or (computer == 0 and younum == 1):
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
