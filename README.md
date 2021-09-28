#### 1. setup 

- 和 beforeCreate、created 差不多同时执行
- 页面加载时只执行一次

#### 2. vue2 的响应式数据 和 vue3 的响应式数据区别

- vue2
  - 当你把一个普通的 JavaScript 对象传入 Vue 实例作为 data 选项，Vue 将遍历此对象所有的 property，并使用 Object.defineProperty 把这些 property 全部转为 getter/setter。
  - 缺陷：Vue 无法检测 property 的添加或移除。所以对于对象上新增的属性无法响应。
  - 解决： this.$set
- vue3
  - 用 ES6的 Proxy 实现
-     Object.defineProperty(data, 'count', {
          get(){},
          set(){}
      })
      new Proxy(data, {
          get(key) {},
          set(key,value) {}
      })

#### 3. vue2 的 和 vue3 的 生命周期 区别

- beforeDestory 变成 beforeUnMount
- destoryed 变成 unmounted

为了更好的语义化，一个组件是 mount 到 unMount 的过程

#### 4. HTML `<pre>` 
表示预定义格式文本。在该元素中的文本通常按照原文件中的编排，以等宽字体的形式展现出来，文本中的空白符（比如空格和换行符）都会显示出来。
