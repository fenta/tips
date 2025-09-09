### 显示全部字符串内容
```
set print element 0
```

### 线程锁
```
set scheduler-locking on
```

### 美化打印
```
info pretty-printer
```

### 设置信号中断行为
```
handle SIGFPE stop nopass
```


### 打印std::string 内容指针和长度
```
p $msg._M_dataplus._M_p
p *(uint64_t*)($msg._M_dataplus._M_p - 24)
```


### 导出内存内容至文件
```
dump binary memory ./file start stop
```
