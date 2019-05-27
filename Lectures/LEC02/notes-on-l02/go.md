# 基本类型
- 声明变量：`var`
- 声明常量：`const`

## 类型列表
- `bool`
- `string`
- `int` `int8` `int16` `int32` `int64`
- `uint` `uint8` `uint16` `uint32` `uint64`
- `uintptr`
- `byte`：`uint8` 别名
- `rune`：`int32` 别名，表示一个unicode码点
- `float32` `float64`
- `complex64` `complex128`

## 说明
- `int` `uint` `uintptr` 宽度在32位系统上是32位，在64位系统上是64位
- 零值
  - 数值类型：0
  - 布尔类型：false
  - 字符串：""

# 控制流程
## 循环
go 只有一种循环结构：`for` 循环
```go
sum := 0
for i := 0; i < 10; i++ {
    sum += i
}   
for ; sum < 1000; {
    sum += sum
}
for sum < 1000 {
    sum += sum
}
for {
}
```
初始化语句中声明的变量作用域只存在 `for` 中

## 条件
```go
if x < 0 {
    return sqrt(-x) + "i"
}
if v := math.Pow(x, n); v < lim {
    return v
}
```
初始化语句中声明的变量作用域只存在 `if` 中

```go
switch os := runtime.GOOS; os {
case "darwin":
    fmt.Println("OS X.")
case "linux":
    fmt.Println("Linux.")
default:
    fmt.Printf("%s.\n", os)
}
```

## 推迟
`defer`