# tips

- 不要用 serde_jso n的 json! 。用了相当于对一个动态类型的Object进行json格式化，返回数据量大的时候，json格式化直接拖垮系统