# TIL: Today I Learned 💡

This is a living collection of new findings, coding tips and gotchas that I found in my everyday work.

## Data Science

#### Create train/split datasets with a mask

This code splits the dataset in 80% for training and 20% for testing:

```python
mask = np.random.rand(len(df)) < 0.8
train = data_set[mask]
test = data_set[~mask]
```

## Python

#### Reverse a string

When you pass step size `-1` it reverses the string:

```python
mystring[::-1]
```
