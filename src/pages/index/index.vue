<template>
  <div class="uzhuang" @pagescroll="scroll" id="uzhuang" >
    <header>
      <image class="header_img" mode="widthFix" src="http://resource.uzhuang.com/mini_zhu/v1/header.png"></image>
    </header>
    <div class="content" >
      <div class="white">
        <div class="text_center">
          <p>别担心</p>
          <p>请个管家帮您全程监管装修</p>
        </div>
        <div class="icon">

            <div class="card">
            <span class="icon-2 svg" @click="changeColor(1)" :class="{'color_blue':color_bol==1}"></span>
             <span :class="{'color_grey':color_bol!==1}">帮您省钱</span>
            </div>
             <div class="card" >
            <span class="icon-1 svg" @click="changeColor(2)" :class="{'color_blue':color_bol==2}"></span>
             <span :class="{'color_grey':color_bol!==2}"> 帮您省力 </span>
             </div>
              <div class="card" >
              <span class="icon-4 svg" @click="changeColor(3)" :class="{'color_blue':color_bol==3}">
              <span class="path1"></span>
              <span class="path2"></span>
            </span>
              <span :class="{'color_grey':color_bol!==3}">帮您省心</span>
              </div>
              <div class="card" >
             <span class="icon-3 svg" @click="changeColor(4)" :class="{'color_blue':color_bol==4}"></span>

              <span :class="{'color_grey':color_bol!==4}">帮您省时</span>
              </div>
            <!-- <image class="svg color_blue " :class="{'color_blue':color_bol}"  :src=val @click="changeColor(i)"></image> -->
            <!-- <span>{{list_tips[i]}}</span> -->
        </div>
        <div class="dialog">
          <div class="shet" :class="classObject"></div>

          <p v-if="color_bol==1">审核图纸有效性、审核材料单价、审核工程量、审核报价单增漏项，从开始就帮您省钱</p>
          <p v-if="color_bol==2">25次上门服务、198个施工节点验收、108项材料验收、20个服务节点日志</p>
          <p v-if="color_bol==3">不用花精力查攻略、不用记挂代办事项、不用跟工长扯皮周旋、不用担心环保污染</p>
          <p v-if="color_bol==4">不用三天两头请假去盯工地，管家会“事无巨细”帮您打理</p>

        </div>
      </div>

      <div class="white">
        <div class="text_center">
          <p>选择适合您的管家服务</p>
          <p>三大精选管家服务套餐，帮您解决装修痛点</p>
        </div>
        <div class="type_btn">
          <button class="btn"  v-for="(val,i) in list_btn" :key="i" :class="{primary:btn_bol==i}"  @tap="changeBtn(i)">{{val}}</button>
             <div class="sanjiao" :class="btnObject"></div>  


          <!-- <button class="btn" hover-class="primary">轻奢款1688元</button>
          <button class="btn" hover-class="primary">尊享款3588元</button> -->
        </div>
        <div class="text_center">
          <p  class="primary">{{rate}}次上门+2次环保检测</p>
          <div class="compt">
          <span>省心指数</span>
           <image class="icon imgs"  style="padding-top:10rpx" v-for="(val,i) in num" :key="i" mode="widthFix" src="http://resource.uzhuang.com/mini_zhu/v1/xin.png"></image>
          </div>
        </div>
        <div class="img_large">
          <image class="img imgs" mode="widthFix"  src="http://resource.uzhuang.com/mini_zhu/v1/jichu.png" v-show="btn_bol==0"></image>
          <image class="img imgs" mode="widthFix" src="http://resource.uzhuang.com/mini_zhu/v1/qingshe.png" v-show="btn_bol==1"></image>
          <image class="img imgs" mode="widthFix" src="http://resource.uzhuang.com/mini_zhu/v1/zunxiang.png" v-show="btn_bol==2"></image>
          <div class="tips">
              <image class="icon " mode="widthFix"  src="http://resource.uzhuang.com/mini_zhu/v1/fuwu.png"></image>
              <span>上门服务</span>
          </div>
        </div>
      </div>
      <div class="white">
        <div class="compt_big">
                <div  class="text_header">
                    <p>没时间去工地，手机实时查看最新进度</p>
                    <p>足不出户，轻松完成验收、评价、打分</p>
                </div>
                <div class="image_one">
                <image  class="icon imgs" mode="widthFix"  src="http://resource.uzhuang.com/mini_zhu/v1/shouji.png"  ></image>
                </div>
            </div>
      </div>
      

      <div class="white_picker" >
        <div class="compt_big" >
                <div  class="text_header">
                    <p>100个用户成为100个朋友</p>
                    <p>99.8%的好评率，用心去服务才能获得用户的认可</p>
                </div>
                    <view class="swiper_wrap" >
                            <swiper   :autoplay="bol"  :circular="bol"   @tap="choseCoupon"  :style="[{ height: swiperH}]"  interval="3000" duration="500"  indicator-active-color="#2D8CF0"  >
                                  <block v-for="(item, index) in dataImg" :index="index" :key="index">
                                    <swiper-item>
                                        <!-- <div class="image_two"> -->
                                      <image :src="item"   mode="widthFix" class="imgs"  style="300px" @load="imgHeight" />
                                        <!-- </div> -->
                                      </swiper-item>
                                  </block>
                                      </swiper>
                                </view>
            </div>
      </div>
         <div class="white">
        <div class="compt_big">
                <div  class="text_header">
                    <p>上市公司背书+中装协深度战略合作</p>
                    <p>中国建筑装饰协会授予“互联网管家服务研究中心”</p>
                </div>
                 <div class="image_one" style="margin-top:40rpx;">
                <image    mode="widthFix" class="imgs"    src="http://resource.uzhuang.com/mini_zhu/v1/rongyu.png"   ></image>
                 </div>
            </div>
      </div>
      <div class="white" > 
           <div class="image_one">
           <image mode="widthFix" class="imgs" src="http://resource.uzhuang.com/mini_zhu/v1/tuihuan.png" ></image>
           </div>
      </div>
      <div class="white" style="padding-top:40rpx;" id="submit">
        <div class="conter">
           <div class="input">
              <!-- <view class="section__title">{{customer_name}}</view> -->
             <input type="text"   :value="customer_name" @input="inputName" maxlength="10" placeholder="请输入您的姓名"  /> 
             
           </div>
           <div class="input">
             <input type="number" :value="customer_tel" @input="inputTel" placeholder="请输入您的手机号"/> 
           </div>    

           <div class="input">
             <picker @change="bindCityChange" :value="city_id" :range="city_list"  range-key="name">
               <image mode="widthFix" class="imgs icon" src="http://resource.uzhuang.com/mini_zhu/v1/xiajiantou20.png"></image>
           <view class="picker">
            {{currentCity}}
           </view>
            </picker>
           </div>
           <div class="input">
          <picker @change="bindMealChange" circular :value="sever_id" :range="meal_list"  range-key="meal">
             <image mode="widthFix" class="imgs icon" src="http://resource.uzhuang.com/mini_zhu/v1/xiajiantou20.png"></image>
           <view class="picker">
            {{currentMeal}}
           </view>
            </picker>
           </div>
        </div>
        <button size="string" class="btn_submit" @tap="submitGo" >立即预约您的专属管家</button>
      </div>
      <div class="btn_large" v-if="btn_show" @click="scrollBottom">
        <span>
           预约专属管家
           </span>
        <!-- <button class="btn_large">预约专属管家</button>   -->
      </div>
      <div>
    
  </div>

    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      list_btn: ["基础款1088元", "轻奢款1688元", "尊享款3588元"],
      color_bol: true,
      btn_bol: false,
      list_tips: ["帮您省钱", "帮您省力", "帮您省心", "帮您省时"],
      bol:true,
      images: {},
      move: "move1",
      movebanner: "movebanner",
      scrollTop: "",
      btn_show: true,
      num: 3,
      customer_name: "",
      customer_tel: "",
      rate: 5,
      swiperH: "",
      sever_id: "4",
      dataImg: [
        "swiper1",
        "swiper2",
        "swiper3",
        "swiper4",
        "swiper5",
        "swiper6",
        "swiper7",
        "swiper8",
        "swiper9",
        "swiper10",
        "swiper11",
        "swiper12",
        "swiper13",
        "swiper14",
        "swiper15",
        "swiper16",
        "swiper17"
      ],
      city_list: [
        { lid: "3360", pid: "0", name: "北京市" },
        { lid: "3362", pid: "0", name: "天津市" },
        { lid: "328", pid: "0", name: "深圳市" },
        { lid: "326", pid: "0", name: "广州市" },
        { lid: "3361", pid: "0", name: "上海市" },
        { lid: "435", pid: "0", name: "西安市" },
        { lid: "213", pid: "0", name: "杭州市" },
        { lid: "200", pid: "0", name: "南京市" },
        { lid: "295", pid: "0", name: "武汉市" },
        { lid: "278", pid: "0", name: "郑州市" },
        { lid: "382", pid: "0", name: "成都市" },
        { lid: "262", pid: "0", name: "青岛市" },
        { lid: "165", pid: "0", name: "大连市" },
        { lid: "336", pid: "0", name: "惠州市" },
        { lid: "204", pid: "0", name: "苏州市" },
        { lid: "215", pid: "0", name: "温州市" },
        { lid: "214", pid: "0", name: "宁波市" },
        { lid: "205", pid: "0", name: "南通市" },
      ],
      meal_list: [
        { val: 4, meal: "基础款1088元" },
        { val: 2, meal: "轻奢款1688元" },
        { val: 1, meal: "尊享款3588元" }
      ],
      city_id: 3360,
      currentCity: "北京市",
      currentMeal: "基础款1088元"
      // classObject: {
      //   // active: true,
      //   move: true
      // }
    };
  },

  computed: {
    classObject: {
      get() {
        return this.move || "";
      },
      set() {}
    },
    btnObject: {
      get() {
        return this.movebanner || "";
      },
      set() {}
    }
  },
  onLoad() {
    const _this = this;
    // wx.request({
    //   url: "http://guanjia.uzhuang.com/index.php?r=order/get-area", //仅为示例，并非真实的接口地址
    //   header: {
    //     "content-type": "application/json" // 默认值
    //   },
    //   success: function(res) {
    //     _this.city_list = res.data.data;
    //     console.log(res.data);
    //   },
    //   fail: function() {
      //     _this.getLocation();
    //   }
    // });
        _this.getLocation();
  },
  onShareAppMessage: function (ops) {
   if (ops.from === 'button') {
     // 来自页面内转发按钮
     console.log(ops.target)
   }
   return {
     title: '不懂装修，就找装修管家',
     path: '/pages/index/main',
     success: function (res) {
       // 转发成功
       console.log("转发成功:" + JSON.stringify(res));

     },
     fail: function (res) {
       // 转发失败
       console.log("转发失败:" + JSON.stringify(res));
     }
   }

 },
  beforeMount() {
   
  },
  onPageScroll(e) {
    
    this.scrollTop = e.scrollTop;
    if (e.scrollTop >= 1400) {
      this.btn_show = false;
    } else {
      this.btn_show = true;
    }
  },

  methods: {

    getLocation: function() {
      var page = this;
      wx.getLocation({
        type: "wgs84", //默认为 wgs84 返回 gps 坐标，gcj02 返回可用于 wx.openLocation 的坐标
        success: function(res) {
          // success
          var longitude = res.longitude;
          var latitude = res.latitude;
          page.loadCity(longitude, latitude);
        }
      });

    },
    loadCity: function(longitude, latitude) {
      var page = this;
      wx.request({
        url:
          "https://api.map.baidu.com/geocoder/v2/?ak=PpF3imTkQbf7LVo4KK64V1ioBY9Ovmwl&location=" +
          latitude +
          "," +
          longitude +
          "&output=json",
        data: {},
        header: {
          "Content-Type": "application/json"
        },
        success: function(res) {
          var city = res.data.result.addressComponent.city;
          console.log(page);

          page.city_list.forEach(el => {
            if (el.name == city) {
              page.city_id = el.lid;
              page.currentCity = city;
            }
          });
        },
        fail: function() {
          // page.setData({ currentCity: "获取定位失败" });
        }
      });
    },
    imgHeight(e) {
      var winWid = wx.getSystemInfoSync().windowWidth; //获取当前屏幕的宽度
      var imgh = e.mp.detail.height; //图片高度
      var imgw = e.mp.detail.width; //图片宽度
      this.swiperH = winWid * imgh / imgw - 20 + "px"; //等比设置swiper的高度。 即 屏幕宽度 / swiper高度 = 图片宽度 / 图片高度  ==》swiper高度 = 屏幕宽度 * 图片高度 / 图片宽度
      // this.swiperH=imgh+"px";
      console.log(winWid, imgh, imgw);
      //  this.styleObject.height=swiperH;
      // console.log(this,e, "style");
    },
    inputTel(e) {
      this.customer_tel = e.mp.detail.value;
    },
    inputName(e) {
      this.customer_name = e.mp.detail.value;
    },
    submitfor() {},
    changeColor(i) {
      this.color_bol = i;
      this.move = "move" + i;
    },
    changeBtn(i) {
      this.num = i + 3;
      this.btn_bol = i;
      this.movebanner="movebanner"+i;
      switch (i) {
        case 0:
          this.rate = 5;
          break;
        case 1:
          this.rate = 13;
          break;

        case 2:
          this.rate = 23;
          break;

        default:
          this.rate = 5;
          break;
      }
    },
    bindCityChange(e) {

      this.city_id = this.city_list[+e.target.value].lid;
      this.currentCity = this.city_list[+e.target.value].name;
      console.log(this.city_id, this.currentCity);
    },
    bindMealChange(e) {
      this.currentMeal = this.meal_list[+e.target.value].meal;
      console.log(e.target.value);
      this.sever_id = this.meal_list[+e.target.value].val;
      console.log(this.currentMeal, this.sever_id);
    },
    submitGo() {
      if (!this.customer_name) {
        wx.showToast({
          title: "请填写姓名",
          icon: "none",
          duration: 1000
        });
        return;
      }
      if(!/^[\u4e00-\u9fa5]{2,10}$/.test(this.customer_name)){
         wx.showToast({
          title: "请您输入中文姓名",
          icon: "none",
          duration: 1000
        });
        return;
      }

      if (!this.customer_tel) {
        wx.showToast({
          title: "请填写电话",
          icon: "none",
          duration: 1000
        });
        return;
      }
      if (!(/^1[34578]\d{9}$/.test(this.customer_tel))) {
         wx.showToast({
          title: "您输入的手机号格式不正确",
          icon: "none",
          duration: 1000
        });
        return;
      }
      const _this = this;
      wx.request({
        url: "https://gj.uzhuang.com/index.php?r=order/sign-up", //仅为示例，并非真实的接口地址
        header: {
          "content-type": "application/x-www-form-urlencoded" // 默认值
        },
        method: "POST",
        data: {
          server_id: _this.sever_id + "",
          city_id: _this.city_id,
          customer_tel: _this.customer_tel,
          customer_name: _this.customer_name
        },

        success: function(res) {
          if (res.code==0) {
            wx.showToast({
              title: "添加成功",
              icon: "success",
              duration: 1000
            });
            _this.customer_tel="";
            _this.customer_name="";

            
          } else {
               wx.showToast({
              title: "添加失败",
              icon: "none",
              duration: 1000
            });
          }
          // alert("注册成功")
          // _this.city_list = res.data.data;
          // console.log(res.data);
        },
        fail: function(res) {
          wx.showToast({
            title: "添加失败",
            icon: "none",
            duration: 1000
          });
        }
      });
    },
    scrollBottom() {
      wx
        .createSelectorQuery()
        .select("#uzhuang")
        .boundingClientRect(function(rect) {
          // 使页面滚动到底部
          wx.pageScrollTo({
            scrollTop: 2155
          });
        })
        .exec();
    },
    dataCamp() {
      this.dataImg = this.dataImg.map(
        val => "http://resource.uzhuang.com/mini_zhu/v1/" + val + ".png"
      );
      console.log(this.dataImg);
    }
  },
  created() {

    this.dataCamp();
  }
};
</script>
<style lang="scss">
@import url("../../../dist/static/icon/icon/style.wxss");
@media screen and (min-width: 320px) {
  page {
    font-size: 14px;
  }
}

@media screen and (min-width: 360px) {
  page {
    font-size: 16px;
  }
}

@media screen and (min-width: 400px) {
  page {
    font-size: 18px;
  }
}

@media screen and (min-width: 440px) {
  page {
    font-size: 20px;
  }
}

@media screen and (min-width: 480px) {
  page {
    font-size: 22px;
  }
}

@media screen and (min-width: 640px) {
  page {
    font-size: 25px;
  }
}

page {
  // font-family: "华文细黑", Courier New, Courier, monospace;
  // font-family: 'Courier New', Courier, monospace;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  background-color: #f1f1f1;
  font-size: 30rpx;
  height: 100%;
}

.btn_large {
  position: fixed;
  // top: 0rpx;
  bottom: 0%;
  display: flex;
  align-items: center;
  width: 100%;
  height: 100rpx;
  background: #5d78ff;
  opacity: 0.95;
  justify-content: center;
  text-align: center;
  line-height: 1.5;
  color: #f1f1f1;
}
.imgs {
  width: 100%;
  height: 100%;
}
.color_blue {
  fill: #5d78ff;
  color: #5d78ff;
  border: 1px solid #5d78ff !important;
}

.color_grey {
  color: #999999;
}
.move1 {
  left: 7% !important;
}
.move2 {
  left: 32% !important;
}
.move3 {
  left: 60% !important;
}
.move4 {
  left: 87% !important;
}
.movebanner0 {
  left: 13% !important;
}
.movebanner1 {
  left: 46% !important;
}
.movebanner2 {
  left: 80% !important;
}
.movebanner3 {
  left: 80% !important;
}

.image_one {
  display: flex;
  justify-content: center;
  margin: 20rpx;
  //  margin-top: 20px;
}
.image_two {
  display: flex;
  justify-content: center;
  margin: 20rpx;
}
.white {
  background: rgb(254, 254, 254);
  margin: 3%;
  opacity: 0.9;
  border-radius: 5px;
  overflow: hidden;
  box-sizing: border-box;
}
.white_picker {
  background: rgb(254, 254, 254);
  margin: 3%;
  opacity: 0.9;
  border-radius: 5px;
  overflow: scroll;
  box-sizing: border-box;
  height: 100%;
  .swiper_wrap {
    height: 100%;
    box-sizing: border-box;
    padding: 20px;
    padding-top: 10px;
  }
}

.uzhuang {
  // background-image: url("../../../static/img/header.png");
  width: 100%;
  height: 100%;
  background: #f1f1f1;
  .header_img {
    width: 100%;
    height: 708rpx;
  }
  .content {
    position: absolute;
    top: 475rpx;
    // background: #f1f1f1;
    .compt_big {
      width: 100%;
      height: 100%;
      // display: flex;
      // // justify-content: center;
      // align-items: center;
      .text_header {
        padding-top: 40rpx;
        display: block;
        text-align: center;
        margin-bottom: 30rpx;
      }
      .icon {
        margin: 0 auto;
      }
    }
    .text_center {
      padding-top: 60rpx;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      vertical-align: middle;
      .primary {
        color: #5d78ff;
      }
      .compt {
        font-size: 14px;
        display: flex;
        justify-content: center;
        align-items: center;
        .icon {
          width: 25rpx;
          height: 25rpx;
          margin-left: 10rpx;
        }
      }
      p {
        // font-size: 29rpx;
        // font-weight:bold;
        line-height: 1.5;
      }
    }

    .icon {
      display: flex;
      justify-content: space-around;
      border-radius: 20%;
      .card {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: space-around;
        padding: 50rpx 0px 24px 0rpx;
        // box-sizing: border-box;
        //   padding:  50px,0,24px,0px;

        span {
          font-size: 24rpx;
          // color: #999999;
          padding-top: 50rpx;
        }
        .svg {
          // position: absol;
          // text-align:left;
          display: block;
          // width: 80rpx;
          // height: 80rpx;
          // margin: 20rpx;
          padding: 20rpx;
          border: 1px solid #e4e4e4;
          border-radius: 50%;
        }
      }
    }

    .dialog {
      position: relative;
      margin: 30rpx;
      padding: 20rpx;
      box-sizing: border-box;
      border-radius: 2px;
      background: #f7f7f7;
      .shet {
        margin: 0px;
        padding: 0px;
        width: 0;
        height: 0;
        position: absolute;
        left: 5%;
        top: -15px;
        margin: 0px;
        border-width: 10px;
        border-style: solid;
        border-color: transparent transparent #f7f7f7 transparent;
      }
      p {
        // background: #f7f7f7;
        color: #666666;
        //   padding: 10px;
        line-height: 1.5;
        font-size: 28rpx;
      }
    }

    .type_btn {
      margin: 24rpx;
      margin-bottom: 0px;
      margin-top: 25px;
      display: flex;
      justify-content: space-between;
      position: relative;
      //   font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;

      .btn {
        display: flex;
        align-items: center;
        font-size: 25rpx;
        line-height: 1.5;
        height: 62rpx;
       
      }
       .sanjiao {
          margin: 0px;
          padding: 0px;
          width: 0px;
          height: 0px;
          // background: red;
          position: absolute;
          left: 13%;
          top: 60rpx;
          margin: 0px;
          border-width: 13rpx;
          border-style: solid;
          border-color:  #657FFF transparent transparent  transparent;
        }
      .primary {
        background: #657FFF;
        color: #ffffff;
      }
    }
    .img_large {
      margin: 30rpx 24px 60rpx;
      position: relative;
      display: flex;
      // align-items: center;
      justify-content: center;
      // float: right;
      .img {
        //    display: flex;
        //    align-items: center;
      }
      .tips {
        display: flex;
        position: absolute;
        right: 0px;
        top: 495rpx;
        align-items: center;
        .icon {
          width: 10px;
          height: 10px;
        }
        span {
          font-size: 10px;
          color: #999999;
        }
      }
    }
    .input {
      border: 1px solid #dddddd;
      border-radius: 5px;
      margin: 30rpx;
      padding: 15rpx;
      .text {
      }
      .icon {
        float: right;
        vertical-align: middle;
        padding-top: 9rpx;
        width: 15px;
        height: 20px;
      }
    }
    .btn_submit {
      margin: 20px;
      background: #5d78ff;
      color: white;
    }
  }
}
</style>


