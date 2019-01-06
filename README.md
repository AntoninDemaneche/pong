```
from tkinter import *

#Positions 
refreshrate=50
flag = 0
v,dx,dy=0,-10,15

#Raquette
PosXG=30 
PosYG=140
PosXD=450
PosYD=140
x=42
y=152
dx=10
dy=10
def move():
    global x,y,dx,dy,flag,PosXD,PosYD,PosXG,PosYG,balle
    xp, yp = x+dx, y+dy
    print (xp,yp)
    if xp >= PosXD + 5 and yp < PosYD+50 and yp > PosYD-10:
        dx = -dx
    if xp <= PosXG - 5 and yp < PosYG+50 and yp > PosYG-10:
        dx = -dx
    if yp> Hauteur -15 or yp < 15:
        dy = -dy
    x, y = x+dx, y+dy
    Canevas.coords(balle,x,y,x+16,y+16)
  
    if flag > 0:
        Mafenetre.after(50,move)

  
def start():
    global flag
    flag=flag+1
    if flag==1:
        move()
    "Start"
 

 
     
def Clavier(event):
   
    global PosXD, PosYD,PosXG,PosYG
    touche=event.keysym
    print("Touche :", touche)
     
     
 
    #déplacement vers le haut
    if touche == 'Up':
        PosYD=PosYD-20
    #déplacement vers le bas
    if touche == 'Down':
        PosYD=PosYD+20
         
    Canevas.coords(droite,PosXD-10,PosYD-10,PosXD+10,PosYD+50)
 
    if touche == 'a':
        PosYG=PosYG-20
    #déplacement vers le bas
    if touche == 'q':
        PosYG=PosYG+20
    Canevas.coords(gauche,PosXG-10,PosYG-10,PosXG+10,PosYG+50)
     
     
     
Mafenetre = Tk() 
Mafenetre.title('PONG') 
largeur = 480 
Hauteur = 320 

Canevas = Canvas(Mafenetre, width = largeur, height = Hauteur, bg='black')
Canevas.pack()

Button(Mafenetre, text='Start',command=start).pack(side=LEFT, padx=10)

Button(Mafenetre, text='Quitter',command=Mafenetre.destroy).pack(side=LEFT,padx=5,pady=5)
droite = Canevas.create_rectangle(PosXD-10,PosYD-10,PosXD+10,PosYD+50,width=2,outline='white',fill='white')
gauche = Canevas.create_rectangle(PosXG-10,PosYG-10,PosXG+10,PosYG+50,width=2,outline='white',fill='white')
balle = Canevas.create_oval(x,y,x+16,y+16,width=1,outline='white',fill='white')

 
 
Canevas.focus_set()
 
Canevas.bind('<Key>', Clavier) 
#Créer une boucle
Mafenetre.mainloop()
```
