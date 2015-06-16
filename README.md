# mazerunner

A game where 1-4 players race to be the first out of the maze.
Each player will connect to a gameserver with a client. The Client is only providing a UI and will not handle any of the game mechanics. The gameserver will handle all the game mechanics and host the game even for a single player. Starting area will have 4 entrances to the maze. Any player can use any entrance each turn. Player's can pick path's found by other players. 

Gameplay:
    - Players will randomly decide who goes first
    - Each player will take turns trying to escape the maze
        - each player starts at 50 hp and 0 resources, 0 map pieces
            - if a player reaches 0 hp they lose the game
            - resources are used to buy item modifiers from the shop
            - if a player reaches 10 map pieces, they win
    - Steps of player's turn:
        - Decide Heal or Move through the Maze
            - heal will ignore your atk and resource dice
                - stay in base and heal the amount determined by your heal dice
            - movement will allow you to exit the base and traverse the maze
        - Pick your dice (1-2 atk dice, 2-4 heal/movement dice, and 1-2 resource dice)
            - atk dice determine the attack power you get for this turn
            - heal/movement dice determine how far you can traverse in the maze this turn
            - resource dice determines how many resources you get when you find them in the maze this turn
        - Roll Dice (4 base dice, up to 2 additional from item modifier cards)
            - atk face gain additional attack dice to roll
                - each player gets 1 base attack dice to roll
            - heal/movement faces determines number of health to recover this turn or number of steps to take in the maze
            - resource face determines number of resource dices to roll
                - each player gets 1 base resource dice to roll
            - Max of 3 rolls
            - after each roll you may select any number of dice to not roll again
            - you may return any selected dice to the rolling pool in subsequent rolls
            - if all dice rolls are used or all dice have been saved (whichever comes first) will end the dice roll step
        - move or heal
            - if healing was chosen, recover your hp and move to the shopping step
            - if movement was chosen, pick an entrance and enter the maze
                - traverse the maze 1 block at a time until all movement count reaches 0
                    - once movement count reaches 0 return to base
                - movement count is equal to the dice roll
                - after each step roll the encounter die to determine what you encounter
                    - encounter die is rolled only for untravelled spaces
                        - travelled spaces count as half a step (travel 2 spaces per step)
                    1) Monster - found a monster, draw a card from the monster deck
                        - if atk roll>monster health you killed it, gain loot listed on monster card
                        - if atk roll< monster health, exchange damage and retreat
                            - retreat back to base to end turn or travel another path
                            - monster remains at this block
                                - monsters will follow you 1 block for every 2 blocks you move
                    2) Resource - found resources, gain resources equal to your resource roll
                    3) item modifier - found an item, draw a card from the item modifier deck
                    4) chance - something random happens draw a card from the chance deck
                        - secret portal to another location in the maze
                        - found a map piece, increase map count by 1
                        - found a monster, draw a card from the monster deck and fight
                        - found resources, draw a card from the resource deck
                    5) nothing - nothing happens on this block
                    - after each encounter roll you may choose to continue on or return to base
                        - returning to base ends your movement step, proceed to shop step
        - shop (pick buy item modifier or trade resources)
            - exchange resources for any of the item modifiers sold at the shop
                - 3 cards are revealed from the item modifier deck at the start of the game
                - each card bought is replaced by another card
            - exchange resources for other resources at a 3:1 ratio (3 of the same resource for 1 of another)
        - end turn
        
