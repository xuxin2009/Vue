<template>
  <div class="manage tc">
    <button v-on:click="add">新增</button>
    <div class="input-area" v-show="showAdd">
      <input type="text" placeholder="请输入人员姓名" v-model="nameValue">
      <button class="OkButton" v-on:click="addName">确定</button>
    </div>
      <table>
        <tr>
          <th>姓名</th>
          <th>操作</th>
        </tr>
        <tr v-for="item in peoples">
          <td>
            {{item.name}}
          </td>
          <td><button class="btn">删除</button>&nbsp;&nbsp;<button class="btn">编辑</button></td>
        </tr>
      </table>
    <footer-nav v-bind:class="{'isManage':isNowPage}"></footer-nav>
  </div>
</template>
<script >
  import FooterNav from '../../components/Footer'
  export default {
    components:{
      FooterNav
    },
    data:function(){
      return{
        isNowPage:true,
        showAdd:false,
        peoples:[{'name':'jack'},{'name':'sean'}],
        nameValue:''
      }
    },
    methods:{
        add(){
        this.showAdd=true
      },
      addName(){
        var name=this.nameValue;
        if(name.trim()=="")
        {
          alert("请输入新增人员名字！")
        }
        else
        {
          var data={};
          data.name=name;
          this.peoples.push(data)
        }
      }
    }
  }
</script>
<style>

  Button{background-color:#41b883;width: 150px;height: 50px;}
  .OkButton{width: 80px;height: 40px;}
  input{width: 200px;height: 30px;margin-top: 10px;}
  table{align-self: center;border: 1px black solid;width: 400px;height: 100px;}
  td{width: 100px;border: 1px black solid;}
  .btn{width: 50px;height: 30px; }

</style>
