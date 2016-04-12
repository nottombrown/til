# Transpose a Vector

Transposing doesn't work how you'd expect it to on a single vector, do the following:

```python
>>> a = np.arange(4)
>>> a
array([0, 1, 2, 3])
>>> a.T
array([0, 1, 2, 3])
>>> a[np.newaxis, :].T
array([[0],
       [1],
       [2],
       [3]])
```
