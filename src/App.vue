<template>
  <div>
    <div class="button">
      <div>
        <t-button class="discoloration" type="warning">点击变色</t-button>
      </div>

      <div class="bt">
        <button class="btn"><span>悬浮变色</span></button>
      </div>

      <div>
        <!-- 发光按钮 -->
        <button class="btns">科技按钮</button>
      </div>
    </div>

    <!-- <t-button type="warning">测试</t-button> -->
    <br />
    <br />
    <br />
    <t-input v-model="val"></t-input>
    <t-input type="warning" v-model="val"></t-input>
    <t-input type="" v-model="val"></t-input>
    <p>{{ val }}</p>

    <br />
    <br />
    <br />

    <t-friend></t-friend>
  </div>
</template>

<script setup>
import { ref } from "vue";
const val = ref("");
</script>

<style lang="scss">
.button {
  display: flex;
  width: 800px;
  // margin-right: 20px;
  justify-content: space-around;
  border: 2px solid #ccc;
  padding: 10px;
}
.discoloration {
  display: inline-block;
  padding: 15px 25px;
  font-size: 24px;
  cursor: pointer;
  text-align: center;
  text-decoration: none;
  outline: none;
  color: #fff;
  background-color: rgb(16, 185, 214);
  border: none;
  border-radius: 15px;
  box-shadow: 0 5px #999;
}
.btns {
  position: relative;
  padding: 1rem 3rem;
  font-size: 1.5rem;
  line-height: 1.5;
  color: #fff;
  outline: transparent;
  border: transparent;
  cursor: pointer;
  user-select: none;
  white-space: nowrap;
  border-radius: 4em;
  background: linear-gradient(90deg, #00dbde, #fc00ff, #00dbde);
  background-size: 300%;
  animation: glow 8s linear infinite;
  z-index: 0; // 避免伪元素移到后面
  &::before {
    position: absolute;
    content: "";
    top: -5px;
    bottom: -5px;
    left: -5px;
    right: -5px;
    z-index: -1;
    border-radius: inherit;
    background: inherit; // 可以顺带继承动画
    background-size: inherit;
    opacity: 0;
    filter: blur(20px);
    transition: 0.5s;
  }
  &:hover {
    &:before {
      opacity: 1;
    }
  }
}

@keyframes glow {
  to {
    background-position: 300%;
  }
}
.discoloration:hover {
  background-color: #1795bb;
}
.discoloration:active {
  background-color: #1795bb;
  box-shadow: 0 5px #666;
  transform: translateY(4px);
}

// 悬浮变色
.bt {
  display: flex;
  justify-content: center;
}
.btn {
  width: 155px;
  height: 73px;
  color: #fff;
  background: linear-gradient(
    0deg,
    rgba(0, 172, 238, 1) 0%,
    rgba(2, 126, 251, 1) 100%
  );
  font-family: "Lato", sans-serif;
  font-weight: 500;
  border-radius: 10px;
  box-shadow: inset 2px 2px 2px 0px rgba(255, 255, 255, 0.5),
    7px 7px 20px 0px rgba(0, 0, 0, 0.1), 4px 4px 5px 0px rgba(0, 0, 0, 0.1);
  transition: all 0.3s ease;
  cursor: pointer;
  border: none;
  position: relative;
  line-height: 120px;
  padding: 0;
}
.btn span {
  position: relative;
  display: block;
  width: 100%;
  height: 80px;
  line-height: 80px;
  font-size: 20px;
  font-weight: 600;
}
.btn::before,
.btn::after {
  position: absolute;
  content: "";
  top: 0;
  right: 0;
  background: rgba(2, 126, 251, 1);
  transition: all 0.3s ease;
}
.btn::before {
  width: 0;
  height: 2px;
}
.btn::after {
  height: 0;
  width: 2px;
}
.btn span::before,
.btn span::after {
  position: absolute;
  content: "";
  bottom: 0;
  left: 0;
  background: rgba(2, 126, 251, 1);
  transition: all 0.3s ease;
}
.btn span::before {
  width: 0;
  height: 2px;
}
.btn span::after {
  height: 0;
  width: 2px;
}

.btn:hover {
  background: transparent;
  color: rgba(2, 126, 251, 1);
}

.btn:hover::before {
  width: 100%;
}
.btn:hover::after {
  height: 100%;
}
.btn span:hover::before {
  width: 100%;
}
.btn span:hover::after {
  height: 100%;
}
</style>