import turtle
import colorsys
import math

# Screen setup
screen = turtle.Screen()
screen.bgcolor("black")
screen.title("Rainbow Heart")

t = turtle.Turtle()
t.speed(0)
t.width(2)
t.hideturtle()

# Heart equation
def heart(t):
    x = 16 * math.sin(t) ** 3
    y = (13 * math.cos(t)
         - 5 * math.cos(2 * t)
         - 2 * math.cos(3 * t)
         - math.cos(4 * t))
    return x * 15, y * 15

# Draw colorful rays
h = 0
for angle in range(360):
    theta = math.radians(angle)

    x, y = heart(theta)

    color = colorsys.hsv_to_rgb(h, 1, 1)
    h += 1 / 360

    t.pencolor(color)

    # Draw line
    t.penup()
    t.goto(0, 0)
    t.pendown()
    t.goto(x, y)

    # Draw heart endpoint
    t.penup()
    t.goto(x, y)
    t.pendown()
    t.begin_fill()
    t.circle(3)
    t.end_fill()

turtle.done()