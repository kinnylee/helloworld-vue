<template>
  <div id="app">
    <h1>lesson 1:  vue 生命周期</h1>
    <h1>{{title}}</h1>
    <button @click="randomTitle()">改变</button>
    <button @click="destroyVm()">销毁实例</button>
    <hr />
    <h1>lesson 2: 数据链路，函数式更新链路上的所有数据</h1>
    <p><strong class="data-label">A</strong><input type="text" v-model="a"></p>
    <p><strong class="data-label">B</strong><input type="text" v-model="b"></p>
    <p><strong class="data-label">C=A*2+2</strong> answer =  {{c}}</p>
    <p><strong class="data-label">D=A+B*2</strong> answer =  {{d}}</p>
    <p><strong class="data-label">E=B/2</strong> answer =  {{e}}</p>
    <p><strong class="data-label">F=C+D</strong> answer =  {{f}}</p>
    <p><strong class="data-label">G=D-E</strong> answer =  {{g}}</p>
  </div>
</template>

<script>

export default {
  name: 'App',
  data(){
        return{
            title: "Hello World",
            a:3,
            b:4

        }
    },
    methods: {
        randomTitle(){
            this.title='Hello '+['China', 'World', 'Universe', 'Beijing', 'Shenzhen'][Math.floor(Math.random()*4.999)]
        },
        destroyVm(){
            this.$destroy()
        }
    },
    beforeCreate(){
        console.log("before create")
    },
    created(){
        console.log("created")
    },
    beforeMount(){
        console.log('before mount')
    },
    mounted(){
        console.log("mounted")
    },
    beforeUpdate(){
        console.log("before update")
    },
    updated(){
        console.log("updated")
    },
    beforeDestroy(){
        console.log("before destory")
    },
    destroyed(){
        console.log("destroyed")
    },
    computed: {
        c(){
            return this.a*2+2
        },
        d(){
            return Number(this.a)+this.b*2
        },
        e() {
            return this.b/2
        },
        f(){
            return Number(this.c)+Number(this.d)
        },
        g(){
            return this.d+this.e
        }
    }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
