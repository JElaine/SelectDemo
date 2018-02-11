<template>
  <div class="m-select-container">
    <div class="m-select" @click="showSelect">
      <input type="text" placeholder="请选择" v-model="value" readonly>
      <i class="input-btn"></i>
      <transition name="slide">
        <ul v-show="showHint">
          <li v-for="item in items" @click="selectItem(item,$event)">{{item}}</li>
        </ul>
      </transition>
    </div>
  </div>
</template>

<script>
export default {
  name: 'app',
  data() {
    return {
      showHint: false,
      value: '',
      items: ['文学', '科技', '英文', '中文', '数理化']
    }
  },
  methods: {
    selectItem(value, event) {
      this.value = value;
      //判断li中是否存在className select，如果存在先将其移除
      let children = document.querySelector('ul').childNodes;
      _.forEach(children, (element) => {
        if (element.classList.contains('select')) {
          element.classList.remove('select');
        }
      });
      //为当前li添加className select
      event.target.classList.add('select');
    },
    showSelect() {
      this.showHint = !this.showHint;
      //三角箭头旋转
      if (this.showHint) {
        document.querySelector('.input-btn').style.webkitTransform = "rotate(180deg)";
      } else {
        document.querySelector('.input-btn').style.webkitTransform = "rotate(0deg)";
      }

    }
  }
}
</script>

<style lang="less" scope>
* {
  padding: 0;
  margin: 0;
}

.m-select-container {
  margin: 100px auto;
  width: 140px;
  .m-select {
    position: relative;
    .input-btn {
      height: 35px;
      width: 20px;
      position: absolute;
      right: 0;
      top: 0;
      transition: 0.5s;
      &:after {
        border: 8px solid transparent;
        border-top: 8px solid #bfcbd9;
        width: 0;
        height: 0;
        position: absolute;
        top: 13px;
        right: 0;
        content: ' ';
      }
    }
    &>input {
      border: 1px solid rgba(131, 145, 165, 0.38);
      border-radius: 3px;
      height: 35px;
      width: 140px;
      padding-left: 10px;
      font-size: 18px;
      cursor: pointer;
      transition: all 1.5s;
      &:hover {
        border: 1px solid #8391a5;
      }
    }
    ul {
      list-style: none;
      width: 150px;
      height: 120px;
      overflow-x: hidden;
      margin-top: 10px;
      border: 1px solid rgba(131, 145, 165, 0.38);
      box-shadow: 3px 3px 3px rgba(136, 136, 136, 0.39);
      &>li {
        height: 35px;
        line-height: 35px;
        text-align: center;
        cursor: pointer;
        &:hover {
          background: #e4e8f1;
        }
        &.select {
          background-color: #20a0ff;
          color: #fff;
        }
      }
    }
    /*过渡效果*/
    .slide-enter,
    .slide-leave-to {
      height: 0;
    }
    .slide-leave-active,
    .slide-enter-active {
      transition: all 0.4s;
      -webkit-transition: all 0.4s;
    }
    /*定义滚动条宽度以及背景*/
     ::-webkit-scrollbar {
      width: 5px;
      height: 30px;
      background-color: #fff;
    }
    /*定义滑块*/
     ::-webkit-scrollbar-thumb {
      border-radius: 2px;
      background-color: #e8e8e8;
    }
  }
}
</style>
