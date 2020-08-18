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

## Golang

#### defer call order

Since I normally use only one `defer` statement, I never thought of the execution order. Actually it’s LIFO:

```go
defer print(2)
defer print(1)
```

So that will actually be printed as `12`, even though the `2` statement is first. More practical case, if you want to close and then remove a file:
```go
defer os.Remove(f.Name())
defer f.Close()
```

## C#

#### Convert object to a template method type

If you want to convert `object` value to a type, specified in a template method, there’s a way to do it without `if-s` and `case-es`:

```csharp
private T GetValue<T>(object objVal)
{
   var converter = TypeDescriptor.GetConverter(typeof(T));
   if (converter == null)
   {
      return default(T);
   }
   return (T)converter.ConvertFrom(objVal);
}
```
