<template>
  <div id="app">
    <h2>Parent</h2>
    <h3>{{msg}}</h3>
    <child1 :title="title1" @getmsg="getmsg"></child1>
    <child2></child2>
  </div>
</template>

<script>
import Child1 from '@/components/Child1'
import Child2 from '@/components/Child2'
export default {
  name: "app",
  provide:{
    woniu:'我是蜗牛'
  },
  data(){
    return {
      msg:'',
      title1:'我是你爸爸'
    }
  },
  methods:{
    getmsg(msg){
      this.msg = msg
    }
  },
  components:{Child1,Child2},
  mounted(){

    this.$on("dispatch",msg=>{
        this.msg = '接收dispatch消息:'+ msg
    })
  }

}

</script>
<style>

div{
  border:1px red solid;
  padding:10px;
  display: inline-block;
  vertical-align: top;
  /* width:50%; */
}
h1,h2{
  font-size:18px;
  margin:5px 0;
  
}
h3{
  color:red;
  font-size:14px;
}
</style>

