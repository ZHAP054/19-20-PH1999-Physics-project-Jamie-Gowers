# 19-20-PH1999-Physics-project-Jamie-Gowers
Student ZHAP054 Foundation Individual Scientific Project
In this commintment, I added the first week's work of tasks. I got pyplot working, and ploted the data I was given and then the data predicted by the equation: V=(Gm/r)**0.5

import numpy as np
import matplotlib.pyplot as pyplot

def makearray(selected):
  galaxy=open("galaxys.txt","r")
  array=np.array([])
  colon=1
  titleskip=True
  for line in galaxy.readlines():
    for word in line.split():
      if titleskip==False:
        if colon==selected:
          g=float(word)
          array=np.append(array,g)
        colon=colon+1
        if colon>5:
          colon=1
      if titleskip==True:
        titleskip=False
        break
  galaxy.close()
  return array
radarray=makearray(1)
velarray=makearray(2)
deltradarray=makearray(3)
deltvelarray=makearray(4)
massarray=makearray(5)

predvelarray=np.array([])
index=0
for rad in radarray:
  val=4.3e-06*massarray[index]
  predvel=(val/rad)**0.5
  predvelarray=np.append(predvelarray,predvel)
  index=index+1

pyplot.plot(radarray,velarray,"ro",label="Atual data")
pyplot.plot(radarray,predvelarray,"ro",label="predicted data")
pyplot.xlabel("Star's orbital radius (kpc)")
pyplot.ylabel("Star's rotational speed km/s")
pyplot.show()
