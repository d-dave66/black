#black
 class blackjack:
    
    def __init__(self,actual_deck):
        self.actual_deck=actual_deck
        from random import shuffle 
        deck=['diamond','clubs','spade','heart']
        number=['queen','king','jack','ace',2,3,4,5,6,7,8,9,10]
        
        
        for card in deck:
                for num in number:
                    
                    cards=[card,num]
                    self.actual_deck.append(cards)
        
        
        shuffle(self.actual_deck)
        
        print("the dealer takes two cards and shows you one of it")
        print(input("to see one of the card press enter\n"))
        print(self.actual_deck[0][1],"of",self.actual_deck[0][0])
                
    def sum_of_cards(self,card1,card2):
        self.card1=card1
        self.card2=card2
        x=0
        
        list_card=[card1,card2]
        
        for value in list_card:
            if value=="queen" or value=="king" or value=="jack":
                x+=10
            elif value=="ace":
                x+=11
                if x>21:
                    x=x-10
                else:
                    pass
            elif value in range(1,20):
                x=x+value
        return x
    
    def hit(self,i,b):
        self.i=i
        self.b=b
        print("the card is",self.actual_deck[self.i][1], "of", self.actual_deck[self.i][0])
        b=self.sum_of_cards(self.actual_deck[self.i][1],self.b)
        if b==21:
            print('itsa fucking blackjack')
        if b>21:
            print("the value of your cards is",b,"and since the value of the card exceeded beyond 21. sorry its a bust")
            
        else:
            print("the value of cards is",b)
            pass
        return b
a=blackjack([])



while True:
    select=int(input("enter the number of players playing \n(right now the program allows only 1)\n\n"))
    if select==1:
        i=3
        player_card1=a.actual_deck[2]

        player_card2=a.actual_deck[3]

        print("the cards you have received is",a.actual_deck[2][1],"of",a.actual_deck[2][0],"and",a.actual_deck[3][1],"of",a.actual_deck[3][0])
        break

    else:
        print("the input entered is invalid enter a valid input")

                

b=a.sum_of_cards(a.actual_deck[2][1],a.actual_deck[3][1])
print("the value of your cards right now is",b)

if b==21:
    print("itsa a black jack")
else:
    while b<21:

        x=input("what would you like to do ? \nhit or stand? \n\nreminder:standing will result in quitting of your game\n")
        if x=='hit':
            i+=1
            d=a.hit(i,b)
            b=d
            if b==21:
                print("you have won the game")
            else:
                pass

        elif x=='stand':
            z=a.sum_of_cards(a.actual_deck[0][1],a.actual_deck[1][1])
            if z<=17:
                print("the dealer has",a.actual_deck[1][1],"of",a.actual_deck[1][0],"and the total value of the dealers card is",z)
                i+=1
                print("dealer hits")
                f=a.hit(i,z)
                z=f
            else:
                print("the dealer has",a.actual_deck[1][1],"of",a.actual_deck[1][0],"and the total value of the dealers card is",z)
                pass
            

            if z>b and z<=21:
                print("YOU lose")
            elif z==b:
                print("its a draw ")
            else: 
                print("you win")

            break

        else:
            print("the input given is wrong. please give an appropriate reply")


        

# z=a.sum_of_cards(a.actual_deck[1][0],a.actual_deck[1][1])
# print(z)

# if z>

        
    

# print("\n\n\n",a.actual_deck[1][0],a.actual_deck[1][1])


