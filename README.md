Download Link: https://assignmentchef.com/product/solved-eecs592-project-2-adversarial-search-and-csps
<br>
Part I:  Problem-solving without code (30 points)

Please submit a single PDF file PartI.pdf of all non-code problem solutions to Canvas.  The PDF file can contain a scan of handwritten or typewritten/typeset solutions, and any supporting graphics.

<h3>1. R&amp;N Problem 5.12:</h3>

Describe how the minimax and alpha–beta algorithms change for two-player, non-zero-sum games in which each player has a distinct utility function and both utility functions are known to both players. If there are no constraints on the two terminal utilities, is it possible for any node to be pruned by alpha–beta? What if the player’s utility functions on any state differ by at most a constant <em>k,</em> making the game almost cooperative?

<h3>2. R&amp;N Problem 6.8:</h3>

Consider the graph with 8 nodes A<sub>1</sub>, A<sub>2</sub>, A<sub>3</sub>, A<sub>4</sub>, H, T, F<sub>1</sub>, F<sub>2</sub>.  A<sub>i</sub> is connected to A<sub>i+1</sub> for all i, each A<sub>i</sub> is connected to H, H is connected to T, and T is connected to each F<sub>i</sub>.  Find a 3-coloring of this graph by hand using the following strategy: backtracking with conflict-directed backjumping, the variable order A<sub>1</sub>, H, A<sub>4</sub>, F<sub>1</sub>, A<sub>2</sub>, F<sub>2</sub>, A<sub>3</sub>, T ,and the value order R, G, B.

<h3>3. Logic Introduction:</h3>

Consider a vocabulary with only four propositions, A, B, C, and D. How many models are there for the following sentences? a.           ¬A  ∨ ¬B ∨ D.

<ol>

 <li>(A ∧ C) ∨ (B ∧ D).</li>

 <li>(A ⇒ B) ∧ A ∧</li>

 <li>(A ⇒ B) ∧ (C ⇒ D).</li>

</ol>

<em> </em>

<h3>4. R&amp;N Problem 7.14:</h3>

<ol>

 <li>According to some political pundits, a person who is radical (R) is electable (E) if he/she is conservative (C), but otherwise is not electable. Which of the following is/are correct representations of this assertion?</li>

</ol>

(i) (R ∧ E) ⇐⇒ C ii R   ⇒ (E ⇐⇒ C) iii  R   ⇒ ((C ⇒ E) ∨ ¬E)




<ol>

 <li>Which of the sentences in part (a) can be expressed in Horn form?</li>

</ol>

<em> </em>

<h2>Part II:  Codes that Solve a Game and a Puzzle</h2>

<em> </em>

<ol>

 <li><strong>Tic-Tac-Toe (30 points): </strong>The rules for the simple child’s game of Tic Tac Toe were presented in lecture and also are available at <u>https://en.wikipedia.org/wiki/Tic-tac-toe</u>. Your task is to write and submit code tictactoe.py (or tictactoe.cpp) in which Autonomous Player X</li>

</ol>

(playing first) fills a blank board space RANDOMLY, while Autonomous Player O (playing second) follows the MINIMAX-DECISION algorithm specified in R&amp;N and on Slide 12 of

Lecture 6.  Because the game is so simple you do NOT have to implement alpha-beta pruning for this problem, although you are welcome to adopt it if you’d like.  Your code should run through all turns of a single game and then exit.  We will check your code with cpplint/pylint.

<strong> </strong>

To facilitate grading, we ask that you input a single integer number seed through the command line (e.g., tictactoe seed) and use the following functions:




<u>Python</u>:  random.seed(seed), random.random() (from library random.py) <u>C/C++</u>:  srand(seed), rand()  (from stdlib)




To assure reasonable random number generation, simple code is provided below to verify that entering a particular seed on the command line generates the same sequence of random number return values.  Note that the C++ and Python numbers are different but repeated executions of either C++ or Python codes give the same value sequences, as expected.  Note that the values are scaled in this example to give integer results between 0-8. On the tic-tac-toe board assume 0=(0,0) (bottom left corner), 1=(1,0) (middle of bottom row), …, 7=(1,2) (middle of top row), and 8=(2,2) (top right corner).

<strong> </strong>

#!/usr/bin/env python import sys import random import math s = int(sys.argv[1]) print “Seed = “, s random.seed(s); for i in range(0,5):     print math.floor(9 * random.random())




// C/C++:

#include &lt;stdio.h&gt;

#include &lt;stdlib.h&gt;

#include &lt;math.h&gt;

int main(int argc, char **argv)

{

int seed = atoi(argv[1]);

srand(seed);

printf(“seed = %d
”,seed);   for (int i=0;i&lt;5;i++)

printf(“%d
”, (int) floor(9*((double) rand())/RAND_MAX));   return 0; }




Your output should be formatted as follows to show each move.  Player X marks a move with lower-case <strong>x</strong>, Player O marks a move with lower-case <strong>o</strong>, and an open (blank) space is marked with a dash (-).  An example program output (that may or may not follow Minimax convention) is shown below.  Do not use spaces between entries or on the blank line to help with grading.  Output terminates when either a player wins or when all board spaces are marked.

<strong> </strong>

<u>Sample output file </u><u>tictactoe.txt</u><u>:</u>




-,-,- -,-,x

-,-,-




-,-,- -,o,x

-,-,-




-,-,x

-,o,x

-,-,-




-,-,x

-,o,x

-,-,o




-,-,x x,o,x

-,-,o




-,-,x x,o,x

-,o,o




-,-,x x,o,x x,o,o




-,o,x x,o,x x,o,o







<ol start="2">

 <li><strong>Sudoku  </strong>Write and submit a code sudoku.py (or sudoku.cpp) that formulates the Sudoku game as a constraint satisfaction problem, using AC-3 to determine all values possible for each cell given arc consistency constraints. You can choose what combination of higher-level <em>k</em>-consistency and search algorithms to apply. Your code should be able to solve “easy” and “hard” Sudoku boards, so make sure your code does not annoy the grader by running slowly at least on intermediate boards.  We will check your code with cpplint/pylint.  If you have more than one source file provide a README and submit your code as sudoku.tar.gz.</li>

</ol>




The input Sudoku board will be read as suinput.csv with the following format (no spaces between entries please).  Note that a 0 indicates that board space is “unknown”.  The output solution board must be written as suoutput.csv with the same format.  Examples are provided below using the lecture puzzle.







<u>suinput.csv:</u>

0,0,0,0,0,0,0,0,2

1,0,0,3,6,0,5,4,0

0,0,0,7,0,8,9,0,0

0,4,0,0,2,0,1,0,0

0,6,0,9,0,1,0,8,0

0,0,2,0,8,0,0,3,0

0,0,4,1,0,5,0,0,0

0,5,8,0,3,4,0,0,6

2,0,0,0,0,0,0,0,0







<u>suoutput.csv:</u>

4,8,6,5,1,9,3,7,2

1,9,7,3,6,2,5,4,8

3,2,5,7,4,8,9,6,1

8,4,9,6,2,3,1,5,7

7,6,3,9,5,1,2,8,4

5,1,2,4,8,7,6,3,9

6,7,4,1,9,5,8,2,3

9,5,8,2,3,4,7,1,6

2,3,1,8,7,6,4,9,5














