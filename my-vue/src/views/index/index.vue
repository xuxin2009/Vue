<template>
  <div>
    欢迎来到人员管理系统
    <footer-nav v-bind:class="{'isIndex':isNowPage}"></footer-nav>
  </div>

</template>
<script>
  import FooterNav from '../../components/Footer'
  export default {
    components:{
      FooterNav
    },
    data:function(){
      return{
        isNowPage:true
      }
    }
  }
</script>

