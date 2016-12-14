<template>
  <div>
      <v-header></v-header>
      <div class="tab">
          <div class="tab-item">
              <a v-link="{path:'/goods'}">商品</a>
          </div>
          <div class="tab-item">
              <a v-link="{path:'/ratings'}">评论</a>
          </div>
          <div class="tab-item">
              <a v-link="{path:'/seller'}">商家</a>
          </div>
      </div>
      <router-view> </router-view>
  </div>
</template>

<script type="text/ecmascript-6">
    import header from 'components/header/header'
    export default {
        components: {
            'v-header': header
        }
    }
</script>
<style lang="scss" rel="stylesheet/scss" scoped>
    .tab {
        display: flex;
        width: 100%;
        height: 40px;
        line-height: 40px;
        .tab-item {
            flex: 1;
            text-align: center;
        }
        .v-link-active {
            background: #e7e7e7;
        }
    }
</style>
