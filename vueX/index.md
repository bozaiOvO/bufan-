# vuex
## 什么是vuex

+ Vuex 是一个专为 Vue.js 应用程序开发的状态管理模式。它采用集中式存储管理应用的所有组件的状态，并以相应的规则保证状态以一种可预测的方式发生变化。
+ 通俗一点，他用来管理一些状态，比如说，这个音乐是播放状态还是暂停状态？这个购物车有多少东西了？
+ 他用来更改和保存一些状态。

## 为什么使用到vuex？
+  因为模块间是不共享作用域的，那么B 模块想要拿到 A 模块的数据，并且他们不是父子组件的时候，比如说，这个播放状态很多模块都会使用到，我们会怎么做？使用父子传值明显是不现实的，最好的做法就使用vuex。

## vuex的安装和使用。
+　在普通vue-cli脚手架中并不会给你提供vuex。所以我们需要自己使用命令行安装。
+　`npm install vuex --save`安装vuex这个包，--save表示将这个依赖包与本项目的依赖关系写入package.json中。
+　安装好了依赖之后，代表你现在拥有了他，但是你还是需要使用他，如何使用？
+　`import Vuex from 'vuex'` 引入他。
+　`Vue.use(Vuex)` 注入他。
+　在一般情况下，我们并不会把vuex的东西来写入到main.js入口文件里。
+　我们会在src下，新创一个文件夹store（仓库），在store里，新建一个index.js用来管理vuex相关的东西。

```
import Vue from 'vue'
import Vuex from 'vuex'
Vue.use(Vuex)
export default new Vuex.Store({
    state:{

    },
    getters:{

    },
    mutations:{

    }
})
```

## vuex的五个核心概念。
### state（状态
+ state 定义了应用状态的数据结构，同样可以在这里设置默认的初始状态。

### Getters（vuex的计算属性。
+ Getters 允许组件从 Store 中获取数据，譬如我们可以从 Store 中的 list 中筛选出我们需要的列表。

### mutations（修改状态。
+ 就是用来修改state状态，我们在平常修改一个变量都是简单粗暴的
```
var a = 1;
a = 2;
//但是在vuex中，不可以直接修改状态，你想修改状态必须通过mutations。

```

### Actions（异步修改状态。
+ 上面说了，mutations是修改状态，但是他不是异步的，只能是同步操作，你如果想异步修改状态就是actions

### Modules(模块)
+ 随着你的项目越来越庞大，那么状态可能本身还需要进行分模块分类管理，这个时候就需要用到模块了。官方文档中已经给出了比较详细的模块操作代码，这里不再做更多讲解。

## 如何在组件中使用vuex呢。

### 在组件中使用state或者getters

+ 在计算属性中引入。
+ 
```
    computed:{
        count(){
            return this.$store.state.count
        }
    }
```

+  
```
import {mapState} from 'vuex'
export default {
    computed:{
        ...mapState([
                'count'
            ])
    }
}

```

### 在组件中使用Mutations

+ 在methods中引入
+ 
```
methods:{
    addC(){
        this.$store.commit('方法名', 参数)
    }
}
```

+ ·
```
import {mapMutations} from 'vuex'
export default{
    methods:{
        ...mapMutations({
            addCount :'addCount'
            }),
        handleClick(){
            this.addCount(参数)
        }
    }
}

```


