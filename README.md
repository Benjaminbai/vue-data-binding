# vue-data-binding
realize vue data binding

# 实现思路
1. 首先在index.html页面定义好app的容器，方便vue接管，引入脚本
2. 在main.js里模拟vue的实例，el/data等
3. 实现vue，并导出，其中需要引入oberver，compiler；observer接收 上一步中模拟的data， compiler中接收上一步模拟的el，和this
4. observer中需要引入定义好的监听和触发器dep，observer中会遍历数据，设置get/set方法，如果数据改变了，就会触发dep的notify方法；同理，当触发dep的listen方法后，返回值
5. dep中就定义两个方法，listen和notify，notify会触发数据中的每个updata方法
6. 接着就是compiler， 会编译html，判断节点类型，如果遇见v-model就监听输入框的input事件，再给input赋值，如果是文本节点，取到{{}}的值传递给watcher，watcher接收三个参数，当前节点，大括号中的值，和当前实例
7. watch里面也要引入dep，并且有对应的更新函数，触发更新函数给当前节点赋值