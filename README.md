print("Author Name-Baljeet singh")
import numpy as np   # module numpy
import matplotlib.pyplot as plt   #module for plots
from astropy.table import Table #table module
X, Y=np.loadtxt('Data.txt', delimiter=',', unpack=True) # to load the data file od students study details

X=np.sort(X) #To sort the data in same manner
Y=np.sort(Y) #to sort the data in same manner

N=len(X)  #the total no of data

a=((N*sum(X*Y))- (sum(X)*sum(Y)))/((N*sum(X*X))-(sum(X))**2)  #slope coefficient
print("slope coefficient=",a)
b=((sum(X*X)*sum(Y)) - (sum(X)*sum(X*Y)))/((N*sum(X*X))-(sum(X))**2) #intercept coefficient
print("intercept coefficient=",b)

Y_=a*X+b
t=Table([X,Y,Y_], names=('x', 'y', 'y_'))#presenting in tabular form
print(t)
plt.title(" % graph of an student based on the no. of study hours.")
plt.xlabel('Study time(in Hrs)')
plt.ylabel("Percentage Secured %")
plt.scatter(X,Y,color='grey',label='given data')
plt.plot(X,Y_,color='pink',label='cal. data')
plt.grid()
plt.legend()
plt.show()
X__=float(input('Enter the time upto student study:'))
Y__=a*X__+b


print("Predicted score if a student studies for ", 'St ',' hrs/ day-',Y__,"%")
