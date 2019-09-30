# 铝镁合金
铝镁合金小程序商城
<!--index.wxml-->
<view style="padding-bottom:100rpx;display:{{now=='index'?'':'none'}};font-family:Microsoft YaHei">
  <scroll-view scroll-y="{{loadfinish}}">
    <view wx:for="{{compose.content}}" wx:for-item="i" wx:for-index="index">
      <!--图片-->
      <view wx:if="{{i.type=='image'}}" class="flex-wrp" style="flex-direction:column">
        <view wx:if="{{i.is_show_title=='1'}}" style="padding-top:12rpx;padding-bottom:12rpx;">
          <text style="font-size:0.8rem;margin-left:12rpx;color:#000000">{{i.title}}</text>
        </view>
        <!--单排-->
        <block wx:if="{{i.paiban=='1'}}">
          <block wx:for="{{i.item2}}" wx:for-item="j">
            <block wx:for="{{j}}" wx:for-item="m">
              <image style="padding:0px;display: flex;width:100%;" mode="widthFix" src="{{yunIp+m.pimage2}}" class="flex-item" bindtap="imageClick" data-type='{{m.type}}' data-word='{{m.word}}'></image>
            </block>
          </block>
        </block>
        <!--双排-->
        <block wx:if="{{i.paiban=='2'}}">
          <block wx:for="{{i.item2}}" wx:for-item="j">
            <view class="flex-wrp" style="flex-direction:row;width:100%;display: flex;">
              <block wx:for="{{j}}" wx:for-item="m">
                <image style="padding:0px;width:50%;" mode="widthFix" src="{{yunIp+m.pimage2}}" class="flex-item" bindtap="imageClick" data-type='{{m.type}}' data-word='{{m.word}}'></image>
              </block>
            </view>
          </block>
        </block>
        <!--三排-->
        <block wx:if="{{i.paiban=='3'}}">
          <block wx:for="{{i.item2}}" wx:for-item="j">
            <view class="flex-wrp" style="flex-direction:row;width:100%;display: flex;">
              <block wx:for="{{j}}" wx:for-item="m">
                <image style="padding:0px;width:33.33%;" mode="widthFix" src="{{yunIp+m.pimage2}}" class="flex-item" bindtap="imageClick" data-type='{{m.type}}' data-word='{{m.word}}'></image>
                <!-- <text class="user-motto"></text>  -->
              </block>
            </view>
          </block>
        </block>
        <!--四排-->
        <block wx:if="{{i.paiban=='4'}}">
          <block wx:for="{{i.item2}}" wx:for-item="j">
            <view class="flex-wrp" style="flex-direction:row;width:100%;display: flex;background:#ff0000">
              <view style="flex-direction:row;width:49.99%;display: flex;">
                <block wx:for="{{j}}" wx:for-item="m" wx:for-index="index">
                  <image wx:if="{{index==0||index==1}}" style="padding:0px;width:51%;" src="{{yunIp+m.pimage2}}" bindtap="imageClick" data-type='{{m.type}}' data-word='{{m.word}}' mode="widthFix"></image>
                  <!-- <text class="user-motto"></text>  -->
                </block>
              </view>
               <view style="flex-direction:row;width:49.99%;display: flex;">
                <block wx:for="{{j}}" wx:for-item="m" wx:for-index="index">
                  <image wx:if="{{index==2||index==3}}" style="padding:0px;width:51%;" src="{{yunIp+m.pimage2}}" bindtap="imageClick" data-type='{{m.type}}' data-word='{{m.word}}' mode="widthFix"></image>
                  <!-- <text class="user-motto"></text>  -->
                </block>
              </view>
            </view>

          </block>
        </block>
      </view>
      <!--轮播-->
      <view wx:elif="{{i.type=='swiper'}}">
        <view wx:if="{{i.is_show_title=='1'}}" style="padding-top:12prx;padding-bottom:12prx;">
          <text style="font-size:0.8rem;margin-left:12rpx;color:#000000;display:flex">{{i.title}}</text>
        </view>
        <swiper style="height:{{heights[index]}}px;" circular="true" indicator-dots="{{i.point==1?true:false}}" autoplay="{{i.is_autoplay==1?true:false}}" interval="{{i.autoplay}}" duration="{{i.speed}}">
          <block wx:for="{{i.item}}" wx:for-item="j">
            <swiper-item>
              <image src="{{yunIp+j.pimage2}}" class="slide-image" style="padding:0px;margin:0px;width:100%;height:100%;display:flex" bindtap="swipeClick" data-type='{{j.type}}' data-word='{{j.word}}' />
            </swiper-item>
          </block>
        </swiper>
      </view>
      <!--商品-->
      <view wx:elif="{{i.type=='product'}}">
        <view wx:if="{{i.paiban=='1'}}" style="background:#f0eff5;width:100%;height:10rpx"></view>
        <view wx:if="{{i.is_show_title=='1'}}" style="padding-top:12rpx;padding-bottom:12rpx;">
          <text style="font-size:0.8rem;margin-left:12rpx;color:#000000">{{i.title}}</text>
        </view>
        <!--单排-->
        <block wx:if="{{i.paiban=='1'}}">
          <block wx:for="{{i.item2}}" wx:for-item="j">
            <view class="flex-wrp" style="flex-direction:row;width:100%;display:flex;">
              <block wx:for="{{j}}" wx:for-item="m">
                <view class="flex-wrp" style="flex-direction:column;width:100%;display:flex;" bindtap="pro_click" data-pid='{{m.pid}}'>

                  <image style="padding:0px;display: flex;width:100%;margin-bottom:12rpx" mode="widthFix" src="{{yunIp+m.pimage2}}" class="flex-item"></image>
                  <text class="text_limite" style="color:#000000;padding-left:12rpx;margin-top:12rpx;padding-right:12rpx;font-size:0.8rem">{{m.name}}</text>
                  <view class="flex-wrp" style="display:flex;flex-direction:row;width:100%;justify-content:space-between;align-items:center;margin-bottom:12rpx">
                    <view class="flex-wrp" style="display:flex;flex-direction:row">
                      <block wx:if="{{m.sale_price==null||m.sale_price==''}}">
                        <text class="flex-item" style="color:#ff4020;padding-left:12rpx;margin-top:12rpx;padding-right:12rpx;font-size:1rem">¥{{m.price}}</text>
                      </block>
                      <block wx:elif="{{m.sale_price!=null&&m.sale_price!=''}}">
                        <text class="flex-item" style="color:#ff4020;padding-left:12rpx;margin-top:12rpx;padding-right:12rpx;font-size:1rem">¥{{m.sale_price[0]}}</text>
                        <text class="flex-item" style="margin-left:20rpx;font-size:0.8rem;">¥{{m.price}}fd</text>
                      </block>
                    </view>
                    <text class="flex-item" style="padding-right:12rpx;font-size:0.8rem;">销量{{m.sale_volume}}件</text>
                  </view>
                </view>
              </block>
            </view>
            <view style="background:#f0eff5;width:100%;height:10rpx"></view>
          </block>
        </block>
        <!--双排-->
        <block wx:if="{{i.paiban=='2'}}">
          <block wx:for="{{i.item2}}" wx:for-item="j" wx:for-index="index">
            <view wx:if="{{index==0}}" style="display:flex">
              <view style="background:#f0eff5;width:100%;height:10rpx"></view>
            </view>
            <view class="flex-wrp" style="flex-direction:row;width:100%;display: flex;">
              <block wx:for="{{j}}" wx:for-item="m">
                <view class="flex-wrp" style="flex-direction:column;width:50%;display: flex;border-right: 5rpx solid #f0eff5;border-left: 5rpx solid #f0eff5" bindtap="pro_click" data-pid='{{m.pid}}'>
                  <image style="padding:0px;display: flex;width:100%;margin-bottom:12rpx" mode="widthFix" src="{{yunIp+m.pimage2}}" class="flex-item"></image>
                  <text class="text_limite" style="color:#000000;padding-left:12rpx;margin-top:12rpx;padding-right:12rpx;font-size:0.7rem">{{m.name}}</text>
                  <view class="flex-wrp" style="display:flex;flex-direction:row;width:100%;justify-content:space-between;align-items:center;margin-bottom:12rpx">
                    <view class="flex-wrp" style="display:flex;flex-direction:row">
                      <block wx:if="{{m.sale_price==null||m.sale_price==''}}">
                        <text class="flex-item" style="color:#ff4020;padding-left:12rpx;margin-top:12rpx;padding-right:12rpx;font-size:0.8rem">¥{{m.price}}</text>
                      </block>
                      <block wx:elif="{{m.sale_price!=null&&m.sale_price!=''}}">
                        <text class="flex-item" style="color:#ff4020;padding-left:12rpx;margin-top:12rpx;padding-right:12rpx;font-size:0.8rem">¥{{m.sale_price[0]}}</text>
                        <text class="flex-item" style="margin-left:17rpx;font-size:0.7rem">¥{{m.price}}fd</text>
                      </block>
                    </view>
                    <text class="flex-item" style="padding-right:12rpx;font-size:0.7rem;">销量{{m.sale_volume}}件</text>
                  </view>
                </view>
              </block>
            </view>
            <view style="background:#f0eff5;width:100%;height:10rpx"></view>
          </block>
        </block>
        <!--三排-->
        <block wx:if="{{i.paiban=='3'}}">
          <block wx:for="{{i.item2}}" wx:for-item="j" wx:for-index="index">
            <view wx:if="{{index==0}}" style="display:flex">
              <view style="background:#f0eff5;width:100%;height:10rpx"></view>
            </view>
            <view class="flex-wrp" style="flex-direction:row;width:100%;display: flex;">
              <block wx:for="{{j}}" wx:for-item="m">
                <view class="flex-wrp" style="flex-direction:column;width:33.33%;display: flex;border-right: 5rpx solid #f0eff5;border-left: 5rpx solid #f0eff5" bindtap="pro_click" data-pid='{{m.pid}}'>
                  <image style="padding:0px;display: flex;width:100%;margin-bottom:12rpx" mode="widthFix" src="{{yunIp+m.pimage2}}" class="flex-item"></image>
                  <text class="text_limite" style="color:#000000;padding-left:12rpx;margin-top:12rpx;padding-right:12rpx;font-size:0.6rem">{{m.name}}</text>
                  <view class="flex-wrp" style="display:flex;flex-direction:row;width:100%;justify-content:space-between;align-items:center;margin-bottom:12rpx">
                    <view class="flex-wrp" style="flex-direction:row;">
                      <block wx:if="{{m.sale_price==null||m.sale_price==''}}">
                        <text class="flex-item" style="color:#ff4020;padding-left:12rpx;margin-top:12rpx;padding-right:12rpx;font-size:0.8rem">¥{{m.price}}</text>
                      </block>
                      <block wx:elif="{{m.sale_price!=null&&m.sale_price!=''}}">
                        <text class="flex-item" style="color:#ff4020;padding-left:12rpx;margin-top:12rpx;padding-right:12rpx;font-size:0.8rem">¥{{m.sale_price[0]}}</text>
                        <text class="flex-item" style="margin-left:14rpx;font-size:0.6rem">¥{{m.price}}fd</text>
                      </block>
                    </view>
                    <text class="flex-item" style="padding-right:12rpx;font-size:0.6rem;">销量{{m.sale_volume}}件</text>
                  </view>
                </view>
              </block>
            </view>
            <view style="background:#f0eff5;width:100%;height:10rpx"></view>
          </block>
        </block>


      </view>
      <!--优惠券-->
      <view wx:elif="{{i.type=='coupon'}}" style="margin-left:20rpx;margin-right:20rpx;margin-top:20rpx">
        <view wx:if="{{i.is_show_title=='1'}}" style="padding-top:12prx;padding-bottom:12prx;">
          <text style="font-size:0.8rem;margin-left:12rpx;color:#000000">{{i.title}}</text>
        </view>
        <!--单排-->
        <block wx:if="{{i.paiban=='1'}}">
          <block wx:for="{{i.item2}}" wx:for-item="j">
            <view class="flex-wrp" style="flex-direction:row;width:100%;display: flex;margin-bottom:10rpx">
              <block wx:for="{{j}}" wx:for-item="m">
                <view style="background-image:url('../../images/youhui.png') ;width:100%;height:384rpx;display: flex;flex-direction:row">
                  <view style="width:58%;height:100%;display: flex;align-items: center;justify-content: center;">
                    <text class="text_limite" style="font-size:1.8rem;color:#ffffff">{{m.pname}}</text>
                  </view>
                  <view style="width:42%;height:100%;display: flex;align-items: center;justify-content: center;">
                    <text wx:if="{{m.ptype=='1'}}" class="user-motto" style="font-size:1.8rem;color:#ffffff">¥{{m.ptype_value}}</text>
                    <text wx:if="{{m.ptype=='2'}}" class="user-motto" style="font-size:1.8rem;color:#ffffff">{{m.ptype_value}}折</text>
                  </view>
                </view>
              </block>
            </view>
          </block>
        </block>

        <!--双排-->
        <block wx:if="{{i.paiban=='2'}}">
          <block wx:for="{{i.item2}}" wx:for-item="j">
            <view class="flex-wrp" style="flex-direction:row;width:100%;display: flex;margin-bottom:10rpx;justify-content:space-between">
              <block wx:for="{{j}}" wx:for-item="m">
                <view style="background-image:url('../../images/youhui2.png') ;width:49.5%;height:192rpx;display: flex;flex-direction:row">
                  <view style="width:58%;height:100%;display: flex;align-items: center;justify-content: center;">
                    <text class="text_limite" style="font-size:1.2rem;color:#ffffff">{{m.pname}}</text>
                  </view>
                  <view style="width:42%;height:100%;display: flex;align-items: center;justify-content: center;">
                    <text wx:if="{{m.ptype=='1'}}" class="user-motto" style="font-size:1.2rem;color:#ffffff">¥{{m.ptype_value}}</text>
                    <text wx:if="{{m.ptype=='2'}}" class="user-motto" style="font-size:1.2rem;color:#ffffff">{{m.ptype_value}}折</text>
                  </view>
                </view>
              </block>
            </view>
          </block>
        </block>

        <!--三排-->
        <block wx:if="{{i.paiban=='3'}}">
          <block wx:for="{{i.item2}}" wx:for-item="j">
            <view class="flex-wrp" style="flex-direction:row;width:100%;display: flex;margin-bottom:10rpx;justify-content:space-between">
              <block wx:for="{{j}}" wx:for-item="m">
                <view style="background-image:url('../../images/youhui3.png') ;width:33%;height:128rpx;display: flex;flex-direction:row">
                  <view style="width:58%;height:100%;display: flex;align-items: center;justify-content: center;">
                    <text class="text_limite" style="font-size:0.8rem;color:#ffffff">{{m.pname}}</text>
                  </view>
                  <view style="width:42%;height:100%;display: flex;align-items: center;justify-content: center;">
                    <text wx:if="{{m.ptype=='1'}}" class="user-motto" style="font-size:0.8rem;color:#ffffff">¥{{m.ptype_value}}</text>
                    <text wx:if="{{m.ptype=='2'}}" class="user-motto" style="font-size:0.8rem;color:#ffffff">{{m.ptype_value}}折</text>
                  </view>
                </view>
              </block>
            </view>
          </block>
        </block>



      </view>
      <!--搜索条-->
      <view wx:elif="{{i.type=='search'}}" bindtap="searchClick">
        <view wx:if="{{i.is_show_title=='1'}}" style="padding-top:12prx;padding-bottom:12prx;">
          <text style="font-size:0.8rem;margin-left:12rpx;color:#000000;display:flex">{{i.title}}</text>
        </view>
        <view style="display:flex;align-items: center;justify-content: center;background:#f0eff5">
          <image style="padding:0px;display: flex;width:95%;margin-top:8rpx;margin-bottom:8rpx" mode="widthFix" src="../../images/search_bar.png" class="flex-item"></image>
        </view>
      </view>

    </view>

  </scroll-view>


</view>


<!--classify.wxml-->
<view wx:if="{{now=='classify'}}" style="display:flex;flex-direction:column;padding-bottom:100rpx;font-family:Microsoft YaHei;">
  <view style="display:flex;align-items: center;justify-content: center;background:#f0eff5;" bindtap="searchClick">
    <image style="padding:0px;display: flex;width:95%;margin-top:8rpx;margin-bottom:8rpx" mode="widthFix" src="../../images/search_bar.png" class="flex-item"></image>
  </view>
  <view style="background:#e3e2e7;width:100%;height:3rpx"></view>
  <block wx:if="{{if_has_second}}">
    <view style="display:flex;flex-direction:row;width:100%;background:#ffffff;height:100%;">
      <view style="width:28%;background:#f8f8f8;height:100%">
        <scroll-view style="background:#f8f8f8;height:{{height_classify_scrollview-80}}px;">
          <view wx:for="{{classifyMsg}}" wx:for-item="i" wx:for-index="index">
            <view style="display:flex;flex-direction:column;width:100%;height:110rpx;" bindtap="first_click" data-index="{{index}}">
              <view style="height:107rpx;width:100%;display:flex;background:{{first_bg[index]}};align-items: center;justify-content: center;">
                <text class="text_limite" style="color:#000000;font-size:1rem">{{i.name}}</text>
              </view>
              <view style="background:#cfcfcf;width:100%;height:3rpx"></view>
            </view>
          </view>
        </scroll-view>
      </view>
      <view style="width:3rpx;height:100%;background:#cfcfcf"> </view>
      <scroll-view style="height:{{height_classify_scrollview-80}}px;width:width:72%">
        <view style="display:flex;flex-direction:column;width:100%;" bindtap="second_click" data-index="{{index2}}" data-indexparent="{{index}}">
          <block wx:for="{{classifyMsg}}" wx:for-item="i" wx:for-index="index" style="display:flex;flex-direction:column;">
            <view wx:for="{{i.second}}" wx:for-item="j" wx:for-index="index2" style="width:100%;background:#ffffff;height:100%;display:{{isShow[index]}};" data-index="{{index}}">
              <view style="display:flex;flex-direction:column;width:100%;height:110rpx;">
                <view style="height:107rpx;width:100%;display:flex;background:#ffffff;align-items: center;justify-content: center;flex-direction:column;">
                  <text class="text_limite" style="color:#000000;font-size:1rem;display:flex;">{{j.name}}</text>
                </view>
                <view style="background:#cfcfcf;width:100%;height:3rpx"></view>
              </view>


            </view>
          </block>
        </view>
      </scroll-view>
    </view>
  </block>
  <block wx:elif="{{!if_has_second}}">
    <view style="display:flex;width:100%;background:#ffffff;height:100%">
      <scroll-view style="height:{{height_classify_scrollview-80}}px;">
        <view wx:for="{{classifyMsg}}" wx:for-item="i" wx:for-index="index">
          <view style="display:flex;flex-direction:column;width:100%;height:110rpx;" bindtap="first_click" data-index="{{index}}">
            <view style="height:107rpx;width:100%;display:flex;background:{{first_bg[index]}};align-items: center;justify-content: center;">
              <text class="text_limite" style="color:#000000;font-size:1rem">{{i.name}}</text>
            </view>
            <view style="background:#cfcfcf;width:100%;height:3rpx"></view>
          </view>
        </view>
      </scroll-view>
    </view>
  </block>
</view>

<!--shopcart.wxml-->

<view wx:if="{{now=='shopcart'}}" style="padding-bottom:100rpx;font-family:Microsoft YaHei">
  <view style="background:#d4d4d4;width:100%;height:3rpx;"></view>
  <scroll-view wx:if="{{shopcarList!=null&&shopcarList!=''}}" scroll-y="true" style="padding-bottom:100rpx">
    <view style="display:flex;flex-direction:column;" wx:for="{{shopcarList}}" wx:for-item="j" wx:for-index="index">
      <view style="display:flex;align-items:center;flex-direction:row;background:#fafafa;margin-top:10rpx;margin-bottom:10rpx;padding-top:10rpx;padding-bottom:10rpx">
        <image src="{{itemBg[index]}}" mode="widthFix" style="margin-left:15rpx;width:55rpx;height:55rpx;" bindtap="item_check_click" data-index="{{index}}" data-pid="{{j.pid}}"></image>
        <view style="margin-left:15rpx;width:200rpx;height:200rpx;background:#ffffff;display:flex;justify-content:center;align-items:center">
          <image style="width:200rpx;" mode="widthFix" src="{{ip+j.pic}}" bindtap="goDetail" data-pid="{{j.pid}}"></image>
        </view>
        <view style="display:flex;flex-direction:column;justify-content:space-between;height:180rpx;margin-left:20rpx;margin-right:10rpx;width:100%;">
          <view style="display:flex;flex-direction:column;">
            <text style="font-size:0.8rem" class='text_limite2'>{{j.name}}</text>
            <text style="margin-top:10rpx;font-size:0.7rem">{{j.chooseAttr}}</text>
          </view>
          <view style="display:flex;flex-direction:row;width:100%;justify-content:space-between;align-items:center;" class="flex-wrp">
            <view style="display:flex;flex-direction:row">
              <block wx:if="{{j.sale_price==null||j.sale_price==''}}">
                <text class="flex-item" style="color:#fd5554;font-size:0.8rem">¥{{j.price}}</text>
              </block>
              <block wx:elif="{{j.sale_price!=null&&j.sale_price!=''}}">
                <text class="flex-item" style="color:#fd5554;font-size:0.8rem">¥{{j.sale_price}}</text>
                <text class="flex-item" style="font-size:0.6rem">¥{{j.price}}</text>
              </block>
            </view>
            <view style="display:flex;flex-direction:row;align-items:center;justify-content:center;" class="flex-item">

              <!-- <view class="bg_btn_cut" style="width:57rpx;height:45rpx; background-repeat: no-repeat;background-size: 57rpx 45rpx;" bindtap="cutPnum" data-index="{{index}}"></view>
              <view class="bg_btn_txt" style="width:57rpx;height:45rpxx; background-repeat: no-repeat;background-size: 57rpx 45rpx;display:flex;align-items:center;justify-content:center;"><text>{{j.pnum}}</text></view>
              <view class="bg_btn_add" style="width:57rpx;height:45rpx; background-repeat: no-repeat;background-size: 57rpx 45rpx" bindtap="addPnum" data-index="{{index}}"></view> -->
              <!-- <image src="../../images/detail_minus.png" style="width:80rpx" mode="widthFix" bindtap="cutPnum" data-index="{{index}}"></image>
              <image src="../../images/detail_num.png" style="width:80rpx" mode="widthFix"></image>
              <image src="../../images/detail_add.png" style="width:80rpx" mode="widthFix" bindtap="addPnum" data-index="{{index}}"></image> -->

              <view class="img_cut" bindtap="cutPnum" data-index="{{index}}"></view>
              <view class="img_num">
                <text style="display:flex;font-size:0.8rem">{{j.pnum}}</text>
              </view>
              <view class="img_add" bindtap="addPnum" data-index="{{index}}"></view>
            </view>
          </view>
        </view>
      </view>
    </view>
  </scroll-view>

  <view wx:if="{{shopcarList==null||shopcarList==''}}" style="height:{{height_classify_scrollview-80}}px;width:100%;display:flex;align-items:center;justify-content:center;flex-direction:column">

    <text style="font-size:0.9rem;color:#8F8F8F">购物车空空如也</text>
  </view>
  <view style="position:fixed;bottom:100rpx;width:100%;background:#ffffff;padding-bottom:0rpx;height:100rpx">
    <view style="background:#d4d4d4;width:100%;height:3rpx;"></view>
    <view style="display:flex;flex-direction:row;padding-bottom:0rpx;bottom:0rpx;height:100%">
      <view style="width:40%;height:100rpx; background: #ffffff;display:flex;flex-direction:row;align-items:center;">
        <view style="display:flex;flex-direction:row;align-items:center;" bindtap="allChooseClick">
          <image mode="widthFix" style="margin-left:20rpx;width:35rpx;height:35rpx;" src="{{allCheckedBg}}"></image>
          <text style="color:#2e2e2e;font-size:0.8rem;margin-left:10rpx;">全选</text>
        </view>
        <view style="display:flex;flex-direction:row;align-items:center;" bindtap="delete_pro">
          <image style="margin-left:20rpx;width:35rpx;height:35rpx" src="../../images/search_delete.png"></image>
          <text style="color:#888888;font-size:0.8rem;margin-left:10rpx">删除</text>
        </view>
      </view>
      <view style="width:35%;height:100rpx;display:flex;justify-content:center;align-items:flex-end;flex-direction:column;padding-right:10rpx">
        <view style="flex-direction:row;">
          <text style="color:#fd5554;font-size:0.8rem">合计：</text>
          <text style="color:#fd5554;font-size:0.8rem">¥{{total_price}}</text>
        </view>
        <view>
          <text style="color:#8f8f8f;font-size:0.8rem;">不含运费</text>
        </view>
      </view>
      <view style="width:25%;color: #fff;height:100%; background: #ff4445;display:flex;justify-content:center;align-items:center;" bindtap="gotoConfirm">结算</view>
    </view>

  </view>
</view>


<!--personal.wxml-->
<view wx:if="{{now=='personal'}}" style="padding-bottom:100rpx;font-family:Microsoft YaHei">
  <scroll-view>
    <image src="{{ip+pic}}" mode="widthFix" style="width:100%;display:flex;height:{{height}}px"></image>
    <view wx:if="{{isLogined==true}}" style="display:flex;flex-direction:row;background:#000000;opacity:0.8;padding-top:10rpx;padding-bottom:10rpx;">
      <text style="margin-left:20rpx;color:#ffffff">欢迎光临，</text>
      <text style="color:#ffffff">{{userInfo.nickName}}！</text>
    </view>
    <view wx:elif="{{isLogined!=true&& canIUse}}" style="display:flex;flex-direction:row;background:#000000;opacity:0.8;padding-top:10rpx;padding-bottom:10rpx;">
      <button style="margin-left:20rpx;color:#ffffff;background:#000000;padding:0rpx" open-type="getUserInfo" bindgetuserinfo="getUserInfo">点击此处授权获取昵称</button>
    </view>
    <view style="display:flex;flex-direction:row;width:100%;justify-content:space-between;align-items:center;padding-top:20rpx;padding-bottom:20rpx" bindtap="goOrderList">
      <text style="color:#000000;margin-left:20rpx;font-size:0.9rem"> 我的订单</text>
      <view style="display:flex;flex-direction:row;justify-content:center;align-items:center;">
        <text style="margin-right:20rpx;font-size:0.8rem;color:#c6c7cc">查看全部订单</text>
        <image src="../../images/personal_you.png" mode="widthFix" style="display:flex;width:15rpx;margin-right:20rpx"></image>
      </view>

    </view>
    <view style="background:#d4d4d4;width:100%;height:3rpx;margin-left:20rpx"></view>
    <view class="flex-wrp" style="flex-direction:row;width:100%;display: flex;margin-top:30rpx">
      <view style="padding:0px;width:25%;display:flex;justify-content:center;align-items:center;" class="flex-item" bindtap="gotoNeedPay">
        <image mode="widthFix" src="../../images/personal_unpaid.png" style="width:35%"></image>
      </view>
      <view style="padding:0px;width:25%;display:flex;justify-content:center;align-items:center;" class="flex-item" bindtap="gotoWaitFa">
        <image mode="widthFix" src="../../images/personal_wait.png" style="width:35%"></image>
      </view>
      <view style="padding:0px;width:25%;display:flex;justify-content:center;align-items:center;" class="flex-item" bindtap="gotoWaitRe">
        <image mode="widthFix" src="../../images/personal_waithuo.png" style="width:35%"></image>
      </view>
      <view style="padding:0px;width:25%;display:flex;justify-content:center;align-items:center;" class="flex-item" bindtap="gotoWaitCo">
        <image mode="widthFix" src="../../images/personal_piingjia.png" style="width:35%"></image>
      </view>
    </view>
    <view style="background:#d4d4d4;width:100%;height:3rpx;margin-top:30rpx"></view>
    <view style="background:#f9f9f9;width:100%;height:30rpx;"></view>
    <view style="background:#d4d4d4;width:100%;height:3rpx;"></view>
    <view wx:if="{{distribution.status=='1'}}">
      <view style="display:flex;flex-direction:row;width:100%;justify-content:space-between;align-items:center;padding-top:20rpx;padding-bottom:20rpx" bindtap="goDistribution">
        <view style="display:flex;flex-direction:row;justify-content:center;align-items:center;">
          <image src="../../images/fenxiao.png" mode="widthFix" style="display:flex;width:30rpx;margin-left:20rpx"></image>
          <text style="margin-left:10rpx;font-size:0.9rem;color:#323232;">我的分销</text>
        </view>
        <image src="../../images/personal_you.png" mode="widthFix" style="display:flex;width:15rpx;margin-right:20rpx"></image>

      </view>
      <view style="background:#d4d4d4;width:100%;height:3rpx;margin-left:20rpx"></view>
      <view style="display:flex;flex-direction:row;width:100%;justify-content:space-between;align-items:center;padding-top:20rpx;padding-bottom:20rpx" bindtap="goCommission">
        <view style="display:flex;flex-direction:row;justify-content:center;align-items:center;">
          <image src="../../images/yongjin.png" mode="widthFix" style="display:flex;width:30rpx;margin-left:20rpx"></image>
          <text style="margin-left:10rpx;font-size:0.9rem;color:#323232;">我的佣金</text>
        </view>
        <image src="../../images/personal_you.png" mode="widthFix" style="display:flex;width:15rpx;margin-right:20rpx"></image>

      </view>
      <view style="background:#d4d4d4;width:100%;height:3rpx;margin-left:20rpx"></view>
    </view>
    <view style="display:flex;flex-direction:row;width:100%;justify-content:space-between;align-items:center;padding-top:20rpx;padding-bottom:20rpx" bindtap="goAddress" data-fromwhere="1">
      <view style="display:flex;flex-direction:row;justify-content:center;align-items:center;">
        <image src="../../images/personal_address.png" mode="widthFix" style="display:flex;width:25rpx;margin-left:22rpx"></image>
        <text style="margin-left:10rpx;font-size:0.9rem;color:#323232;">收货地址</text>
      </view>
      <image src="../../images/personal_you.png" mode="widthFix" style="display:flex;width:15rpx;margin-right:20rpx"></image>
    </view>
    <view style="background:#d4d4d4;width:100%;height:3rpx;margin-left:20rpx"></view>
    <view style="position:relative;display:flex;flex-direction:row;width:100%;justify-content:space-between;align-items:center;padding-top:20rpx;padding-bottom:20rpx">
      <view style="display:flex;flex-direction:row;justify-content:center;align-items:center;" bindtap="goCoupon">
        <image src="../../images/talk_personal.png" mode="widthFix" style="display:flex;width:30rpx;margin-left:20rpx"></image>
        <text style="margin-left:10rpx;font-size:0.9rem;color:#323232;">在线客服</text>
      </view>
      <image src="../../images/personal_you.png" mode="widthFix" style="display:flex;width:15rpx;margin-right:20rpx"></image>
      <contact-button type="default-dark" size="27" session-from="weapp" style="position:absolute;top:0rpx;left:0rpx;opacity: 0">
      </contact-button>
      <contact-button type="default-dark" size="27" session-from="weapp" style="position:absolute;bottom:0rpx;left:0rpx;opacity: 0">
      </contact-button>
      <contact-button type="default-dark" size="27" session-from="weapp" style="position:absolute;top:0rpx;right:0rpx;opacity: 0">
      </contact-button>
      <contact-button type="default-dark" size="27" session-from="weapp" style="position:absolute;bottom:0rpx;right:0rpx;opacity: 0">
      </contact-button>
      <contact-button type="default-dark" size="27" session-from="weapp" style="position:absolute;top:0rpx;right:30rpx;opacity: 0">
      </contact-button>
      <contact-button type="default-dark" size="27" session-from="weapp" style="position:absolute;top:0rpx;right:60rpx;opacity: 0">
      </contact-button>
      <contact-button type="default-dark" size="27" session-from="weapp" style="position:absolute;top:0rpx;right:90rpx;opacity: 0">
      </contact-button>
      <contact-button type="default-dark" size="27" session-from="weapp" style="position:absolute;top:0rpx;right:120rpx;opacity: 0">
      </contact-button>
      <contact-button type="default-dark" size="27" session-from="weapp" style="position:absolute;top:0rpx;right:150rpx;opacity: 0">
      </contact-button>
      <contact-button type="default-dark" size="27" session-from="weapp" style="position:absolute;top:0rpx;right:180rpx;opacity: 0">
      </contact-button>

      <contact-button type="default-dark" size="27" session-from="weapp" style="position:absolute;top:0rpx;left:30rpx;opacity: 0">
      </contact-button>
      <contact-button type="default-dark" size="27" session-from="weapp" style="position:absolute;top:0rpx;left:60rpx;opacity: 0">
      </contact-button>
      <contact-button type="default-dark" size="27" session-from="weapp" style="position:absolute;top:0rpx;left:90rpx;opacity: 0">
      </contact-button>
      <contact-button type="default-dark" size="27" session-from="weapp" style="position:absolute;top:0rpx;left:120rpx;opacity: 0">
      </contact-button>
      <contact-button type="default-dark" size="27" session-from="weapp" style="position:absolute;top:0rpx;left:150rpx;opacity: 0">
      </contact-button>
      <contact-button type="default-dark" size="27" session-from="weapp" style="position:absolute;top:0rpx;left:180rpx;opacity: 0">
      </contact-button>

      <contact-button type="default-dark" size="27" session-from="weapp" style="position:absolute;bottom:0rpx;right:30rpx;opacity: 0">
      </contact-button>
      <contact-button type="default-dark" size="27" session-from="weapp" style="position:absolute;bottom:0rpx;right:60rpx;opacity: 0">
      </contact-button>
      <contact-button type="default-dark" size="27" session-from="weapp" style="position:absolute;bottom:0rpx;right:90rpx;opacity: 0">
      </contact-button>
      <contact-button type="default-dark" size="27" session-from="weapp" style="position:absolute;bottom:0rpx;right:120rpx;opacity: 0">
      </contact-button>
      <contact-button type="default-dark" size="27" session-from="weapp" style="position:absolute;bottom:0rpx;right:150rpx;opacity: 0">
      </contact-button>
      <contact-button type="default-dark" size="27" session-from="weapp" style="position:absolute;bottom:0rpx;right:180rpx;opacity: 0">
      </contact-button>

      <contact-button type="default-dark" size="27" session-from="weapp" style="position:absolute;bottom:0rpx;left:30rpx;opacity: 0">
      </contact-button>
      <contact-button type="default-dark" size="27" session-from="weapp" style="position:absolute;bottom:0rpx;left:60rpx;opacity: 0">
      </contact-button>
      <contact-button type="default-dark" size="27" session-from="weapp" style="position:absolute;bottom:0rpx;left:90rpx;opacity: 0">
      </contact-button>
      <contact-button type="default-dark" size="27" session-from="weapp" style="position:absolute;bottom:0rpx;left:120rpx;opacity: 0">
      </contact-button>
      <contact-button type="default-dark" size="27" session-from="weapp" style="position:absolute;bottom:0rpx;left:150rpx;opacity: 0">
      </contact-button>
      <contact-button type="default-dark" size="27" session-from="weapp" style="position:absolute;bottom:0rpx;left:180rpx;opacity: 0">
      </contact-button>

      <contact-button type="default-dark" size="27" session-from="weapp" style="position:absolute;bottom:0rpx;right:210rpx;opacity: 0">
      </contact-button>
      <contact-button type="default-dark" size="27" session-from="weapp" style="position:absolute;bottom:0rpx;right:240rpx;opacity: 0">
      </contact-button>
      <contact-button type="default-dark" size="27" session-from="weapp" style="position:absolute;bottom:0rpx;right:270rpx;opacity: 0">
      </contact-button>
      <contact-button type="default-dark" size="27" session-from="weapp" style="position:absolute;bottom:0rpx;right:300rpx;opacity: 0">
      </contact-button>
      <contact-button type="default-dark" size="27" session-from="weapp" style="position:absolute;bottom:0rpx;right:330rpx;opacity: 0">
      </contact-button>
      <contact-button type="default-dark" size="27" session-from="weapp" style="position:absolute;bottom:0rpx;right:360rpx;opacity: 0">
      </contact-button>

      <contact-button type="default-dark" size="27" session-from="weapp" style="position:absolute;bottom:0rpx;left:210rpx;opacity: 0">
      </contact-button>
      <contact-button type="default-dark" size="27" session-from="weapp" style="position:absolute;bottom:0rpx;left:240rpx;opacity: 0">
      </contact-button>
      <contact-button type="default-dark" size="27" session-from="weapp" style="position:absolute;bottom:0rpx;left:270rpx;opacity: 0">
      </contact-button>
      <contact-button type="default-dark" size="27" session-from="weapp" style="position:absolute;bottom:0rpx;left:300rpx;opacity: 0">
      </contact-button>
      <contact-button type="default-dark" size="27" session-from="weapp" style="position:absolute;bottom:0rpx;left:330rpx;opacity: 0">
      </contact-button>
      <contact-button type="default-dark" size="27" session-from="weapp" style="position:absolute;bottom:0rpx;left:360rpx;opacity: 0">
      </contact-button>

      <contact-button type="default-dark" size="27" session-from="weapp" style="position:absolute;top:0rpx;right:210rpx;opacity: 0">
      </contact-button>
      <contact-button type="default-dark" size="27" session-from="weapp" style="position:absolute;top:0rpx;right:240rpx;opacity: 0">
      </contact-button>
      <contact-button type="default-dark" size="27" session-from="weapp" style="position:absolute;top:0rpx;right:270rpx;opacity: 0">
      </contact-button>
      <contact-button type="default-dark" size="27" session-from="weapp" style="position:absolute;top:0rpx;right:300rpx;opacity: 0">
      </contact-button>
      <contact-button type="default-dark" size="27" session-from="weapp" style="position:absolute;top:0rpx;right:330rpx;opacity: 0">
      </contact-button>
      <contact-button type="default-dark" size="27" session-from="weapp" style="position:absolute;top:0rpx;right:360rpx;opacity: 0">
      </contact-button>

      <contact-button type="default-dark" size="27" session-from="weapp" style="position:absolute;top:0rpx;left:210rpx;opacity: 0">
      </contact-button>
      <contact-button type="default-dark" size="27" session-from="weapp" style="position:absolute;top:0rpx;left:240rpx;opacity: 0">
      </contact-button>
      <contact-button type="default-dark" size="27" session-from="weapp" style="position:absolute;top:0rpx;left:270rpx;opacity: 0">
      </contact-button>
      <contact-button type="default-dark" size="27" session-from="weapp" style="position:absolute;top:0rpx;left:300rpx;opacity: 0">
      </contact-button>
      <contact-button type="default-dark" size="27" session-from="weapp" style="position:absolute;top:0rpx;left:330rpx;opacity: 0">
      </contact-button>
      <contact-button type="default-dark" size="27" session-from="weapp" style="position:absolute;top:0rpx;left:360rpx;opacity: 0">
      </contact-button>
    </view>
    <!-- <view style="background:#d4d4d4;width:100%;height:3rpx;margin-left:20rpx"></view>
    <view style="display:flex;flex-direction:row;width:100%;justify-content:space-between;align-items:center;padding-top:20rpx;padding-bottom:20rpx">
      <view style="display:flex;flex-direction:row;justify-content:center;align-items:center;" bindtap="goCoupon">
        <image src="../../images/personal_sale.png" mode="widthFix" style="display:flex;width:30rpx;margin-left:20rpx"></image>
        <text style="margin-left:10rpx;font-size:0.9rem;color:#323232;font-weight:600">我的优惠券</text>
      </view>
      <image src="../../images/personal_you.png" mode="widthFix" style="display:flex;width:15rpx;margin-right:20rpx"></image>
    </view> -->
    <view style="background:#d4d4d4;width:100%;height:3rpx;"></view>
    <!-- <view style="position:fixed;bottom:120rpx;width:100%;"> -->
    <view style="display:flex;justify-content:center;align-items:center;margin-bottom:10rpx;margin-top:10rpx">
      <image src="../../images/personal_logo.png" mode="widthFix" style="width:40%"></image>
    </view>
    <!-- </view> -->
  </scroll-view>


  <!--mask-->
  <view class="drawer_screen" bindtap="powerDrawer" data-statu="close" wx:if="{{showModalStatus2}}"></view>
  <!--content-->
  <!--使用animation属性指定需要执行的动画-->
  <view animation="{{animationData2}}" class="drawer_box" wx:if="{{showModalStatus2}}">

    <!--drawer content-->
    <view class="drawer_title">未授权</view>
    <view class="drawer_content">
      <view style="display:flex;justify-content:center;align-items:center;">
        完成授权，可进行更多操作
      </view>
    </view>
    <view class="btn_ok" bindtap="getOpenid">授权</view>
    <!-- <button  style="color:#E8E8EA;background:#ffffff;padding:0rpx" open-type="getUserInfo" bindgetuserinfo="getUserInfo">授权</button> -->
  </view>
</view>


<!--底部导航-->
<view style="position:fixed;bottom:0px;overflow:auto;width:100%;background:{{color_nag_bg}};height:100rpx;font-family:Microsoft YaHei">
  <view style="display:flex;align-items:center;flex-direction:row;">
    <view style="display:flex;align-items:center;flex-direction:column;justify-content:center;flex:1" bindtap="click_index">
      <image src="{{now=='index'?ip+image_index_light:ip+image_index_dark}}" mode="widthFix" style="width:40rpx;margin-top:10rpx" bindload="load_img_index"></image>
      <text style="font-size:0.6rem;margin-top:5rpx;color:{{now=='index'?color_index_light:color_index_dark}}">{{txt_index}}</text>
    </view>
    <view style="display:flex;align-items:center;flex-direction:column;justify-content:center;flex:1" bindtap="click_classify">
      <image src="{{now=='classify'?ip+image_classify_light:ip+image_classify_dark}}" mode="widthFix" style="width:40rpx;margin-top:10rpx" bindload="load_img_classify"></image>
      <text style="font-size:0.6rem;margin-top:5rpx;color:{{now=='classify'?color_classify_light:color_classify_dark}}">{{txt_classify}}</text>
    </view>
    <view style="display:flex;align-items:center;flex-direction:column;justify-content:center;flex:1" bindtap="click_shopcart">
      <image src="{{now=='shopcart'?ip+image_shopcart_light:ip+image_shopcart_dark}}" mode="widthFix" style="width:40rpx;margin-top:10rpx" bindload="load_img_shopcart"></image>
      <text style="font-size:0.6rem;mmargin-top:5rpx;color:{{now=='shopcart'?color_shopcart_light:color_shopcart_dark}}">{{txt_shopcart}}</text>
    </view>
    <view style="display:flex;align-items:center;flex-direction:column;justify-content:center;flex:1" bindtap="click_personal">
      <image src="{{now=='personal'?ip+image_personal_light:ip+image_personal_dark}}" mode="widthFix" style="width:40rpx;margin-top:10rpx" bindload="load_img_personal"></image>
      <text style="font-size:0.6rem;margin-top:5rpx;color:{{now=='personal'?color_personal_light:color_personal_dark}}">{{txt_personal}}</text>
    </view>
  </view>
</view>
<view wx:if="{{!loadfinish}}" style="position:fixed;bottom:0px;overflow:auto;width:100%;background:#fffdfd;height:100%;font-family:Microsoft YaHei">
  <view style="align-items:center;justify-content:center;width:100%;height:100%;display:flex">
    <image src="../../images/loading_page.gif" mode="widthFix" style="width:30%"></image>
  </view>
</view>
