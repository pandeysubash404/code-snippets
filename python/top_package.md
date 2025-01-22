# Python Top 18 Packages Program Snippets

This document contains small program snippets of the most popular Python packages. 

## 1. NumPy: Array Operations
Library for numerical computing, providing support for arrays, matrices, and mathematical functions.

```python
import numpy as np

def numpy_test():
    arr = np.array([1, 2, 3, 4, 5])
    print("Array:", arr)
    print("Sum of array:", np.sum(arr))
    print("Mean of array:", np.mean(arr))

numpy_test()
```
Expected Output:
```text
Array: [1 2 3 4 5]
Sum of array: 15
Mean of array: 3.0
```

## 2. Pandas: DataFrame Operations
Data manipulation and analysis library, offering data structures like DataFrames for handling structured data.

```python
import pandas as pd

def pandas_test():
    data = {'Name': ['Ram', 'Hari', 'Shyam'], 'Age': [25, 30, 35]}
    df = pd.DataFrame(data)
    print("DataFrame:")
    print(df)

pandas_test()
```
Expected Output:
```text
DataFrame:
    Name  Age
0    Ram   25
1   Hari   30
2  Shyam   35
```

## 3. Matplotlib: Plotting
Plotting library for creating static, animated, and interactive visualizations in Python.

```python
import matplotlib.pyplot as plt

def matplotlib_test():
    x = [1, 2, 3, 4, 5]
    y = [1, 4, 9, 16, 25]
    plt.plot(x, y)
    plt.title("Simple Plot")
    plt.xlabel("X-axis")
    plt.ylabel("Y-axis")
    plt.show()

matplotlib_test()
```

## 4. Pytest: Unit Test Example
Framework that makes building simple and scalable test cases easy, with rich features and support for fixtures.

```python
def test_addition():
    assert 2 + 2 == 4
    print("Addition test passed.")

def test_subtraction():
    assert 5 - 3 == 2
    print("Subtraction test passed.")

test_addition()
test_subtraction()
```
Expected Output:
```text
Addition test passed.
Subtraction test passed.
```

## 5. SymPy: Symbolic Math
Symbolic mathematics library that allows for algebraic manipulations, calculus, and solving equations.

```python
import sympy as sp

def sympy_test():
    x = sp.symbols('x')
    expr = sp.sin(x)**2 + sp.cos(x)**2 
    simplified_expr = sp.simplify(expr)
    print("Simplified Expression:", simplified_expr)

sympy_test()
```
Expected Output:
```text
Simplified Expression: 1
```

## 6. SciPy: Optimization Example
Library for scientific and technical computing, offering modules for optimization, integration, and signal processing.

```python
from scipy.optimize import minimize

def scipy_test():
    def objective(x):
        return x**2

    result = minimize(objective, 2)
    print("Optimization result:", result)

scipy_test()
```
Expected Output:
```text
Optimization result:   message: Optimization terminated successfully.
  success: True
   status: 0
      fun: 3.5662963072207506e-16
        x: [-1.888e-08]
      nit: 2
      jac: [-2.287e-08]
 hess_inv: [[ 5.000e-01]]
     nfev: 6
     njev: 3
```

## 7. Scikit-learn: Machine Learning Example
Machine learning library that provides simple and efficient tools for data mining and data analysis.

```python
from sklearn.linear_model import LinearRegression
import numpy as np

def sklearn_test():
    X = np.array([[1], [2], [3], [4], [5]])
    y = np.array([1, 2, 3, 4, 5])

    model = LinearRegression()
    model.fit(X, y)
    print("Coefficient:", model.coef_)
    print("Intercept:", model.intercept_)

sklearn_test()
```
Expected Output:
```text
Coefficient: [1.]
Intercept: -8.881784197001252e-16
```

## 8. Requests: HTTP Request Example
Simple HTTP library for sending HTTP requests, handling responses, and managing sessions.

```python
import requests

def requests_test():
    response = requests.get('https://jsonplaceholder.typicode.com/todos/1')
    print("Response:", response.json())

requests_test()
```
Expected Output:
```text
Response: {'userId': 1, 'id': 1, 'title': 'delectus aut autem', 'completed': False}
```

## 9. Astropy: Astrophysics Calculation
Package for astronomy and astrophysics, providing functionality for coordinate transformations and other astronomical calculations.

```python
from astropy import units as u
from astropy.constants import c

def astropy_test():
    distance = 100 * u.pc
    time = distance / c
    print("Time for light to travel 100 parsecs:", time)

astropy_test()
```
Expected Output:
```text
Time for light to travel 100 parsecs: 3.3356409519815204e-07 pc s / m
```

## 10. Atomicwrites: File Write Example
Provides atomic file writes to ensure file integrity during concurrent writes.

```python
from atomicwrites import atomic_write

def atomicwrites_test():
    with atomic_write('test.txt', mode='w') as f:
        f.write("This is a test.")
    print("File 'test.txt' has been written successfully.")

atomicwrites_test()

```
Expected Output:
```text
File 'test.txt' has been written successfully.
```

## 11. Attrs: Data Class Example
Creating classes without writing boilerplate code, allowing for easier definition of classes with attributes.

```python
import attr

@attr.s
class Person:
    name = attr.ib()
    age = attr.ib()

def attrs_test():
    p = Person(name="Ram", age=25)
    print("Person:", p)

attrs_test()
```
Expected Output:
```text
Person: Person(name='Ram', age=25)
```

## 12. Autograd: Automatic Differentiation
Automatic differentiation, enabling gradient-based optimization and machine learning.

```python
import autograd.numpy as np
from autograd import grad

def autograd_test():
    def func(x):
        return x**2 + 2*x

    gradient = grad(func)
    print("Gradient at x=3:", gradient(3))

autograd_test()
```
Expected Output:
```text
Gradient at x=3: 8.0
```

## 13. BeautifulSoup4: HTML Parsing
Parsing HTML and XML documents and extracting data from them.

```python
from bs4 import BeautifulSoup

def bs4_test():
    html = "<html><head><title>Test Page</title></head><body><p>Welcome!</p></body></html>"
    soup = BeautifulSoup(html, 'html.parser')
    print("Title:", soup.title.string)
    print("Body:", soup.body.string)

bs4_test()
```
Expected Output:
```text
Title: Test Page
Body: Welcome!
```

## 14. Biopython: DNA Sequence Example
Collection of tools for bioinformatics, offering functionality for sequence analysis and working with biological data.

```python
from Bio.Seq import Seq

def biopython_test():
    seq = Seq("AGTACACTGGT")
    print("Complement:", seq.complement())
    print("Reverse Complement:", seq.reverse_complement())

biopython_test()
```
Expected Output:
```text
Complement: TCATGTGACC
Reverse Complement: ACCAGTGTACT
```

## 15. Bitarray: Bit Manipulation
Efficiently creating and manipulating bit arrays in Python.

```python
from bitarray import bitarray

def bitarray_test():
    arr = bitarray('10101')
    print("Bitarray:", arr)
    arr.setall(False)
    print("After reset:", arr)

bitarray_test()
```
Expected Output:
```text
Bitarray: bitarray('10101')
After reset: bitarray('00000')
```

## 16. Bleach: HTML Sanitization
Sanitizing HTML, removing potentially dangerous content like scripts or styles.

```python
import bleach

def bleach_test():
    html = "<script>alert('danger');</script><b>Bold Text</b>"
    safe_html = bleach.clean(html)
    print("Safe HTML:", safe_html)

bleach_test()
```
Expected Output:
```text
Safe HTML: &lt;script&gt;alert('danger');&lt;/script&gt;<b>Bold Text</b>
```

## 17. Boost-histogram: Histogram Operations
High-performance, multi-dimensional histogram library designed for large datasets.

```python
import boost_histogram as bh
import numpy as np

def boost_histogram_test():
    data = np.random.randn(1000)
    hist = bh.Histogram(bh.axis.Regular(10, -3, 3))
    hist.fill(data)
    print("Histogram:", hist)

boost_histogram_test()
```
Expected Output:
```text
Histogram:                  ┌───────────────────────────────────────────────────────────┐
[-inf,   -3) 3   │▊                                                          │
[  -3, -2.4) 8   │█▉                                                         │
[-2.4, -1.8) 29  │███████                                                    │
[-1.8, -1.2) 74  │█████████████████▉                                         │
[-1.2, -0.6) 152 │████████████████████████████████████▊                      │
[-0.6,    0) 218 │████████████████████████████████████████████████████▋      │
[   0,  0.6) 240 │██████████████████████████████████████████████████████████ │
[ 0.6,  1.2) 161 │██████████████████████████████████████▉                    │
[ 1.2,  1.8) 71  │█████████████████▏                                         │
[ 1.8,  2.4) 40  │█████████▋                                                 │
[ 2.4,    3) 4   │█                                                          │
[   3,  inf) 0   │                                                           │
                 └───────────────────────────────────────────────────────────
```

## 18. Brotli: Compression Example
Compression library for the Brotli algorithm, used for data compression and decompression.

```python
import brotli

def brotli_test():
    data = b"Hello, world!"
    compressed = brotli.compress(data)
    decompressed = brotli.decompress(compressed)
    print("Decompressed data:", decompressed)

brotli_test()
```
Expected Output:
```text
Decompressed data: b'Hello, world!'
```