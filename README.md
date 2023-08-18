# simple-tlv
`简化版`tlv结构的编码解码功能，提供简单的TLV编解码，满足自己传输数据时需要使用TLV编码的需求

# simple-tlv

```go
import tlv "github.com/yzw-trt/simple-tlv"
```


## 操作接口
```go
  type Container interface {
	GetByte(key uint8) (b byte, exists bool)
	GetBytes(key uint8) (b []byte, exists bool)

	SetByte(key uint8, value byte)
	SetBytes(key uint8, value []byte)

	Remove(key uint8)

	Bytes() []byte

	NoEntries() int
}
```

## 生成TLV
```go
    //创建tlv对象
    c := tlv.NewContainer()
    //添加一个tlv成员
    c.SetBytes(TimestampKey, timeBytes)
    //将tlv对象转换为字节流
    packet := c.Bytes()
```  
## 解析TLV
```go
    //将字节流转换为tlv对象
    c, err := tlv.UnmarshalTLVContainer(bodyBytes) 
    //获取一个成员
    timeBytes ,ok := c.GetBytes(TimestampKey)
```
