Download Link: https://assignmentchef.com/product/solved-cs2401-project-6-game-of-othello
<br>
The final project for CS2401 will be a single large project which is to be submitted in three stages and therefore counts as three projects. For this project we will be implementing a game of OTHELLO, with the final product being a game that can play an intelligent game of OTHELLO against a human opponent, namely your instructor.

This game <strong>must</strong> be derived from the author’s game class, and I have made a copy of this class available in ~jdolan/cs2401/projects/game. The files are <em>game.h</em> and <em>game.cc</em>. I have also included in this directory a file called <em>colors.h</em> which was created by a former student who has given us permission to use it. It allows you to adjust the colors of the screen during a text-based console or ssh session. I have altered the <em>play</em> function in the game class, by commenting out some of the code, so that it will work for the first phase of the project. By the end we will return to the original author’s game class with only a couple of little alterations.

The game class actually creates a map for us in how the project is developed, and at the end we will find that most of the ”AI” has already been written for us in this parent class. If you look at <em>game.h</em>, you will see that there are virtual functions that “must be overridden” and some that “may optionally be overridden.” Eventually you will write a child version for all the mandatory overrides, but you probably do not need to override any of the optional ones. (Although the <em>winning </em>function is an exception – his version doesn’t work.)

The rules of this game appear on a separate sheet. Basically the game consists of two-sided playing pieces and the goal is to out-flank your opponent which allows you to “capture” his pieces by flipping them over to your color. Pieces are out-flanked when you position a piece is such a way that one or more of your opponent’s pieces in a row are between two of your pieces. Every move consists of putting a piece onto the board. The pieces are never moved from their original location, and the game continues until there are no more moves available to either player. At that time the player with the most pieces showing his or her color wins.




The first stage is the <strong>design stage</strong>. In this part you decide how you will represent the pieces and how you will display the board. Good grades are given for the quality of the design, the attractiveness of the board, and the ease of the user interface. This first stage should be <u>derived from the game class</u>. You know that you will be creating a child class for Othello, and that that class will have some way of storing the board. The board should be a two-dimensional array of spaces, pieces or pointers<a href="#_ftn1" name="_ftnref1">[1]</a> to spaces or pieces, where the <u>spaces are another class</u> which you have written. This board becomes the principle private member of the Othello class. The spaces class should be able to store all the attributes that a space (or you can call it a piece) might have – emptiness, black, white, as well as mutators and accessor functions to transform a piece/space from one state to another.

You should then implement your design to the stage where I can see the board displayed and be allowed to make one initial move. The first step in doing this is to write your space/piece class, which will <strong>not </strong>be derived from anything, but has the ability to change states. (I think a function called “flip” might be useful.) Then, when you write your Othello class, which will be derived from the author’s game class, the best first step, after declaring your board, <strong>is to create stubs for all of the author’s</strong> <strong>purely virtual functions. </strong>(A stub is a function with an empty implementation, which exists merely to validate a call, or to allow the program to compile.) For this stage you should implement the <em>display_status, make_move, </em>and an<em> is_legal </em>which returns true if the move is any of the four allowable initial moves<em>. </em>Notice that the author expects the move to be entered and passed around as a string, and you need to stay with this as it is an essential part of the design. Think of the string as merely a container for characters. (Remember you will have inherited the <em>get_user_move</em> function – just go ahead and use it.)




Blackboard submission of this 50 point stage (6a) is due at 11:59 p.m. on Mon. April 13<sup>th</sup>

(Late penalty reduced to 4% per day.)

In the second stage you implement a two-player game which allows two humans to play the game against each other on the computer. (Basically you will have one of the humans “be” the computer in the terms of the author’s game class.) All rules should be enforced. This stage will involve a much more extensive <em>is_legal</em> function, since now that function must embody all the rules of the game.




Blackboard submission of this 50 point stage (6b) is due at 11:59 p.m. on Tues. April 21<sup>st</sup>

(Late penalty reduced to 3% per day.)

In the final stage the computer will play an “intelligent” game against a human opponent. Again all rules should be enforced and the computer should not cheat. This is frequently called the “AI” stage of the game, and you will find that much of the AI work is done by the author’s game class.

Electronic submission of this 50 point stage (6c) is due at 11:59 p.m. on Sun., April 26<sup>th</sup>(Late penalty reduced to 2% per day.)First stage play function will look like this:

restart( );




//        while (!is_game_over( ))

//        {

display_status( );

//            if (last_mover( ) == COMPUTER)

make_human_move( );

//           else

//              make_computer_move( );

//    }

display_status( );

//  return winning( );

return HUMAN;

}   // Only the colored lines will be active.




The second stage play function will look like this:

restart( );




while (!is_game_over( ))

{

display_status( );

//if (last_mover( ) == COMPUTER)

make_human_move( );

// else

//     make_computer_move( );

}

display_status( );

return winning( );

}// in your functions the second human player will be     //referred to as COMPUTER




The third stage play function will be returned to the original:

restart( );




while (!is_game_over( ))

{

display_status( );

if (last_mover( ) == COMPUTER)

make_human_move( );

else

make_computer_move( );

}

display_status( );

return winning( );

}




You change this function for the various stages by commenting out the appropriate lines of code in <em>game.cc</em>. In general this will be the only alteration that we’re doing on the author’s game class.

<a href="#_ftnref1" name="_ftn1">[1]</a> Pointers make this a lot harder, so I’m not recommending this for any but the most adventuresome.