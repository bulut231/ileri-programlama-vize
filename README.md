# ileri-programlama-vize
vize ödevi (eğik atış kodlama)
import math
import random as rnd
import matplotlib.pyplot as plt

topkonumx = [0]
topkonumy = [7]
g=10
hizmax=1800
hizmin=330  




hedefbaslangic = 20000+(200*rnd.randint(-10,10))
hedefbitis = hedefbaslangic+1000+100*rnd.randint(-2, 2)
#hedef = hedefbaslangic + (hedefbitis-hedefbaslangic)

i=0
while 1==1: 
 
    baslangichiz = (hizmax+hizmin)/2
    yatayhiz = baslangichiz*math.cos(math.pi/6)
    duseyhiz = baslangichiz*math.sin(math.pi/6)
    ucusuresi = (2*duseyhiz)/g
    menzil = yatayhiz*ucusuresi
    #hmax = (duseyhiz**2)/2*g
    
   
   
    if menzil>hedefbaslangic and menzil<hedefbitis:
        print("hedefi vurdun !")
        plt.figure
        plt.xlabel("mesafe(menzil)")
        plt.axis([0,25000,0,5000])
        plt.ylabel("yukseklik (metre)")
        
        for c in range(round(ucusuresi)): 
            atis=yatayhiz*c
            yukarimenzil=duseyhiz*c-g/2*c**2
            topkonumx.append(atis)
            topkonumy.append(yukarimenzil)
            plt.plot(topkonumx,topkonumy)
        i+=1
        plt.title("deneme sayisi= %d"%(i))
        break
    elif menzil<hedefbaslangic:
        print("onune dustu")
        hizmin=baslangichiz
        i+=1
    else:
        print("uzagina dustu")
        hizmax=baslangichiz
        i+=1
print(i,". seferde vuruş gerceklesmistir hedefi vurmak icin gereken hiz",baslangichiz,"tir")

       
