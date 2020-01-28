# v-if和v-for的优先级？
v-for和v-if同时使用，有一个先后运行的优先级，v-for比v-if优先级更高，这就说明在v-for每次的循环赋值中每一次调用v-if的判断，所以不推荐v-if和v-for在同一个标签中同时使用

# vue组件data选项为什么必须是个函数，而vue的跟实例则没有此限制？
如果data是一个函数的话，这样每复用一次组件，就会返回一份新的data，类似于给每个组件实例创建一个私有的数据空间，让各个组件实例维护各自的数据。而单纯的写成对象形式，就使得所有组件实例共用了一份data，就会造成一个变了全都会变的结果。所以说vue组件的data必须是函数。这都是因为js的特性带来的，跟vue本身设计无关。

# vue中key的作用和工作原理？说说你对它的理解
key主要用在Vue的虚拟 DOM 算法，在新旧 nodes 对比时辨识 VNodes。如果不使用 key，Vue 会使用一种最大限度减少动态元素并且尽可能的尝试就地修改/复用相同类型元素的算法。而使用 key 时，它会基于 key 的变化重新排列元素顺序，并且会移除 key 不存在的元素。有相同父元素的子元素必须有独特的 key。重复的 key 会造成渲染错误。

# 怎么理解Vue中的diff算法？
我们都知道，操作dom的代价极大，所以vue中用虚拟dom，而diff算法是理解虚拟dom的很重要的环节，vue中diff算法，就是通过对比新旧虚拟dom，来替换新的dom，这样便极大的减少操作dom的代价。

# 说说mvp,mvc,mvvm的理解
mvp 是model view Presenter  model指数据，view视图，Presenter处理层，所有的处理都在Presenter里执行，包括视图的所有数据都是直接从处理层读取。
mvc 基本上和mvp差不多，但是view是直接从model拿取相应的数据。
mvvm 是view viewmodel model  mvvm区别于mvc实现了数据与视图的分离，通过数据驱动，只关心数据变化即可。

# 谈谈你对vue组件之间通信的理解
组件通信主要有：父传子（props），子传父（$emit）和兄弟组件（eventBus、vuex）等传递，其他组件通信还有：$attrs 不被props包含的都在$attr中，可以直接调用  $listeners  包含了父作用域中的 (不含 .native 修饰器的) v-on 事件监听器。依赖注入provide/inject 这个可以跨层级传参   ，$parent 向父组件传参 $children 向子组件传参  ref 如果用于dom元素则指向dom，如果是组件则是组件的实例
