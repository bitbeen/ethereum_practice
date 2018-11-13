## ABI

```go
type ABI struct {

    Constructor Method
    Methods     map[string]Method
    Events      map[string]Event
}
```

> ABI代表一个合约ABI对象

## Method

```go
type Method struct {
    Name    string
    Const   bool
    Inputs  Arguments //代表传递给该方法的参数
    Outputs Arguments //方法返回的
}
```

> Method
>
> * name:方法名称
> * const:是否为常量
>   ```json
>   {
>   "constant": true,
>   "inputs": [
>   {
>      "name": "a",
>      "type": "string"
>   }
>   ],
>   "name": "search",
>   "outputs": [],
>   "payable": false,
>   "stateMutability": "view", 如果此处为非view,那constant为false
>   "type": "function"
>   },
>   ```
> * Inputs:方法的输入参数
> * Outputs:方法返回值参数
>   ```json
>   {
>   "constant": false,
>   "inputs": [
>   {
>      "name": "a", //参数名字
>      "type": "uint256[]" //参数类型
>   }
>   ],
>   "name": "say",
>   "outputs": [
>   {
>      "name": "",//可以直接将返回值赋值给某个参数
>      "type": "uint256" //返回值类型
>   }
>   ],
>   "payable": false,
>   "stateMutability": "nonpayable",
>   "type": "function"
>   }
>   ```

## Event

```go
type Event struct {
    Name      string
    Anonymous bool
    Inputs    Arguments
}
```
>event
```json
    {
            "anonymous": false,
            "inputs": [
                {
                    "indexed": true,
                    "name": "a",
                    "type": "uint256"
                },
                {
                    "indexed": false,
                    "name": "b",
                    "type": "uint256"
                }
            ],
            "name": "go",
            "type": "event"
      }
```

## Argument

```go
type Argument struct {
    Name    string
    Type    Type
    Indexed bool // indexed is only used by events
}

type Arguments []Argument
```

> Argument 表示合约方法中的参数名字和参数的具体类型
>
> ```json
> {
>     "name": "a",
>     "type": "string"
> }
> ```
>
> ```json
> {
> "indexed": true,
> "name": "a",
> "type": "uint256"
> },
> ```



