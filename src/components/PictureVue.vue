<template>
  <div>
    <div v-for="item in value">
      <a v-on:click="swipe" v-if="item.thumb && withGallery">
        <img :src="item.thumb" :class="classes"/>
      </a>
      <img v-if="item.thumb && !withGallery" :src="item.thumb" :class="classes"/>
    </div>
    <div v-if="withGallery" class="pswp" tabindex="-1" role="dialog" aria-hidden="true">

      <!-- Background of PhotoSwipe.
           It's a separate element as animating opacity is faster than rgba(). -->
      <div class="pswp__bg"></div>

      <!-- Slides wrapper with overflow:hidden. -->
      <div class="pswp__scroll-wrap">

        <!-- Container that holds slides.
            PhotoSwipe keeps only 3 of them in the DOM to save memory.
            Don't modify these 3 pswp__item elements, data is added later on. -->
        <div class="pswp__container">
          <div class="pswp__item"></div>
          <div class="pswp__item"></div>
          <div class="pswp__item"></div>
        </div>

        <!-- Default (PhotoSwipeUI_Default) interface on top of sliding area. Can be changed. -->
        <div class="pswp__ui pswp__ui--hidden">

          <div class="pswp__top-bar">

            <!--  Controls are self-explanatory. Order can be changed. -->

            <div class="pswp__counter"></div>

            <button class="pswp__button pswp__button--close" title="Close (Esc)"></button>

            <button class="pswp__button pswp__button--share" title="Share"></button>

            <button class="pswp__button pswp__button--fs" title="Toggle fullscreen"></button>

            <button class="pswp__button pswp__button--zoom" title="Zoom in/out"></button>

            <!-- Preloader demo http://codepen.io/dimsemenov/pen/yyBWoR -->
            <!-- element will get class pswp__preloader--active when preloader is running -->
            <div class="pswp__preloader">
              <div class="pswp__preloader__icn">
                <div class="pswp__preloader__cut">
                  <div class="pswp__preloader__donut"></div>
                </div>
              </div>
            </div>
          </div>

          <div class="pswp__share-modal pswp__share-modal--hidden pswp__single-tap">
            <div class="pswp__share-tooltip"></div>
          </div>

          <button class="pswp__button pswp__button--arrow--left" title="Previous (arrow left)">
          </button>

          <button class="pswp__button pswp__button--arrow--right" title="Next (arrow right)">
          </button>

          <div class="pswp__caption">
            <div class="pswp__caption__center"></div>
          </div>

        </div>

      </div>

    </div>
  </div>
</template>

<script>
  import PhotoSwipe from 'photoswipe'
  import PhotoSwipeUIDefault from '../../node_modules/photoswipe/dist/photoswipe-ui-default.min'

  export default {
    props: {
      value: null,
      withGallery: null,
      classes: ''
    },
    data () {
      return {
      }
    },
    name: 'PictureView',
    mounted: function () {
    },
    methods: {
      thumb: function (bytes) {
        return 'data:image/png;base64,' + bytes
      },
      swipe: function () {
        let pswpElement = document.querySelectorAll('.pswp')[0]
        let options = {
          history: false,
          focus: false,
          showAnimationDuration: 0,
          hideAnimationDuration: 0
        }
        let gallery = new PhotoSwipe(pswpElement, PhotoSwipeUIDefault, this.value, options)
        gallery.init()
      }
    }
  }
</script>

<style scoped>
</style>
