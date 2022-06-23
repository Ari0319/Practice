<!--
//响应式变量（系统自带）
<script setup>
let cot = $ref(0) //$ref语法糖声明了一个响应式变量cot，因此cot变量值发生变化时，相对应的页面内容会重新渲染
function inc () {
  cot++
}
</script>

<template>
  <h1>Home</h1>
  <p>cot: {{ cot }}</p>
  <button @click="inc">Click Me</button>
</template>
-->

<!--
//高级数据绑定
<script setup>
let search = $ref('') //首先定义了一个会被自动追踪的变量search
let upper = $computed(() => search.toUpperCase()) //使用$computed()定义的upper变量是一个计算属性
</script>

<template>
  <p>Your input: {{ search }}</p> //将被自动追踪的变量search用{{ }}在页面上显示出来
  <p :class="upper === search ? 'green' : 'red'"> //p元素使用了属性绑定 : 。使用冒号修饰的元素属性内容可以是JS脚本表达式。并且可以在其中使用定义好的变量。
    Upper Case: {{ upper }}
  </p>
  <input v-model="search"> //input元素上使用双向绑定v-model。双向是指用户的输入会自动改变search变量的值，改变search变量的值也会改变用户的输入。
  <button @click="search = ''">Clear</button> //但点击按钮时，search变量会被赋值为空字符串
</template>

<style scoped>
input { background: #eee; }
.green { color: green; }
.red { color: red; }
</style>
-->

<!--
//控制结构（感觉有点像制作todo-list）
<script setup>
let content = $ref(''), list = $ref([]) //定义两个响应式变量中的空字符串，一个空字符串，一个空数组
</script>

<template>
  <p v-if="content">Your input: {{ content }}</p> 
  <p v-else>You don't have any input</p>
  //通过v-if和v-else可以简单的根据一个表达式（content）的真假来控制元素的显示情况。
  <input v-model="content">
  <button @click="list.push(content)">Add</button> //在点击Add按钮以后，当前输入框的内容content就会被添加到数组的尾部。
  <p v-for="item in list">{{ item }}</p> //v-for会自动循环list中的内容，并对每一个项目生成一个v-for所在的HTML元素（包括它的内容）。在每个项目的元素中，我们可以读取item作为当前循环的项目值。
</template>

<style scoped>
input { background: #eee; }
</style>
-->


<!--
<script setup>
import List from './List.vue' //直接使用import关键字，通过相对路径引入组件，然后就可以直接用在template中
</script>

<template>
  <list v-for="i in 3"></list> //这里演示了v-for的另一种小用法，我们可以直接在被循环的位置写一个数字n，表示循环n次。
</template>
//List组件会被渲染三次，但是这三个组件并不共享数据。他们的输入框变量content和列表变量list都是独立的
-->

<script setup>
import TodoList from './TodoList.vue'
</script>

<template>
<TodoList v-for="i in 3"></TodoList>
</template>