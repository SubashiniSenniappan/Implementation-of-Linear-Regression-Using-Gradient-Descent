# Implementation-of-Linear-Regression-Using-Gradient-Descent

## AIM:
To write a program to predict the profit of a city using the linear regression model with gradient descent.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1. Start the program.
2.import numpy as np.
3.Give the header to the data.
4.Find the profit of population.
5.Plot the required graph for both for Gradient Descent Graph and Prediction Graph. 6.End the program.


## Program:
```
/*
Program to implement the linear regression using gradient descent.
Developed by: Subashini.S
RegisterNumber:  212222240106
*/
import numpy as np
import matplotlib.pyplot as plt
import pandas as pd

data=pd.read_csv("ex1.txt",header =None)

plt.scatter(data[0],data[1])
plt.xticks(np.arange(5,30,step=5))
plt.yticks(np.arange(-5,30,step=5))
plt.xlabel("Population of City (10,000s)")
plt.ylabel("Profit ($10,000")
plt.title("Profit Prediction")

def computeCost(X,y,theta):

  m=len(y)
  h=X.dot(theta)
  square_err=(h-y)**2
  j=1/(2*m)* np.sum(square_err)
  return j

data_n=data.values
m=data_n[:,0].size
X=np.append(np.ones((m,1)),data_n[:,0].reshape(m,1),axis=1)
y=data_n[:,1].reshape(m,1)
theta=np.zeros((2,1))

computeCost(X,y,theta)

def gradientDescent(X,y,theta,alpha,num_iters):
  m=len(y)
  J_history=[]

  for i in range (num_iters):
    predictions=X.dot(theta)
    error = np.dot(X.transpose(),(predictions-y))
    descent=alpha*1/m * error
    theta-=descent
    J_history.append(computeCost(X,y,theta))

  return theta,J_history  

theta,J_history = gradientDescent(X,y,theta,0.01,1500)
print("h(x) ="+str(round(theta[0,0],2))+" + "+str(round(theta[1,0],2))+"x1" )

plt.plot(J_history)
plt.xlabel("Iteration")
plt.ylabel("$J(\Theta)$")
plt.title("Cost function using Grading Descent")

plt.scatter(data[0],data[1])
x_value=[x for x in range(25)]
y_value=[y*theta[1]+theta[0] for y in x_value]
plt.plot(x_value,y_value,color="r")
plt.xticks(np.arange(5,30,step=5))
plt.yticks(np.arange(-5,30,step=5))
plt.xlabel("Population of City(10,000s)")
plt.ylabel("Profit ($10,000")
plt.title("Profit Prediction")

def predict (x,theta):
  predictions=np.dot(theta.transpose(),x)
  return predictions[0]

predict1=predict(np.array([1,3.5]),theta)*10000
print("For population = 35,000,we predict a profit a profit of $"+str(round(predict1,0)))

predict2=predict(np.array([1,7]),theta)*10000
print("For population =70,000,we predict a profit a profit of $"+str(round(predict2,0)))
```

## Output:

### COMPUTE COST VALUE
![image](https://github.com/SubashiniSenniappan/Implementation-of-Linear-Regression-Using-Gradient-Descent/assets/119404951/2ffae377-fbdc-42a3-a7e8-9b3043ee2485)
## H(X) VALUE
![image](https://github.com/SubashiniSenniappan/Implementation-of-Linear-Regression-Using-Gradient-Descent/assets/119404951/5b26aefb-07ae-4837-9e2a-2eb5dff7b2cc)
## COST FUNCTION USING GRADIENT DESCENT GRAPH
![image](https://github.com/SubashiniSenniappan/Implementation-of-Linear-Regression-Using-Gradient-Descent/assets/119404951/42eb96c4-12be-48b7-ae6b-b273c0e19501)
## PROFIT PREDICTION GRAPH
![image](https://github.com/SubashiniSenniappan/Implementation-of-Linear-Regression-Using-Gradient-Descent/assets/119404951/fedde34b-82c4-4f6f-9fa8-3d62cfd2cac7)
## PROFIT FOR THE POPULATION 35,000
![image](https://github.com/SubashiniSenniappan/Implementation-of-Linear-Regression-Using-Gradient-Descent/assets/119404951/2a4d6782-6c39-420c-8089-6b9204e20909)
## PROFIT FOR THE POPULATION 70,000
![image](https://github.com/SubashiniSenniappan/Implementation-of-Linear-Regression-Using-Gradient-Descent/assets/119404951/116e4dce-3ee7-4efc-9a23-4b68d77909e4)






## Result:
Thus the program to implement the linear regression using gradient descent is written and verified using python programming.
