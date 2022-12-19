import numpy as np
import math
def circonv(x,y):
    g=np.array(x)
    h=np.array(y)
    if g.size != h.size:
        raise Exception("Sequences not of same length")
    N = g.size 
    htr=np.concatenate([[h[0]], h[:0:-1]])
    y=np.zeros(N)
    for n in np.arange(N):
        y[n]=np.sum(g*htr)
        htr=np.roll(htr,1)
    Y=y.tolist()
    return Y
def os(sig,imp):
    M=len(imp)
    N=len(sig)+2*(M-1)
    L=N-M+1
    h=imp+[0]*(L-1)
    x_block=[0]*N
    Y=[]
    i=0
    j=0
    while i<len(sig):
        x_block=x_block[len(x_block)-M+1:]+sig[i:((j+1)*L)]
        i=(j+1)*L
        j=j+1
        if len(x_block)<N:
            x_block=x_block+[0]*(N-len(x_block))
        y_block=circonv(x_block,h)
        Y=Y+y_block[M-1:]
    return Y 
sig1=[3,-1,0,1,3,2,0,1,2,1] #input signal
imp1=[1,1,1] #input impulse
print(os(sig1,imp1))
