# 获取 proxy 对象的值

## 解值法
```javascript
  var data = {
  username: 'frank',
  age: 20
}

var proxy = new Proxy(data,{
  set: function(obj, prop, value){
    obj[prop] = value
    $('input[name='+prop+']').val(value)
  }
})

$('input[name=username]').val(data.username).on('input',function(){
  data.username = parseInt(this.value,10)
})

$('input[name=age]').val(data.age).on('input',function(){
  data.age = parseInt(this.value,10)
})


$('button').on('click', function(){
  proxy.age += 1
})
  JSON.parse(JSON.stringify(proxy))
  ```