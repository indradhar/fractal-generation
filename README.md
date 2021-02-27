# fractal-generation
*Generating Fractals Using IFS code with the help of deterministic and Random Iteration algorithms* <br />

*The Deterministic Algorithm is based on the idea of directly computing a sequence of sets {An = W∘n(A)}* <br />
*Random Iteration Algorithm is founded in ergodic theory (a branch of mathematics that studies statistical properties of deterministic dynamical systems. A central question of ergodic theory is the behavior of a dynamical system when it is allowed to run for a long time). starting from an initial set A0.* <br />

The [code](https://github.com/indradhar/fractal-generation/blob/main/Code%20For%20Fractal%20Generation.ipynb) for fractal generation computes and plots successive sets An+1 starting from an initial set A0, using the IFS code.

# The Deterministic Algorithm: #

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


1. The result of running a higher-resolution version of this program and printing the contents of the graphics screen is presented in Figure 1. In this case we have kept each successive image produced by the program. 

2. Note that the program begins by drawing a box in the array t(i,j). This box has no impact on the final computed image of a Sierpinski triangle. We can start from any other (nonempty) set of points in the array t(i,j). 

3. To adapt the Program so that it runs with other IFS codes will usually require changing coordinates to ensure that each of
the transformations of the IFS maps the pixel array s(i,j) into itself.

4. As it stands in Program, the array s(i,j) is a discretized representation of the square in R2 with lower left comer at
(1, 1) and upper right comer at (100, 100). 

5. Failure to adjust coordinates correctly will lead to unpredictable and exciting results! 

# Random Iteration Algorithm

This algorithm is also used to compute the attractor of an IFS in R2. In order to run the algorithm, we needs a set of probabilities.

In general, If the IFS is given by X; wn: n = 1, 2, ... , N , then there would be N numbers {pi: i = 1, 2, ... , N} such that p1 + p2 + p3 + ⋯ + pn = 1 and pi > 0 for i = 1,2, ⋯ N. These probabilities pi play an important role in the computation of images of the attractor of an IFS using the Random Iteration Algorithm.

The Random Iteration Algorithm proceeds as follows:<br />
Step 1. An initial point, x0 ∈ X, is chosen.<br />
Step 2. One of the transformations is selected "at random“ from the set {w1, w2, ⋯ wn}. The probability that Wi is selected is Pi, for i =1, 2, ⋯.<br />
Step 3. The selected transformation is applied to x0 to produce a new point x1 ∈ X. <br />
Step 4. Again, a transformation is selected, in the same manner, independently of the previous choice, and applied to x1 to produce a new point x2. <br />
Step 5. The process is repeated a number of times, resulting in a finite sequence of points {xn: n = 1, 2, ⋯ , numits}, where numits is a positive integer.<br />

*The Random Iteration Algorithm*

//Iterated Function System Data <br />
a 1 0.5 ∶ b 1 = 0 ∶ c 1 = 0 ∶ d 1 = .5 ∶ e[1] = 1 ∶ f[1] = 1  <br />
a 2 0.5 ∶ b 2 = 0 ∶ c 2 = 0 ∶ d 2 = .5 ∶ e 2 = 50 ∶ f[2] = 1   <br />
a 3 0.5 ∶ b 3 = 0 ∶ c 3 = 0 ∶ d 3 = .5 ∶ e[3] = 50 ∶ f[3] = 50  <br />

screen 1 : cls //initialize computer graphics  <br />
window (0,0) − (100,100) //set plotting window to 0 < x < 100, 0 < y < 100  <br />
x = 0 ∶ y = 0: numits = 1000 //initialize (x, y) and define the number of iterations, numits  <br />
for n = 1 to numits //Random Iteration begins!  <br />
k = int(3 ∗ rnd − 0.00001) + 1 //choose one of the numbers 1, 2, and 3 with equal probability  <br />

//apply affine transformation number k to (x,y)  <br />

newx = a k ∗ x + b k ∗ y + e k  <br />
newy = c[k] ∗ x + d[k] ∗ y + f[k] <br />
x = newx ∶ y = newy //set (x, y) to the point thus obtained <br />
if n > 10 then pset (x,y) //plot (x, y) after the first 10 iterations <br />
next end <br />
We demonstrate the implementation of the algorithm. The following algorithm computes and plots a thousand points on the attractor corresponding to the IFS code provided in the [code](https://github.com/indradhar/fractal-generation/blob/main/Code%20For%20Fractal%20Generation.ipynb).

1. In applying the Random Iteration Algorithm, the rate at which a picture of the attractor is produced depends on the probabilities.
2. In each case the program is halted after a relatively small number of iterations, to stop the image from becoming “saturated”. 
3. The results are diverse textures.
4. In each case the attractor of the IFS is the same set, the filled square ∎.
5. However, the points produced by the Random Iteration Algorithm “rain down” on ∎ with different frequencies at different places.
6. Places where the “rainfall” is highest appear “darker” or “denser” than those places where the “rainfall” is lower.
7. In the end all places on the attractor get wet!
8. The Random Iteration Algorithm gives one a glimpse of this “density”, which get lost with increasing number of iterations.
9. This is true, and much more as well! The “density” is so beautiful that a new mathematical concept is needed to describe it precisely. The concept is called measure!
10. Measures can be used to describe intricate distributions of “mass” on metric spaces.


## Fractals Generated By Using Both the Alogithms <br />
![](https://github.com/indradhar/fractal-generation/blob/main/Barnsley%20Fern%20fractal.png)<br />
![](https://github.com/indradhar/fractal-generation/blob/main/Dragon%20curve%20fractal.png)<br />
![](https://github.com/indradhar/fractal-generation/blob/main/IFSfractalUsingIterationMethod%20(2).png)<br />
![](https://github.com/indradhar/fractal-generation/blob/main/IFSfractalUsingIterationMethod%20(3).png)<br />
![](https://github.com/indradhar/fractal-generation/blob/main/IFSfractalUsingIterationMethod%20(4).png)<br />
![](https://github.com/indradhar/fractal-generation/blob/main/IFSfractalUsingIterationMethod%20(5).png)<br />
![](https://github.com/indradhar/fractal-generation/blob/main/IFSfractalUsingIterationMethod%20(6).png)<br />
![](https://github.com/indradhar/fractal-generation/blob/main/IFSfractalUsingIterationMethod%20(7).png)<br />
![](https://github.com/indradhar/fractal-generation/blob/main/IFSfractalUsingIterationMethod%20(8).png)<br />
![](https://github.com/indradhar/fractal-generation/blob/main/Levy%20C%20curve%20fractal.png)<br />
![](https://github.com/indradhar/fractal-generation/blob/main/Sierpinski%20Triangle%20fractal.png)<br />
![](https://github.com/indradhar/fractal-generation/blob/main/ques1%20fractal.png)<br />
![](https://github.com/indradhar/fractal-generation/blob/main/ques2%20fractal.png)<br />
![](https://github.com/indradhar/fractal-generation/blob/main/random%20fractal.png)<br />
![](https://github.com/indradhar/fractal-generation/blob/main/Fractal%201.jpeg)<br />
![](https://github.com/indradhar/fractal-generation/blob/main/Fractal%202.jpeg)<br />
![](https://github.com/indradhar/fractal-generation/blob/main/Fractal%204.jpeg)<br />
![](https://github.com/indradhar/fractal-generation/blob/main/Fractal%205.jpeg)<br />
![](https://github.com/indradhar/fractal-generation/blob/main/Fractal%206.jpeg)<br />
![](https://github.com/indradhar/fractal-generation/blob/main/Fractal%207.jpeg)<br />
![](https://github.com/indradhar/fractal-generation/blob/main/Fractal%203.jpeg)<br />
