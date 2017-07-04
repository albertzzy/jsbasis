# jsbasis

## 闭包与内存泄漏

[闭包内存泄漏](http://www.ruanyifeng.com/blog/2017/04/memory-leak.html?utm_source=tuicool&utm_medium=referral)

[内存泄漏](http://www.cnblogs.com/chuaWeb/p/5196330.html) 

[闭包](http://www.jb51.net/article/83524.htm)

## 常用放法



## thunk

    *延迟求值，curry化
    thunk函数替换多参数函数，将其替换成单参数版本，且只接受回调函数作为参数
    ```javascript

        function thunkify(fn){
            return function(){
                var args = new Array(arguments.length);
                var ctx = this;

                for(var i = 0; i < args.length; ++i) {
                args[i] = arguments[i];
                }

                return function(done){
                var called;

                args.push(function(){
                    if (called) return;
                    called = true;
                    done.apply(null, arguments);
                });

                try {
                    fn.apply(ctx, args);
                } catch (err) {
                    done(err);
                }
                }
            }
        };

    ```
    要想yield一个异步操作，此异步操作要是一个thunk函数，但
    thunk函数只是Generator函数自动执行的一种方案，promise也是

    [thunk](http://www.ruanyifeng.com/blog/2015/05/thunk.html)

    [co](http://www.ruanyifeng.com/blog/2015/05/co.html)



## http
    [PUT请求方法](http://www.jianshu.com/p/5d8fdf0dd149)
    [HEAD请求方法,204，206](http://blog.163.com/wang_hai_fei/blog/static/30902031201333115425644/)