
# Vue
- vue优点
    - 轻量级框架：只关注视图层，是一个构建数据的视图集合，大小只有几十 kb
    - 简单易学：国人开发，中文文档，不存在语言障碍 ，易于理解和学习
    - 双向数据绑定：保留了 angular 的特点，在数据操作方面更为简单
    - 组件化：保留了 react 的优点，实现了 html 的封装和重用，在构建单页面应用方面有着独特的优势
    - 视图，数据，结构分离：使数据的更改更为简单，不需要进行逻辑代码的修改，只需要操作数据就能完成相关操作；
    - 虚拟DOM：dom 操作是非常耗费性能的， 不再使用原生的 dom 操作节点，极大解放 dom 操作，但具体操作的还是 dom 不过是换了另一种方式；
    - 运行速度更快：相比较于 react 而言，同样是操作虚拟 dom ，就性能而言， vue 存在很大的优势。
1. v-show和v-if指令的共同点和不同点
    - 共同点：
        - 都能控制元素的显示和隐藏
    - 不同点： 
        - v-show本质就是通过控制css中的display设置为none，控制隐藏，只会编译⼀次；v-if是动态的向DOM树内添加或者删除DOM元素，若初始值为false，就不会编译了。⽽且v-if不停的销毁和创建⽐较消耗性能
2. 如何获取dom（<font color=red>ref="domName" 用法：this.$refs.domName</font> ）
    - vue中，在mounted之后的钩子 函数中才能进行dom操作，mounted完成dom挂载
        - 选择器获取
       ```
        <template>
            <div>
                <canvas id='cvs' >
            </div>
        </template>
        <script>
            export default{
                mounted(){
                    let canvas=document.querySelector('#cvs');
                }
            }
         </script>
       ```
       - ref获取
       ```
        <template>
            <div>
                <canvas ref='cvs' >
            </div>
        </template>
        <script>
            export default{
                mounted(){
                    let canvas=this.$refs.cvs;
                }
            }
        </script>
       ```
3. vue当中的指令和它的用法？
    - <font color=red>v-model</font> 双向数据绑定；
    - <font color=red>v-for</font> 循环；
    - <font color=red>v-if v-show </font> 显示与隐藏；
    - <font color=red>v-on</font> 事件；
    - <font color=red>v-once</font> 只绑定一次；

  一般用在v-for里面数据层次太多，render函数没有自动更新，需手动强制刷新。迫使 Vue 实例重新渲染。注意它仅仅影响实例本身和插入插槽内容的子组件，而不是所有子组件。

## 



https://juejin.cn/post/6844904087402594312
