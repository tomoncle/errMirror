# python

### Can't pickle <type 'cStringIO.StringO'>: attribute lookup cStringIO.StringO failed 
原因: pickle不能序列化非纯python语言编写的对象,如request对象,引用了cStringIO这个非python库,就会报以上异常.去掉这个参数,或者对象即可
