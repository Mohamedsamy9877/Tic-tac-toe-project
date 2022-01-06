# Tic-tac-toe-project
 
Description of the game:
 Tic Tac Toe, also known as "Noughts and Crosses" or "X's and O's", is a solved game. This means there is a known, mathematically proven strategy to follow for the best result each game. In Tic Tac Toe, two players who follow the right strategy will always tie, with neither player winning. Against an opponent who doesn't know this strategy, however, you can still win whenever they make a mistake.

Board cases:
Basically, to find the validity of an input grid, we can think of the conditions when an input grid is invalid. Let no. of “X”s be countX and no. of “O”s be countO. Since we know that the game starts with X, a given grid of Tic-Tac-Toe game would be definitely invalid if following two conditions meet 
a) countX != countO AND 
b) countX != countO + 1
Since “X” is always the first move, second condition is also required.
Now does it mean that all the remaining board positions are valid one? The answer is NO. Think of the cases when input grid is such that both X and O are making straight lines. This is also not valid position because the game ends when one player wins. So we need to check the following condition as well 
c) If input grid shows that both the players are in winning situation, it’s an invalid position. 
d) If input grid shows that the player with O has put a straight-line (i.e. is in win condition) and countX != countO, it’s an invalid position. The reason is that O plays his move only after X plays his move. Since X has started the game, O would win when both X and O has played equal no. of moves. 
e) If input grid shows that X is in winning condition than xCount must be one greater that oCount.
Armed with above conditions i.e. a), b), c) and d), we can now easily formulate an algorithm/program to check the validity of a given Tic-Tac-Toe board position. 
1)  countX == countO or countX == countO + 1
2)  If O is in win condition then check 
     a)     If X also wins, not valid
     b)     If xbox != obox , not valid
3)  If X is in win condition then check if xCount is
     one more than oCount or not 


some coding:

    call    read_keyboard


    ; calculate draw position                   

    sub     al, 49               

    mov     bh, 0

    mov     bl, al                                  

                                
    call    update_draw                                    

                                                      
    call    check  


    ; check if game ends                   

    cmp     win_flag, 1  

    je      game_over  


    call    change_player 

         
    jmp     main_loop   



change_player:   

    lea     si, player    

    xor     ds:[si], 1 


    Ret


update_draw:

    mov     bl, game_pointer[bx]

    mov     bh, 0


    lea     si, player

    

    cmp     ds:[si], "0"

    je      draw_x     

             
    cmp     ds:[si], "1"

    je      draw_o              


    draw_x:

    mov     cl, "x"

    jmp     update


