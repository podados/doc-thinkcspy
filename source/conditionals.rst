..  Copyright (C)  Peter Wentworth, Jeffrey Elkner, Allen B. Downey and Chris Meyers.
    Permission is granted to copy, distribute and/or modify this document
    under the terms of the GNU Free Documentation License, Version 1.3
    or any later version published by the Free Software Foundation;
    with Invariant Sections being Foreword, Preface, and Contributor List, no
    Front-Cover Texts, and no Back-Cover Texts.  A copy of the license is
    included in the section entitled "GNU Free Documentation License".


.. |rle_start| image:: illustrations/rle_start.png
   
.. |rle_end| image:: illustrations/rle_end.png
 
.. |rle_open| image:: illustrations/rle_open.png
   
.. |rle_close| image:: illustrations/rle_close.png    
    
|    
    
Conditionals
============

.. index::
    single: modulus operator
    single: operator; modulus

The modulus operator
--------------------

The **modulus operator** works on integers (and integer expressions) and gives
the remainder when the first number is divided by the second. In Python, the
modulus operator is a percent sign (``%``). The syntax is the same as for other
operators:

.. sourcecode:: python
    
    >>> q = 7 // 3     # This is integer division operator
    >>> print(q)
    2
    >>> r  = 7 % 3
    >>> print(r)
    1

So 7 divided by 3 is 2 with a remainder of 1.

The modulus operator turns out to be surprisingly useful. For example, you can
check whether one number is divisible by another---if ``x % y`` is zero, then
``x`` is divisible by ``y``.

Also, you can extract the right-most digit or digits from a number.  For
example, ``x % 10`` yields the right-most digit of ``x`` (in base 10).
Similarly ``x % 100`` yields the last two digits.

It is also extremely useful for doing conversions, say from seconds,
to hours, minutes and seconds. So let's write a program to ask the user to enter
some seconds, and we'll convert them into hours, minutes, and remaining seconds.

.. sourcecode:: python

    total_secs = int(input("How many seconds, in total?"))
    hours = total_secs // 3600      
    secs_still_remaining = total_secs % 3600
    minutes =  secs_still_remaining // 60 
    secs_finally_remaining = secs_still_remaining  % 60
    
    print("Hrs=", hours, "  mins=", minutes,  
                             "secs=", secs_finally_remaining)

.. index::
    single: boolean value
    single: value; boolean
    single: boolean expression
    single: expression; boolean
    single: logical operator
    single: operator; logical 
    single: operator; comparison
    single: comparison operator

Boolean values and expressions
------------------------------

The Python type for storing true and false values is called ``bool``, named
after the British mathematician, George Boole. He created *Boolean
algebra*, which is the basis of all modern computer arithmetic.

There are only two boolean values, ``True`` and ``False``.  Capitalization
is important, since ``true`` and ``false`` are not boolean values.

.. sourcecode:: python
    
    >>> type(True)
    <class 'bool'> 
    >>> type(true)
    Traceback (most recent call last):
      File "<interactive input>", line 1, in <module>
    NameError: name 'true' is not defined

A **boolean expression** is an expression that evaluates to a boolean value.
The operator ``==`` compares two values and produces a boolean value:

.. sourcecode:: python
    
    >>> 5 == 5
    True
    >>> 5 == 6
    False

In the first statement, the two operands are equal, so the expression evaluates
to ``True``; in the second statement, 5 is not equal to 6, so we get ``False``.

The ``==`` operator is one of six common **comparison operators**; the others are:

.. sourcecode:: python
    
    x != y               # x is not equal to y
    x > y                # x is greater than y
    x < y                # x is less than y
    x >= y               # x is greater than or equal to y
    x <= y               # x is less than or equal to y

Although these operations are probably familiar to you, the Python symbols are
different from the mathematical symbols. A common error is to use a single
equal sign (``=``) instead of a double equal sign (``==``). Remember that ``=``
is an assignment operator and ``==`` is a comparison operator. Also, there is
no such thing as ``=<`` or ``=>``.

.. index::
    single: logical operator
    single: operator; logical 
    
Logical operators
-----------------

There are three **logical operators**: ``and``, ``or``, and ``not``. The
semantics (meaning) of these operators is similar to their meaning in English.
For example, ``x > 0 and x < 10`` is true only if ``x`` is greater than 0 *and*
at the same time, x is less than 10.

``n % 2 == 0 or n % 3 == 0`` is true if *either* of the conditions is true,
that is, if the number is divisible by 2 *or* divisible by 3.

Finally, the ``not`` operator negates a boolean expression, so ``not(x > y)``
is true if ``(x > y)`` is false, that is, if ``x`` is less than or equal to
``y``.


.. index:: conditional branching, conditional execution, if, elif, else,
           if statement, compound statement, statement block, block, body,
           pass statement

.. index::
    single: statement; if
    single: compound statement; header
    single: compound statement; body
    single: conditional statement
    single: statement; pass

Conditional execution
---------------------

In order to write useful programs, we almost always need the ability to check
conditions and change the behavior of the program accordingly. **Conditional
statements** give us this ability. The simplest form is the **if**
statement:

.. sourcecode:: python
    
    if x % 2 == 0:
        print(x, " is even.")
        print("Did you know that 2 is the only even number that is prime?")
    else:
        print(x, " is odd.") 
        print("Did you know that multiplying two odd numbers " + 
                                             "always gives an odd result?")
    

The boolean expression after the ``if`` statement is called the **condition**.
If it is true, then all the indented statements get executed. If not, then all the statements
indented under the `else` clause get executed. 

.. sidebar::  Flowchart of a **if** statement with an **else** 

   .. image:: illustrations/flowchart_if_else.png  

The syntax for an ``if`` statement looks like this:

.. sourcecode:: python
    
    if BOOLEAN EXPRESSION:
        STATEMENTS_1        # executed if condition evaluates to True
    else:
        STATEMENTS_2        # executed if condition evaluates to False

As with the function definition from the last chapter and other compound
statements like ``for``, the ``if`` statement consists of a header line and a body. The header
line begins with the keyword ``if`` followed by a *boolean expression* and ends with
a colon (:).

The indented statements that follow are called a **block**. The first
unindented statement marks the end of the block. 

Each of the statements inside the first block of statements are executed in order if the boolean
expression evaluates to ``True``. The entire first block of statements 
is skipped if the boolean expression evaluates to ``False``, and instead
all the statements under the ``else`` clause are executed. 

There is no limit on the number of statements that can appear under the two clauses of an
``if`` statement, but there has to be at least one statement in each block.  Occasionally, it is useful
to have a section with no statements (usually as a place keeper, or scaffolding, 
for code you haven't written yet). In that case, you can use the ``pass`` statement, which
does nothing except act as a placeholder.

.. sourcecode:: python
    
    if True:          # This is always true
        pass          # so this is always executed, but it does nothing
    else:
        pass 


.. index:: alternative execution, branch, wrapping code in a function

Omitting the `else` clause
--------------------------

.. sidebar::  Flowchart of an **if** with no **else** 

   .. image:: illustrations/flowchart_if_only.png

Another form of the ``if`` statement is one in which the ``else`` clause is omitted entirely.  
In this case, when the condition evaluates to ``True``, the statements are
executed, otherwise the flow of execution continues to the statement after the ``if``.

      
.. sourcecode:: python

    if x < 0:
        print("The negative number ",  x, " is not valid here.")
        x = 42
        print("I've decided to use the number 42 instead.")
        
    print("The square root of ", x, "is", math.sqrt(x))
    
In this case, the print function that outputs the square root is the one after the ``if`` - not
because we left a blank line, but because of the way the code is indented.    Note too that
the function call ``math.sqrt(x)`` will give an error unless you have an ``import math`` statement, 
usually placed near the top of your script.  

.. admonition:: Python terminology
    
    Python documentation sometimes uses the term **suite** of statements to mean what we
    have called a *block* here. They mean the same thing, and since most other languages and
    computer scientists use the word *block*, we'll stick with that.
    
    Notice too that ``else`` is not a statement.  The ``if`` statement has 
    two *clauses*, one of which is the (optional) ``else`` clause.
      
        
.. index::
    single: chained conditional 
    single: conditional; chained

Chained conditionals
--------------------

Sometimes there are more than two possibilities and we need more than two
branches. One way to express a computation like that is a **chained
conditional**:
   
.. sourcecode:: python
    
    if x < y:
        STATEMENTS_A
    elif x > y:
        STATEMENTS_B
    else:
        STATEMENTS_C

Flowchart of this chained conditional 

.. image:: illustrations/flowchart_chained_conditional.png        
        
``elif`` is an abbreviation of ``else if``. Again, exactly one branch will be
executed. There is no limit of the number of ``elif`` statements but only a
single (and optional) final ``else`` statement is allowed and it must be the last
branch in the statement:

.. sourcecode:: python
    
    if choice == 'a':
        function_a()
    elif choice == 'b':
        function_b()
    elif choice == 'c':
        function_c()
    else:
        print("Invalid choice.")

Each condition is checked in order. If the first is false, the next is checked,
and so on. If one of them is true, the corresponding branch executes, and the
statement ends. Even if more than one condition is true, only the first true
branch executes.


.. index::
    single: nested conditionals
    single: conditionals; nested

Nested conditionals
-------------------

One conditional can also be **nested** within another. (It is the same theme of
composibility, again!)  We could have written
the previous example as follows:

.. sidebar:: Flowchart of this nested conditional

   .. image:: illustrations/flowchart_nested_conditional.png

.. sourcecode:: python
    
    if x < y:
        STATEMENTS_A
    else:
        if x > y:
            STATEMENTS_B
        else:
            STATEMENTS_C

The outer conditional contains two branches. 
The second branch contains another ``if`` statement, which
has two branches of its own. Those two branches could contain
conditional statements as well.

Although the indentation of the statements makes the structure apparent, nested
conditionals very quickly become difficult to read.  In general, it is a good
idea to avoid them when you can.

Logical operators often provide a way to simplify nested conditional
statements. For example, we can rewrite the following code using a single
conditional:

.. sourcecode:: python
    
    if 0 < x:            # assume x is an int here
        if x < 10:
            print("x is a positive single digit.")

The ``print`` function is called only if we make it past both the
conditionals, so we can use the ``and`` operator:

.. sourcecode:: python
    
    if 0 < x and x < 10:
        print("x is a positive single digit.")


.. index::
    single: return statement
    single: statement; return

The ``return`` statement
------------------------

The ``return`` statement, with or without a value, depending on whether the 
function is fruitful or not, allows you to terminate the execution of a function
before you reach the end. One reason to use it is if you detect an error
condition:

.. sourcecode:: python
    
    def print_square_root(x):
        if x <= 0:
            print("Positive numbers only, please.")
            return
    
        result = x**0.5
        print("The square root of", x, "is", result)

The function ``print_square_root`` has a parameter named ``x``. The first thing
it does is check whether ``x`` is less than or equal to 0, in which case it
displays an error message and then uses ``return`` to exit the function. The
flow of execution immediately returns to the caller, and the remaining lines of
the function are not executed.


.. index::
    single: type conversion
    single: type; conversion

Type conversion
---------------

We've had a first look at this in an earlier chapter.  Seeing it again won't hurt! 

Many Python types comes with a built-in function that attempts to convert values
of another type into its own type. The ``int(ARGUMENT)`` function, for example,
takes any value and converts it to an integer, if possible, or complains
otherwise:

.. sourcecode:: python
    
    >>> int("32")
    32
    >>> int("Hello")
    ValueError: invalid literal for int() with base 10: 'Hello'

``int`` can also convert floating-point values to integers, but remember
that it truncates the fractional part:

.. sourcecode:: python
    
    >>> int(-2.3)
    -2
    >>> int(3.99999)
    3
    >>> int("42")
    42
    >>> int(1.0)
    1

The ``float(ARGUMENT)`` function converts integers and strings to floating-point
numbers:

.. sourcecode:: python
    
    >>> float(32)
    32.0
    >>> float("3.14159")
    3.14159
    >>> float(1)
    1.0

It may seem odd that Python distinguishes the integer value ``1`` from the
floating-point value ``1.0``. They may represent the same number, but they
belong to different types. The reason is that they are represented differently
inside the computer.

The ``str(ARGUMENT)`` function converts any argument given to it to type
``string``:

.. sourcecode:: python
    
    >>> str(32)
    '32'
    >>> str(3.14149)
    '3.14149'
    >>> str(True)
    'True'
    >>> str(true)
    Traceback (most recent call last):
      File "<interactive input>", line 1, in <module>
    NameError: name 'true' is not defined

``str(ARGUMENT)`` will work with any value and convert it into a string.  As
mentioned earlier, ``True`` is boolean value; ``true`` is not.

.. index:: bar chart

A Turtle Bar Chart
------------------

The turtle has a lot more power than we've seen so far.  If you want to see the full documentation,
look at http://docs.python.org/library/turtle.html, or within PyScripter, use *Help* and search for the
turtle module.

Here are a couple of new tricks for our turtles: 

* We can get a turtle to display text on the canvas at the turtle's current position.  The method is
  ``alex.write("Hello")``.
* One can fill a shape (circle, semicircle, triangle, etc.) with a fill colour.  It is a two-step process.
  First you call the method ``alex.begin_fill()``, then you draw the shape, then call ``alex.end_fill()``. 
* We've previously set the color of our turtle - we can now also set it's fillcolour, which need not
  be the same as the turtle and the pen colour.  We use ``alex.color("blue","red")`` to set the turtle
  to draw in blue, and fill in red. 
  
  
Ok, so can we get tess to draw a bar chart?  Let us start with some data to be charted,

``xs = [48, 117, 200, 240, 160, 260, 220]``

Corresponding to each data measurement, we'll draw a simple rectangle of that height, with a fixed width.

.. sourcecode:: python

    def draw_bar(t, height):
        """ Get turtle t to draw one bar, of height. """
        t.left(90)           
        t.forward(height)     # Draw up the left side
        t.right(90)
        t.forward(40)         # width of bar, along the top
        t.right(90)
        t.forward(height)     # And down again!
        t.left(90)            # put the turtle facing the way we found it.
        t.forward(10)         # leave small gap after each bar
 
    ...    
    for v in xs:              # assume xs and tess are ready 
        draw_bar(tess, v)    

.. image:: illustrations/tess_bar_1.png

Ok, not fantasically impressive, but it is a nice start!  The important thing here
was the mental chunking, or how we broke the problem into smaller pieces. Our chunk
is to draw one bar, and we wrote a function to do that. Then, for the whole
chart, we repeatedly called our function.

Next, at the top of each bar, we'll print the value of the data.
We'll do this in the body of ``draw_bar``, by adding   ``t.write('  ' + str(height))`` 
as the new third line of the body.
We've put a little space in front of the number, and turned the 
number into a string.  Without this extra space we tend
to cramp our text awkwardly against the bar to the left.   
The result looks a lot better now:

.. image:: illustrations/tess_bar_2.png

And now we'll add two lines to fill each bar.  Our final program, at :download:`tess_barchart.py <resources/ch05/tess_barchart.py>`, now looks like this:

.. sourcecode:: python
   :linenos:
   
    def draw_bar(t, height):
        """ Get turtle t to draw one bar, of height. """
        t.begin_fill()               # added this line
        t.left(90)
        t.forward(height)
        t.write('  '+ str(height))   
        t.right(90)
        t.forward(40)
        t.right(90)
        t.forward(height)
        t.left(90)
        t.end_fill()             # added this line
        t.forward(10)                 

    wn = turtle.Screen()         # Set up the window and its attributes
    wn.bgcolor("lightgreen")

    tess = turtle.Turtle()       # create tess and set some attributes
    tess.color("blue", "red")
    tess.pensize(3)

    xs = [48,117,200,240,160,260,220]

    for a in xs:
        draw_bar(tess, a)

    wn.mainloop()

It produces the following, which is more satisfying:

.. image:: illustrations/tess_bar_3.png


Mmm.  Perhaps the bars should not be joined to each other at the bottom.  We'll need to pick up the pen while making the gap between the bars.  We'll leave that as an exercise for you!

Glossary
--------

.. glossary::

    block
        A group of consecutive statements with the same indentation.

    body
        The block of statements in a compound statement that follows the
        header.

    boolean expression
        An expression that is either true or false.

    boolean value
        There are exactly two boolean values: ``True`` and ``False``. Boolean
        values result when a boolean expression is evaluated by the Python
        interepreter.  They have type ``bool``.

    branch
        One of the possible paths of the flow of execution determined by
        conditional execution.

    chained conditional
        A conditional branch with more than two possible flows of execution. In
        Python chained conditionals are written with ``if ... elif ... else``
        statements.

    comparison operator
        One of the operators that compares two values: ``==``, ``!=``, ``>``,
        ``<``, ``>=``, and ``<=``.

    condition
        The boolean expression in a conditional statement that determines which
        branch is executed.

    conditional statement
        A statement that controls the flow of execution depending on some
        condition. In Python the keywords ``if``, ``elif``, and ``else`` are
        used for conditional statements.

    logical operator
        One of the operators that combines boolean expressions: ``and``,
        ``or``, and ``not``.

    modulus operator
        An operator, denoted with a percent sign ( ``%``), that works on
        integers and yields the remainder when one number is divided by
        another.

    nesting
        One program structure within another, such as a conditional statement
        inside a branch of another conditional statement.

    prompt
        A visual cue that tells the user to input data.

    type conversion
        An explicit function call that takes a value of one type and computes a
        corresponding value of another type.

    wrapping code in a function
        The process of adding a function header and parameters to a sequence
        of program statements is often refered to as "wrapping the code in
        a function".  This process is very useful whenever the program
        statements in question are going to be used multiple times.  It is
        even more useful when it allows the programmer to express their mental
        chunking, and how they've broken a complex problem into pieces.


Exercises
---------

#. Evaluate the following numerical expressions in your head, then use
   the Python interpreter to check your results:

    #. ``>>> 5 % 2``
    #. ``>>> 9 % 5``
    #. ``>>> 15 % 12``
    #. ``>>> 12 % 15``
    #. ``>>> 6 % 6``
    #. ``>>> 0 % 7``
    #. ``>>> 7 % 0``

   What happened with the last example? Why? If you were able to correctly
   anticipate the computer's response in all but the last one, it is time to
   move on. If not, take time now to make up examples of your own. Explore the
   modulus operator until you are confident you understand how it works.
   
#. You look at the clock and it is exactly 2pm.  You set an alarm to go off
   in 51 hours.  At what time does the alarm go off?  
   
#. Write a Python program to solve the general version of the above problem.
   Ask the user for the time now (in hours), and ask for the number of hours to wait.  
   Your program should output what the time will be on the clock when the alarm goes off.
   
#. Assume the days of the week are numbered 0,1,2,3,4,5,6 from Sunday to Saturday.
   Write a function which is given the day number, and it returns the day name (a string).
 
#. You go on a wonderful holiday (perhaps to jail, if you don't like happy exercises)
   leaving on day number 3 (a Wednesday).  You return home after 137 sleeps. 
   Write a general version of the program which asks for the starting day number, and
   the length of your stay, and it will tell you the name of day of the week you will return on.   
   
#. Give the logical opposites of these conditions
    
    #.  ``a > b`` 
    #.  ``a >= b``
    #.  ``a >= 18  and  day == 3``
    #.  ``a >= 18  and  day != 3``
    
#.  What do these expressions evaluate to?

    #.  ``3 == 3``
    #.  ``3 != 3``
    #.  ``3 >= 4``
    #.  ``not (3 < 4)``
    
#.  Write a function which is given an exam mark, and it returns a string --- the grade for that mark --- according to this 
    scheme:   
    
    .. table::  
    
       =======   =====
       Mark      Grade
       =======   =====
       >= 75     First   
       [70-75)   Upper Second   
       [60-70)   Second   
       [50-60)   Third 
       [45-50)   F1 Supp   
       [40-45)   F2   
       < 40      F3   
       =======   =====    
    
    The square and round brackets denote closed and open intervals. 
    A closed interval includes the number, and open interval excludes it.   So 39.99999 gets grade F3, but 40 gets grade F2.
    Assume ::
    
       xs = [83, 75, 74.9, 70, 69.9, 65, 60, 59.9, 55, 50, 
                            49.9, 45, 44.9, 40, 39.9, 2, 0 
    
    Test your function by printing the mark and the grade for all the elements in this list.
    
#.  Modify the turtle bar chart program so that the pen is up for the small gaps between each bar.

#.  Modify the turtle bar chart program so that the bar for any value 
    of 200 or more is filled with red, values between [100 and 200) are filled with yellow,
    and bars representing values less than 100 are filled with green.    
  
#.  In the turtle bar chart program, what do you expect to happen if one or more 
    of the data values in the list is negative?   Try it out.  Change the
    program so that when it prints the text value for the negative bars, it puts
    the text below the bottom of the bar. 
  
#.  Write a function ``find_hypot`` which, given the length of two sides of a right-angled triangle, returns
    the length of the hypotenuse.  (Hint:  ``x ** 0.5`` will return the square root.)
    
#.  Write a function ``is_rightangled`` which, given the length of three sides of a triangle, 
    will determine whether the triangle is right-angled.  Assume that the third argument to the
    function is always the longest side.  It will return ``True`` if the triangle 
    is right-angled, or ``False`` otherwise.  
    
    Hint: floating point arithmetic is not always exactly accurate,
    so it is not safe to test floating point numbers for equality. 
    If a good programmer wants to know whether
    ``x`` is equal or close enough to ``y``, they would probably code it up as
    
    .. sourcecode:: python
    
      if  abs(x-y) < 0.000001:    # if x is approximately equal to y
          ...    
   
#.  Extend the above program so that the sides can be given to the function in any order.