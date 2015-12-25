# An Introduction to R

# Installing R
# 		The home page for R is http://www.r-project.org. You can download the installation file by 
# clicking on the homepage and finding the “download R” link. 

# Basics Concepts
# 		R stores data as objects, which is why it is called an “object-oriented” language. R then uses 
# functions to interact with the objects. The line between objects and functions can become somewhat 
# blurred because all functions are stored as objects and all objects can only be interacted with via 
# functions, but a simple way of remembering the difference can be summarized in the following quote.

#	“Everything that exists in R is an object.
#	Everything that you do in R is a function.”
	
#	At its core, R is for storing data as one or more objects and then analyzing it in some way with one or more functions. 

# Even More Basic
#	If you are ever feeling overwhelmed by what you are learning or doing in R, never forget that everything you do in R is just a function designed for one of the following six purposes. Determine which step you are trying to perform, and proceed from there. 

#	1) Arithmetic: Addition, Subtraction, Division, Multiplication
#	2) Arithmetic Shortcuts: pre-programmed shortcuts that evaluate an arithmetic expression without you
#	having to write out the equation each time.
#	3) Data Storage: Methods to store data: numbers, letters, or symbols.
#	4) Data Shaping: Methods to describe, reshape, or subset stored data.
#	5) Iteration: Methods to apply arithmetic or arithmetic shortcuts to stored data.
#	6) Plotting: Methods to make graphs or other visual representations of stored data.

#	One last thing before we begin. Always remember, "The first rule of R is always talk about R".	Spell things out for future readers of your programs as explicitly as possible – especially for me, because I’m grading you! You want other programmers to easily recognize what you are trying to accomplish with a particular line of code. A popular saying in computer programming is: 

#	"Always annotate your code, because the sucker trying to figure what you did six months from now
#	is going to be you."

#	To do this you should always leave thorough comments in your code. Comments in R are always preceded by the # symbol. Anything that follows a # symbol will not be executed by the software.

# x <- 2 * 5; everything on this line is a comment 
# none of this will execute if you copy it into R
>

> 2 * 5 # comments can be placed after a statement. Whatever is in front of the # WILL execute.
[1] 10

######################
##### Arithmetic #####
######################
# If you have ever used a scientific or graphing calculator, then you already intuitively know all the 
# basics of doing arithmetic in R. Yay, you've learned about 1/6 of R without doing anything! 
# But, let's just start with a quick review anyway.

# Addition
> 2+2
[1] 4

# Subtraction
> 5-3
[1] 2

# Multiplication
> 3*4
[1] 12

# Division
> 1/5
[1] 0.5

# Make sure you always pay attention to the order of operations (i.e., PEMDAS). Compare the following two 
# expressions.

> (1+3)/(5/6)
[1] 4.8
> 1+3/5/6
[1] 1.1

# Also, be careful about those tricksy negative signs!
> -5^2
[1] -25

> (-5)^2
[1] 25

##############################
#### Arithmetic Shortcuts ####
##############################
#	Of course, writing out the arithmetic every time wouldn't be any better than just using a calculator. 
# The first benefit that R has over a calculator is it has many functions for arithmetic expressions that 
# you can use as shortcuts.

# For example, if I wanted to take the square root of a number. I could just write out the expression.
> 4^(1/2)
[1] 2

# But, but I can use sqrt() function to do this as well. Note that all functions have two parts. 
# The function name - i.e., sqrt - and a set of function arguments – i.e., the object that you want 
# the function to evaluate, in this case, the number 4. Function arguments are always placed in
# parentheses.
> sqrt(4)
[1] 2

# Now you might be thinking, that doesn't really save any time compared to writing out the expression. 
# True, but arithmetic shortcuts/functions will save you time on more complex expressions.

# Let's try typing out 10!
> 10*9*8*7*6*5*4*3*2*1
[1] 3628800

# Versus using the factorial function
> factorial(10) # much clearer!
[1] 3628800

# The second most important benefit of functions is that they explicitly say what your code is doing.
# Seeing factorial(10) makes it immediately obvious that you are calculating the factorial of ten.

######################
#### Data Storage ####
######################

#	These shortcuts probably still don't seem that impressive if you consider that most calculators 
# already have buttons for square roots, factorials, and the like. However, the arithmetic shortcuts 
# (i.e., functions) in R don't really shine unless if they're paired with stored data.

# Let's consider a quadratic equation, 5x^2+3x+7. Let's say we want to solve this equation for x=4
# that's easy to do in the way we've already learned.

> 5*(4^2)+(3*4)+7
[1] 99

# But what if we want to solve this equation for multiple values of x? Let's try solving for x = 1,2,3, and 4.

# We can do this by telling R to perform the function on all four numbers at once using the c() command. 
# The c() function tells R to treat the values inside the parentheses, separated by commas, as a single unit.

> 5*c(1,2,3,4)^2+3*c(1,2,3,4)+7
[1] 15 33 61 99

# But what if we had a very long equation and/or a very long list of x values we want solve for? Typing out 
# all of the x values with c() every time x appears in the equation could get very hard to read very quickly.

> 9*c(1,2,3,4,5,6,7,8,9,10)^3+6*c(1,2,3,4,5,6,7,8,9,10)^2+8*c(1,2,3,4,5,6,7,8,9,10)+2
[1]   25  114  323  706 1317 2210 3439 5058 7121 9682

# A better alternative involves learning how to store data as an object, and then plug the object into 
# equations. The most fundamental type of data object in R, and computer science, is an array.

# An array is essentially a set of values saved to your computer memory that is referenced by a name.

# Here's an example of how to make an array named "x"
> x<-array(data=c(1,2,3,4),dim=4)

# Let's break each of the steps in the above example. "x" represents the name of the array. 
# Once we've made the array named x, then typing x will return the values in the array.

> x
[1] 1 2 3 4

# Similarly performing arithmetic on x will apply that expression to all values in x
> x+4
[1] 5 6 7 9

> factorial(x)
[1]  1  2  6 24

> 5*x^2+3*x+7
[1] 15 33 61 99

# The "<-" symbol tells R to store the output of the command on the right, "array()", under the variable 
# name on the left - i.e., "x". You can also use arrows in the opposite direction "->". 
# However, the "<-" is overwhelmingly the convention, and is strongly preferred – i.e., I will be really 
# disappointed in you as a human being if you write things out in the wrong direction.

> array(data=c(1,2,3,4),dim=4)->x

# The "data=" is your way of telling it what values you want stored in the array. In this case, the four 
# numbers c(1,2,3,4), but you could substitute any list of values or even a single value.

# Single value
> x<-array(data=5,dim=1)

# The final part of array, "dim=" indicates how many values you want in the array. If you indicate more 
# values to the array then you provide, R will simply repeat the values you did give it until the array 
# is full.
> x<-array(data=c(1,2,3,4,5),dim=10)
> x
[1] 1 2 3 4 5 1 2 3 4 5

# This is a really bad behavior that most computer languages would not allow. The potential for introducing 
# error into your calculation in this way isn't trivial, so be careful!

# Perhaps the most interesting aspect of "dim=" is that you can also give it multiple values with c().
> x<-array(data=c(0,1),dim=c(4,6))
> x
     [,1] [,2] [,3] [,4] [,5] [,6]
[1,]    0    0    0    0    0    0
[2,]    1    1    1    1    1    1
[3,]    0    0    0    0    0    0
[4,]    1    1    1    1    1    1

# Eseentialy, you told R to make 6 arrays with 4 values and store them within a single object x.

# You can do this as many times as you'd like. 
# For example, 2 sets of 6 sets of arrays with 4 values.

> x<-array(data=c(0,1),dim=c(4,6,2))
, , 1

     [,1] [,2] [,3] [,4] [,5] [,6]
[1,]    0    0    0    0    0    0
[2,]    1    1    1    1    1    1
[3,]    0    0    0    0    0    0
[4,]    1    1    1    1    1    1

, , 2

     [,1] [,2] [,3] [,4] [,5] [,6]
[1,]    0    0    0    0    0    0
[2,]    1    1    1    1    1    1
[3,]    0    0    0    0    0    0
[4,]    1    1    1    1    1    1

# We therefore describe arrays based on the number of arrays referenced within them. A single array is a
# 1-dimensional array. An array of arrays is a 2 dimensional array. An array of arrays of arrays is a 
# 3-dimensional array, and so forth. 

# The majority of work done in R is either 1- or 2-dimensional. This has led to the emergence of shorthand 
# terms. A “vector” is a one-dimensional array and a “matrix” is a 2-dimensional array. The overwhelming 
# majority of R users exclusively use vectors or matrices rather than arrays. Importantly, not only is there 
# a difference in terminology, there are actually separate functions, for convenience, that specifically use 
# these terms.

# Because the the matrix and vector terminology are so ubiquitous, many R users do not even know about
# the array() function, and how it relates to vectors and matrices.

# Compare a 2-dimensional array
> x<-array(data=c(0,1),dim=c(4,6))
> x
     [,1] [,2] [,3] [,4] [,5] [,6]
[1,]    0    0    0    0    0    0
[2,]    1    1    1    1    1    1
[3,]    0    0    0    0    0    0
[4,]    1    1    1    1    1    1

# With a Matrix
> y<-matrix(data=c(0,1),nrow=4,ncol=6)
> y
     [,1] [,2] [,3] [,4] [,5] [,6]
[1,]    0    0    0    0    0    0
[2,]    1    1    1    1    1    1
[3,]    0    0    0    0    0    0
[4,]    1    1    1    1    1    1

# We can check if these two objects are identical with the identical() function.
> identical(x,y)
[1] TRUE

# Based on what you've seen above, you may think that you have deduced the appropriate pattern for writing out
# a vector
> z<-vector(data=c(1,2,3,4),dim=4)
Error: unexpected '>' in ">"

# NOPE! Doesn't work.

# Vectors are somewhat more primitive than 1-dimensional arrays. You can make them just by using the c()
# function we've been using all along.
> z<-c(1,2,3,4)
> z
[1] 1 2 3 4

# You can what type of array something is by using is()
> is(z,"vector")
[1] TRUE

# Even more confusingly, although 1-dimensional arrays and vectors should, in principle, be identical, 
# this is not true in R.

# Let's make a 1-dimensional array.
> q<-array(c(1,2,3,4),4)
> q
[1] 1 2 3 4

# Let's test if the 1-D array, q, is identical with the previous vector, z.
> identical(z,q)
[1] FALSE

# So, fair warning, be careful as to whether you are using vectors, matrices, or arrays.

# By the way, you may have noticed that I did not specify the arguments "data=" or "dim=", 
# that I wanted to plug in. That's because R is smart and knows what I meant so long as I put each
# argument in the correct order.

# This will give me 1 array of 2 arrays of 3 arrays of 4 arrays, all with the number 4
> q<-array(4,c(1,2,3,4))

# Altneratively I can put the arguments in out of order so long as I specify what they are.
> q<-array(dim=4,data=c(1,2,3,4))
> q
[1] 1 2 3 4

########################
#### Data Storage 2 ####
########################
# What if I want to store something other than a number?

