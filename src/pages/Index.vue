<template>
  <q-layout view="lHh lpr lFf">
    <!-- 页首 -->
    <q-header elevated class="q-py-sm" style="background-color: #f5f5f5;" :style="'border-bottom: 2px solid '+ theme_color">
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="leftDrawerOpen = !leftDrawerOpen"
          class="custom_tab mobile-only"
        />

        <q-toolbar-title class="custom_tab mobile-only" style="overflow: visible; min-width: 100px;font-size: 18px;"  >
          QCL Digital
        </q-toolbar-title>
        <q-img style="height: 50px; max-width:150px" src="/assets/brand.png" class="desktop-only" contain/>
        <q-select
            v-model="lang"
            :options="langOptions"
            label="Language"
            dense
            borderless
            emit-value
            map-options
            options-dense
            style="min-width: 80px"
            class="desktop-only"
            transition-show="flip-up"
            transition-hide="flip-down"
          />
        <q-tabs v-model="selected_tab" shrink mobile-arrows style="padding: 0 30px">
          <q-tab name="t_0" :style= "[selected_tab == 't_0' ? {backgroundColor: theme_color} : {}]" class="q-mr-sm q-py-xs custom_tab" @click="scrollToElement('id_portfolio');"  :label="$t('Portfolio')" />
          <q-tab name="t_1" :style= "[selected_tab == 't_1' ? {backgroundColor: theme_color} : {}]" class="q-mr-sm q-py-xs custom_tab" @click="scrollToElement('id_about_us');"  :label="$t('AboutUs')" />
          <q-tab name="t_2" :style= "[selected_tab == 't_2' ? {backgroundColor: theme_color} : {}]" class="q-mr-sm q-py-xs custom_tab" @click="scrollToElement('id_services');"  :label="$t('Services')" />
          <q-tab name="t_3" :style= "[selected_tab == 't_3' ? {backgroundColor: theme_color} : {}]" class="q-mr-sm q-py-xs custom_tab" @click="scrollToElement('id_contact_us');"  :label="$t('Testimonial')" />
          <!--
          <q-tab name="t_4" :style= "[selected_tab == 't_4' ? {backgroundColor: theme_color} : {}]" class="q-mr-sm q-py-xs custom_tab" @click="scrollToElement('id_team');"  :label="$t('Team')" />
          <q-tab name="t_5" :style= "[selected_tab == 't_5' ? {backgroundColor: theme_color} : {}]" class="q-mr-sm q-py-xs custom_tab" @click="scrollToElement('id_pricing');"  :label="$t('Pricing')" />
          <q-tab name="t_6" :style= "[selected_tab == 't_6' ? {backgroundColor: theme_color} : {}]" class="q-mr-sm q-py-xs custom_tab" @click="scrollToElement('id_news');"  :label="$t('News')" />
          -->
        </q-tabs>
      </q-toolbar>
    </q-header>
    <!--  侧边栏 -->
    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      bordered
      class="mobile-only"
      content-style="background-color: #f5f5f5;"
        overlay
    >
      <div class="row">
        <q-img style="height: 50px; width:100px;" src="/assets/brand.png" class="mobile-only" contain/>
        <q-select
            v-model="lang"
            :options="langOptions"
            label="Language"
            dense
            borderless
            emit-value
            map-options
            options-dense
            style="width: 80px; "
            class="mobile-only"
            transition-show="flip-up"
            transition-hide="flip-down"
          />
       </div>
      <q-list>
        <q-item
          clickable
          v-ripple
          @click="leftDrawerOpen=!leftDrawerOpen;scrollToElement('id_portfolio')"
        >
          <q-item-section>{{ $t('Portfolio') }}</q-item-section>
        </q-item>
        <q-item
          clickable
          v-ripple
          @click="leftDrawerOpen=!leftDrawerOpen;scrollToElement('id_about_us')"
        >
          <q-item-section>{{ $t('AboutUs') }}</q-item-section>
        </q-item>
        <q-item
          clickable
          v-ripple
          @click="leftDrawerOpen=!leftDrawerOpen;scrollToElement('id_services')"
        >
          <q-item-section>{{ $t('Services') }}</q-item-section>
        </q-item>
        <q-item
          clickable
          v-ripple
          @click="leftDrawerOpen=!leftDrawerOpen;scrollToElement('id_contact_us')"
        >
          <q-item-section>{{ $t('Testimonial') }}</q-item-section>
        </q-item>
      </q-list>
    </q-drawer>
    <!-- 页身 -->
    <q-page-container>
      <q-page>
    <!-- 轮播 autoplay -->
        <q-carousel
          animated
          v-model="slide"
          arrows
          swipeable
          navigation
          infinite
          control-color="amber-7 "
          transition-prev="slide-right"
          transition-next="slide-left"
          height="639px"

        >
          <q-carousel-slide class="q-pa-none" :name="1" >
            <div class="full-height full-width flex flex-center" >
              <div class="custom-caption">
                <lottie-web-cimo
                ref="lottie_web"
                :path="lottieOptions.path1"
                :loop="lottieOptions.loop"
                :animation-speed="lottieOptions.animationSpeed"
                :viewBoxSize="lottieOptions.viewBoxSize1"
                @isLottieFinish="handleLottieFinish"
                />
                <div class="text-h3 animation_1" :style="'color:'+theme_color">WELCOME TO <span >{{ $t('name') }}</span></div>
                <div @click="scrollToElement('id_portfolio')" style="margin:0 auto;width:100px">
                  <lottie-web-cimo
                  ref="lottie_web"
                  :path="lottieOptions.path2"
                  :loop="lottieOptions.loop"
                  :animation-speed="lottieOptions.animationSpeed"
                  :viewBoxSize="lottieOptions.viewBoxSize2"
                  @isLottieFinish="handleLottieFinish"
                  />
                </div>
              </div>
            </div>
          </q-carousel-slide>
          <q-carousel-slide class="q-pa-none" :name="2" img-src="/assets/image_2.jpg">
            <div class="full-height full-width flex flex-center" >
              <div class="custom-caption">
                <div class="text-h3 animation_2" style="font-size:65px;"><span :style="'color:'+theme_color">{{ $t('Carousel1') }}</span></div><br><br><br>
                <div class="text-h6 animation_1">{{$t('Carousel2')}}</div><br><br><br>
                <div class="animation_2">
                  <q-btn size="md" :style="'background:'+ theme_color +'; color: white'" :label="$t('Button1')" @click="scrollToElement('id_about_us')"/>
                </div>
              </div>
            </div>
          </q-carousel-slide>
          <q-carousel-slide class="q-pa-none" :name="3" img-src="/assets/image_3.jpg">
            <div class="full-height full-width flex flex-center" >
              <div class="custom-caption">
                <div class="text-h3 animation_2" style="font-size:65px;"><span :style="'color:'+theme_color">{{ $t('name') }}</span></div><br><br><br>
                <div class="text-h6 animation_1">{{$t('Carousel3')}}</div><br><br><br>
                <div class="animation_2">
                  <q-btn size="md" :style="'background:'+ theme_color +'; color: white'" :label="$t('Button1')" @click="scrollToElement('id_services')"/>
                </div>
              </div>
            </div>
          </q-carousel-slide>
        </q-carousel>
    <!-- 简介 -->
        <!-- scroll observer -->
        <q-scroll-observer @scroll="onScroll" />
        <div style="background: #f7f7f7" id="id_portfolio" >
          <br>
          <div class="row">
            <div class="col-md-12 col-lg-12 col-xs-12 col-sm-12">
              <h5 class="text-center">{{$t('portfolio1')}}
                <br>
                <span class="text-center text-grey text-h6">{{$t('portfolio2')}}</span>
              </h5>
            </div>
          </div>
          <br>
          <div class="row text-center" style="padding-bottom: 99px">
            <div class="col-md-12 col-sm-12 col-xs-12 col-lg-12">
              <div style="line-height:0">
                <!-- <span v-for="index in 6" :key="index">
                  <q-flashcard :no-hover="hover" :style="style">
                    <q-flashcard-section transition="nudge-in" :active="active">
                      <img :src="'/assets/'+index+'.jpg'" width=340 height=263>
                    </q-flashcard-section>
                    <q-flashcard-section transition="fade-in" class="fit" :active="active">
                      <div class="fit" :style="background_style"></div>
                      <q-flashcard-section transition="drop-down" class="text-center my-header" :active="active">
                        Profile Title
                      </q-flashcard-section>
                      <q-flashcard-section transition="slide-up-in" class="my-text" :active="active">
                        For beautiful eyes, look for the good in others; for beautiful lips, speak only words of kindness; and for poise, walk with the knowledge that you are never alone.
                      </q-flashcard-section>
                      <q-flashcard-section transition="fade-in" class="fit flex justify-center items-end q-pb-lg"
                                           :active="active">
                        <q-btn class="q-mr-md" :style="'color:'+theme_color" style="background-color:white" round
                               icon="card_giftcard"/>
                        <q-btn :style="'color:'+theme_color" style="background-color:white" round icon="link"/>
                      </q-flashcard-section>
                    </q-flashcard-section>
                  </q-flashcard>
                  <br v-if="index==3"/>
                </span>-->

                <q-dialog v-model="icon">
                  <q-card>
                    <q-card-section class="row items-center q-pb-none">
                      <div class="text-h6">微信扫码</div>
                      <q-space />
                      <q-btn icon="close" flat round dense v-close-popup />
                    </q-card-section>

                    <q-card-section>
                      <q-img  src="/assets/gh_cf2442cab29b_258.jpg"  contain/>
                    </q-card-section>
                  </q-card>
                </q-dialog>

                <span >
                  <q-flashcard :no-hover="hover" :style="style">
                    <q-flashcard-section transition="nudge-in" :active="active">
                      <img :src="'/assets/'+2+'.jpg'" width=340 height=263>
                    </q-flashcard-section>
                    <q-flashcard-section transition="fade-in" class="fit" :active="active">
                      <div class="fit" :style="background_style"></div>
                      <q-flashcard-section transition="drop-down" class="text-center my-header" :active="active">
                        {{$t('portfolio3')}}
                      </q-flashcard-section>
                      <q-flashcard-section transition="slide-up-in" class="my-text" :active="active">
                        {{$t('portfolio4')}}
                      </q-flashcard-section>
                      <q-flashcard-section transition="fade-in" class="fit flex justify-center items-end q-pb-lg"
                                           :active="active">
                        <q-btn class="q-mr-md" :style="'color:'+theme_color" style="background-color:white" round
                               icon="card_giftcard" @click="externalLink('https://www.qcldigital.com')" />
                        <q-btn :style="'color:'+theme_color" style="background-color:white" round icon="link" @click="icon = true"/>
                      </q-flashcard-section>
                    </q-flashcard-section>
                  </q-flashcard>
                </span>
                <span >
                  <q-flashcard :no-hover="hover" :style="style">
                    <q-flashcard-section transition="nudge-in" :active="active">
                      <img :src="'/assets/'+3+'.jpg'" width=340 height=263>
                    </q-flashcard-section>
                    <q-flashcard-section transition="fade-in" class="fit" :active="active">
                      <div class="fit" :style="background_style"></div>
                      <q-flashcard-section transition="drop-down" class="text-center my-header" :active="active">
                        {{$t('portfolio5')}}
                      </q-flashcard-section>
                      <q-flashcard-section transition="slide-up-in" class="my-text" :active="active">
                        {{$t('portfolio6')}}
                      </q-flashcard-section>
                      <q-flashcard-section transition="fade-in" class="fit flex justify-center items-end q-pb-lg"
                                           :active="active">
                        <q-btn class="q-mr-md" :style="'color:'+theme_color" style="background-color:white" round
                               icon="card_giftcard"/>
                        <q-btn :style="'color:'+theme_color" style="background-color:white" round icon="link"/>
                      </q-flashcard-section>
                    </q-flashcard-section>
                  </q-flashcard>
                </span>
                <span >
                  <q-flashcard :no-hover="hover" :style="style">
                    <q-flashcard-section transition="nudge-in" :active="active">
                      <img :src="'/assets/'+4+'.jpg'" width=340 height=263>
                    </q-flashcard-section>
                    <q-flashcard-section transition="fade-in" class="fit" :active="active">
                      <div class="fit" :style="background_style"></div>
                      <q-flashcard-section transition="drop-down" class="text-center my-header" :active="active">
                        {{$t('portfolio7')}}
                      </q-flashcard-section>
                      <q-flashcard-section transition="slide-up-in" class="my-text" :active="active">
                        {{$t('portfolio8')}}
                      </q-flashcard-section>
                      <q-flashcard-section transition="fade-in" class="fit flex justify-center items-end q-pb-lg"
                                           :active="active">
                        <q-btn class="q-mr-md" :style="'color:'+theme_color" style="background-color:white" round
                               icon="card_giftcard"/>
                        <q-btn :style="'color:'+theme_color" style="background-color:white" round icon="link"/>
                      </q-flashcard-section>
                    </q-flashcard-section>
                  </q-flashcard>
                </span>
                <span >
                  <q-flashcard :no-hover="hover" :style="style">
                    <q-flashcard-section transition="nudge-in" :active="active">
                      <img :src="'/assets/'+1+'.jpg'" width=340 height=263>
                    </q-flashcard-section>
                    <q-flashcard-section transition="fade-in" class="fit" :active="active">
                      <div class="fit" :style="background_style"></div>
                      <q-flashcard-section transition="drop-down" class="text-center my-header" :active="active">
                        {{$t('portfolio9')}}
                      </q-flashcard-section>
                      <q-flashcard-section transition="slide-up-in" class="my-text" :active="active">
                        {{$t('portfolio10')}}
                      </q-flashcard-section>
                      <q-flashcard-section transition="fade-in" class="fit flex justify-center items-end q-pb-lg"
                                           :active="active">
                        <q-btn class="q-mr-md" :style="'color:'+theme_color" style="background-color:white" round
                               icon="card_giftcard" @click="externalLink('https://www.qcldigital.com')" />
                        <q-btn :style="'color:'+theme_color" style="background-color:white" round icon="link" @click="icon = true"/>
                      </q-flashcard-section>
                    </q-flashcard-section>
                  </q-flashcard>
                </span>
              </div>
            </div>
          </div>
        </div>
    <!-- 关于我们 -->
        <div id="id_about_us">
          <div class="row">
            <div class="col-md-12 col-lg-12 col-xs-12 col-sm-12">
              <h5 class="text-center">{{$t('about_us1')}}
                <br>
                <span
                  class="text-center text-grey text-caption">{{$t('about_us2')}}</span>
              </h5>
            </div>
          </div>
          <div class="row text-center flex flex-center">
            <div class="col-md-12 col-lg-12 col-sx-12 col-sm-12 q-gutter-md flex flex-center">
              <div class="col-md-4 col-lg-4 col-sx-12 col-sm-12">
                <q-card @mouseover="hoverOver(1)" @mouseout="hoverOutTimeout(1)" style="border: none;" class="my-card text-center box-shadow" flat bordered>
                  <q-img
                    src="/assets/about_1.jpg"
                  />

                  <q-card-section>
                    <div class="text-overline text-orange-9">QCL Digital</div>
                    <div :class="about_heading_1" :style="'color: ' + about_heading_color_1" class="about_heading_1 text-h6 q-mt-sm q-mb-xs">{{$t('about_us3')}}</div>
                    <div class="text-caption text-grey-9">
                      {{$t('about_us4')}}
                    </div>
                  </q-card-section>
                </q-card>
              </div>
              <div class="col-md-4 col-lg-4 col-sx-12 col-sm-12">
                <q-card @mouseover="hoverOver(2)" @mouseout="hoverOutTimeout(2)" :style="'color: ' + about_heading_color_2" style="border: none;" class="my-card text-center box-shadow" flat bordered>
                  <q-img
                    src="/assets/about_2.jpg"
                  />

                  <q-card-section>
                    <div class="text-overline text-orange-9">QCL Digital</div>
                    <div :class="about_heading_2" :style="'color: ' + about_heading_color_2" class="text-h6 q-mt-sm q-mb-xs">{{$t('about_us5')}}</div>
                    <div class="text-caption text-grey-9">
                      {{$t('about_us6')}}
                    </div>
                  </q-card-section>
                </q-card>
              </div>
            </div>
          </div>
        </div>
        <br>
        <br>
    <!-- 服务 -->
        <div style="background: #f7f7f7" id="id_services">
          <div class="row">
            <div class="col-md-12 col-lg-12 col-xs-12 col-sm-12">
              <h5 class="text-center">{{$t('services1')}}
                <br>
                <span
                  class="text-center text-grey text-caption">{{$t('services2')}}</span>
              </h5>
            </div>
          </div>
          <div class="q-pa-xl">
            <div class="row q-col-gutter-sm ">
              <div class="col-md-4 col-lg-4 col-sm-12 col-xs-12">
                <q-item class="box-shadow q-pa-none q-ml-xs ">
                  <q-item-section side :style="'background-color:' + theme_color" class="q-pa-sm q-mr-none text-white">
                    <q-icon name="compare_arrows" size="65px"></q-icon>
                  </q-item-section>
                  <q-item-section class="q-pa-md q-ml-none">
                    <q-item-label class="text-h6 text-grey-9 text-uppercase">{{$t('services3')}}</q-item-label>
                    <q-item-label class="text-grey-8">{{$t('services4')}} </q-item-label>
                    <span  class="text-grey text-caption">{{$t('services9')}}</span>
                    <span  class="text-grey text-caption">{{$t('services10')}}</span>
                    <span  class="text-grey text-caption">{{$t('services11')}}</span>
                    <span  class="text-grey text-caption">{{$t('services12')}}</span>
                  </q-item-section>
                </q-item>
              </div>
              <div class="col-md-4 col-lg-4 col-sm-12 col-xs-12">
                <q-item class="box-shadow q-pa-none q-ml-xs">
                  <q-item-section side :style="'background-color:' + theme_color" class="q-pa-sm q-mr-none text-white">
                    <q-icon name="web" size="65px"></q-icon>
                  </q-item-section>
                  <q-item-section class="q-pa-md q-ml-none">
                    <q-item-label class="text-h6 text-grey-9 text-uppercase">{{$t('services5')}} </q-item-label>
                    <q-item-label class="text-grey-8">{{$t('services6')}} </q-item-label>
                    <span  class="text-grey text-caption">{{$t('services13')}}</span>
                    <span  class="text-grey text-caption">{{$t('services14')}}</span>
                    <span  class="text-grey text-caption">{{$t('services15')}}</span>
                  </q-item-section>
                </q-item>
              </div>
              <div class="col-md-4 col-lg-4 col-sm-12 col-xs-12">
                <q-item class="box-shadow q-pa-none q-ml-xs q-mr-xs">
                  <q-item-section side :style="'background-color:' + theme_color" class="q-pa-sm q-mr-none text-white">
                    <q-icon name="dynamic_feed" size="65px"></q-icon>
                  </q-item-section>
                  <q-item-section class="q-pa-md q-ml-none">
                    <q-item-label class="text-h6 text-grey-9 text-uppercase">{{$t('services7')}} </q-item-label>
                    <q-item-label class="text-grey-8">{{$t('services8')}} </q-item-label>
                    <span  class="text-grey text-caption">{{$t('services16')}}</span>
                    <span  class="text-grey text-caption">{{$t('services17')}}</span>
                    <span  class="text-grey text-caption">{{$t('services18')}}</span>
                  </q-item-section>
                </q-item>
              </div>
            </div>
          </div>
        </div>
    <!-- 客户 -->
        <!-- <div class="quote" id="id_testimonial">
          <div style="background-color: #000000ad !important;">
            <q-carousel
              v-model="review_slide"
              swipeable
              animated
              infinite
              autoplay
              arrows
              navigation
              padding
              navigation-position="bottom"
              class="text-white full-height bg-transparent q-mx-xl"
            >
              <q-carousel-slide style="padding-bottom: 140px" name="style" class="column no-wrap flex-center">
                <img :style="'margin-top:100px;border-radius:5px;border: 4px solid ' + theme_color" src="/assets/team_1.jpg" width=150 height=150>
                <div class="q-mt-md text-h6 text-center">
                   <span :style="'color:'+theme_color">John Doe</span><br><span class="text-overline">Organization Founder</span>
                </div>
                <div class="q-mt-md text-h6 text-center">
                  Lorem ipsum dolor sit amet, consectetur
                  adipiscing elit, sed do eiusmod tempor incididunt ut<br>
                  labore et dolore magna aliqua.
                </div>
              </q-carousel-slide>
              <q-carousel-slide style="padding-bottom: 140px" name="tv" class="column no-wrap flex-center">
                <img :style="'margin-top:100px;border-radius:5px;border: 4px solid ' + theme_color" src="/assets/team_2.jpg" width=150 height=150>
                <div class="q-mt-md text-h6 text-center">
                   <span :style="'color:'+theme_color">John Doe</span><br><span class="text-overline">Lead Developer</span>
                </div>
                <div class="q-mt-md text-h6 text-center">
                  Lorem ipsum dolor sit amet, consectetur
                  adipiscing elit, sed do eiusmod tempor incididunt ut<br>
                  labore et dolore magna aliqua.
                </div>
              </q-carousel-slide>
              <q-carousel-slide style="padding-bottom: 140px" name="layers" class="column no-wrap flex-center">
                <img :style="'margin-top:100px;border-radius:5px;border: 4px solid ' + theme_color" src="/assets/team_3.jpg" width=150 height=150>
                <div class="q-mt-md text-h6 text-center">
                   <span :style="'color:'+theme_color">John Doe</span><br><span class="text-overline">Product Owner</span>
                </div>
                <div class="q-mt-md text-h6 text-center">
                  Lorem ipsum dolor sit amet, consectetur
                  adipiscing elit, sed do eiusmod tempor incididunt ut<br>
                  labore et dolore magna aliqua.
                </div>
              </q-carousel-slide>
            </q-carousel>
          </div>
        </div>-->
    <!-- 团队 -->
        <!--<div id="id_team">
          <div class="row" >
            <div class="col-md-12 col-lg-12 col-xs-12 col-sm-12">
              <h5 class="text-center">Our Team
                <br>
                <span
                  class="text-center text-grey text-h6">Lorem ipsum dolor sit amet, consectetur adipiscing elit.</span>
              </h5>
            </div>
          </div>
          <div class="row text-center flex flex-center">
            <div class="col-md-12 col-lg-12 col-sx-12 col-sm-12 q-px-xl" style="width:100%;overflow:auto;">
              <q-carousel
              v-model="team_slide"
              transition-prev="slide-right"
              transition-next="slide-left"
              swipeable
              animated
	            infinite
              autoplay
              control-color="primary"
              navigation
              padding
              height="300px"
              class="rounded-borders"
            >
              <q-carousel-slide v-for="val in [1,2,3]" :key="val" :name="val" class="column no-wrap">
                <div class="row fit justify-center items-center q-gutter-xs q-col-gutter no-wrap">
                  <span v-for="index in 4" :key="index">
                  <q-flashcard :no-hover="hover" :style="team_style">
                    <q-flashcard-section transition="['nudge-out', 'fade-out']" :active="active">
                      <img :src="'/assets/team_'+index+'.jpg'" width=260 height=263>
                    </q-flashcard-section>
                    <q-flashcard-section transition="fade-in" class="fit" :active="active">
                      <div class="fit" :style="background_style"></div>
                      <q-flashcard-section transition="shake-down" class="text-center team-header" :active="active">
                        JOHN DOE
                      </q-flashcard-section>
                      <q-flashcard-section transition="spin-in" class="team-text" :active="active">
                        Founder and Director
                      </q-flashcard-section>
                      <q-flashcard-section style="padding-bottom: 50px" transition="slide-up-in" class="fit flex justify-center items-end"
                                           :active="active">
                        <q-btn class="q-mr-md" :style="'color:'+theme_color" style="background-color:white" round
                               icon="card_giftcard"/>
                        <q-btn :style="'color:'+theme_color" style="background-color:white" round icon="link"/>
                      </q-flashcard-section>
                    </q-flashcard-section>
                  </q-flashcard>
                  </span>
                </div>
              </q-carousel-slide>
            </q-carousel>
            </div>
          </div>
        </div>-->
    <!-- 价格 -->

        <!--<div class="pricing" id="id_pricing">
          <div class="" style="background-color: #000000ad !important;">
            <div class="row">
              <div class="col-md-12 col-lg-12 col-xs-12 col-sm-12">
                <h5 class="text-center text-white">Our Pricing Plan
                  <br>
                  <span
                    class="text-center text-grey text-h6">Lorem ipsum dolor sit amet, consectetur adipiscing elit.</span>
                </h5>
              </div>
            </div>
            <div class="row q-col-gutter-sm q-px-xl">
              <div class="col-lg-3 col-md-3 col-xs-12 col-sm-6 q-px-lg">
                <q-card>
                  <q-card-section class="text-white" style="background: #ec982f">
                    <div class="text-h6 text-center">
                      FREE
                    </div>
                  </q-card-section>
                  <q-card-section class="q-pa-md">
                    <q-list dense padding style="border-bottom: 1px solid lightgrey;">
                      <q-item><span class="text-weight-bold">For small size companies</span></q-item>
                      <q-item>
                          50 GB storage
                      </q-item>
                      <q-item>
                          10 Domains
                      </q-item>
                      <q-item>
                          15 Projects
                      </q-item>
                      <q-item>
                          Free Deployment
                      </q-item>
                    </q-list>
                  </q-card-section>
                  <q-card-section class="q-pa-none" style="color: #ec982f">
                    <div class="text-center">
                      <span class="text-h2 text-center">$0</span>/mo
                    </div>
                  </q-card-section>
                  <q-card-section>
                    <div class="text-center q-px-lg">
                      <q-btn size="md" class="full-width q-pa-xs"
                         style="background: #ec982f; color: white" label="Choose Plan"/>
                         <br>
                         <div class="q-mt-md">Terms and Conditions apply</div>
                    </div>
                  </q-card-section>
                </q-card>
              </div>
              <div class="col-lg-3 col-md-3 col-xs-12 col-sm-6 q-px-lg">
                <q-card>
                  <q-card-section class="text-white" style="background: #f4655f">
                    <div class="text-h6 text-center">
                      STANDARD
                    </div>
                  </q-card-section>
                  <q-card-section class="q-pa-md">
                    <q-list dense padding style="border-bottom: 1px solid lightgrey;">
                      <q-item><span class="text-weight-bold">For medium companies</span></q-item>
                      <q-item>
                          50 GB storage
                      </q-item>
                      <q-item>
                          10 Domains
                      </q-item>
                      <q-item>
                          15 Projects
                      </q-item>
                      <q-item>
                          Free Deployment
                      </q-item>
                    </q-list>
                  </q-card-section>
                  <q-card-section class="q-pa-none" style="color: #f4655f">
                    <div class="text-center">
                      <span class="text-h2 text-center">$50</span>/mo
                    </div>
                  </q-card-section>
                  <q-card-section>
                    <div class="text-center q-px-lg">
                      <q-btn size="md" class="full-width q-pa-xs"
                         style="background: #f4655f; color: white" label="Choose Plan"/>
                         <br>
                         <div class="q-mt-md">Terms and Conditions apply</div>
                    </div>
                  </q-card-section>
                </q-card>
              </div>
              <div class="col-lg-3 col-md-3 col-xs-12 col-sm-6 q-px-lg">
                <q-card>
                  <q-card-section class="text-white q-pa-md" style="background: #8b3bbd">
                    <div class="text-h6 text-center">
                      PREMIUM
                    </div>
                  </q-card-section>
                  <q-card-section class="q-pa-md">
                    <q-list dense padding style="border-bottom: 1px solid lightgrey;">
                      <q-item><span class="text-weight-bold">For average companies</span></q-item>
                      <q-item>
                          50 GB storage
                      </q-item>
                      <q-item>
                          10 Domains
                      </q-item>
                      <q-item>
                          15 Projects
                      </q-item>
                      <q-item>
                          Free Deployment
                      </q-item>
                    </q-list>
                  </q-card-section>
                  <q-card-section class="q-pa-none" style="color: #8b3bbd">
                    <div class="text-center">
                      <span class="text-h2 text-center">$250</span>/mo
                    </div>
                  </q-card-section>
                  <q-card-section>
                    <div class="text-center q-px-lg">
                      <q-btn size="md" class="full-width q-pa-xs"
                         :style="'background: #8b3bbd; color: white'" label="Choose Plan"/>
                         <br>
                         <div class="q-mt-md">Terms and Conditions apply</div>
                    </div>
                  </q-card-section>
                </q-card>
              </div>
              <div class="col-lg-3 col-md-3 col-xs-12 col-sm-6 q-px-lg">
                <q-card>
                  <q-card-section class="text-white" style="background: #3b97d1">
                    <div class="text-h6 text-center">
                      PROFESSIONAL
                    </div>
                  </q-card-section>
                  <q-card-section class="q-pa-md">
                    <q-list dense padding style="border-bottom: 1px solid lightgrey;">
                      <q-item><span class="text-weight-bold">For large companies</span></q-item>
                      <q-item>
                          50 GB storage
                      </q-item>
                      <q-item>
                          10 Domains
                      </q-item>
                      <q-item>
                          15 Projects
                      </q-item>
                      <q-item>
                          Free Deployment
                      </q-item>
                    </q-list>
                  </q-card-section>
                  <q-card-section class="q-pa-none" style="color: #3b97d1">
                    <div class="text-center">
                      <span class="text-h2 text-center">$500</span>/mo
                    </div>
                  </q-card-section>
                  <q-card-section>
                    <div class="text-center q-px-lg">
                      <q-btn size="md" class="full-width q-pa-xs"
                         style="background:#3b97d1; color: white" label="Choose Plan"/>
                         <br>
                         <div class="q-mt-md">Terms and Conditions apply</div>
                    </div>
                  </q-card-section>
                </q-card>
              </div>
            </div>
          </div>
        </div>-->
    <!-- 新闻 -->
        <!--<div id="id_news">
          <div class="row">
            <div class="col-md-12 col-lg-12 col-xs-12 col-sm-12">
              <h5 class="text-center">Latest News
                <br>
                <span
                  class="text-center text-grey text-h6">Lorem ipsum dolor sit amet, consectetur adipiscing elit.</span>
              </h5>
            </div>
          </div>
          <div class="row text-center flex flex-center">
            <div class="col-md-12 col-lg-12 col-sx-12 col-sm-12 q-gutter-md flex flex-center">
              <div class="col-md-4 col-lg-4 col-sx-12 col-sm-12">
                <q-card @mouseover="hoverOver(1)" @mouseout="hoverOutTimeout(1)" style="border: none;" class="my-card text-center box-shadow" flat bordered>
                  <q-img
                    src="/assets/about_1.jpg"
                  />

                  <q-card-section class="text-left">

                    <div :class="about_heading_1" :style="'color: ' + about_heading_color_1" class="about_heading_1 text-h6 q-mt-sm q-mb-xs">LATEST NEWS 1</div>
                    <div class="text-caption text-grey-9 q-mt-sm">
                      Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.
                    </div>
                    <div><br>
                    <q-btn size="sm" :style="'background:'+ theme_color +'; color: white'" label="READ MORE"/>
                    </div>
                  </q-card-section>
                </q-card>
              </div>
              <div class="col-md-4 col-lg-4 col-sx-12 col-sm-12">
                <q-card @mouseover="hoverOver(2)" @mouseout="hoverOutTimeout(2)" :style="'color: ' + about_heading_color_2" style="border: none;" class="my-card text-center box-shadow" flat bordered>
                  <q-img
                    src="/assets/about_2.jpg"
                  />

                  <q-card-section class="text-left">

                    <div :class="about_heading_2" :style="'color: ' + about_heading_color_2" class="text-h6 q-mt-sm q-mb-xs">LATEST NEWS 2</div>
                    <div class="text-caption text-grey-9 q-mt-sm">
                      Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.
                    </div>
                    <div><br>
                    <q-btn size="sm" :style="'background:'+ theme_color +'; color: white'" label="READ MORE"/>
                    </div>
                  </q-card-section>
                </q-card>
              </div>
              <div class="col-md-4 col-lg-4 col-sx-12 col-sm-12">
                <q-card @mouseover="hoverOver(3)" @mouseout="hoverOutTimeout(3)" style="border: none;" class="my-card text-center box-shadow" flat bordered>
                  <q-img
                    src="/assets/about_3.jpg"
                  />

                  <q-card-section class="text-left">

                    <div :class="about_heading_3" :style="'color: ' + about_heading_color_3" class="text-h6 q-mt-sm q-mb-xs">LATEST NEWS 3</div>
                    <div class="text-caption text-grey-9 q-mt-sm">
                      Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore
                      et dolore magna aliqua.
                    </div>
                    <div><br>
                    <q-btn size="sm" :style="'background:'+ theme_color +'; color: white'" label="READ MORE"/>
                    </div>
                  </q-card-section>
                </q-card>
              </div>
            </div>
          </div>
        </div>-->
    <!-- 卡片 -->
        <!--<div class="row">
          <div class="col-md-3 col-lg-3 col-xs-12 col-sm-12">
            <q-card class="q-pa-sm flex flex-center text-center box-shadow" style="margin: 40px;">


              <q-card-section>
                <q-icon size="110px" name="ballot" :style="'color:'+theme_color"/>
                <div class="text-h6">Web &nbsp;Design</div>

              </q-card-section>

              <q-card-section class="q-pt-none">
                Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do
                eiusmod tempor incididunt.
              </q-card-section>
            </q-card>
          </div>
          <div class="col-md-3 col-lg-3 col-xs-12 col-sm-12">
            <q-card class="q-pa-sm flex flex-center text-center box-shadow" style="margin: 40px;">


              <q-card-section>
                <q-icon size="110px" name="view_comfy" :style="'color:'+theme_color"/>
                <div class="text-h6">Graphics Design</div>

              </q-card-section>

              <q-card-section class="q-pt-none">
                Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do
                eiusmod tempor incididunt.
              </q-card-section>
            </q-card>
          </div>
          <div class="col-md-3 col-lg-3 col-xs-12 col-sm-12">
            <q-card class="q-pa-sm flex flex-center text-center box-shadow" style="margin: 40px;">


              <q-card-section>
                <q-icon size="110px" name="people" :style="'color:'+theme_color"/>
                <div class="text-h6">Wordpress Theme</div>

              </q-card-section>

              <q-card-section class="q-pt-none">
                Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do
                eiusmod tempor incididunt.
              </q-card-section>
            </q-card>
          </div>

          <div class="col-md-3 col-lg-3 col-xs-12 col-sm-12">
            <q-card class="q-pa-sm flex flex-center text-center box-shadow" style="margin: 40px;">


              <q-card-section>
                <q-icon size="110px" name="people" :style="'color:'+theme_color"/>
                <div class="text-h6">Wordpress Plugin</div>

              </q-card-section>

              <q-card-section class="q-pt-none">
                Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do
                eiusmod tempor incididunt.
              </q-card-section>
            </q-card>
          </div>
        </div>-->
    <!-- 联系我们 -->
        <div class="contact_us" id="id_contact_us">
          <div style="background-color: #000000ad !important;">
            <div class="row" id="id_news">
              <div class="col-md-12 col-lg-12 col-xs-12 col-sm-12">
                <h5 class="text-center text-white">{{$t('contact_us1')}}
                  <br>
                  <span
                    class="text-center text-grey text-h6">{{$t('contact_us2')}}</span>
                </h5>
              </div>
            </div>

            <q-form ref="form">
            <div class="row text-center flex flex-center q-pb-lg">
              <div class="col-md-6 col-lg-6 col-sx-12 col-sm-12 q-gutter-lg q-px-xl q-pb-none q-ma-none">
                <q-input bg-color="white" outlined :label="$t('contact_us3')" ref="userName" v-model="userName" :rules="[val => !!val || $t('validation_msg1')]">
                <template v-slot:append>
                  <q-icon name="account_circle" :style="'color:' + theme_color" />
                </template>
                </q-input>
                <q-input bg-color="white" outlined :label="$t('contact_us6')" ref="email" v-model="email" :rules="[val => !!val || $t('validation_msg1')]" :error-message="$t('validation_msg4')" :error="!isValidEmail">
                    <template v-slot:append>
                      <q-icon name="alternate_email" :style="'color:' + theme_color" />
                    </template>
                </q-input>
                <q-input bg-color="white" outlined :label="$t('contact_us4')" ref="phone" v-model="phone" :rules="[val => !!val || $t('validation_msg1')]" :error-message="$t('validation_msg5')" :error="!isValidPhone">
                    <template v-slot:append>
                      <q-icon name="add_ic_call" :style="'color:' + theme_color" />
                    </template>
                </q-input>
              </div>
              <div class="col-md-6 col-lg-6 col-sx-12 col-sm-12 q-gutter-lg q-px-xl q-pb-none q-ma-none">
                <q-input class="" type="textarea" bg-color="white" outlined :label="$t('contact_us5')" ref="message" v-model="message"  :rules="[val => !!val || $t('validation_msg1')]"  :error-message="$t('validation_msg6')" :error="!isValidMessage">
                <template v-slot:append>
                  <q-icon name="event" :style="'color:' + theme_color" />
                </template>
                </q-input>
              </div>
            </div>
            <div class="row flex flex-center text-center q-pb-xl q-mt-md">
              <div class="col-md-12 col-lg-12 col-sx-12 col-sm-12">
                <q-btn size="lg" :style="'background:'+ theme_color +'; color: white'" :label="$t('contact_us7')" @click="sendMsg();"/>
              </div>
            </div>
          </q-form>
          </div>
        </div>
    <!-- 底栏 -->
        <q-toolbar class="flex flex-center text-white" style="background-color: #1c1b21;" :style="'border-top: 2px solid '+ theme_color">
           <div class="q-pa-sm q-gutter-sm">
              <q-btn round type="a" href="mailto:tech.admin@qcldigital.com"
                     :style="'background:'+ theme_color +'; color: white !important;'" icon="email" />
	          </div>
        </q-toolbar>
        <q-toolbar class="flex flex-center text-white" style="background-color: #1c1b21;" >
             <div class="text-center desktop-only">
                  <p>© 2020-2023 qcldigital.com 版权所有 ICP证：<a style="color: #fff" href="http://beian.miit.gov.cn/" target="_blank">沪ICP备 2021000351号</a><a target="_blank" href="http://www.beian.gov.cn/portal/registerSystemInfo?recordcode=31010102006784" style="color: rgb(255, 255, 255);"><img src="/assets/icons/gongan.png"/>沪公网安备 31010102006784号</a></p>
              </div>



             <div class="text-center copy mobile-only">
                  <p>© 2020-2023 qcldigital.com 版权所有
                  ICP证：<a style="color: #fff" href="http://beian.miit.gov.cn/" target="_blank">沪ICP备 2021000351号</a><br><a target="_blank" href="http://www.beian.gov.cn/portal/registerSystemInfo?recordcode=31010102006784" style="color: rgb(255, 255, 255);"><img src="/assets/icons/gongan.png"/>沪公网安备 31010102006784号</a></p>
              </div>
        </q-toolbar>

      </q-page>
    </q-page-container>
  </q-layout>
</template>

<style src="@quasar/quasar-ui-qflashcard/dist/index.css"></style>

<script>
  import { scroll,Quasar } from 'quasar'
  const { getScrollTarget, setScrollPosition } = scroll
  import {QFlashcard, QFlashcardSection} from '@quasar/quasar-ui-qflashcard'
  import LottieWebCimo from 'components/lottie-web-cimo.vue'
    export default {
        components: {
            QFlashcard,
            QFlashcardSection,
            LottieWebCimo
        },
        data() {
            this.$i18n.locale=String(Quasar.lang.getLocale()).indexOf("en")>-1?'en-us':'zh-hans';
            return {
                slide: 1,
		            review_slide: 'style',
                selected_tab: 't_0',
                team_slide: 1,
                bg_color: 'rgb(0, 163, 82)',
                hover: false,
                active: false,
                theme_color: '#fec969',
                background_style: 'background-color:rgba(0, 0, 0, 0.2);',
                about_heading_1: [],
                about_heading_2: [],
                about_heading_3: [],
                about_heading_color_1: '#424242',
                about_heading_color_2: '#424242',
                about_heading_color_3: '#424242',
                lang: this.$i18n.locale,
                langOptions: [
                    { value: 'zh-hans', label: '中文' },
                    { value: 'en-us', label: 'English' }
                ],
                leftDrawerOpen: false,
                lottieOptions: {
                  path1: '/assets/lf20_gzl797gs.json',
                  viewBoxSize1: '0 0 500 400',
                  path2: '/assets/39814-dssqdfzazae.json',
                  viewBoxSize2: '0 0 500 500',
                  loop: true,
                  animationSpeed: 1,
                },
                icon: false,
                scrollInfo: {},
                userName:null,
                phone:null,
                email:null,
                message:null,
            }
        },
       watch: {
         lang(lang) {
           this.$i18n.locale = lang
         }
       },
        computed: {
            style() {
                return {
                    width: '340px',
                    height: '263px',
                    textAlign: 'center',
                    boxShadow: '1px 1px 2px #e6e6e6',
                    display: 'inline-block'
                }
            },
            team_style() {
                return {
                    width: '260px',
                    height: '263px',
                    textAlign: 'center',
                    boxShadow: '1px 1px 2px #e6e6e6',
                    display: 'inline-block'
                }
            },
            isValidEmail () {
              const re = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
              return this.email==null || this.email&&this.email.length==0||re.test(String(this.email).toLowerCase());
            },
            isValidPhone () {
              const re = /^(?:\+?86)?1(?:3\d{3}|5[^4\D]\d{2}|8\d{3}|7(?:[0-35-9]\d{2}|4(?:0\d|1[0-2]|9\d))|9[0-35-9]\d{2}|6[2567]\d{2}|4(?:(?:10|4[01])\d{3}|[68]\d{4}|[579]\d{2}))\d{6}$/;
              return this.phone==null || this.phone&&this.phone.length==0||re.test(String(this.phone).toLowerCase());
            },
            isValidMessage () {
             return this.message==null || this.message&&this.message.length==0||(this.message.length <= 100 && this.message.length >= 5);
            }
        },
        methods: {
          scrollToElement (id) {
            let el = document.getElementById(id)
            const target = getScrollTarget(el)
            const offset = el.offsetTop + 3
            const duration = 900
            setScrollPosition(target, offset, duration)
          },
          sendMsg () {
            this.$refs.userName.validate();
            this.$refs.message.validate();
            this.$refs.phone.validate();
            this.$refs.email.validate();
            if (!this.$refs.userName.hasError &&!this.$refs.message.hasError &&!this.$refs.phone.hasError && !this.$refs.email.hasError &&(this.email.length>0 || this.phone.length>0)) {
              let msgtxt=this.userName+'向你发起了联系请求,请即时处理\n联系邮箱：' +  this.email + '\n联系电话：'+this.phone+'\n咨询内容：'+this.message+'\n联系时间：'+new Date();
              this.$axios.post(
                'https://mandrillapp.com/api/1.0/messages/send',
                {
                  "key":"OaKg1wWehJpYDGKHS3tbvw",
                  "message":{
                      "from_email":"no-reply@qcldigital.com",
                      "subject":"联系我们 - qcldigital.com",
                      "text":msgtxt,
                      "to":[
                        {
                            "email":"tech.admin@qcldigital.com",
                            "type":"to"
                        }
                      ]
                  }
                },
                {
                  headers: {
                    'Content-Type' : 'application/json',
                  }
                }
                )
                .then((response) => {
                   this.$q.notify({
                     color: 'positive',
                     position: 'bottom',
                     message: this.$t('validation_msg2'),
                     icon: 'announcement'
                   });
                   this.$refs.userName.resetValidation();
                   this.$refs.phone.resetValidation();
                   this.$refs.email.resetValidation();
                   this.$refs.message.resetValidation();
                   this.userName = null;
                   this.phone = null;
                   this.email = null;
                   this.message = null;
                   this.$refs.form.reset();
                })
                .catch((error) => {
                   this.$q.notify({
                     color: 'negative',
                     position: 'bottom',
                     message: this.$t('validation_msg3'),
                     icon: 'report_problem'
                   });
                })
            }
          },
          hoverOver: function(index) {
            this['about_heading_color_' + index] = this.theme_color;
            this['about_heading_' + index] = ['animated', 'bounceIn'];
          },
          hoverOutTimeout: function(index) {
            this['about_heading_color_' + index] = '#424242';
            setTimeout(() => {
              this['about_heading_' + index] = [];
            }, 1000);
          },
          play () {
            this.$refs.lottie_web.play()
          },
          stop () {
            this.$refs.lottie_web.stop()
          },
          pause () {
            this.$refs.lottie_web.pause()
          },
          handleLottieFinish (isFinish) {
            // 事件处理
          },
          externalLink: function (link) {
              window.open(link, '_blank');
          },
          onScroll (info) {
            this.scrollInfo = info;
            if(info.position>=document.getElementById('id_portfolio').offsetTop&&info.position<document.getElementById('id_about_us').offsetTop) {
              this.selected_tab='t_0';
              this.active=true;
            }
            else {
              this.active=false;
            }
            if(info.position>=document.getElementById('id_about_us').offsetTop&&info.position<document.getElementById('id_services').offsetTop) this.selected_tab='t_1';
            if(info.position>=document.getElementById('id_services').offsetTop&&info.position<document.getElementById('id_contact_us').offsetTop) this.selected_tab='t_2';
            if(info.position>=document.getElementById('id_contact_us').offsetTop) this.selected_tab='t_3';
          }

        }
    }
</script>

<style lang="sass" scoped>
    .main_line
      font-size: 75px
      letter-spacing: 5px
      line-height: 60px
      font-weight: 600

    .custom-caption
      text-align: center
      padding: 12px
      color: white

    .animation_1
      -webkit-animation: bounceIn 1s ease-in 800ms both
      animation: bounceIn 1s ease-in 800ms both

    .animation_2
      -webkit-animation: flipInX 2s ease-in-out 800ms both
      animation: flipInX 1s ease-in-out 800ms both

    .animation_3
      -webkit-animation: lightSpeedIn 1s ease-in 800ms both
      animation: lightSpeedIn 1s ease-in 800ms both

    .description
      padding: 10px
      background-color: black
      color: white
      box-shadow: 1px 1px 2px #e6e6e6

    .my-header
      width: 200px
      top: 0
      max-height: 65px
      min-height: 25px
      color: black
      background-color: rgba(255,255,255, 0.8)
      text-transform: uppercase
      text-align: center
      font-size: 15px
      margin: 20px 0 0 68px
      padding: 5px 15px
      line-height: normal


    .my-text
      width: 100%
      top: 0
      height: 90px
      color: white
      text-align: center
      font-size: 15px
      margin: 79px 0 0 0
      padding: 20px
      line-height: normal
      font-family: Georgia, serif
      font-style: italic

    .my-button-container
      width: 100%

    .my-button
      text-decoration: none
      text-transform: uppercase
      margin: 0 0 20px 0
      text-align: center
      padding: 7px 14px
      background-color: #000
      color: #fff
      text-transform: uppercase
      box-shadow: 0 0 1px #000
      transition-delay: 0.2s

    .my-button:hover
      box-shadow: 0 0 5px #000

    .box-shadow:hover
      box-shadow: 0 10px 13px -6px rgba(0, 0, 0, 0.2), 0 20px 31px 3px rgba(0, 0, 0, 0.14), 0 8px 38px 7px rgba(0, 0, 0, 0.12) !important

    .my-card
      width: 350px
      max-width: 350px
      margin-top: 10px

    .team-header
      width: 100%
      top: 0
      height: 45px
      color: white
      text-transform: uppercase
      text-align: center
      font-size: 17px
      margin: 60px 0 0 0
      padding: 12px

    .team-text
      width: 100%
      top: 0
      height: 90px
      color: white
      text-align: center
      font-size: 15px
      margin: 100px 0 0 0
      padding: 20px
      line-height: normal
      font-family: Georgia, serif
      font-style: italic

    .quote
      background: url(/assets/parallax.jpg)
      background-size: cover
      background-position: center
      background-attachment: fixed
      background-repeat: no-repeat

    .pricing
      background: url(/assets/pricing.jpg)
      background-size: cover
      background-position: center
      background-attachment: fixed
      background-repeat: no-repeat

    .contact_us
      background: url(/assets/contact_us.jpg)
      background-size: cover
      background-position: center
      background-attachment: fixed
      background-repeat: no-repeat

    .custom_tab
      color: black

    .copy
      white-space: pre-line
</style>

