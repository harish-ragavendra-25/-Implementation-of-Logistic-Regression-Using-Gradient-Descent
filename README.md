# Implementation-of-Logistic-Regression-Using-Gradient-Descent
## AIM:
To write a program to implement the the Logistic Regression Using Gradient Descent.
## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook
## Algorithm
1.Use the standard libraries in python for finding linear regression.
2.Set variables for assigning dataset values.
3.Import linear regression from sklearn.
4.Predict the values of array.
5.Calculate the accuracy, confusion and classification report by importing the required modules from sklearn.
6.Obtain the graph.
## Program:
```
/*
Program to implement the the Logistic Regression Using Gradient Descent.
Developed by: HARISH RAGAVENDRA S
RegisterNumber:  212222230045
*/
```
```
/*
Program to implement the the Logistic Regression Using Gradient Descent.
Developed by: HARISH RAGAVENDRA S
RegisterNumber:  212222230045
import numpy as np
import matplotlib.pyplot as plt
from scipy import optimize

data = np.loadtxt("/content/ex2data2.txt",delimiter = ',')
x= data[:,[0,1]]
y= data[:,2]
print('Array Value of x:')
x[:5]

print('Array Value of y:')
y[:5]

print('Exam 1-Score graph')
plt.figure()
plt.scatter(x[y == 1][:,0],x[y == 1][:,1],label='Admitted')
plt.scatter(x[y == 0][:,0],x[y == 0][:,1],label=' Not Admitted')
plt.xlabel('Exam 1 score')
plt.ylabel('Exam 2 score')
plt.legend()
plt.show()


def sigmoid(z):
  return 1/(1+np.exp(-z))
  
print('Sigmoid function graph: ')
plt.plot()
x_plot = np.linspace(-10,10,100)
plt.plot(x_plot,sigmoid(x_plot))
plt.show()


def costFunction(theta,x,y):
  h = sigmoid(np.dot(x,theta))
  j = -(np.dot(y,np.log(h))+np.dot(1-y,np.log(1-h)))/x.shape[0]
  grad = np.dot(x.T,h-y)/x.shape[0]
  return j,grad


print('X_train_grad_value: ')
x_train = np.hstack((np.ones((x.shape[0],1)),x))
theta = np.array([0,0,0])
j,grad = costFunction(theta,x_train,y)
print(j)
print(grad)


print('y_train_grad_value: ')
x_train=np.hstack((np.ones((x.shape[0],1)),x))
theta=np.array([-24,0.2,0.2])
j,grad=costFunction(theta,x_train,y)
print(j)
print(grad)

def cost(theta,x,y):
  h = sigmoid(np.dot(x,theta))
  j = -(np.dot(y,np.log(h))+np.dot(1-y,np.log(1-h)))/x.shape[0]
  return j


def cost(theta,x,y):
  h = sigmoid(np.dot(x,theta))
  j = -(np.dot(y,np.log(h))+np.dot(1-y,np.log(1-h)))/x.shape[0]
  return j

print('res.x:')
x_train = np.hstack((np.ones((x.shape[0],1)),x))
theta = np.array([0,0,0])
res = optimize.minimize(fun=cost,x0=theta,args=(x_train,y),method='Newton-CG',jac=gradient)
print(res.fun)
print(res.x)


def plotDecisionBoundary(theta,x,y):
  x_min,x_max = x[:,0].min()-1,x[:,0].max()+1
  y_min,y_max = x[:,1].min()-1,x[:,1].max()+1
  xx,yy = np.meshgrid(np.arange(x_min,x_max,0.1),np.arange(y_min,y_max,0.1))
  x_plot = np.c_[xx.ravel(),yy.ravel()]
  x_plot = np.hstack((np.ones((x_plot.shape[0],1)),x_plot))
  y_plot = np.dot(x_plot,theta).reshape(xx.shape)
  plt.figure()
  plt.scatter(x[y == 1][:,0],x[y == 1][:,1],label='Admitted')
  plt.scatter(x[y == 0][:,0],x[y == 0][:,1],label='Not Admitted')
  plt.contour(xx,yy,y_plot,levels=[0])
  plt.xlabel('Exam  1 score')
  plt.ylabel('Exam 2 score')
  plt.legend()
  plt.show()

print('DecisionBoundary-graph for exam score: ')
plotDecisionBoundary(res.x,x,y)

print('Proability value: ')
prob=sigmoid(np.dot(np.array([1,45,85]),res.x))
print(prob)


def predict(theta,x):
  x_train = np.hstack((np.ones((x.shape[0],1)),x))
  prob = sigmoid(np.dot(x_train,theta))
  return (prob >=0.5).astype(int)


print('Prediction value of mean:')
np.mean(predict(res.x,x)==y)
*/
```
## Output:
![Screenshot 2023-11-11 164656](https://github.com/harish-ragavendra-25/-Implementation-of-Logistic-Regression-Using-Gradient-Descent/assets/114852180/f37b7fbd-7298-4660-9050-9aa4480a21b0)
![Screenshot 2023-11-11 164642](https://github.com/harish-ragavendra-25/-Implementation-of-Logistic-Regression-Using-Gradient-Descent/assets/114852180/82e98f39-a51d-46e0-9e3c-d74e8c93e76c)
![Screenshot 2023-11-11 164636](https://github.com/harish-ragavendra-25/-Implementation-of-Logistic-Regression-Using-Gradient-Descent/assets/114852180/11043870-1653-4e86-8ee3-245f177316fc)
![Screenshot 2023-11-11 164628](https://github.com/harish-ragavendra-25/-Implementation-of-Logistic-Regression-Using-Gradient-Descent/assets/114852180/e9d849ca-3d05-4228-a27f-3e734e08bc28)
![Screenshot 2023-11-11 164620](https://github.com/harish-ragavendra-25/-Implementation-of-Logistic-Regression-Using-Gradient-Descent/assets/114852180/b8772c68-4cfb-4789-a065-1e8a264195bf)
![Screenshot 2023-11-11 164611](https://github.com/harish-ragavendra-25/-Implementation-of-Logistic-Regression-Using-Gradient-Descent/assets/114852180/8913dfa4-ea2d-4ee7-8ed1-e044e139dafb)
![Screenshot 2023-11-11 164556](https://github.com/harish-ragavendra-25/-Implementation-of-Logistic-Regression-Using-Gradient-Descent/assets/114852180/c212601c-2512-4354-b63a-883d47c71324)
![Screenshot 2023-11-11 164543](https://github.com/harish-ragavendra-25/-Implementation-of-Logistic-Regression-Using-Gradient-Descent/assets/114852180/47c18228-287a-4ca6-b699-c80abc1f461c)

## Result:
Thus the program to implement the the Logistic Regression Using Gradient Descent is written and verified using python programming
