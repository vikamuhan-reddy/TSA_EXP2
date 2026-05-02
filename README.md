# Ex.No: 02 LINEAR AND POLYNOMIAL TREND ESTIMATION
### Date: 02-05-2026
### Reg no: 212223240181
### Name: Vikamuhnan Reddy
## AIM:
To Implement Linear and Polynomial Trend Estiamtion Using Python.

## ALGORITHM:
Import necessary libraries (NumPy, Matplotlib)

Load the dataset

Calculate the linear trend values using least square method

Calculate the polynomial trend values using least square method

End the program
## PROGRAM:
#### A - LINEAR TREND ESTIMATION
```python
import pandas as pd, numpy as np, matplotlib.pyplot as plt

d = pd.read_csv('/content/AirPassengers.csv', parse_dates=['Month'], index_col='Month')
r = d['#Passengers'].resample('YE').sum().reset_index()
r['Year'] = r['Month'].dt.year

X = r['Year'] - r['Year'].mean()
b, a = np.polyfit(X, r['#Passengers'], 1)

print(f"Linear Equation: y = {a:.2f} + {b:.2f}(Year - {r['Year'].mean():.0f})")

r['Linear Trend'] = a + b * X
r.set_index('Year')[['#Passengers','Linear Trend']].plot(marker='o')

plt.title('Linear Trend')
plt.grid(); plt.show()

```
#### B- POLYNOMIAL TREND ESTIMATION
```python
import pandas as pd, numpy as np, matplotlib.pyplot as plt

d = pd.read_csv('/content/AirPassengers.csv', parse_dates=['Month'], index_col='Month')
r = d['#Passengers'].resample('YE').sum().reset_index()
r['Year'] = r['Month'].dt.year

X = r['Year'] - r['Year'].mean()
c, b, a = np.polyfit(X, r['#Passengers'], 2)

print(f"Polynomial Equation: y = {a:.2f} + {b:.2f}(Year - {r['Year'].mean():.0f}) + {c:.4f}(Year - {r['Year'].mean():.0f})²")

r['Polynomial Trend'] = a + b * X + c * X**2
r.set_index('Year')[['#Passengers','Polynomial Trend']].plot(marker='o')

plt.title('Polynomial Trend (Degree 2)')
plt.grid(); plt.show()
```
## OUTPUT
#### A - LINEAR TREND ESTIMATION
<img width="439" height="368" alt="Screen Shot 2026-05-02 at 08 53 42" src="https://github.com/user-attachments/assets/0b4a5173-77aa-4962-b402-2c7a9b48b45f" />

#### B- POLYNOMIAL TREND ESTIMATION
<img width="519" height="366" alt="Screen Shot 2026-05-02 at 08 54 10" src="https://github.com/user-attachments/assets/60f9bbd9-b441-4680-ada3-d7a7376b5b25" />



## RESULT:
Thus the python program for linear and Polynomial Trend Estiamtion has been executed successfully.
