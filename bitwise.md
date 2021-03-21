# Bitwise operator notes
Here are some snippets on Bitwise operations

### Get the ith bit from an specific number

```go
x&(1<<i)
```

## Set the ith bit on an specific number

```go
x|(1<<i)
```

# Clear the ith bit on an specific number

```go
x&(^(1<<i))
```

# Checks if only one specific position bit is set

```go
x&(x-1) == 0
```
