from vpython import *
import warnings
warnings.filterwarnings("ignore")
# Parámetros del oscilador armónico
escena = canvas(background = color.white)
#las partes del oscilador
bola = sphere(radius = 1.25, pos = vector(5, 0, 0), color = color.red,
              make_trail = True, trail_type="points")
resorte = helix(pos = vector(-1, 0, 0), axis = vector(5, 0, 0),
                 radius = 0.5, coils = 13, thickness = 0.2, color = color.yellow)#condicion inicial del resorte sin estirar o comprimir
paredL = box(pos=vector(-1.1,0,0), size=vector(0.2,20,20), color=color.green,opacity=0.3)
m=10 #masa de la bola
k= 2 #constante del resorte
dt=0.01 #intervalo de tiempo
dx=0 #velocidad inicial
t=0 #tiempo inicial
x0=resorte.pos.x+resorte.axis.x
def ace(x):
    a=-(k/m)*(x-x0)
    return a
while t<11:
    rate(100)
    ddx=ace(bola.pos.x)#aceleracion
    dx=dx+ddx*dt#velocidad
    bola.pos.x=bola.pos.x+dx*dt#posicion
    print(t, bola.pos.x)
  
    t = t + dt
while t<11:
    rate(100)
    ddx=ace(resorte.pos.x)#aceleracion
    dx=dx+ddx*dt#velocidad
    resorte.pos.x=resorte.pos.x+dx*dt#posicion
    print(t, resorte.pos.x)
    
    t = t + dt
while True:
    rate(30)
