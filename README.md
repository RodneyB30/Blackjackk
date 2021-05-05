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


#Instruction 
#1, bet
#2,select option H,S,D,E 
#3, win:) or lose :/

#Furture steps
# If i would have more time and knowledge i would definitly make this game into a visual perspective of the cards and chips that when betting in.

#code start here 

#Rodneyyy:)!!



from random import choice
 
def GrandTotal(palm):

  ACE = palm.count(11)

  Total = sum(palm)
  if Total > 21 and ACE > 0:
    while ACE > 0 and Total > 21:
      Total -= 10
      ACE -= 1
  return Total


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
      player_action = input("You wanna to play again [y/n]? ").lower()
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
          print(" STOP JOKING AROUND:/ Enter a real bet plz.")
      except ValueError:
        print("STOP JOKING AROUND:/ Enter a real bet plz..")

    
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

          if player_action == "h":
           
            player.append(choice(FiveTwo_cards))

           
            break

          elif player_action == "s":
           
            end_turn = True

            
            break

          elif player_action == "d":
           
            double_money = True

           
            bet_number *= 2

           
            player.append(choice(FiveTwo_cards))

           
            break

          elif player_action == "e":
           
            early_surrender = True

            
            bet_number /= 2

          
            end_turn = True

          
            break

          else:
            print("READ CARfullY Try again!!.")

   
    while True:
      
      computer_turn = []

      
      computer_turn.append(choice(FiveTwo_cards))
      computer_turn.append(choice(FiveTwo_cards))

      if double_money:
       
        computer_turn.append(choice(FiveTwo_cards))

       
        Totalc_card = GrandTotal(computer_turn)
      elif early_surrender:
        
        Totalc_card = GrandTotal(computer_turn)

      else:
        
        while True:
          Totalc_card = GrandTotal(computer_turn)
          if Totalc_card < 18:
            computer_turn.append(choice(FiveTwo_cards))
          else:
            break

     
      print("-"*100)
      print(" AI has %s for a GrandTotal of %d" % (computer_turn, Totalc_card))

     
      if Totalc_card > 21:
        print("--> The AI went OVER 21 BUSTED!!")
        computerbusted = True
        if playerbusted == False:
          print("The player wins yaaay!")

          
          player_money += bet_number

         
          computer_money -= bet_number

         
          playerwins += 1
          
      elif Totalc_card > Totalp_card:
        print("The AI wins!")

        
        player_money -= bet_number

        
        computer_money += bet_number

       
        computerwins += 1
        
      elif Totalc_card == Totalp_card:
        print("No one won... DRAW!")
      
      elif Totalp_card > Totalc_card:
        if playerbusted == False:
          print(" player wins yaay!")

         
          player_money += bet_number

         
          computer_money -= bet_number

          
          playerwins += 1
          
        elif computerbusted == False:
          print(" AI wins!")

         
          player_money -= bet_number

          
          computer_money += bet_number

          
          computerwins += 1
      
      break
 
    print("-"*50)
    print("Wins, player = %d computer = %d" % (playerwins, computerwins))
    print("-"*50)
    inp = input("Press Enter (q to quit): ").lower()
    if 'q' in inp:
      break

  print(" Thanks for playing have a wonderfull day!!")



if __name__ == '__main__':
  MainGame()

  

