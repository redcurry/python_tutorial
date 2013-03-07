Python is a general purpose scripting language with support for object-oriented
programming. It is such a powerful language that it is often used for
developing large applications. The nice thing about Python is that it is easy
to learn. Also, because it is so popular, there are many useful tools that can
be added on to Python to make you more productive.

The first command that we will learn is 'print', which simply prints to the
standard output whatever follows. Text, called strings, must be surrounded by
either single quotes or double quotes:

  print 'My name is', 'Carlos'

There are two arguments: 'My name is' and 'Carlos'. Notice that a space is
added between arguments when they are printed.

You can assign a value to a variable using the equals sign, and then use the
variable as an argument to a command:

  first_name = 'Carlos'
  print 'My name is', first_name

So far we have been working with strings, but there are various types of
objects in Python. For example, you can assign a number to a variable and use
it:

  price = 29.99
  paid = 50
  print 'Change:', paid - price

Here I subtracted two variables, where one contains an integer and another
contains a real number (also called floating-point number). The distinction
between integers and floating-point numbers is actually important, as I will
show you in a bit.

Other mathematical operations on numbers are addition (+), multiplication (*),
division (/), remainder (%), and power (**). When you divide two integers, the
true result may be not be an integer (e.g., 1 / 2 is 0.5). However, dividing
two integers in Python before version 3.0 always results in an integer, where
the fractional part is thrown away, so 1 / 2 returns 0. To get the true result,
convert one of the integers to a floating-point number:

  print float(1) / 2

As you learned in math, mathematical operations have a specific order of
precedence: power, multiplication and division, and then addition and
subtraction. You can change this order by using parentheses:

  print 2 * 3 + 4, 'is not the same as', 2 * (3 + 4)



***
Task: Given the diameter of a circle, print out its circumference and area.
The diameter will be in the variable d, and pi will be in PI.
Possible answer:
  print 'Circumference:', PI * d, ', Area:', PI * (float(d) / 2) ** 2
Note: Important to say float(d) (or 2.0) in case d is an integer
***


15 min.


Numbers may also be compared with comparison operators:

  ==   equal to
  !=   not equal to
  <    less than
  >    greater than
  <=   less than or equal to
  >=   greater than or equal to

The result is a True or False value (also called a boolean value), which in
turn can be operated on:

  not   returns False if True, or True if False
  or    returns True if either or both is True, otherwise False
  and   returns True if both are True, otherwise False

Comparisons and boolean operations can be used in an if statement, which runs
commands within it if the condition is True:

  if price > paid:
    print 'Not enough money!'
  elif price == paid:
    print 'Exact amount of money.'
  else:
    print 'More than enough money.'



***
Task: Given three numbers in a, b, and c, print the largest number.
Possible answer:
  if a > b and a > c:
    print a
  elif b > a and b > c:
    print b
  else:
    print c
***



Lists are another type of object in Python. Assign a list to a variable:

  numbers = [1, 2, 3, 4, 5]

Here are some operations on lists:

  x in numbers   returns True if x is in the list
  numbers[i]     returns or assigns the value located at position (0-based)
  numbers[i:j]   returns a list containing items from i to j - 1
  len(numbers)   returns the length of the list

These operations also work on strings (think of it as a list of characters):

  first_name[1]  returns the second character in string first_name

You can go through each element in a list (or string) using a for loop:

  for x in numbers:
    print x



***
Task: Given a list of positive numbers, print out the maximum number.
Possible answer:
  maximum = 0
  for x in numbers:
    if x > maximum:
      maximum = x
  print maximum
***


40 min.


Functions are pieces of code that can be called by a name and a list of
arguments required by that function. For example, the len() function returns
the length of a list or a string. The range() function returns a list of
numbers from 0 to n - 1 if given one argument, or from i to j - 1 if given two
arguments.

  print range(10)
  print len(range(10))

Some functions are attached to an object (in this case, they are called
methods) that operate on the object. For example, to add an item to a list:

  numbers = range(10)
  numbers.append(100)
  print numbers



***
Task: Given a list of numbers, print out the average
Possible answer:
  sum = 0
  for x in numbers:
    sum = sum + x
  print float(sum) / len(numbers)
***



Let's make this program a little more useful by allowing it to take numbers
from the standard input rather than hard-coding the numbers. To read from
the standard input, use the stdin file in the sys package:

  import sys
  for line in sys.stdin:
    print int(line)



***
Task: Print out the mean of integers given from the standard input
Possible answer:
  import sys
  sum = 0
  n = 0
  for line in sys.stdin:
    sum += int(line)
    n += 1
  print float(sum) / n
***


50 min.


You can define your own functions. This allows you to re-use your code if you
need to without having to typing it again, which could introduce errors.  It is
also good to modularize code into functions so that they are easier to change
or improve without affecting the rest of your program. It also makes your
program easier to understand.

You define a function as follows:

  def add_nums(x, y, z):
    return x + y + z

Functions need to be defined before being used in the main program.  The
variables x, y, and z here are local to the function. Assigning a new value to
x inside the function will not affect the variable used to call the program:

  x = 10
  def change_value(x):
    x = 20
  print x

However, compound objects (like lists) may be modified inside a function as
long as the variable is not re-assigned:

  numbers = [1, 2, 3, 4, 5]
  def change(nums):
    nums[0] = 100
  print numbers



***
Task: Write a function that calculates the mean of the argument numbers,
and use it to calculate the mean of numbers given from standard input.
Possible answer:
  def mean(numbers):
    sum = 0
    for x in numbers:
      sum += x
    return float(sum) / len(numbers)

  numbers = []
  for line in sys.stdin:
    numbers.append(int(line))
  print mean(numbers)
***


70 min.



One important advice for designing functions is that "functions should do ONE
thing; they should do it well; the should do it only."

What ONE thing is exactly can be tricky; it depends on the problem you're
trying to solve and how it can be decomposed into parts.

But in general, you want your functions to be small; this makes them easy to
understand and easier to correct for errors.

Another important advice is to use descriptive names for your functions; this
makes your code easier to read and easier to understand, which again, reduces
the amount of errors that can creep in.



Dictionaries are another useful data type in Python. Think of it as a list of
key and value pairs. The key is like an index that can be almost any arbitrary
object, which then allows you to obtain a value associated with the key. The
value may be any kind of object. For example,

  flight_gates = {'UA 3839': 'H3', 'AA 382': 'F2B'}
  print flight_gates['UA 3839']

You may add entries to a dictionary as follows:

  flight_gates['UA 652'] = 'G12'

You can go through the keys of a dictionary in a similar way that you did with
a list:

  for flight in flight_gates:
    print flight, flight_gates[flight]



***
Task: Write a program to print out a histogram of the number of words
(separated by a space) from the given standard input.
Possible answer:
  import sys

  histogram = {}
  for line in sys.stdin:
    words = line.split()
    for word in words:
      if word in histogram:
        histogram[word] += 1
      else:
        histogram[word] = 1

  for word in histogram:
    print word, histogram[word]
***

90 min.
