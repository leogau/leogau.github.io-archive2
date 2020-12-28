# An empty network



```python
weight = 0.1
```

```python
def neural_network(input, weight):
    prediction = input * weight
    return prediction
```

# Inserting one input datapoint

```python
number_of_toes = [8.5, 9.5, 10, 9]
input = number_of_toes[0]
pred = neural_network(input, weight)
print(pred)
```

    0.8500000000000001
    

# An empty network with multiple inputs

```python
weights = [0.1, 0.2, 0]
def neural_network(input, weights):
    pred = w_sum(input, weights)
    return pred
```

# Inserting one input datapoint

```python
toes = [8.5, 9.5, 9.9, 9.0]
wlrec = [0.65, 0.8, 0.8, 0.9]
nfans = [1.2, 1.3, 0.5, 1.0]
```

```python
input = [toes[0], wlrec[0], nfans[0]]
```

```python
pred = neural_network(input, weights)
```

```python
def w_sum(a, b):
    assert(len(a) == len(b))
    output = 0
    for i in range(len(a)):
        output += (a[i] * b[i])
    return output
```

```python
print(pred)
```

    0.9800000000000001
    

```python
def elementwise_multiplication(vec_a, vec_b):
    output = []
    for i in range(len(vec_a)):
        output.append(vec_a[i] * vec_b[i])
    return output
```

```python
def elementwise_addition(vec_a, vec_b):
    output = []
    for i in range(len(vec_a)):
        output.append(vec_a[i] + vec_b[i])
    return output
```

```python
def vector_sum(vec_a):
    output = 0
    for i in range(len(vec_a)):
        output += vec_a[i]
    return output
```

```python
def vector_average(vec_a):
    sum = 0
    for i in range(len(vec_a)):
        sum += vec_a[i]
    return sum / len(vec_a)
```

```python
def dot_product(vec_a, vec_b):
    mul = elementwise_multiplication(vec_a, vec_b)
    return vector_sum(mul)
```

```python
print(dot_product(input, weights))
```

    0.9800000000000001
    

# The Same Thing In NumPy

```python
import numpy as np
```

```python
weights = np.array([0.1, 0.2, 0])
```

```python
def neural_network(input, weights):
    pred = input.dot(weights)
    return pred
```

```python
toes = np.array([8.5, 9.5, 9.9, 9.0])
wlrec = np.array([0.65, 0.8, 0.8, 0.9])
nfans = np.array([1.2, 1.3, 0.5, 1.0])
```

```python
input = np.array([toes[0], wlrec[0], nfans[0]])
```

```python
pred = neural_network(input, weights)
print(pred)
```

    0.9800000000000001
    

# Network With Multiple Outputs

```python
weights = [0.3, 0.2, 0.9]
```

```python
def neural_network(input, weights):
    pred = ele_mul(input, weights)
    return pred
```

```python
def ele_mul(number, vector):
    output = [0, 0, 0]
    assert(len(output) == len(vector))
    for i in range(len(vector)):
        output[i] = number * vector[i]
    return output
```

```python
wlrec = [0.65, 0.8, 0.8, 0.9]
input = wlrec[0]
pred = neural_network(input, weights)
```

```python
print(pred)
```

    [0.195, 0.13, 0.5850000000000001]
    

# Network With Both Multiple Inputs and Multiple Outputs

```python
weights = [[0.1, 0.1, -0.3],
           [0.1, 0.2, 0.0],
           [0.0, 1.3, 0.1]]
```

```python
def neural_network(input, weights):
    pred = vect_mat_mul(input, weights)
    return pred
```

```python
toes = [8.5, 9.5, 9.9, 9.0]
wlrec = [0.65, 0.8, 0.8, 0.9]
nfans = [1.2, 1.3, 0.5, 1.0]
```

```python
input = [toes[0], wlrec[0], nfans[0]]
```

```python
def w_sum(a, b):
    assert(len(a) == len(b))
    output = 0
    for i in range(len(a)):
        output += (a[i] * b[i])
    return output
```

```python
def vect_mat_mul(vect, matrix):
    assert(len(vect) == len(matrix))
    output = [0, 0, 0]
    for i in range(len(vect)):
        output[i] = w_sum(vect, matrix[i])
    return output
```

```python
pred = neural_network(input, weights)
```

```python
print(pred)
```

    [0.555, 0.9800000000000001, 0.9650000000000001]
    
