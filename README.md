import turtle
import colorsys
ventana = turtle.Screen()
ventana.bgcolor("black")
ventana.title("Fractal Espiral - GitHub")
t = turtle.Turtle()
t.speed(0) # Velocidad máxima
turtle.tracer(2) # Mejora la velocidad de renderizado
numero_de_colores = 36
numero_de_lados = 200
for i in range(numero_de_lados):
    color = colorsys.hsv_to_rgb(i / numero_de_colores, 1, 1)
    t.pencolor(color)
    # Avanzamos y giramos para crear la espiral
    t.forward(i * 1.5)
    t.left(59)
t.hideturtle()
turtle.done()

