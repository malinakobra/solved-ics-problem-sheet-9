Download Link: https://assignmentchef.com/product/solved-ics-problem-sheet-9
<br>
<table width="572">

 <tbody>

  <tr>

   <td width="201"><strong>Problem 9.1: </strong><em>JK flip-flops</em></td>

   <td width="248"> </td>

   <td width="123"> </td>

  </tr>

 </tbody>

</table>

JK flip-flops, also colloquially known as jump/kill flip-flops, augment the behaviour of SR flip-flops. The letters J and K were presumably picked by Eldred Nelson in a patent application.

The sequential digital circuit shown below shows the design of a JK flip-flop based on two SR NAND latches. Assume the circuit’s output is <em>Q </em>= 0 and that the inputs are <em>J </em>= 0 and <em>K </em>= 0, and that the clock input is <em>C </em>= 0. (You can make use of the fact that we already know how an SR

NAND latch behaves.)

<ol>

 <li>Suppose <em>J </em>transitions to 1 and <em>C </em>transitions to 1 soon after. Create a copy of the drawing and indicate for each line whether it carries a 0 or a 1.</li>

 <li>Some time later, <em>C </em>transitions back to 0 and soon after <em>J </em>transitions to 0 as well. Create another copy of the drawing and indicate for each line whether it carries a 0 or a 1.</li>

 <li>Some time later, <em>J </em>and <em>K </em>both transition to 1 and <em>C </em>transitions to 1 soon after. Create another copy of the drawing and indicate for each line whether it carries a 0 or a 1.</li>

 <li>Finally, <em>C </em>transitions back to 0 and soon after <em>J </em>and <em>K </em>both transition to 0 as well. Create another copy of the drawing and indicate for each line whether it carries a 0 or a 1.</li>

</ol>

<strong>Problem 9.2: </strong><em>ripple counter using d flip-flops                                                                           </em>

The following circuit shows a 3-bit ripple counter consisting of three positive edge triggered D flip-flops and a negation gate on the clock input <em>C</em>.

<ol>

 <li>Complete the following timing diagram. Assume that gate delays are very short compared to the speed of the clock signal (i.e., you can ignore the impact of gate delays).</li>

 <li>Can you make ripple counters arbitrary “long” or is there a limit on the number of D flip flops that can be chained? Explain.</li>

</ol>

<strong>Problem 9.3: </strong><em>integer expression simplification (haskell)                                                            </em>

Our goal is to simplify integer expressions that may include constants and variables and which are constructed using a sum and a product operator. For example, we want to write an program that can simplify (2·<em>y</em>)·(3+(2·2)) to 14·<em>y</em>. We can represent expressions in Haskell using the following

<table width="404">

 <tbody>

  <tr>

   <td width="188">data type:</td>

   <td width="216"> </td>

  </tr>

  <tr>

   <td width="188">1 data Exp = C Int</td>

   <td width="216"><em>— a constant integer</em></td>

  </tr>

  <tr>

   <td width="188">2                                                 | V String</td>

   <td width="216"><em>— a variable with a name</em></td>

  </tr>

  <tr>

   <td width="188">3                                                | S Exp Exp</td>

   <td width="216"><em>— a sum of two expressions</em></td>

  </tr>

  <tr>

   <td width="188">4                                                | P Exp Exp</td>

   <td width="216"><em>— a product of two expressions</em></td>

  </tr>

  <tr>

   <td colspan="2" width="404">5                                                   deriving (Show, Eq)</td>

  </tr>

 </tbody>

</table>

We use the following rules to simplify expressions:

S1 Adding two constants <em>a </em>and <em>b </em>yields a constant, which has the value <em>a</em>+<em>b</em>, e.g., 3+5 = 8.

S2 Adding 0 to a variable yields the variable, i.e., 0+<em>x </em>= <em>x </em>and <em>x</em>+0 = <em>x</em>.

S3 Adding a constant <em>a </em>to a sum consisting of a constant <em>b </em>and a variable yields the sum of the <em>a</em>+<em>b </em>and the variable, e.g., 3+(5+<em>y</em>) = 8+<em>y</em>.

P1 Multiplying two constants <em>a </em>and <em>b </em>yields a constant, which as the value <em>a </em>· <em>b</em>, e.g., 3 · 5 = 15.

P2 Multiplying a variable with 1 yields the variable, i.e., 1 · <em>y </em>= <em>y </em>and <em>y </em>· 1 = <em>y</em>.

P3 Multiplying a variable with 0 yields the constant 0, i.e., 0 · <em>y </em>= 0 and <em>y </em>· 0 = 0.

P4 Multiplying a constant <em>a </em>with a product consisting of a constant <em>b </em>and a variable yields the product of <em>a </em>· <em>b </em>and the variable, e.g., 3 · (2 · <em>y</em>) = 6 · <em>y</em>.

The usual associativity rules apply. Note that we have left out distributivity rules.

<ol>

 <li>Implement a function simplify :: Expr -&gt; Expr, which simplifies expressions that do not contain variables. In other words, simplify returns the (constant) value of an expression that does not contain any variables.</li>

 <li>Extend the function simplify to handle variables as described above.</li>

</ol>

Submit your Haskell code plus an explanation (in Haskell comments) as a plain text file. Below is a template providing a collection of test cases.

1 module Main (main) where

2

3 import Test.HUnit

4

<ul>

 <li>data Exp = C Int <em>— a constant integer</em></li>

 <li>| V String <em>— a variable with a name</em></li>

 <li>| S Exp Exp <em>— a sum of two expressions</em></li>

 <li>| P Exp Exp <em>— a product of two expressions</em></li>

 <li>deriving (Show, Eq)</li>

</ul>

10

<ul>

 <li>simplify :: Exp -&gt; Exp</li>

 <li>simplify _ = undefined</li>

</ul>

13

<ul>

 <li>tI0 = TestList</li>

 <li>[ simplify (C 3) ~?= C 3 <em>— 3 = 3</em></li>

 <li>, simplify (V “y”) ~?= V “y” <em>— y = y</em></li>

 <li>]</li>

</ul>

18

<ul>

 <li>tS1 = TestList</li>

 <li>[ simplify (S (C 3) (C 5)) ~?= C 8 <em>— 3 + 5 = 8</em></li>

 <li>]</li>

</ul>

22

<ul>

 <li>tS2 = TestList</li>

 <li>[ simplify (S (C 0) (V “y”)) ~?= V “y” <em>— 0 + y = y</em></li>

 <li>, simplify (S (V “y”) (C 0)) ~?= V “y” <em>— y + 0 = y</em></li>

 <li>]</li>

</ul>

27

<ul>

 <li>tS3 = TestList</li>

 <li>[ simplify (S (S (C 3) (V “y”)) (C 5)) ~?= S (C 8) (V “y”) <em>— (3 + y) + 5) = 8 + y</em></li>

 <li>, simplify (S (S (V “y”) (C 3) ) (C 5)) ~?= S (C 8) (V “y”) <em>— (y + 3) + 5) = 8 + y</em></li>

 <li>, simplify (S (C 3) (S (C 5) (V “y”))) ~?= S (C 8) (V “y”) <em>— 3 + (5 + y) = 8 + y</em></li>

 <li>, simplify (S (C 3) (S (V “y”) (C 5))) ~?= S (C 8) (V “y”) <em>— 3 + (y + 5) = 8 + y</em></li>

 <li>]</li>

</ul>

34

<ul>

 <li>tS4 = TestList</li>

 <li>[ simplify (S (S (C 3) (C 5)) (C 8)) ~?= C 16 <em>— (3 + 5) + 8 = 16</em></li>

 <li>, simplify (S (C 3) (S (C 5) (C 8))) ~?= C 16 <em>— 3 + (5 + 8) = 16</em></li>

 <li>, simplify (S (C 5) (V “y”)) ~?= S (C 5) (V “y”) <em>— 5 + y = 5 + y</em></li>

 <li>, simplify (S (V “y”) (C 5)) ~?= S (V “y”) (C 5) <em>— y + 5 = y + 5</em></li>

 <li>, simplify (S (V “x”) (V “y”)) ~?= S (V “x”) (V “y”) <em>— x + y = x + y</em></li>

 <li>]</li>

</ul>

42

<ul>

 <li>tP1 = TestList</li>

 <li>[ simplify (P (C 3) (C 5)) ~?= C 15 <em>— 3 * 5 = 15</em></li>

 <li>]</li>

</ul>

46

<ul>

 <li>tP2 = TestList</li>

 <li>[ simplify (P (C 1) (V “y”)) ~?= V “y” <em>— 1 * y = y</em></li>

 <li>, simplify (P (V “y”) (C 1)) ~?= V “y” <em>— y * 1 = y</em></li>

 <li>]</li>

</ul>

51

<ul>

 <li>tP3 = TestList</li>

 <li>[ simplify (P (C 0) (V “y”)) ~?= C 0 <em>— 0 * y = 0</em></li>

 <li>, simplify (P (V “y”) (C 0)) ~?= C 0 <em>— y * 0 = 0</em></li>

 <li>]</li>

</ul>

56

<ul>

 <li>tP4 = TestList</li>

 <li>[ simplify (P (P (C 3) (V “y”)) (C 2)) ~?= P (C 6) (V “y”) <em>— (3 * y) * 2) = 6 * y</em></li>

 <li>, simplify (P (P (V “y”) (C 3) ) (C 2)) ~?= P (C 6) (V “y”) <em>— (y * 3) * 2) = 6 * y</em></li>

 <li>, simplify (P (C 3) (P (C 2) (V “y”))) ~?= P (C 6) (V “y”) <em>— 3 * (2 * y) = 6 * y</em></li>

 <li>, simplify (P (C 3) (P (V “y”) (C 2))) ~?= P (C 6) (V “y”) <em>— 3 * (y * 2) = 6 * y</em></li>

 <li>]</li>

</ul>

63

<ul>

 <li>tP5 = TestList</li>

 <li>[ simplify (P (P (C 3) (C 5)) (C 8)) ~?= C 120 <em>— (3 * 5) * 8 = 120</em></li>

 <li>, simplify (P (C 3) (P (C 5) (C 8))) ~?= C 120 <em>— 3 * (5 * 8) = 120</em></li>

 <li>, simplify (P (C 5) (V “y”)) ~?= P (C 5) (V “y”) <em>— 5 * y = 5 * y</em></li>

 <li>, simplify (P (V “y”) (C 5)) ~?= P (V “y”) (C 5) <em>— y * 5 = y * 5</em></li>

 <li>, simplify (P (V “x”) (V “y”)) ~?= P (V “x”) (V “y”) <em>— x * y = x * y</em></li>

 <li>]</li>

</ul>

71

<ul>

 <li>tM0 = TestList [</li>

 <li><em>— (2 * y) * (3 + (2 * 2)) = 14 * y</em></li>

 <li>simplify (P (P (C 2) (V “y”)) (S (C 3) (P (C 2) (C 2)))) ~?= P (C 14) (V “y”)</li>

 <li><em>— x + (1 + -1) = x</em></li>

 <li>, simplify (S (V “x”) (S (C 1) (C (-1)))) ~?= V “x”</li>

 <li><em>— (1 + -1) * x = 0</em></li>

 <li>, simplify (P (S (C 1) (C (-1))) (V “x”)) ~?= C 0</li>

 <li><em>— (2 + -1) * x = x</em></li>

 <li>, simplify (P (S (C 2) (C (-1))) (V “x”)) ~?= V “x”</li>

 <li><em>— (2 * 2) * (3 + 4) = 28</em></li>

 <li>, simplify (P (P (C 2) (C 2)) (S (C 3) (C 4))) ~?= C 28</li>

 <li>]</li>

</ul>

84

85 main = runTestTT $ TestList [tI0, tS1, tS2, tS3, tS4, tP1, tP2, tP3, tP4, tP5, tM0 ]