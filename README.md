# 19-20-PH1999-Physics-project-Jamie-Gowers
Student ZHAP054 Foundation Individual Scientific Project

import numpy as np
import matplotlib.pyplot as pyplot
def findbestfit(t):
  x=np.array([5,10,15,20,25])
  y=np.array([0.2,0.5,0.8,1.0,1.3])
  yerr=np.array([0.05,0.05,0.05,0.05,0.05])
  Xsquarray=np.array([])
  fx=t*x
  index=0
  for i in x:
    val=(y[index]-fx[index])**2
    Xsquarray=np.append(Xsquarray,val/0.0025)
    index=index+1
  best_fit=np.sum(Xsquarray)
  return best_fit

chiimon=10000
for grad in np.arange(0.045, 0.055, 0.0005):
  newchi=findbestfit(grad)
  if newchi<chiimon:
    bestfit=newchi
    chiimon=newchi
print(bestfit)
  #my prediction from veiwing the raw data is that when fx/x is 0.05, fx/x is most like y/x
  # this created a chi**2 of 3, the minimizer code creates 2.1375, so i wasnt to far off.
