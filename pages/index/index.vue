<template>
  <view class="demo">
    <view class="demo-item" v-for="(item, index) in list" :key="index">
      <view class="demo-title">{{ item.title }}</view>
      <view class="demo-content" v-for="(item1, index1) in item.item" :key="index1" @click="clickItem(item1)">
        <view class="demo-content-left">
          <view class="demo-content-left-label">{{ item1.label }}</view>
          <view class="demo-content-left-title">{{ item1.title }}</view>
        </view>
        <!-- 注释掉cc-icon组件:为了验证unpackage/dist下的打包文件中的components是否就会没有该组件 -->
        <!-- <view class="demo-content-icon"><cc-icon type="arrowright" size="22" color="#979797"></cc-icon></view> -->
      </view>
    </view>
  </view>
</template>

<script>
  export default {
    data() {
      return {
        list: [{
          title: '基础组件',
          item: [{
              label: 'Button-1',
              title: '按钮',
              url: '/views/button/index'
            },
            {
              label: 'Cell-2',
              title: '单元格',
              url: '/views/cell/index'
            },
            {
              label: 'Toast-3',
              title: '轻提示',
              url: '/views/toast/index'
            }
          ]
        }]

      }
    },
    onLoad() {

    },
    methods: {
      clickItem(item) {
        uni.navigateTo({
          url: item.url
        })
      }
    }
  }
</script>

<style lang="scss" scoped>
  .demo {
    background: #f7f8fa;
    padding: #{topx(30)} #{topx(25)};

    &-title {
      font-size: 14px;
      color: #909ca4;
      margin-bottom: #{topx(20)};
    }

    &-content {
      position: relative;
      display: flex;
      align-items: center;
      padding: 0 #{topx(40)};
      background: #fff;
      height: #{topx(45)};
      background: #fff;
      border-radius: #{topx(22)};
      margin-bottom: #{topx(13)};

      &-left {
        display: flex;
        align-items: center;
        font-weight: 700;
        color: #333;

        &-title {
          margin-left: #{topx(10)};
        }
      }

      &-icon {
        position: absolute;
        top: 50%;
        transform: translateY(-50%);
        right: #{topx(30)};
      }
    }
  }
</style>
