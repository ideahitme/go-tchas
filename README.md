# go-tchas
Some golang related gotchas

### List of gotchas

#### Avoid `fmt.scanf`: 

Reading 100000 space separated integers from stdin

`1` is a lot slower than `2`

1. 

```
  n := 100000
  for i := 0; i < n; i++ {
    var n int
    fmt.Scanf(&n)
  }

```

2. 

```
  n := 100000
  scanner := bufio.NewScanner(os.Stdin)
	scanner.Split(bufio.ScanWords)
  for i :=0; i < n; i++ {
    scanner.Scan()
    var n int
    n, _ = strconv.Atoi(scanner.Text())
  }

```