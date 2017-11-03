<template>
  <!-- 文字部分 -->
  <div class="hello">
    <span>{{msg}}</span>
    <h2>Essential Links</h2>
    <h6>{{msgCN}}</h6>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      msgCN:'必不可少的环节',
      system:'生态系统'
    }
  },

  beforeCreate (){
    console.log('beforeCreate-在实例初始化之后，数据观测 (data observer) 和 event/watcher 事件配置之前被调用')
    // 实例刚刚创建，this值是VueComponent实例,能打印出来
    console.log(this);
    // 数据观测之前，所以this.msg是undefined
    console.log(this.msg);
  },
  created (){
    // 在实例创建完成后被立即调用。在这一步，实例已完成以下的配置：数据观测 (data observer)，属性和方法的运算，watch/event 事件回调。然而，挂载阶段还没开始，$el 属性目前不可见。
    // 实例刚刚创建，this值是VueComponent实例
    console.log(this)

    //$el 属性目前不可见,打印出来是undefined
    console.log("this.$el")
    console.log(this.$el)
    console.log("this.$el")

    this.msg = 'pp'
  },
  beforeMount (){
    // 在挂载开始之前被调用：相关的 render 函数首次被调用。
    console.log('beforeMount')
    // 是咧以创建好，VueComponent
    console.log(this)
    //还没开始挂载 undefined
    console.log(this.$el)

    console.log('beforeMount')
  },
  mounted (){
    // el 被新创建的 vm.$el 替换，并挂载到实例上去之后调用该钩子。
    // 如果 root 实例挂载了一个文档内元素，当 mounted 被调用时 vm.$el 也在文档内
    console.log('mounted')
    // $el是：<div class="hello"><h2>Essential Links</h2><h6>{{msgCN}}</h6></div>
    console.log(this.$el);
    console.log('mounted')
  },
  beforeUpdate (){
    // 数据更新时调用，发生在虚拟 DOM 重新渲染和打补丁之前。
    // 你可以在这个钩子中进一步地更改状态，这不会触发附加的重渲染过程。
    console.log('beforeUpdate-------------------')
    // 更改数据
    this.msg="updata"
    console.log(this.msg)
    console.log('beforeUpdate-------------------')
  },
  updated (){
    // 由于数据更改导致的虚拟 DOM 重新渲染和打补丁，在这之后会调用该钩子。当这个钩子被调用时，组件 DOM 已经更新，所以你现在可以执行依赖于 DOM的操作。然而在大多数情况下，你应该避免在此期间更改状态。如果要相应状态改变，通常最好使用计算属性或 watcher 取而代之。
    console.log('updated')
  },
  beforeDestroy (){
    // 实例销毁之前调用。在这一步，实例仍然完全可用。
    console.log('beforeDestroy')
  },
  destroyed(){
    // Vue 实例销毁后调用。调用后，Vue 实例指示的所有东西都会解绑定，
    // 所有的事件监听器会被移除，所有的子实例也会被销毁

  }


}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
