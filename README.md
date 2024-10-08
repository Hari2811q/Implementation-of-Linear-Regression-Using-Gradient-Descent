# Implementation-of-Linear-Regression-Using-Gradient-Descent

## AIM:
To write a program to predict the profit of a city using the linear regression model with gradient descent.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1.Import the required library and read the dataframe.
2.Write a function computeCost to generate the cost function.
3.Perform iterations og gradient steps with learning rate.
4.Plot the Cost function using Gradient Descent and generate the required graph.
## Program:
```
/*
Program to implement the linear regression using gradient descent.
Developed by: Hariprasath R
RegisterNumber: 212223040059 
*/
```

```

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
Profit Prediction Graph


![image](https://github.com/user-attachments/assets/1d4473e2-4693-4dcc-a0f7-444d9048a7fc)


Compute Cost Value


![image](https://github.com/user-attachments/assets/670b3d29-a3c3-4f5d-9d3d-c1599285cdaf)


h(x) value


![image](https://github.com/user-attachments/assets/ae85a1e9-2125-4273-a89b-febbb2813e71)


Cost function using Gradient Descent Graph


![image](https://github.com/user-attachments/assets/7c69681e-1e2c-49f7-8f12-236b944f80e6)


Profit Prediction Graph


![image](https://github.com/user-attachments/assets/2b0e41b3-4785-4c12-ae91-553248da6a90)


Profit for the Population 35,000


![image](https://github.com/user-attachments/assets/1c8c77de-88d3-425c-97ee-7dccfd1490cc)


Profit for the Population 70,000


![image](https://github.com/user-attachments/assets/e5bd7198-2588-4c14-a7b1-d617166aaf75)

## Result:
Thus the program to implement the linear regression using gradient descent is written and verified using python programming.
