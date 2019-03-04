# Cards
A Unique Solution to the *Millions* of Playing Card Games
### Inspiration
This project was inspired by initially wanting to build a software methodology to track points while playing a physical card game with multiple players. However, as the coding process began, it eventually sprouted into a full fledged card game playing system. More importly, one core design feature that was implemented was to have support for any variant of any card game. The code includes several classes that allow the user to easily create their own custom game with any set of arbitrary rules without any restrictions. 
### Code and Class Structure
Below is the list of all classes and what they do. To test content, all classes have their << operator overloaded to easily be printed in the debug process. Most also contain a debug function that gets all values and prints them to the output window. All code is broken up between having seperate .h and .cpp files. When going through the code for the first time, read through the header files in the order explained below.
##### card.h/card.cpp
The card class is the most foundational class that simply encapsulates all the data contained by a card. This information includes suit, name, color and value. All functions in this class are setters and getters. When modifiying this code or using it to design a game, you should not have to make any changes to this class unless you would like add specific features or unique values to each card. Primarily, these features would be like adding joker cards or giving them their own seperate purpose within a game that you create. Ensure that a seperate constructor is created if you would like to add in different parameters. One thing to primarily keep in mind is that apart from when the cards are instantiated, **only card pointers are used throughout the entire gameplay** since it simplfies having to create and destroy the objects. For convenience and better readability, the operators for comparision and printing/debugging have been overloaded.
##### cardManager.h/cardManager.cpp
The cardManager class is responsible for handling all interaction with the cards. Generating the deck and storing it is one of the most important functions that this class does. It also deals with other aspects of maintaining a deck such as sorting it, shuffling it and viewing specific cards. It is also unlikely that in implementing a game that you will need to modify this class very much. The only circumstances in whcih changes should be made to this class is if you would like to add in a different structure to the order of cards or if you would like to play with only a portion of a deck or just a specific set of cards. Aspects such as including multiple decks are not handled by this class but are handled by the gameManager class. This class also has an optional enum that can be implemented if you want to incorporate specific features with the suits. 
##### player.h/player.cpp
The player class handles the creation of a player and all their attributes. Much of the data within the player is instantiated on creation. The only part that changes is the specific hand that the player receives. Operations that can be performed with the player include viewing the hand, drawing a card, giving a card etc. Unless you have the players perform unique actions with the hand of cards like passing multiple cards or changing them in an unconventional way, you should not have to modify this class. Comparison operators for this class too have been overloaded.
##### gameManager.h/gameManager.cpp
The gameManager class handles all events that pertain to the game. This includes initializing all players and the deck, handing out cards as well as performing actions like rotating and letting each player have their turn. This is the class that combines all the other classes together into a cohesive whole. Your main function should create an instance of this class and use it to perform all actions that pertain to the gameplay. Most changes that you do to incorporate new rules or features will likely happen in this class. 
##### circularLinkedList/listNode
These are classes that you will likely never have to handle. These classes were built to have easy trasitioning between players when deciding whose turn it will be. The listNode class encapsulates a player. To some extent it was also to get some practice in building a circularLinkedList instead of using one that already exists. Unless you add some seriously game changing features like the ability to skip over turns or shuffle people mid-game, I highly recommend not making changes to this class. Much of it is pointer logic and can easily break if one is not cautious. 
### How to use
- Download the files
- Create an instance of gameManager within the main function
- Create players and add them to the linkedList (gameManager constructor handles this)
- Decide on what you want the game to be
- Create a simple function that performs that game action on each player
- Pass that function to the gameManager function playRound()
- Enjoy playing the game
