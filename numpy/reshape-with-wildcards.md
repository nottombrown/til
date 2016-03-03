# Reshape with wildcards

Sometimes you don't want to have to explicitly calculate the dimensions of an array that you're transforming

```python
array = np.zeros((10,20,30))
print(array.shape) # (10, 20, 30)

reshaped = array.reshape((10,-1))

print(reshaped.shape) # (10, 600)
```
