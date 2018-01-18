
'''
poker program 
'''
#define what a hand is and their ranks

#n-kind, straight, flush 
#can represent each hand as a list of values ['JS', 'QH', '2C']
# -----------
# User Instructions
# 
# Modify the hand_rank function so that it returns the
# correct output for the remaining hand types, which are:
# full house, flush, straight, three of a kind, two pair,
# pair, and high card hands. 
# 
# Do this by completing each return statement below.
#
# You may assume the following behavior of each function:
#
# straight(ranks): returns True if the hand is a straight.
# flush(hand):     returns True if the hand is a flush.
# kind(n, ranks):  returns the first rank that the hand has
#                  exactly n of. For A hand with 4 sevens 
#                  this function would return 7.
# two_pair(ranks): if there is a two pair, this function 
#                  returns their corresponding ranks as a 
#                  tuple. For example, a hand with 2 twos
#                  and 2 fours would cause this function
#                  to return (4, 2).
# card_ranks(hand) returns an ORDERED tuple of the ranks 
#                  in a hand (where the order goes from
#                  highest to lowest rank). 


def poker(hands):
    "Return the best hand: poker([hand, ...]) => hand"
    return max(hands, key=hand_rank)

def hand_rank(hand):
    "Return a value indicating the ranking of a hand"
    ranks = card_ranks(hand)
    if straight(ranks) and flush(hand):
        return (8, max(ranks)) 
    elif kind(4, ranks):
        return (7, kind(4, ranks), kind(1, ranks))
    elif kind(3, ranks) and kind(2, ranks)):
        return (6, kind(3, ranks), kind(2, ranks))
    elif flush(hand):
        return (5, ranks)
    elif straight(hand):
        return (4, max(ranks))
    elif kind(3, ranks):
        return (3, kind(3, ranks), ranks)
    elif two_pair(ranks):
        return (2, two_pair(ranks), ranks)
    elif kind(2, ranks):
        return (1, kind(2, ranks), ranks)
    else:
        return (0, ranks)

def card_ranks(cards):
    #gets the number of a card string
    ranks = ["--23456789TJQKA".index(r) for r,s in cards]
    ranks.sort(reverse=True)
    return ranks

def straight(ranks):
    return(max(len(ranks)) - min(len(ranks)) == 4) and len(set(ranks)) == 5

def flush(hand):
    suits = [s for r,s in hand]
    return len(set(suits)) == 1

def kind(n, ranks):
    #iterate n times for same 
   count = 0
   for r in ranks:
       if ranks.count(r)== n:
           return r
    reurn None

def two_pair(ranks):
   pair = kind(2, ranks) 

def test():
    "Test cases for the functions in poker program"
    sf = "6C 7C 8C 9C TC".split()
    fk = "9D 9H 9S 9C 7D".split()
    fh = "3D 3C 3H 7C 7D".split()
    tp = "5S 5D 9H 9C 6S".split()
    fkranks = card_ranks(fk)
    tpranks = card_ranks(tp)
    assert kind(4, fkranks) == 9
    assert kind(3, fkranks) == None
    assert kind(2, fkranks) == None
    assert kind(1, fkranks) == None
    assert kind(1, fkranks) == 7
    assert two_pair(fkranks) == None
    assert two_pair(tpranks) == (9,5)
    
    assert straight([9, 8, 7, 6, 5]) == True
    assert straight([9, 8, 8, 6, 5]) == False
    assert flush(sf) == True
    assert flush(fk) == False
    assert card_ranks(sf) == [10, 9, 8, 7, 6]
    assert card_ranks(fk) = [9, 9, 9, 9, 7]
    assert card_ranks(fh) = [10, 10, 10, 7, 7]
    assert card_ranks(sf)
    assert poker([sf, fk, fh]) == sf
    assert poker([fh, fk]) == fk
    assert poker([fh, fh]) == fh
    assert poker([sf]) == sf
    assert poker(99*[fh], [sf]) == fh
    
    assert hand_rank([sf]) == (8,10)
    assert hand_rank([fk]) == (7,9,7)
    
    assert hand_rank([fh]) == (6,10,7)
    return "test passes"

print test()

