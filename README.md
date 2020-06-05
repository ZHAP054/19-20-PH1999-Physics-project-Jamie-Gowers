# 19-20-PH1999-Physics-project-Jamie-Gowers
Student ZHAP054 Foundation Individual Scientific Project
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

def findbestfit(inputval):
  dark_mass_in_orbit_array=np.array([])
  for rad in radarray:
    arcval=rad-np.arctan(rad/1.87)
    mass_containd=4*np.pi*inputval*3.4969*arcval
    dark_mass_in_orbit_array=np.append(dark_mass_in_orbit_array,mass_containd)
  totalmassarray=np.array([])
  index=0
  for mass in massarray:
    totalmassarray=np.append(totalmassarray,mass+dark_mass_in_orbit_array[index])
    index=index+1
  predvelarray=np.array([])
  index=0
  for rad in radarray:
    val=4.3e-06*totalmassarray[index]
    predvel=(val/rad)**0.5
    predvelarray=np.append(predvelarray,predvel)
    index=index+1
  index=0
  Xsquarray=np.array([])
  for rad in radarray: 
    val=(velarray[index]-predvelarray[index])**2
    Xsquarray=np.append(Xsquarray,val/16.81)
    index=index+1
    best_fit=np.sum(Xsquarray)
  return (best_fit)
chiimon=10000
for valofpo in np.arange(0.8e+08,1.1e+08,0.001e+08):
  newchi=findbestfit(valofpo)
  if newchi<chiimon:
    bestchi=newchi
    bestpo=valofpo
    chiimon=newchi
  if newchi<519.6457 and newchi>517.6457:
    print(valofpo)

dark_mass_in_orbit_array=np.array([])
for rad in radarray:
  arcval=rad-np.arctan(rad/1.87)
  mass_containd=4*np.pi*bestpo*3.4969*arcval
  dark_mass_in_orbit_array=np.append(dark_mass_in_orbit_array,mass_containd)
totalmassarray=np.array([])
index=0
for mass in massarray:
  totalmassarray=np.append(totalmassarray,mass+dark_mass_in_orbit_array[index])
  index=index+1
predvelarray=np.array([])
index=0
for rad in radarray:
  val=4.3e-06*totalmassarray[index]
  predvel=(val/rad)**0.5
  predvelarray=np.append(predvelarray,predvel)
  index=index+1

Radius(kpc)	velocity(km/s)	∆Radius(kpc)	∆v(km/s)	Mass(solar masses)
0.7329905	44.781902	0.05		4.1		1.23E+08
1.1688017	59.18528	0.05		4.1		3.07E+08
1.4849969	70.86315	0.05		4.1		4.97E+08
1.883676	80.01302	0.05		4.1		7.01E+08
2.363244	89.16407	0.05		4.1		1.05E+09
2.7228281	96.17328	0.05		4.1		1.45E+09
3.1221209	104.35038	0.05		4.1		2.00E+09
3.5220268	111.554726	0.05		4.1		2.93E+09
3.9216874	119.14818	0.05		4.1		3.93E+09
4.320857	127.51984	0.05		4.1		5.11E+09
4.6799507	135.30725	0.05		4.1		6.60E+09
5.040639	140.56548	0.05		4.1		8.49E+09
5.482584	145.24123	0.05		4.1		1.17E+10
5.8856797	147.3872	0.05		4.1		1.37E+10
6.288653	149.72774	0.05		4.1		1.55E+10
7.0568533	150.12807	0.05		4.1		1.87E+10
7.9052067	151.69687	0.05		4.1		2.12E+10
8.752579	154.82211	0.05		4.1		2.30E+10
9.478863	157.55647	0.05		4.1		2.43E+10
10.246204	159.31865	0.05		4.1		2.62E+10
11.13488	161.08261	0.05		4.1		2.77E+10
11.901854	163.42845	0.05		4.1		2.90E+10
12.749717	165.77548	0.05		4.1		3.02E+10
13.557871	166.95459	0.05		4.1		3.14E+10
14.287344	164.63058	0.05		4.1		3.20E+10
15.13901	160.94649	0.05		4.1		3.25E+10
15.950232	157.26178	0.05		4.1		3.26E+10
16.758877	157.66269	0.05		4.1		3.29E+10
17.526955	158.25757	0.05		4.1		3.31E+10
18.254711	158.65729	0.05		4.1		3.34E+10
19.10331	159.83700	0.05		4.1		3.42E+10
19.992353	161.0173	0.05		4.1		3.53E+10
20.84181	160.83514	0.05		4.1		3.63E+10
21.530594	158.89964	0.05		4.1		3.69E+10
22.420618	158.52353	0.05		4.1		3.67E+10
23.109035	157.17169	0.05		4.1		3.65E+10
23.998323	157.96289	0.05		4.1		3.68E+10
24.847658	157.97528	0.05		4.1		3.81E+10
25.576273	157.01314	0.05		4.1		3.95E+10
26.386023	155.66307	0.05		4.1		4.08E+10
27.154222	156.06339	0.05		4.1		4.21E+10
27.964094	154.51877	0.05		4.1		4.28E+10
28.813921	153.75296	0.05		4.1		4.34E+10
29.542412	152.98537	0.05		4.1		4.38E+10
30.432314	152.8038	0.05		4.1		4.43E+10
31.200884	152.62045	0.05		4.1		4.44E+10
31.968225	154.38264	0.05		4.1		4.45E+10
32.817436	154.58958	0.05		4.1		4.51E+10
33.626205	154.79594	0.05		4.1		4.56E+10
34.353104	156.55754	0.05		4.1		4.67E+10
35.20207	157.1536	0.05		4.1		4.78E+10
35.93142	155.02414	0.05		4.1		4.86E+10
36.901844	155.4274	0.05		4.1		4.98E+10
