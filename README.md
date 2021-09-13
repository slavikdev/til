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

and you can reverse every word in a string, maintaining the word order:

```python
' '.join(s[::-1] for s in strs.split())
```

#### Create array/matrix with prefilled values

Creates 3x3 matrix where all elements equal to -1:

```python
[[-1]*3]*3
```

```bash
[[-1, -1, -1], [-1, -1, -1], [-1, -1, -1]]
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

## TypeScript

#### Type casting to an object with methods

If you have a class with attributes and methods and you want to type cast a JSON object to an instance of the class, then `const obj = json as MyClass` will only assign attributes, i.e. later calling something like `obj.myMethod()` will cause a no method error. To create a proper object you need to use `Object.assign`:

```typescript
const obj = Object.assign(new MyClass(), json as MyClass)
obj.myMethod() // this will work now
```

