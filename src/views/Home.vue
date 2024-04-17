<template>
  <div class="home">
    <div class="header">
      <div class="logo">COSTAR</div>

      <div class="nav">
        <a href="">买家中心</a>
        <a href="">卖家中心</a>
        <a href="">联系方式：15227205028</a>
      </div>
    </div>

    <div class="swiper">
      <div class="swiper-wrapper">
        <div class="swiper-slide">
          <img class="img_blur"
            src="https://img1.baidu.com/it/u=2097410864,753347067&fm=253&fmt=auto&app=138&f=JPEG?w=533&h=300" alt="">
          <img src="https://img1.baidu.com/it/u=2097410864,753347067&fm=253&fmt=auto&app=138&f=JPEG?w=533&h=300" alt="">
        </div>
        <div class="swiper-slide">
          <img class="img_blur"
            src="https://img1.baidu.com/it/u=2097410864,753347067&fm=253&fmt=auto&app=138&f=JPEG?w=533&h=300" alt="">
          <img src="https://img1.baidu.com/it/u=2097410864,753347067&fm=253&fmt=auto&app=138&f=JPEG?w=533&h=300" alt="">
        </div>
        <div class="swiper-slide">
          <img class="img_blur"
            src="https://img1.baidu.com/it/u=2097410864,753347067&fm=253&fmt=auto&app=138&f=JPEG?w=533&h=300" alt="">
          <img src="https://img1.baidu.com/it/u=2097410864,753347067&fm=253&fmt=auto&app=138&f=JPEG?w=533&h=300" alt="">
        </div>
      </div>
      <!-- 如果需要分页器 -->
      <div class="swiper-pagination"></div>

      <!-- 如果需要导航按钮 -->
      <div class="swiper-button-prev"></div>
      <div class="swiper-button-next"></div>

      <!-- 如果需要滚动条 -->
      <div class="swiper-scrollbar"></div>
    </div>

    <div class="content">
      <div class="title">企业介绍</div>
      <div class="desc">
        <p>东光县文忠塑料厂，坐落于享有“塑料之乡”美誉的河北省沧州市东光县，自2005年创立以来，已稳健运营二十余年，成为业界的佼佼者。厂区占地8亩，车间面积3000㎡，仓库1500 ㎡
          ，为高效生产提供了坚实的基础。工厂配备了四台大型吹膜机，汇聚了30多名技艺精湛的员工，年产量高达7000余吨，展现出强大的生产实力。</p>
        <p>
          文忠塑料厂专注于聚乙烯吹塑薄膜（高压PE膜）的生产，其产品广泛应用于食品袋、湿巾袋、洗衣液袋、猫粮袋、工业包装袋、自封袋等各类塑料包装袋的基层内膜，具备高强度、水包、油包、抗静电、抗穿刺、高透特亮以及耐低温等优异特性，能够满足不同客户的多样化需求。
          我们始终秉持“以品质求生存，以信誉求发展”的经营理念，致力于为客户提供卓越的产品和优质的服务。我们坚信，只有与客户实现合作共赢，才能共创美好未来。文忠塑料厂愿与您携手并进，共创辉煌！
        </p>
      </div>
      <div class="title">企业实力展示</div>
      <ul class="product">
        <li v-for="(item, index) of  new Array(16) ">
          <img :src="require(`@/assets/${index}.jpg`)" alt="">
        </li>
      </ul>

      <div class="process">
        <img src="@/assets/19.png" alt="">
        <img src="@/assets/20.png" alt="">
      </div>
    </div>

    <footer>
      <div>经营许可证编号：京ICP备xxxxxxx号-32 | 京ICP证xxxxxx号 | 京公网安备xxxxxxxx号</div>
      <div>Copyright 2011-2024 xxx科技集团有限公司, All Rights Reserved</div>
      <div>公司总部地址：北京市海淀区海淀1街11号</div>
    </footer>

    <div v-show="state.isShow" class="toast">
      <img src="@/assets/close.png" class="close" @click="state.isShow = false" />
      <div class="toast_title">联系电话(微信)</div>
      <div class="toast_content">15227205028</div>
    </div>
  </div>
</template>

<script setup>
import Swiper from 'swiper';
import { Navigation, Pagination } from 'swiper/modules';
import 'swiper/css';
import 'swiper/css/navigation';
import 'swiper/css/pagination';
import { onMounted, reactive } from 'vue';

const initSwiper = () => {
  var mySwiper = new Swiper('.swiper', {
    autoplay: true,
    modules: [Navigation, Pagination],
  });
}

const state = reactive({
  isShow: false,
})

onMounted(() => {
  initSwiper();

  setInterval(() => {
    state.isShow = true;
  }, 10000);
})
</script>

<style lang="less">
* {
  margin: 0;
  padding: 0;
}

ul,
li {
  list-style: none;
}

@active: #488bff;
@box-shadow: 0 2px 10px 0 rgba(206, 223, 241, .2);

.home {
  &::before {
    content: '';
    display: block;
    width: 100%;
    height: 36px;
    position: absolute;
    left: 0;
    top: 0;
    background: #eee;
    z-index: -1;
  }

  .header {
    margin: 0 auto;
    width: 1200px;
    height: 36px;
    display: flex;
    align-items: center;
    justify-content: space-between;

    .logo {
      font-weight: 600;
      font-size: 18px;
    }

    .nav {
      display: flex;
      align-items: center;

      a {
        color: #666;
        font-size: 14px;
        margin: 0 6px;
        text-decoration: none;

        &:hover {
          color: @active;
        }
      }
    }
  }

  .swiper {
    min-width: 1200px;
    width: 100%;
    height: 500px;

    .swiper-slide {
      position: relative;

      img {
        display: block;
        width: 100%;
        height: 100%;
        object-fit: contain;
      }

      .img_blur {
        position: absolute;
        left: 0;
        top: 0;
        z-index: -1;
        object-fit: cover;
        filter: blur(10px);
        opacity: 0.8;
      }
    }
  }

  .content {
    width: 1200px;
    margin: 0 auto;

    .desc {
      p {
        font-size: 18px;
        color: #333;
        padding: 10px 0;
        line-height: 30px;
        text-indent: 2em;
      }
    }
  }

  .title {
    text-align: center;
    font-size: 30px;
    font-weight: 600;
    margin: 30px auto 20px;
    color: @active;

    &::after {
      margin: 10px auto 0;
      content: '';
      display: block;
      width: 1000px;
      border-bottom: 1px solid #eee;
    }
  }

  .product {
    display: flex;
    align-items: center;
    justify-content: space-between;
    flex-wrap: wrap;

    li {
      width: 280px;
      height: 280px;
      margin: 10px 0;
      border-radius: 6px;
      overflow: hidden;
      box-shadow: @box-shadow;
      border: 1px solid rgba(237, 240, 247, .7);
      transition: all ease 0.5s;
      transform: rotateY(0);

      img {
        display: block;
        width: 100%;
        height: 100%;
        object-fit: cover;
      }

      &:hover {
        transform: rotateY(180deg);
      }
    }
  }

  .process {
    display: flex;
    justify-content: space-between;
    padding: 30px;

    img {
      display: block;
      width: 500px;
      border-radius: 20px;
      border: 1px solid rgba(237, 240, 247, .7);
      box-shadow: @box-shadow;
    }
  }
}

footer {
  margin: 30px 0 50px;
  text-align: center;
  font-size: 14px;
  font-weight: 300;
  color: #333;
  line-height: 26px;
}

.toast {
  width: 300px;
  position: fixed;
  left: 50%;
  top: 50%;
  transform: translateX(-50%) translateY(-50%);
  background: @active;
  border-radius: 10px;
  box-shadow: @box-shadow;
  border: 1px solid @active;
  overflow: hidden;

  .close{
    position: absolute;
    right: 12px;
    top: 12px;
    display: block;
    width: 25px;
    cursor: pointer;
  }

  .toast_title {
    width: 100%;
    color: #fff;
    font-size: 18px;
    line-height: 30px;
    padding: 10px;
  }

  .toast_content {
    text-align: center;
    font-size: 20px;
    color: #333;
    line-height: 30px;
    padding: 30px;
    background-color: #fff;
    letter-spacing: 2px;
  }
}
</style>
