# Blackjackk
#RodneyB
"Each participant attempts to beat the dealer by getting a count as close to 21 as possible, without going over 21"
#To do List:
#import
#need a function 
#while loop
#count
#if,else and elif
#open edit save into a file ect


#code start here 

#Rodneyyy:)!!
 # fix ace


from random import choice

# ---def GrandTotal(palm)

 #Ace = 11  
 # total = sum(pam)

 
def MainGame():
  FiveTwo_cards = [2, 3, 4, 5, 6, 7, 8, 9, 10, 10, 10, 10, 11]

  computerwins = 0 
  playerwins = 0

  player_money = 50000                  
  computer_money = 100000

  minimum_bet = 500
  maximum_bet = 50000

  while True:
    player = []

    player.append(choice(FiveTwo_cards))
    player.append(choice(FiveTwo_cards))

    playerbusted = False 
    computerbusted = False 

    
    double_money = False

    
    early_surrender = False

    bet_number = 0

    end_turn = False

    print("*"*100)
    print("The player has : $%.2f" % player_money)
    print("The computer has : $%.2f" % computer_money)
    print("*"*100)

    if computer_money <= minimum_bet:
      print("computer has no money left :)...your rich!! YOU WON!")
      player_action = input("Do You wanna to play again [y/n]? ").lower()
      if player_action == 'y':
        MainGame()
      else:
        break

    if player_money <= minimum_bet:
      print("you have no money left :/ save your money next time...")
      player_action = input("You wanna play again [y/n]? ").lower()
      if player_action == 'y':
        MainGame()
      else:
        break

    while True:
      try:
        bet_number = float(input(" Enter how much you want to bet please [%s-%s]: " % (minimum_bet, maximum_bet)))
        if bet_number >= minimum_bet and bet_number <= maximum_bet:
          break
        else:
          print(" STOP JOKING AROUND:/ Enter a real bet plz-_-")
      except ValueError:
        print("STOP JOKING AROUND:/ Enter a real bet plz -_-")

    while end_turn == False:
      Totalp_card = GrandTotal(player)

      print("-"*50)
      print(" you have these cards %s with a grandTotal value of %d" % (player, Totalp_card))

      if Totalp_card > 21:
        print("--> You went over 21 :/ BUSTED!")
        playerbusted = True

        end_turn = True

      elif Totalp_card == 21:
        print("\a you hit a BLACKJACK!!! letss goo!!")

        end_turn = True

      elif double_money:
        end_turn = True
      
      else:

        while True:
          player_action = input("  [D]ouble Money [H]it/more [S]tand/finished  [E]arly surrender: ").lower()


## NOTE- nnext if and elife of the action on the input ---
          #  NOTEEE##--- need cumputer total cards after the players inpute 
          # #
          #
  
if __name__ == '__main__':
  MainGame()

