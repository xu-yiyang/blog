# 面试
## mobx和redux区别
  1.redux状态是只读的，不能直接修改它；mobx状态可变的，可以直接修改  
  2.mobx相对来说状态管理更加简单，学习成本低  
  3.mobx面向对象编程，使用observer绑定状态，观察这个状态，一旦变更就自动更新；redux函数式编程，reducer就是一个存函数，接受输出然后输出新状态，每次都是返回一个新的数据
## vue和react的区别
  vue是mvvm，双向绑定，他监听的是一个数据变化然后去改变ui；
  react是单向数据流，讲求一个函数式编程，一个函数代表一个ui组件，数据不可变。状态变更时，记录新树和旧树的差异，最后把差异更新到真正的dom中
## TCP三次握手
  1、客户端发送syn包到服务器，等待服务器确认接收。2、服务器确认接收syn包并确认客户的syn，并发送回来一个syn+ack的包给客户端。3、客户端确认接收服务器的syn+ack包，并向服务器发送确认包ack，二者相互建立联系后，完成tcp三次握手。四次握手就是中间多了一层 等待服务器再一次响应回复相关数据的过程
## 链判断运算符(Optional Chaining)
  ES2020链判断运算符，使用a?.c?.b代替a && a.c && a.c.b
## 构造函数包含return
  ```
  function A(){
    this.x=3
    return 'ok'; //如果返回基本数据类型，仍然会返回新对象实列
  }
  var b = new A()
  b.x; //3
  ----------------
  function A(){
    this.x=3
    return {x: 4}; //如果返回引用类型（对象、数组、函数），返回值就是return的值
  }
  var b = new A()
  b.x; //4
  ```
## js实现深拷贝的几种方法
  1.使用es6
  ```
  var a=[1,2,3]
  var b=[...a];
  ```
  2.使用concat()方法
  ```
  var a=[1,2,3]
  var c=[];
  var b=c.concat(a);
  ```
  3.使用递归
  ```
  function deep(obj) {
    //判断拷贝的要进行深拷贝的是数组还是对象，是数组的话进行数组拷贝，对象的话进行对象拷贝
    var objClone = Array.isArray(obj) ? [] : {};
    //进行深拷贝的不能为空，并且是对象或者是
    if (obj && typeof obj === "object") {
      for (key in obj) {
        if (obj.hasOwnProperty(key)) {//只遍历自身属性
          if (obj[key] && typeof obj[key] === "object") {
            objClone[key] = deep(obj[key]);
          } else {
            objClone[key] = obj[key];
          }
        }
      }
    }
    return objClone;
  }
  ```
<!-- <my-btn>11</my-brn> -->
## 常用状态码
  + 1xx（请求处理中）
  + 2xx（请求处理完毕）
      * 200（请求成功）
  + 3xx（重定向）
      * 301（永久重定向）
      * 302（临时重定向）
      * 304（请求资源没有变化，使用缓存）
  + 4xx（客户端请求错误）
      * 400（请求参数错误）
      * 401（没有权限访问，一般表示未登陆）
      * 403（禁止访问，一般表示权限不够，需要更高的权限）
      * 404（请求的资源不存在）
  + 5xx（服务器端错误）
      * 500（服务器内部出错）
      * 503（服务器在维护）
## Eventloop
  在node中,其中有3个阶段,他们的执行顺序：  
  times -> poll（停留，一直等到有任务才往下一个阶段） -> check  
  对应api:  
  times -> setTimeout/setInterval  
  check -> setImmediate  
  当前阶段后面执行api：  
  nextTick -> 如：times(setTimeout)中写nextTick,执行顺序就是time -> nextTick -> poll  
  promise.then(fn) -> then后立即把fn放入当前队列后面  
  await同promise，resolve后放入队列  
    
  在chrome中，2个阶段：  
  宏任务（一会执行）MacroTask  
  微任务（马上执行）MicroTask  
  对应api:  
  宏任务 -> setTimeout/setInterval  
  微任务 -> promise.then(fn)（then后立即把fn放入当前队列后面）/ await转promise  
  注: new Promise(fn),这个fn是立即执行的，不放进任何阶段  

## react diff 原理：(就是一个函数)
  使用tree diff将新旧两棵树逐层对比，找出那些节点需要更新，如果节点是组件使用component diff，如果是标签使用element diff  
  component diff：如果不同组件，直接删除替换，相同只更新属性   
  element diff：不同标签直接删除替换，相同只更新属性  
  key作用，来标识一个组件，来判断是选择删除还是移动操作，比如，a-b组件，当只是位置换成b-a,如果有添加key值，那只进行位置交换  