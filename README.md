# TIL: Today I Learned 💡

This is a living collection of new findings, coding tips and gotchas that I found in my everyday work.

## Data Science

#### Create train/split datasets with a mask

```python
mask = np.random.rand(len(df)) < 0.8
train = data_set[mask]
test = data_set[~mask]
```
