<template xmlns:v-bind="http://www.w3.org/1999/xhtml" xmlns:v-on="http://www.w3.org/1999/xhtml">
  <div class="manage tc">
    <button v-on:click="add">新增</button>
    <div class="input-area" v-show="showAdd">
      <input type="text" placeholder="请输入人员姓名" v-model="nameValue">
      <button class="OkButton" v-on:click="addName">确定</button>
    </div>
      <div align="center">
        <table>
          <tr>
            <th>姓名</th>
            <th>操作</th>
          </tr>
          <tr v-for="(item,index) in peoples" class="tc">
            <td>
              {{item.name}}
            </td>
            <td v-bind:id="index"><button class="btn" v-on:click="detele">删除</button>
              &nbsp;&nbsp;
              <button class="btn" v-on:click="edit">编辑</button></td>
          </tr>
        </table>

      </div>
    <div  class="wrap" v-show="showEdit">
      <div class="content">
        <input type="text" placeholder="请输入新姓名" v-model="newName">
        <button class="btn" v-on:click="editName">确定</button>
        <button class="btn" v-on:click="cancel">取消</button>
      </div>

    </div>
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
        showEdit:false,
        peoples:[{'name':'jack'},{'name':'sean'}],
        nameValue:'',
        newName:'',
        editId:0
      }
    },
    methods:{
        add:function(){
        this.showAdd=true
      },
      addName:function(){
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
      },
      detele:function(e){
        var id= e.target.offsetParent.id
        this.peoples.splice(id,1);
      },
      edit:function(e)
      {
        var id= e.target.offsetParent.id
        this.showEdit=true
        this.editId=id
        this.newName=this.peoples[id].name
      },
      cancel:function()
      {
        this.showEdit=false
      },
      editName:function(){
        var v=this.newName

    if(v.trim()=="")
    {
      alert("请输入名字")
    }
    else{
      this.peoples[this.editId].name=this.newName
      this.showEdit=false
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
