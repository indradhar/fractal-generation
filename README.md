# fractal-generation
*Generating Fractals Using IFS code with the help of deterministic and Random Iteration algorithms* <br />

*The Deterministic Algorithm is based on the idea of directly computing a sequence of sets {An = W∘n(A)}* <br />
*Random Iteration Algorithm is founded in ergodic theory (a branch of mathematics that studies statistical properties of deterministic dynamical systems. A central question of ergodic theory is the behavior of a dynamical system when it is allowed to run for a long time). starting from an initial set A0.* <br />

The [code](https://github.com/indradhar/fractal-generation/blob/main/Code%20For%20Fractal%20Generation.ipynb) for fractal generation computes and plots successive sets An+1 starting from an initial set A0, using the IFS code.

# The Deterministic Algorithm: #

'''python
fractal_generator()
{
  dim s(100,100) : dim t 100,100

  //allocate two arrays of pixels <br />
  a 1 = 0.5: b 1 = 0: c 1 = 0: d 1 = 0.5: e 1 = 1: f(1) = 1<br />
  a 2 = 0.5: b 2 = 0: c 2 = 0: d 2 = 0.5: e 2 = 50: f(2) = 1<br />
  a 3 = 0.5: b 3 = 0: c 3 = 0: d 3 = 0.5: e 3 = 25: f(3) = 50<br />
  //input the IFS code<br />

  for i = 1 to 100<br />

  //input the initial set A(0), in this case a square, into the array t(i,j)

  t(i, 1) = 1: pset(i, 1) ‘A(0) can be used as a condensation set <br />
  t(1, i) = 1: pset(1, i) ‘A(0) is plotted on the screen

  t(100, i) = 1: pset(100, i)<br />
  t(i, 100) = 1: pset(i, 100)<br />
  next: do<br />
  for i = 1 to 100<br />

  //apply W to set A(n) to make A(n + 1) in the array s(i,j)<br />

  for j = 1 to 100 : if t(i,j) = 1 then<br />
  s a 1 ∗ i + b 1 ∗ j + e 1 , c 1 ∗ i + d 1 ∗ j + f 1 = 1<br />
  s(a(2) ∗ i + b(2) ∗ j + e(2), c(2) ∗ i + d(2) ∗ j + f(2)) = 1<br />
  s(a(3) ∗ i + b(3) ∗ j + e(3), c(3) ∗ i + d(3) ∗ j + f(3)) = 1<br />

  //and apply W to A(n)<br />

  end if: next j: next i<br />
  cls <br />
  //clears the screen--omit to obtain sequence with a A(0) as condensation set<br />

  for i = 1 to 100: for j = 1 to 100<br />
  t(i,j) = s(i,j)<br />

  //put A(n + 1) into the array t(i,j)<br />

  s(i,j) = 0

  //reset the array s(i,j) to zero

  if t(i,j) = 1 then<br />
  pset(i,j) ‘plot A(n + 1)<br />
  end if : next : next<br />
  loop until instat<br />

  //if a key has been pressed then stop,

  otherwise compute A(n + 1) = W(A(n + 1))<br />
}
'''

1. The result of running a higher-resolution version of this program and printing the contents of the graphics screen is presented in Figure 1. In this case we have kept each successive image produced by the program. 

2. Note that the program begins by drawing a box in the array t(i,j). This box has no impact on the final computed image of a Sierpinski triangle. We can start from any other (nonempty) set of points in the array t(i,j). 

3. To adapt the Program so that it runs with other IFS codes will usually require changing coordinates to ensure that each of
the transformations of the IFS maps the pixel array s(i,j) into itself.

4. As it stands in Program, the array s(i,j) is a discretized representation of the square in R2 with lower left comer at
(1, 1) and upper right comer at (100, 100). 

5. Failure to adjust coordinates correctly will lead to unpredictable and exciting results! 

![](https://github.com/indradhar/fractal-generation/blob/main/Barnsley%20Fern%20fractal.png)
![](https://github.com/indradhar/fractal-generation/blob/main/Dragon%20curve%20fractal.png)
![](https://github.com/indradhar/fractal-generation/blob/main/IFSfractalUsingIterationMethod%20(2).png)
![](https://github.com/indradhar/fractal-generation/blob/main/IFSfractalUsingIterationMethod%20(3).png)
![](https://github.com/indradhar/fractal-generation/blob/main/IFSfractalUsingIterationMethod%20(4).png)
![](https://github.com/indradhar/fractal-generation/blob/main/IFSfractalUsingIterationMethod%20(5).png)
![](https://github.com/indradhar/fractal-generation/blob/main/IFSfractalUsingIterationMethod%20(6).png)
![](https://github.com/indradhar/fractal-generation/blob/main/IFSfractalUsingIterationMethod%20(7).png)
![](https://github.com/indradhar/fractal-generation/blob/main/IFSfractalUsingIterationMethod%20(8).png)
![](https://github.com/indradhar/fractal-generation/blob/main/Levy%20C%20curve%20fractal.png)
![](https://github.com/indradhar/fractal-generation/blob/main/Sierpinski%20Triangle%20fractal.png)
![](https://github.com/indradhar/fractal-generation/blob/main/ques1%20fractal.png)
![](https://github.com/indradhar/fractal-generation/blob/main/ques2%20fractal.png)
![](https://github.com/indradhar/fractal-generation/blob/main/random%20fractal.png)
![](https://github.com/indradhar/fractal-generation/blob/main/Fractal%201.jpeg)
![](https://github.com/indradhar/fractal-generation/blob/main/Fractal%202.jpeg)
![](https://github.com/indradhar/fractal-generation/blob/main/Fractal%203.jpeg)
![](https://github.com/indradhar/fractal-generation/blob/main/Fractal%204.jpeg)
![](https://github.com/indradhar/fractal-generation/blob/main/Fractal%205.jpeg)
![](https://github.com/indradhar/fractal-generation/blob/main/Fractal%206.jpeg)
![](https://github.com/indradhar/fractal-generation/blob/main/Fractal%207.jpeg)
