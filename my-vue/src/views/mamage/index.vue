<template>
  <div class="manage tc">
    <button>新增</button>
    <div class="input-area">
      <input type="text" placeholder="请输入人员姓名">
      <button>确定</button>
    </div>
      <table>
        <tr>
          <th>姓名</th>
          <th>操作</th>
        </tr>
        <tr>
          <td>张三</td>
          <td><span>删除</span><span>编辑</span></td>
        </tr>
      </table>
    <footer-nav></footer-nav>
  </div>
</template>
<script >
  import FooterNav from '../../components/Footer'
  export default {
    components:{
      FooterNav
    }
  }
</script>
<style>


</style>
