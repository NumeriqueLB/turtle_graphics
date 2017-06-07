
#-----Statement of Authorship----------------------------------------#
#
#  This is an individual assessment item.  By submitting this
#  code I agree that it represents my own work.  I am aware of
#  the University rule that a student must not act in a manner
#  which constitutes academic dishonesty as stated and explained
#  in QUT's Manual of Policies and Procedures, Section C/5.3
#  "Academic Integrity" and Section E/2.1 "Student Code of Conduct".
#
#    Student no: n9143165
#    Student name: Nicholas Beaumont
#
#  NB: Files submitted without a completed copy of this statement
#  will not be marked.  All files submitted will be subjected to
#  software plagiarism analysis using the MoSS system
#  (http://theory.stanford.edu/~aiken/moss/).
#
#--------------------------------------------------------------------#



#-----Assignment Description-----------------------------------------#
#
#  BUILDING BLOCKS
#
#  This assignment tests your skills at defining functions, processing
#  data stored in lists and performing the arithmetic calculations
#  necessary to display a complex visual image.  The incomplete
#  Python script below is missing a crucial function, "stack_blocks".
#  You are required to complete this function so that when the
#  program is run it produces a picture of a pile of building blocks
#  whose arrangement is determined by data stored in a list which
#  specifies the blocks' locations.  See the instruction
#  sheet accompanying this file for full details.
#
#  Note that this assignment is in two parts, the second of which
#  will be released only just before the final deadline.  This
#  template file will be used for both parts and you will submit
#  your final solution as a single file, whether or not you
#  complete both parts of the assignment.
#
#--------------------------------------------------------------------#



#-----Preamble-------------------------------------------------------#
#
# This section imports necessary functions and defines constant
# values used for creating the drawing canvas.  You should not change
# any of the code in this section.
#

# Import the functions needed to complete this assignment.  You
# should not need to use any other modules for your solution.

from turtle import *
from math import *

# Define constant values used in the main program that sets up
# the drawing canvas.  Do not change any of these values.

block_size = 250 # pixels
top_and_bottom_border = 75 # pixels
left_and_right_border = 150 # pixels
canvas_width = (block_size + left_and_right_border) * 2
canvas_height = (block_size + top_and_bottom_border) * 2

#
#--------------------------------------------------------------------#



#-----Functions for Managing the Canvas------------------------------#
#
# The functions in this section are called by the main program to
# set up the drawing canvas for your image.  You should not change
# any of the code in this section.
#

# Set up the canvas and draw the background for the overall image
def create_drawing_canvas():

    # Set up the drawing canvas
    setup(canvas_width, canvas_height)

    # Set the coordinate system so that location (0, 0) is centred on
    # the point where the blocks will be stacked
    setworldcoordinates(-canvas_width / 2, -top_and_bottom_border,
                        canvas_width / 2, canvas_height - top_and_bottom_border)

    # Draw as fast as possible
    tracer(False)

    # Colour the sky blue
    bgcolor('sky blue')

    # Draw the ground as a big green rectangle (sticking out of the
    # bottom edge of the drawing canvas slightly)
    overlap = 50 # pixels
    penup()
    goto(-(canvas_width / 2 + overlap), -(top_and_bottom_border + overlap)) # start at the bottom-left
    fillcolor('pale green')
    begin_fill()
    setheading(90) # face north
    forward(top_and_bottom_border + overlap)
    right(90) # face east
    forward(canvas_width + overlap * 2)
    right(90) # face south
    forward(top_and_bottom_border + overlap)
    end_fill()
    penup()

    # Draw a friendly sun peeking into the image
    goto(-canvas_width / 2, block_size * 2)
    color('yellow')
    dot(250)

    # Reset everything ready for the student's solution
    color('black')
    width(1)
    penup()
    home()
    setheading(0)
    tracer(True)



# As a debugging aid, mark the coordinates of the centres and corners
# of the places where the blocks will appear
def mark_coords(show_corners = False, show_centres = False):

    # Go to each coordinate, draw a dot and print the coordinate, in the given colour
    def draw_each_coordinate(colour):
        color(colour)
        for x_coord, y_coord in coordinates:
            goto(x_coord, y_coord)
            dot(4)
            write(' ' + str(x_coord) + ', ' + str(y_coord), font = ('Arial', 12, 'normal'))

    # Don't draw lines between the coordinates
    penup()

    # The list of coordinates to display
    coordinates = []

    # Only mark the corners if the corresponding argument is True
    if show_corners:
        coordinates = [[-block_size, block_size * 2], [0, block_size * 2], [block_size, block_size * 2],
                       [-block_size, block_size], [0, block_size], [block_size, block_size],
                       [-block_size, 0], [0, 0], [block_size, 0]]
        draw_each_coordinate('dark blue')

    # Only mark the centres if the corresponding argument is True
    if show_centres:
        coordinates = [[-block_size / 2, block_size / 2], [block_size / 2, block_size / 2],
                       [-block_size / 2, block_size + block_size / 2], [block_size / 2, block_size + block_size / 2]]
        draw_each_coordinate('red')

    # Put the cursor back how it was
    color('black')
    home()


# End the program by hiding the cursor and releasing the window
def release_drawing_canvas():
    tracer(True)
    hideturtle()
    done()

#
#--------------------------------------------------------------------#



#-----Test data------------------------------------------------------#
#
# These are the data sets you will use to test your code.
# Each of the data sets is a list specifying the locations of
# the building blocks:
#
# 1. The name of the block, from 'Block A' to 'Block D'
# 2. The place to put the block, either 'Top left', 'Top right',
#    'Bottom left' or 'Bottom right'
# 3. The block's orientation, meaning the direction in which the top
#    of the block is pointing, either 'Up', 'Down', 'Left' or 'Right'
# 4. An optional mystery value, 'X' or 'O', whose purpose will be
#    revealed only in the second part of the assignment
#
# Each data set does not necessarily mention all four blocks.
#
# You can create further data sets, but do not change any of the
# given ones below because they will be used to test your submission.
#

# The following data set doesn't require drawing any blocks
# at all.  You may find it useful as a dummy argument when you
# first start developing your "draw_attempt" function.

arrangement_00 = []

# Each of the following data sets specifies drawing just one block
# in an upright orientation.  You may find them useful when
# creating your individual pieces.

arrangement_01 = [['Block A', 'Bottom left', 'Up', 'O']]
arrangement_02 = [['Block B', 'Bottom right', 'Up', 'O']]
arrangement_03 = [['Block C', 'Bottom left', 'Up', 'O']]
arrangement_04 = [['Block D', 'Bottom right', 'Up', 'O']]

# Each of the following data sets specifies drawing just one block
# in non-upright orientations.  You may find them useful when
# ensuring that you can draw all the blocks facing in different
# directions.

arrangement_10 = [['Block A', 'Bottom left', 'Down', 'O']]
arrangement_11 = [['Block A', 'Bottom right', 'Left', 'O']]
arrangement_12 = [['Block A', 'Bottom left', 'Right', 'O']]

arrangement_13 = [['Block B', 'Bottom left', 'Down', 'O']]
arrangement_14 = [['Block B', 'Bottom right', 'Left', 'O']]
arrangement_15 = [['Block B', 'Bottom left', 'Right', 'O']]

arrangement_16 = [['Block C', 'Bottom left', 'Down', 'O']]
arrangement_17 = [['Block C', 'Bottom right', 'Left', 'O']]
arrangement_18 = [['Block C', 'Bottom left', 'Right', 'O']]

arrangement_19 = [['Block D', 'Bottom left', 'Down', 'O']]
arrangement_20 = [['Block D', 'Bottom right', 'Left', 'O']]
arrangement_21 = [['Block D', 'Bottom left', 'Right', 'O']]

# The following data sets all stack various numbers of
# blocks in various orientations

arrangement_30 = [['Block C', 'Bottom right', 'Up', 'O'],
                  ['Block D', 'Top right', 'Up', 'O']]
arrangement_31 = [['Block A', 'Bottom left', 'Up', 'O'],
                  ['Block C', 'Bottom left', 'Up', 'O']]

arrangement_32 = [['Block B', 'Bottom right', 'Up', 'O'],
                  ['Block D', 'Bottom left', 'Up', 'O'],
                  ['Block C', 'Top right', 'Up', 'O']]
arrangement_33 = [['Block B', 'Bottom right', 'Up', 'O'],
                  ['Block D', 'Bottom left', 'Up', 'O'],
                  ['Block A', 'Top left', 'Up', 'O']]
arrangement_34 = [['Block B', 'Bottom left', 'Up', 'O'],
                  ['Block A', 'Bottom right', 'Up', 'O'],
                  ['Block D', 'Top left', 'Up', 'O'],
                  ['Block C', 'Top right', 'Up', 'O']]

arrangement_40 = [['Block C', 'Bottom right', 'Left', 'O'],
                  ['Block D', 'Top right', 'Right', 'O']]
arrangement_41 = [['Block A', 'Bottom left', 'Down', 'O'],
                  ['Block C', 'Bottom left', 'Up', 'O']]

arrangement_42 = [['Block B', 'Bottom right', 'Left', 'O'],
                  ['Block D', 'Bottom left', 'Left', 'O'],
                  ['Block C', 'Top right', 'Down', 'O']]
arrangement_43 = [['Block B', 'Bottom right', 'Right', 'O'],
                  ['Block D', 'Bottom left', 'Left', 'O'],
                  ['Block A', 'Top left', 'Right', 'O']]
arrangement_44 = [['Block B', 'Bottom left', 'Down', 'O'],
                  ['Block A', 'Bottom right', 'Left', 'O'],
                  ['Block D', 'Top left', 'Right', 'O'],
                  ['Block C', 'Top right', 'Up', 'O']]

arrangement_50 = [['Block B', 'Bottom right', 'Left', 'O'],
                  ['Block D', 'Bottom left', 'Left', 'O'],
                  ['Block C', 'Top right', 'Down', 'X']]
arrangement_51 = [['Block B', 'Bottom right', 'Right', 'O'],
                  ['Block D', 'Bottom left', 'Left', 'O'],
                  ['Block A', 'Top left', 'Right', 'X']]
arrangement_52 = [['Block B', 'Bottom left', 'Down', 'O'],
                  ['Block A', 'Bottom right', 'Left', 'O'],
                  ['Block D', 'Top left', 'Right', 'O'],
                  ['Block C', 'Top right', 'Up', 'X']]

arrangement_60 = [['Block B', 'Bottom right', 'Left', 'X'],
                  ['Block D', 'Bottom left', 'Left', 'O'],
                  ['Block C', 'Top right', 'Down', 'O']]
arrangement_61 = [['Block B', 'Bottom right', 'Right', 'O'],
                  ['Block D', 'Bottom left', 'Left', 'X'],
                  ['Block A', 'Top left', 'Right', 'O']]
arrangement_62 = [['Block B', 'Bottom left', 'Down', 'X'],
                  ['Block A', 'Bottom right', 'Left', 'X'],
                  ['Block D', 'Top left', 'Right', 'O'],
                  ['Block C', 'Top right', 'Up', 'O']]

# The following arrangements create your complete image, but
# oriented the wrong way

arrangement_80 = [['Block C', 'Bottom right', 'Left', 'O'],
                  ['Block D', 'Top right', 'Left', 'X'],
                  ['Block A', 'Bottom left', 'Left', 'O'],
                  ['Block B', 'Top left', 'Left', 'O']]

arrangement_81 = [['Block B', 'Bottom right', 'Right', 'X'],
                  ['Block D', 'Bottom left', 'Right', 'X'],
                  ['Block A', 'Top right', 'Right', 'O'],
                  ['Block C', 'Top left', 'Right', 'O']]

arrangement_89 = [['Block A', 'Bottom right', 'Down', 'O'],
                  ['Block C', 'Top right', 'Down', 'O'],
                  ['Block B', 'Bottom left', 'Down', 'O'],
                  ['Block D', 'Top left', 'Down', 'O']]

# The following arrangements should create your complete image
# (but with the blocks stacked in a different order each time)

arrangement_90 = [['Block C', 'Bottom left', 'Up', 'O'],
                  ['Block D', 'Bottom right', 'Up', 'O'],
                  ['Block B', 'Top right', 'Up', 'X'],
                  ['Block A', 'Top left', 'Up', 'O']]

arrangement_91 = [['Block D', 'Bottom right', 'Up', 'X'],
                  ['Block C', 'Bottom left', 'Up', 'X'],
                  ['Block A', 'Top left', 'Up', 'O'],
                  ['Block B', 'Top right', 'Up', 'O']]

arrangement_92 = [['Block D', 'Bottom right', 'Up', 'X'],
                  ['Block B', 'Top right', 'Up', 'O'],
                  ['Block C', 'Bottom left', 'Up', 'O'],
                  ['Block A', 'Top left', 'Up', 'O']]

arrangement_99 = [['Block C', 'Bottom left', 'Up', 'O'],
                  ['Block D', 'Bottom right', 'Up', 'O'],
                  ['Block A', 'Top left', 'Up', 'O'],
                  ['Block B', 'Top right', 'Up', 'O']]

#
#--------------------------------------------------------------------#



#-----Student's Solution---------------------------------------------#
#
#  Complete the assignment by replacing the dummy function below with
#  your own "stack_blocks" function.
#

#These functions tell the turtle where to go on the canvas.
def top_left():
    penup()
    goto(0,250)
    setheading(0)
    pendown()
    
def top_right():
    penup()
    goto(250,250)
    setheading(0)
    pendown()
    
def bottom_left():
    penup()
    goto(0,0)
    setheading(0)
    pendown()

def bottom_right():
    penup()
    goto(250,0)
    setheading(0)
    pendown()
    
#These three shapeshifter functions will help the turtle to rotate the blocks.
def shapeshifter_one():
    penup()
    left(90)
    forward(250)
    pendown()

def shapeshifter_two():
    penup()
    left(90)
    forward(250)
    left(90)
    forward(250)
    pendown()

def shapeshifter_three():
    penup()
    left(90)
    forward(250)
    left(90)
    forward(250)
    left(90)
    forward(250)
    pendown()
    
#The first block function.
def block_a():
    #Background
    pendown()
    color('white')
    begin_fill()
    left(180)
    forward(250)
    right(90)
    forward(250)
    right(90)
    forward(250)
    right(90)
    forward(250)
    left(90)
    end_fill()
    
    #Outer aqua shield.
    color('aqua')
    begin_fill()
    left(180)
    forward(170)
    right(90)
    forward(170)
    right(90)
    forward(170)
    right(90)
    forward(170)
    end_fill()

    #Inner maroon shield.
    right(90)
    color('maroon4')
    begin_fill()
    forward(160)
    right(90)
    forward(160)
    right(90)
    forward(160)
    right(90)
    forward(160)
    end_fill()

    #Letter 'W'.
    penup()
    color('white')
    right(135)
    forward(150)
    right(135)
    pendown()
    begin_fill()
    forward(15)
    right(60)
    forward(50)
    left(120)
    forward(25)
    right(120)
    forward(25)
    left(120)
    forward(50)
    right(60)
    forward(15)
    right(120)
    forward(80)
    right(120)
    forward(25)
    left(120)
    forward(25)
    right(120)
    forward(80)
    end_fill()
    penup()
    right(120)
    forward(105)
    right(90)
    forward(105)
    
    #Border.
    pendown()
    color('black')
    width(3)
    right(90)
    forward(250)
    right(90)
    forward(250)
    right(90)
    forward(250)
    right(90)
    forward(250)
    penup()

#Second block function.
def block_b():
    #Background
    color('white')
    begin_fill()
    left(180)
    forward(250)
    right(90)
    forward(250)
    right(90)
    forward(250)
    right(90)
    forward(250)
    left(90)
    end_fill()
    
    #Outer aqua shield.
    color('aqua')
    left(180)
    forward(250)
    begin_fill()
    right(90)
    forward(170)
    right(90)
    forward(170)
    right(90)
    forward(170)
    end_fill()

    #Inner maroon shield.
    color('maroon4')
    right(90)
    forward(10)
    begin_fill()
    forward(160)
    right(90)
    forward(160)
    right(90)
    forward(160)
    end_fill()

    #Letter 'H'.
    penup()
    color('white')
    right(90)
    forward(160)
    right(90)
    forward(160)
    right(90)
    forward(105)
    right(90)
    forward(10)
    pendown()
    begin_fill()
    forward(10)
    right(90)
    forward(35)
    left(90)
    forward(30)
    left(90)
    forward(35)
    right(90)
    forward(10)
    right(90)
    forward(80)
    right(90)
    forward(10)
    right(90)
    forward(35)
    left(90)
    forward(30)
    left(90)
    forward(35)
    right(90)
    forward(10)
    right(90)
    forward(80)
    end_fill()
    penup()
    forward(55)
    right(90)
    forward(150)
    
    #Border.
    color('black')
    width(3)
    right(90)
    penup()
    forward(160)
    pendown()
    right(90)
    forward(160)
    right(90)
    forward(250)
    right(90)
    forward(250)
    right(90)
    forward(250)
    right(90)
    forward(150)
    penup()

#Third block function.
def block_c():
    #Background.
    color('white')
    begin_fill()
    left(180)
    forward(250)
    right(90)
    forward(250)
    right(90)
    forward(250)
    right(90)
    forward(250)
    left(90)
    end_fill()
    
    #Outer aqua shield.
    pendown()
    color('aqua')
    left(90)
    begin_fill()
    forward(250)
    left(90)
    forward(170)
    right(-90)

    #A for-loop in order to get the curve of the outer shield.
    for i in range(100):
        forward(2)
        left(0.5)
    forward(116)
    end_fill()

    #Inner maroon shield.
    color('maroon4')
    left(130)
    penup()
    forward(10)
    pendown()
    begin_fill()
    forward(240)
    left(90)
    forward(160)
    left(90)

    #Another for-loop to get the curve on the inner shield.
    for i in range(101):
        forward(2)
        left(0.5)
    forward(101)
    end_fill()
    penup()
    right(50.5)
    forward(8)
    pendown()

    #Golden Hammer handle.
    penup()
    color('gold')
    left(180)
    forward(145)
    left(120)
    pendown()
    begin_fill()
    forward(60)
    right(120)
    forward(15)
    right(60)
    forward(60)
    end_fill()

    #Golden Hammer.
    penup()
    right(120)
    forward(15)
    right(120)
    pendown()
    begin_fill()
    forward(40)
    right(90)
    forward(30)
    left(90)
    forward(30)
    left(90)
    forward(40)
    left(30)
    forward(30)
    left(30)
    forward(15)
    left(120)
    forward(30)
    right(90)
    forward(50)
    end_fill()
    penup()
    right(60)
    forward(130)
    
    #Border.
    color('black')
    pendown()
    width(3)
    right(90)
    forward(250)
    right(90)
    forward(250)
    right(90)
    forward(250)
    right(90)
    forward(250)
    penup()

#Fourth and final block function.
def block_d():
    #Background.
    color('white')
    begin_fill()
    left(180)
    forward(250)
    right(90)
    forward(250)
    right(90)
    forward(250)
    right(90)
    forward(250)
    left(90)
    end_fill()
    
    #Outer aqua shield.
    color('aqua')
    left(180)
    forward(250)
    pendown()
    right(90)
    begin_fill()
    forward(250)
    right(90)
    forward(170)
    right(90)

    #A for-loop to get the curve on the outer shield.
    for i in range(100):
        forward(2)
        right(0.5)
    forward(116)
    end_fill()
    
    #Inner maroon shield.
    color('maroon4')
    right(130)
    penup()
    forward(10)
    pendown()
    begin_fill()
    forward(240)
    right(90)
    forward(160)
    right(90)

    #Another for-loop to get the curve of the inner shield.
    for i in range(101):
        forward(2)
        right(0.5)
    forward(101)
    end_fill()
    penup()
    left(50.5)
    forward(8)
    pendown()

    #Golden Hammer.
    penup()
    color('gold')
    left(180)
    forward(158)
    right(60)
    pendown()
    begin_fill()
    forward(30)
    left(90)
    forward(30)
    right(90)
    forward(30)
    right(90)
    forward(40)
    right(30)
    forward(30)
    right(30)
    forward(15)
    right(120)
    forward(30)
    left(90)
    forward(40)
    end_fill()

    #Golden Hammer handle.
    penup()
    left(120)
    pendown()
    begin_fill()
    forward(60)
    right(60)
    forward(10)
    right(120)
    forward(60)
    right(600)
    forward(15)
    end_fill()
    penup()
    forward(117)
    left(90)
    forward(250)
    
    #Border.
    pendown()
    color('black')
    width(3)
    left(90)
    forward(250)
    left(90)
    forward(250)
    left(90)
    forward(250)
    left(90)
    forward(250)
    penup()

def stack_blocks(arrangement):
    for parameter in (arrangement):
        #These for-loops tell the turtle which position to start drawing from depending on what value is in the list.
        if len(arrangement) >= 1:
            if 'Top right' in arrangement[0]:
                top_right()
            if 'Top left' in arrangement[0]:
                top_left()
            if 'Bottom left' in arrangement[0]:
                bottom_left()
            if 'Bottom right' in arrangement [0]:
                bottom_right()
                
            #These two for-loops tell the turtle to move down if the block below it is missing. 
            if 'Top left' in arrangement[0]:
                if 'Bottom left' and 'X' in arrangement[0]:
                    print 'hi'
                    bottom_left()
                elif 'Bottom left' and 'X' in arrangement[1]:
                    print 'pi'
                    bottom_left()
                elif 'Bottom left' and 'X' in arrangement[2]:
                    print 'mi'
                    bottom_left()
                elif 'Bottom left' and 'X' in arrangement[3]:
                    print'li'
                    bottom_left()
            
            if 'Top right' in arrangement[0]:
                if 'Bottom right' and 'X' in arrangement[0]:
                    bottom_right()
                elif 'Bottom right' and 'X' in arrangement[1]:
                    bottom_right()
                elif 'Bottom right' and 'X' in arrangement[2]:
                    bottom_right()
                elif 'Bottom right' and 'X' in arrangement[3]:
                    bottom_right()
            else:
                pass
            
            #These for-loops rotate the block depending on the value in the list.                
            if 'Down' in arrangement[0]:
                if 'Block A' and 'Down' in arrangement[0]:
                    shapeshifter_two()
                elif 'Block B' and 'Down' in arrangement[0]:
                    shapeshifter_two()
                elif 'Block C' and 'Down' in arrangement[0]:
                    shapeshifter_two()
                elif 'Block D' and 'Down' in arrangement[0]:
                    shapeshifter_two()
                    
            if 'Right' in arrangement[0]:
                if 'Block A' and 'Right' in arrangement[0]:
                    shapeshifter_three()
                elif 'Block B' and 'Right' in arrangement[0]:
                    shapeshifter_one()
                elif 'Block C' and 'Right' in arrangement[0]:
                    shapeshifter_three()
                elif 'Block D' and 'Right' in arrangement[0]:
                    shapeshifter_one()
                    
            if 'Left' in arrangement[0]:
                if 'Block A' and 'Left' in arrangement[0]:
                    shapeshifter_one()
                elif 'Block B' and 'Left' in arrangement[0]:
                    shapeshifter_three()
                elif 'Block C' and 'Left' in arrangement[0]:
                    shapeshifter_one
                elif 'Block D' and 'Left' in arrangement[0]:
                    shapeshifter_three()
                    
            #These for-loops tell the turtle whether or not to draw the block depending on if there is an 'X' or 'O' value in the list.                   
            if 'Block A' in arrangement[0]:
                if 'Block A' and 'O' in arrangement[0]:
                    block_a()
                elif 'Block A' and 'X' in arrangement[0]:
                    pass               
            if 'Block B' in arrangement[0]:
                if 'Block B' and 'O' in arrangement[0]:
                    block_b()
                elif 'Block B' and 'X' in arrangement[0]:
                    pass
            if 'Block C' in arrangement[0]:
                if 'Block C' and 'O' in arrangement[0]:
                    block_c()
                elif 'Block C' and 'X' in arrangement[0]:
                    pass               
            if 'Block D' in arrangement[0]:
                if 'Block D' and 'O' in arrangement[0]:
                    block_d()
                elif 'Block D' and 'X' in arrangement[0]:
                    pass
        else:
            break

        if len(arrangement) >= 2:
            #These for-loops tell the turtle which position to start drawing from depending on what value is in the list.
            if 'Top left' in arrangement[1]:
                top_left()
            if 'Top right' in arrangement[1]:
                top_right()
            if 'Bottom right' in arrangement[1]:
                bottom_right()
            if 'Bottom left' in arrangement[1]:
                bottom_left()
                
            #These two for-loops tell the turtle to move down if the block below it is missing.                
            if 'Top left' in arrangement[1]:
                if 'Bottom left' and 'X' in arrangement[0]:
                    bottom_left()
                elif 'Bottom left' and 'X' in arrangement[1]:
                    bottom_left()           
            if 'Top right' in arrangement[1]:
                if 'Bottom right' and 'X' in arrangement[0]:
                    bottom_right()
                elif 'Bottom right' and 'X' in arrangement[1]:
                    bottom_right()

            #These for-loops rotate the block depending on the value in the list.                
            if 'Down' in arrangement[1]:
                if 'Block A' and 'Down' in arrangement[1]:
                    shapeshifter_two()
                elif 'Block B' and 'Down' in arrangement[1]:
                    shapeshifter_two()
                elif 'Block C' and 'Down' in arrangement[1]:
                    shapeshifter_two()
                elif 'Block D' and 'Down' in arrangement[1]:
                    shapeshifter_two()
                    
            if 'Right' in arrangement[1]:
                if 'Block A' and 'Right' in arrangement[1]:
                    shapeshifter_three()
                elif 'Block B' and 'Right' in arrangement[1]:
                    shapeshifter_one()
                elif 'Block C' and 'Right' in arrangement[1]:
                    shapeshifter_three()
                elif 'Block D' and 'Right' in arrangement[1]:
                    shapeshifter_one()
                    
            if 'Left' in arrangement[1]:
                if 'Block A' and 'Left' in arrangement[1]:
                    shapeshifter_one()
                elif 'Block B' and 'Left' in arrangement[1]:
                    shapeshifter_three()
                elif 'Block C' and 'Left' in arrangement[1]:
                    shapeshifter_one()
                elif 'Block D' and 'Left' in arrangement[1]:
                    shapeshifter_three()
                    
            #These for-loops tell the turtle whether or not to draw the block depending on if there is an 'X' or 'O' value in the list.                   
            if 'Block A' in arrangement[1]:
                if 'Block A' and 'O' in arrangement[1]:
                    block_a()
                elif 'Block A' and 'X' in arrangement[1]:
                    pass
            if 'Block B' in arrangement[1]:
                if 'Block B' and 'O' in arrangement[1]:
                    block_b()
                elif 'Block B' and 'X' in arrangement[1]:
                    pass
            if 'Block C' in arrangement[1]:
                if 'Block C' and 'O' in arrangement[1]:
                    block_c()
                elif 'Block C' and 'X' in arrangement[1]:
                    pass
            if 'Block D' in arrangement[1]:
                if 'Block D' and 'O' in arrangement[1]:
                    block_d()
                elif 'Block D' and 'X' in arrangement[1]:
                    pass
        else:
            break

        if len(arrangement) >= 3:
            #These for-loops tell the turtle which position to start drawing from depending on what value is in the list.
            if 'Top left' in arrangement[2]:
                top_left()
            if 'Top right' in arrangement[2]:
                top_right()
            if 'Bottom right' in arrangement[2]:
                bottom_right()
            if 'Bottom left' in arrangement[2]:
                bottom_left()
                
            #These two for-loops tell the turtle to move down if the block below it is missing. 
            if 'Top left' in arrangement[2]:
                if 'Bottom left' and 'X' in arrangement[0]:
                    bottom_left()
                elif 'Bottom left' and 'X' in arrangement[1]:
                    bottom_left()
                elif 'Bottom left' and 'X' in arrangement[2]:
                    bottom_left()           
            if 'Top right' in arrangement[2]:
                if 'Bottom right' and 'X' in arrangement[0]:
                    bottom_right()
                elif 'Bottom right' and 'X' in arrangement[1]:
                    bottom_right()
                elif 'Bottom right' and 'X' in arrangement[2]:
                    bottom_right()
            else:
                pass
            
            #These for-loops rotate the block depending on the value in the list. 
            if 'Down' in arrangement[2]:
                if 'Block A' and 'Down' in arrangement[2]:
                    shapeshifter_two()
                elif 'Block B' and 'Down' in arrangement[2]:
                    shapeshifter_two()
                elif 'Block C' and 'Down' in arrangement[2]:
                    shapeshifter_two()
                elif 'Block D' and 'Down' in arrangement[2]:
                    shapeshifter_two()
                    
            if 'Right' in arrangement[2]:
                if 'Block A' and 'Right' in arrangement[2]:
                    shapeshifter_three()
                elif 'Block B' and 'Right' in arrangement[2]:
                    shapeshifter_one()
                elif 'Block C' and 'Right' in arrangement[2]:
                    shapeshifter_three()
                elif 'Block D' and 'Right' in arrangement[2]:
                    shapeshifter_one()
                    
            if 'Left' in arrangement[2]:
                if 'Block A' and 'Left' in arrangement[2]:
                    shapeshifter_one()
                elif 'Block B' and 'Left' in arrangement[2]:
                    shapeshifter_three()
                elif 'Block C' and 'Left' in arrangement[2]:
                    shapeshifter_one()
                elif 'Block D' and 'Left' in arrangement[2]:
                    shapeshifter_three()
                    
            #These for-loops tell the turtle whether or not to draw the block depending on if there is an 'X' or 'O' value in the list.                   
            if 'Block A' in arrangement[2]:
                if 'Block A' and 'O' in arrangement[2]:
                    block_a()
                elif 'Block A' and 'X' in arrangement[2]:
                    pass
            if 'Block B' in arrangement[2]:
                if 'Block B' and 'O' in arrangement[2]:
                    block_b()
                elif 'Block B' and 'X' in arrangement[2]:
                    pass
            if 'Block C' in arrangement[2]:
                if 'Block C' and 'O' in arrangement[2]:
                    block_c()
                elif 'Block C' and 'X' in arrangement[2]:
                    pass
            if 'Block D' in arrangement[2]:
                if 'Block D' and 'O' in arrangement[2]:
                    block_d()
                elif 'Block D' and 'X' in arrangement[2]:
                    pass
        else:
            break

        if len(arrangement) >= 4:
            #These for-loops tell the turtle which position to start drawing from depending on what value is in the list. 
            if 'Top left' in arrangement[3]:
                top_left()
            if 'Top right' in arrangement[3]:
                top_right()
            if 'Bottom left' in arrangement[3]:
                bottom_left()
            if 'Bottom right' in arrangement[3]:
                bottom_right()
                
            #These for-loops tell the turtle to move down if the block below it is missing.               
            if 'Top left' in arrangement[3]:
                if 'Bottom left' and 'X' in arrangement[0]:
                    bottom_left()
                elif 'Bottom left' and 'X' in arrangement[1]:
                    bottom_left()
                elif 'Bottom left' and 'X' in arrangement[2]:
                    bottom_left()
                elif 'Bottom left' and 'O' in arrangement[3]:
                    top_left()
                elif 'Bottom left' and 'X' in arrangement[3]:
                    bottom_left()
            else:
                pass
            
            if 'Top right' in arrangement[3]:
                if 'Bottom right' and 'X' in arrangement[0]:
                    bottom_right()
                elif 'Bottom right' and 'X' in arrangement[1]:
                    bottom_right()
                elif 'Bottom right' and 'X' in arrangement[2]:
                    bottom_right()
                elif 'Bottom right' and 'X' in arrangement[3]:
                    bottom_right()
            else:
                pass
            
            #These two if-loops are patches to fix particular bugs that I was having with arrangements 80, 81, and 90. 
            if arrangement[3] == ['Block A', 'Top left', 'Up', 'O']:
                top_left()

            if arrangement[2] == ['Block A', 'Bottom left', 'Left', 'O']:
                top_left()
            else:
                pass

            #These for-loops rotate the block depending on the value in the list. 
            if 'Down' in arrangement[3]:
                if 'Block A' and 'Down' in arrangement[3]:
                    shapeshifter_two()
                elif 'Block B' and 'Down' in arrangement[3]:
                    shapeshifter_two()
                elif 'Block C' and 'Down' in arrangement[3]:
                    shapeshifter_two()
                elif 'Block D' and 'Down' in arrangement[3]:
                    shapeshifter_two()                    
            if 'Right' in arrangement[3]:
                if 'Block A' and 'Right' in arrangement[3]:
                    shapeshifter_three()
                elif 'Block B' and 'Right' in arrangement[3]:
                    shapeshifter_one()
                elif 'Block C' and 'Right' in arrangement[3]:
                    shapeshifter_three()
                elif 'Block D' and 'Right' in arrangement[3]:
                    shapeshifter_one()                   
            if 'Left' in arrangement[3]:
                if 'Block A' and 'Left' in arrangement[3]:
                    shapeshifter_one()
                elif 'Block B' and 'Left' in arrangement[3]:
                    shapeshifter_three()
                elif 'Block C' and 'Left' in arrangement[3]:
                    shapeshifter_one()
                elif 'Block D' and 'Left' in arrangement[3]:
                    shapeshifter_three()

            #These for-loops tell the turtle whether or not to draw the block depending on if there is an 'X' or 'O' value in the list.                    
            if 'Block A' in arrangement[3]:
                if 'Block A' and 'O' in arrangement[3]:
                    block_a()
                    break
                elif 'Block A' and 'X' in arrangement[3]:
                    pass
            if 'Block B' in arrangement[3]:
                if 'Block B' and 'O' in arrangement[3]:
                    block_b()
                    break
                elif 'Block B' and 'X' in arrangement[3]:
                    break
            if 'Block C' in arrangement[3]:
                if 'Block C' and 'O' in arrangement[3]:
                    block_c()
                    break
                elif 'Block C' and 'X' in arrangement[3]:
                    break
            if 'Block D' in arrangement[3]:
                if 'Block D' and 'O' in arrangement[3]:
                    block_d()
                    break
                elif 'Block D' and 'X' in arrangement[3]:
                    break
        else:
            break
#
#--------------------------------------------------------------------#



#-----Main Program---------------------------------------------------#
#
# This main program sets up the background, ready for you to start
# drawing your jigsaw pieces.  Do not change any of this code except
# where indicated by comments marked '*****'.
#

# Set up the drawing canvas
create_drawing_canvas()

# Control the drawing speed
# ***** Modify the following argument if you want to adjust
# ***** the drawing speed
speed('fastest')

# Decide whether or not to show the drawing being done step-by-step
# ***** Set the following argument to False if you don't want to wait
# ***** while the cursor moves around the screen
tracer(True)

# Give the window a title
# ***** Replace this title with one that describes the picture
# ***** produced by stacking your blocks correctly
title('West Ham United Football Club')

# Display the corner and centre coordinates of the places where
# the blocks must be placed
# ***** If you don't want to display the coordinates change the
# ***** arguments below to False
mark_coords(True, True)

### Call the student's function to display the stack of blocks
### ***** Change the argument to this function to test your
### ***** code with different data sets

stack_blocks(arrangement_99)
# Exit gracefully
release_drawing_canvas()
#
#--------------------------------------------------------------------#
