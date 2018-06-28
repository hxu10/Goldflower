import numpy as np
import scipy.stats as stats
import math
import matplotlib.pyplot as plt




# get the number of the player

def getcardnumber(player):

    temp = np.zeros(3*player)
    occupy = np.zeros(52)
    total = 3*player
    i = 0
    while(i<total):
        rank = int(52 * np.random.random(1))
        if occupy[rank] == 0 :
           occupy[rank] = 1
           temp[i] = rank
           i = i + 1

    cardnumber = np.reshape(temp,(player,3))
    return cardnumber

# get the ranking of the particular card
def getrank(hua1,hua2,hua3,index):

    if index[1]==index[2]:
        return 5
    if index[0]==index[1]:
        return 1
    if hua1==hua2 and hua2==hua3 :
        if index[0]-index[1]==1 and index[1]-index[2]==1 :
            return 4
        return 3
    if index[0]-index[1]==1 and index[1]-index[2]==1:
        return 2
    return 0

# define the ranking›

def ranking(cardnumber,player):


    cardranking = np.zeros(4*(player))
    cardranking = np.reshape(cardranking,(player,4))
    if(player==1):
        cardnumber = np.reshape(cardnumber,(1,3))
    index = np.zeros(3)


    for i_player in range(player):
        hua1 = int(cardnumber[i_player,0]/13)
        hua2 = int(cardnumber[i_player,1]/13)
        hua3 = int(cardnumber[i_player,2]/13)
        for j_card in range(3):
            index[j_card] = cardnumber[i_player,j_card]%13
    
        index = sorted(index,reverse=True)

        if index[1]== index[2]:

            tempcard = index[0]
            index[0] = index[2]
            index[2] = tempcard
        cardranking[i_player,1:4] = index
        #     print hua1,hua2,hua3
        cardranking[i_player,0] = getrank(hua1,hua2,hua3,index)


    return cardranking

def readfile(s):
    if s[0]=='h' and s[1]=='e':
        color = 0
    if s[0]=='h' and s[1]=='o':
        color = 1
    if s[0]=='m' and s[1]=='e':
        color = 2
    if s[0]=='f' and s[1]=='a':
        color = 3
    if s[4]=='J':
        num = 9
    elif s[4]=='Q':
        num = 10
    elif s[4]=='K':
        num = 11
    elif s[4]=='A':
        num = 12
    elif s[4]=='1' and s[5]=='0':
        num = 8
    else:
        num = int(s[4]) - 2

    return num + color * 13

player = 1
totalround = 100000
mycard = np.zeros(3)



f1 = open('mycard.txt','r')
s = np.zeros(3)
s1 = f1.readline()
s2 = f1.readline()
s3 = f1.readline()


mycard[0] = readfile(s1)
mycard[1] = readfile(s2)
mycard[2] = readfile(s3)



#s1 = np.reshape(s1,(2,3))


myranking = ranking(mycard,1)
totalranking = np.zeros(6)

print mycard
print myranking


for player in [1,2,3,4,5,6,7,8,9]:
 
    totalwin = 0
    for round in range(totalround):
        win = 1

        cardnumber = getcardnumber(player)
    #   print cardnumber
        cardranking = ranking(cardnumber,player)
    #    print cardranking
    #  print "--------------"


    

        for i_p in range(player):
            temprank = int(cardranking[i_p,0])
            totalranking[temprank] = totalranking[temprank] + 1
            if myranking[0,0] > cardranking[i_p,0]:
                continue
            elif myranking[0,0] < cardranking[i_p,0]:
                win = 0
                break
            else:
                if myranking[0,1] < cardranking[i_p,1]:
                    win = 0
                    break
        totalwin = totalwin + win
#    if win==1:
    #        print "you win !"
#    else:
#       print "you lose ! "
    print "player",player
    print "win",totalwin
    print "round",totalround
    print "--------------"


#print totalranking




