# mathtest1
#coding=utf-8
import math
funCMemo=[128]
funCMemoFlag=[128]
count=0
def funC(k):
    if k!=0:
        sum=0
        if funCMemoFlag[k]==1:
            return funCMemo[k]
        count=count+1
        for i in range(k):
            sum+=(funC(i)*funC(k-1-i))/((i+1)*(2*i+1))
        funCMemoFlag[k]=1
        funCMemo[k]=sum
        return sum
    else:
        return 1.0

def funE(n,k):
    sum=0.0
    for i in range(k):
        sum+=funC(i)*(math.pow((math.sqrt(math.pi)*n/2),(2*i+1)))/(2*i+1)
    return sum

erf=0
for i in range(128):
    funCMemo[i]=0
    funCMemoFlag[i]=0
n_num=raw_input("input n:\n") #输入n
k_num=raw_input("input k:\n") #输入k
erf=funE(n_num,k_num)
print("erf={0}\n").format(erf)
print("count={0}\n").format(count)




