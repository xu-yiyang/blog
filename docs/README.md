# js，css小效果集合

  ## 浏览器数据库存储
  参考：http://www.cnblogs.com/xiaowei0705/archive/2011/04/19/2021372.html  
  存储：sessionStorage.setItem('变量名','值');  
  读取：var a=sessionStorage.getItem('变量名')  

  ## json格式转换
  JSON.stringify() //数据转字符串  
  JSON.parse() //字符串转对象数组  

  ## 替换手机号中间4位为*号
  dataSelector.mobile.replace(/(\d{3})\d{4}(\d{4})/, '$1****$2')  

  ## 鼠标移入移出，如果标签中有子元素不会重复触发
  onMouseEnter   onMouseLeave

  ## 鼠标移入移出，如果标签中有子元素会重复触发
  onmouseover   onmouseout

  ## 文字溢出隐藏省略号
  overflow: hidden;  
  text-overflow: ellipsis;  
  white-space: nowrap;  
  ## 多行文字溢出隐藏省略号
  display: -webkit-box;  
  -webkit-box-orient: vertical;  
  -webkit-line-clamp: 2;  
  overflow: hidden;  
  height: 34px;  
  overflow: hidden;

  ## 实现0.5边框宽度
  <http://www.cnblogs.com/PeunZhang/p/4709822.html>

  ## 模块两端对齐
  <http://www.cnblogs.com/PeunZhang/p/3289493.html>

  ## 使页面元素变为可编辑
  ```
  document.designMode="on";
  <p contenteditable="true">是一个帅哥</p><p contenteditable="true">是一个帅哥</p>
  ```

  ## JS 获取当天零点时间戳
  ```
  //当天0点时间戳
  new Date(new Date().toLocaleDateString()).getTime()
  // 当天23:59:59
  new Date(new Date(new Date().toLocaleDateString()).getTime() + 24 * 60 * 60 * 1000 - 1)
  ``` 

  ## 延迟几秒自动跳转到该页面
  window.setTimeout("window.location='index.shtml'",5000);
  

  ## 单选多选点击css事件
  input[type="checkbox"]:checked{}

  ## 判断多选是否选中
  $(this).is(':checked')==true

  ## 判断元素是否隐藏
  if(!$(".dialog-overlay2").is(":hidden"));

  ## 多选框全选
  ```
  $(".j-check-all").click( 
      function(){ 
        if(this.checked){ 
        $("input[name='checkname']").each(function(){this.checked=true;}); 
        }else{ 
        $("input[name='checkname']").each(function(){this.checked=false;}); 
        } 
      } 
  );
  ```

  ## css使用after获取元素属性
  ```
  <h2 data-text="天赐美妞">天赐美妞</h2>
  .text-gradient[data-text]::after {  
    content: attr(data-text);  
  }
  ```

  ## ios弹性滚动
  -webkit-overflow-scrolling: touch;
 ## 实现在一个页面展示多个swiper轮播图的功能
  ```
  $(".swiper-container").each(function(){
    $(this).swiper({
      loop: true,
      initialSlide :0,
      pagination:$('.swiper-pagination',this),
      nextButton: $('.arrow-right',this),
      prevButton:$('.arrow-left',this)
    });
  });
  ```
  <http://blog.csdn.net/amyliyanice/article/details/59483499>

  ## 雪碧图移动端背景图定位公式
  .box_left{ left:0px; background-position:0px 59.1729%;/*背景定位值是：背景图标所在图的位置/(背景图片高度-容器高度)*/ }

  ## 百分比宽度构造正方形
  width: 13%; height: 0px; padding-bottom: 13%; 或 width: 8vw; height: 8vw; 

  ## 发送qq网站出现图片介绍
  ```
  <div style='margin:0 auto;width:0px;height:0px;overflow:hidden;'>     
    <img src="images/UI主图.jpg" width='800' height="800">
  </div>
  ```

  ## 只能输入数字
  ```
  <input onKeypress="return (/[\d]/.test(String.fromCharCode(event.keyCode)))" maxlength="11">
  
  <input type="text" onkeyup="value=value.replace(/[^\d]/g,'') " ng-pattern="/[^a-zA-Z]/" />
  ```

  ## 只能输入数字和限制几位数
  ```
  <input type="number" id="code" value="" placeholder="请输入短信验证码">
  let codeDom = document.getElementById('code')
  var codeValue = ''
  codeDom.oninput = function () {
    if (codeDom.value !== '') {
      codeValue = codeDom.value
    } else if (codeValue.length === 1) {
      codeValue = ''
    }
    codeDom.value = codeValue.replace(/[^\d]/g, '').slice(0, 6)
  }
  ```

  ## nth-child公式
  an+b-----a表示有几种循环样式，b表示循环中的第几个，如:3种样式要循环，a=3,b=1,b=2,b=3

  ## 取消伪类before和after
  设置contrnt:none

  ## 两端对齐
  :after{display:inline-block;content:'';width:100%;}

  ## 返回顶部
  $(".return").click(function(){
      $('body,html').animate({scrollTop:0},200);
  });

  ## 媒体查询
  ```
  @media screen and (max-width:320px){body {font-size:62.5%!important;}}

  @media screen and (min-width:320px){body {font-size:62.5%!important;}}

  @media screen and (min-width:360px){body {font-size:70.3%!important;}}

  @media screen and (min-width:400px){body {font-size:78.1%!important;}}

  @media screen and (min-width:440px){body {font-size:85.9%!important;}}

  @media screen and (min-width:460px){body {font-size:89.9%!important;}}

  @media screen and (min-width:480px){body {font-size:93.8%!important;}}

  @media screen and (min-width:540px){body {font-size:105.5%!important;}}

  @media screen and (min-width:560px){body {font-size:109.4%!important;}}

  @media screen and (min-width:640px){body {font-size:125%!important;}}
  ```

  ## 禁止表单获取光标后页面放大的问题
  ```
  <meta name="apple-mobile-web-app-capable" content="yes">  
  <meta name="viewport" content="width=device-width, initial-scale=1.0,minimum-scale=1.0, maximum-scale=1.0, user-scalable=no">
  ```

  ## 获取最后一个“-”符号位置，截取字符串到最后一个“-”符号为止
  ```
  var txt="asd-czx-asd-aw";
  var txtIndex=$(this).parents("label").siblings('.layer-name').text().lastIndexOf("-");
  if (txtIndex != -1) { 
  console.log(txt.substr(0,txtIndex));//asd-czx-asd
  }
  ```

  ## echarts图标渐变色设置
  ```
  areaStyle: {normal: {
    color: new echarts.graphic.LinearGradient(1, 0, 0, 0, [{
          offset: 0,
          color: 'rgba(0, 0, 0, 1)'
      }, {
          offset: 0.5,
          color: 'rgba(255, 255, 111, 1)'
      }, {
          offset: 1,
          color: 'rgba(28, 159, 255, 1)'
      }])
  }},
  ```

  ## 更改选中文本的样式
  ```
  ::selection
  {
    color: white;
    background-color: red;
  }
  
  ::-moz-selection  /* Firefox needs an extra attention for this */
  {
    color: white;
    background-color: red;
  }
  ```

  ## 垂直居中
  ```
    方法1：
    .Absolute-Center {
      position: absolute;margin: auto;top: 0; left: 0; bottom: 0; right: 0;
    }

    方法2：
    .vc{
        position: relative;
        top: 50%;
        transform: translateY(-50%);
        -webkit-transform: translateY(-50%);
        -o-transform: translateY(-50%);
    }
  ```

  ## iframe交互
  ```
  找到最上层的标签：$("想找的标签",top.window.document)
  {原生：window.parent或jq:$(".close-icon",parent.document)}  iframe页面调用父页面对象

  父页面页面调用iframe对象
  $('iframe的ID').contents().find("要获取的元素").addClass("srtdl");
  ```

  ## 处理数组数据结构相关方法
  ```
    find返回数组或类似结构中满足条件的第一个元素
    const posts = [
      {id: 1, title: 'Title 1'},
      {id: 2, title: 'Title 2'}
    ];
    // 找出id为1的posts
    const title = posts.find(p => p.id === 1).title;

    filter方法可以筛除数组和类似结构中不满足条件的元素，并返回满足条件的元素组成的数组
    const integers = [1, 2, 3, 4, 6, 7];
    const evenIntegers = integers.filter(i => i%2 === 0);
    // evenIntegers的值为[2, 4, 6]

    向数组中新增元素
    const books = ['Positioning by Trout', 'War by Green'];
    const newBooks = [...books, 'HWFIF by Carnegie'];
    // newBooks are now ['Positioning by Trout', 'War by Green', 'HWFIF // by Carnegie']

    如果需要实现用户从购物车中删除物品，但是又不想破坏原来的购物车列表，可以使用filter方法
    const myId = 6;
    const userIds = [1, 5, 7, 3, 6];
    const allButMe = userIds.filter(id => id !== myId);
    // allButMe is [1, 5, 7, 3]

    修改数组中满足条件的元素对象
    const posts = [
      {id: 1, title: 'Title 1'},
      {id: 2, title: 'Title 2'}
    ];
    const updatedPosts = posts.map(p => p.id !== 1 ?
      p : {...p, title: 'Updated Title 1'}
    );
    /*
    updatedPosts is now 
    [
      {id: 1, title: 'Updated Title 1'},
      {id: 2, title: 'Title 2'}
    ];
    */

    找出数组中满足条件的元素
    const posts = [
      {id: 1, title: 'Title 1'},
      {id: 2, title: 'Title 2'}
    ];
    const postInQuestion = posts.find(p => p.id === 2);
    // postInQuestion now holds {id: 2, title: 'Title 2'}

    删除目标对象的一组属性
    const user = {name: 'Shivek Khurana', age: 23, password: 'SantaCl@use'};
    const userWithoutPassword = Object.keys(user)
      .filter(key => key !== 'password')
      .map(key => {[key]: user[key]})
      .reduce((accumulator, current) => 
        ({...accumulator, ...current}),
        {}
      )
    ;
    // userWithoutPassword becomes {name: 'Shivek Khurana', age: 23}
    const user = {name: 'Shivek Khurana', age: 23, password: 'SantaCl@use'};
    const userWithoutPassword = (({name, age}) => ({name, age}))(user);

    将对象转化成请求串
    const params = {color: 'red', minPrice: 8000, maxPrice: 10000};
    const query = '?' + Object.keys(params)
      .map(k =>   
        encodeURIComponent(k) + '=' + encodeURIComponent(params[k])
      )
      .join('&')
    ;
    // encodeURIComponent将对特殊字符进行编码。
    // query is now "color=red&minPrice=8000&maxPrice=10000"

    获取数组中某一对象的下标
    const requiredIndex = posts.findIndex(obj=>obj.id===131)
  ```

  ## js精度计算
  ```
  parseFloat((数学表达式).toFixed(digits))； // toFixed() 精度参数须在 0 与20 之间
  // 运行
  parseFloat((1.0 - 0.9).toFixed(10)) // 结果为 0.1 
  ```
  ## 首字母大写
  ```
  export function initialUpperCase(value = '') {
    return value.replace(/^\S/, s => s.toUpperCase());
  }
  ```
  ## 几种正则
  ```
  value.replace(/[^\a-\z\A-\Z0-9\u0020-\u007F]/g, '') // 过滤中文及中文字符
  /^[\a-\z\A-\Z0-9\u0020-\u007F]+$/i.test(text) // 非中文及字符字符
  'asdasdd{{asdasd}}asdasd{\{asd}}'.match(/\{{.*?\}}/g) // 匹配以{{开头 }}结尾的  
  'asda}}sdd{{asda121323sd}}asdasd{\{112}}'.match(/(?<={{).*?(?=}})/g)  
  // 匹配{{}}直接的内容，https://blog.csdn.net/qq_38111015/article/details/80416823?spm=1001.2101.3001.6650.3&utm_medium=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7ERate-3-80416823-blog-105825552.pc_relevant_multi_platform_whitelistv3&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7ERate-3-80416823-blog-105825552.pc_relevant_multi_platform_whitelistv3&utm_relevant_index=6  
  'asdasdd {{asdasd}} asdasd {\{asd}} 112'.replace(/\{{.*?\}}/g, 'xuxu')  
  // 正则匹配字符串并替换符合的字符

  ```

  ## mac浏览器跨域调试
  ```
  open -n /Applications/Google\ Chrome.app/ --args --disable-web-security --user-data-dir=/Users/xuyiyang/MyChromeDevUserData/Contents/ Chrome.app/
  ```
  ## 箭头生成
  ```
  .arrow_top{
    display:inline-block;
    border-style:solid;
    width:8px; // 长度控制
    height:8px; // 长度控制
    border-width:1px 1px 0 0; // 厚度
    border-color:#ccc; // 颜色
    transform: matrix(0.71,-0.71,0.71,0.71,0,0) // 方向：上
    transform: matrix(0.71,0.71,-0.71,0.71,0,0) // 方向：右
    transform: matrix(-0.71,0.71,-0.71,-0.71,0,0) // 方向：下
    transform: matrix(-0.71,-0.71,0.71,-0.71,0,0) // 方向：左
  }
  ```
  ## 两端对齐，最后一排左对齐
  ```
  <ul>
    <li></li>
    // i标签用于补齐最后一排，使之最后一排左对齐
    <i></i>
    <i></i>
    <i></i>
    <i></i>
    <i></i>
  </ul>

  ul {
    display: flex;
    justify-content: space-between;
    flex-wrap: wrap;
    align-items: flex-start;
    & > i, li {
      width: 269px;
    }
  }

  // 其他方法：https://www.zhangxinxu.com/wordpress/2019/08/css-flex-last-align/
  ```

  ## div禁用
  ```
  .disable {
    cursor: not-allowed;
    pointer-events: none;
  }
  ```

  ## input number类型禁止输入e
  ```
  <input type="number" onkeypress='return( /[\d]/.test(String.fromCharCode(event.keyCode)))' />
  ```

  ## toLocaleString
  ```
  // 将数字自动转换成带%的, useGrouping是否分割千分位
  var a = 0.228423423424234423
  a.toLocaleString(undefined, {useGrouping: false, style: 'percent'}) // 23%

  // 保留几位小数
  var a = 123456.6789
  a.toLocaleString(undefined, {maximumFractionDigits: 2}) //123,456.68

  // 整数补位
  var a = 1.11
  a.toLocaleString(undefined, {useGrouping: false, minimumIntegerDigits: 2}) // 01.11

  属性style是不同样式展示选项：默认是decimal。 选项：
  decimal: 纯数字
  percent： 百分比
  unit： 单位格式，配合unit，单位使用。单位取值
  currency： 用于货币格式，注意这个属性不能单独使用，还得配套使用currency属性
  var a = 123456.6789, 
  a.toLocaleString(undefined, {style: 'decimal'}) //123,456.679
  a.toLocaleString(undefined, {style: 'percent'}) // 12,345,668%
  a.toLocaleString(undefined, {style: 'currency', currency: 'EUR'}) // €123,456.68

  a.toLocaleString(undefined, {style: 'currency', currency: 'CNY'}) // ¥123,456.68
  a.toLocaleString(undefined, {style: 'unit', unit: 'acre'}) // 123,456.679英亩

  其中currency和currencyDisplay也可配套使用，前者制定对应的货币，比如 USD 、EUR 与 CNY （不区分大小写的），后者则是货币符号的展示样式，默认currencyDisplay：symbol:

  var a = 123456.6789, 
  a.toLocaleString(undefined, {style: 'currency', currency: 'CNY', currencyDisplay: 'symbol'}) //  ¥123,456.68

  a.toLocaleString(undefined, {style: 'currency', currency: 'CNY', currencyDisplay: 'code'}) // CNY 123,456.68

  a.toLocaleString(undefined, {style: 'currency', currency: 'CNY', currencyDisplay: 'name'}) // 123,456.68人民币

  ```

  ## 引入svg
  ```
  import icons from './assets/icons.svg'
  <svg className="hero-logo" viewBox="0 0 900 300">
    <use xlinkHref={`${icons}#electron`} />
  </svg>
  ```