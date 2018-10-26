<template>
  <div class="bannerCarousel">

    <div class="bannerCarousel__wrap">
      <div class="bannerCarousel_ui">
        <button class="bannerCarousel__button"
          @click="back()"
          :disabled="visible_content == 0"
        >＜</button >
      </div>

        <div class="bannerCarousel__stage">
          <ul class="bannerCarousel__inner"
            :style="bannerCarouselStyle"
          >
            <li class="bannerCarousel__item"
              v-for="(item, index) in banners"
              :key="index"
            >
              <img class="bannerCarousel__itemImage"
                :src="item.imagePath"
                :alt="item.alt"
              >
            </li>
          </ul>
        </div>

      <div class="bannerCarousel_ui">
        <button class="bannerCarousel__button"
          @click="next()"
          :disabled="visible_content == banners.length - 1"
        >＞</button>
      </div>
    </div>

    <ul class="bannerCarousel__mark">
      <li class="bannerCarousel__markItem"
        v-for="(item, index) in banners"
        :key="index"
        :class="{'bannerCarousel__markItem--visible' : visible_content == index}"
      ></li>
    </ul>

  </div>
</template>

<script>

export default {
  name: 'BannerCarousel',
  data: function() {
    return {
      banners: [
        {
          imagePath: require('../assets/banner/banner1.jpg'),
          href: 'https://www.flickr.com/photos/jun-finder/',
          alt: 'Banner1',
        },
        {
          imagePath: require('../assets/banner/banner2.jpg'),
          href: 'https://www.flickr.com/photos/jun-finder/',
          alt: 'Banner2',
        },
        {
          imagePath: require('../assets/banner/banner3.jpg'),
          href: 'https://www.flickr.com/photos/jun-finder/',
          alt: 'Banner3',
        },
        {
          imagePath: require('../assets/banner/banner4.jpg'),
          href: 'https://www.flickr.com/photos/jun-finder/',
          alt: 'Banner4',
        },
      ],
      transition_name: 'show-next',
      visible_content: 0,
    }
  },
  methods: {
    back() {
      this.transition_name = 'show-prev'
      this.visible_content --
    },
    next() {
      this.transition_name = 'show-next',
      this.visible_content ++
    },
  },
  computed: {
    bannerCarouselStyle() {
      return {
        width: this.banners.length * 640 + 'px',
        transform: 'translateX(' + this.visible_content * -640 + 'px)'
      }
    },
  },
}
</script>

<style lang="scss">
.bannerCarousel {
  width: 820px;
  margin: 0 auto;
  &__wrap {
    display: flex;
    align-items: center;
  }

  &__stage {
    width: 640px;
    overflow: hidden;
  }

  &_ui {
    padding: 0 10px;
    width: 90px;
  }

  &__inner {
    padding: 0;
    margin: 0;
    display: flex;
    top: 0;
    transition: all 0.4s;
  }

  &__item {
    list-style: none;
    margin-right: 5px;
  }

  &__itemImage {
    width: 100%;
  }

  &__button {
    border: solid 1px #ddd;
    background: #fff;
    color: #dddddd;
    width: 70px;
    height: 70px;
    border-radius: 35px;
    line-height: 70px;
    font-size: 35px;
    font-weight: bold;
    box-shadow: 2px 2px 5px rgba(0, 0, 0, 0.4);
    outline: none;

    &:hover {
      opacity: 0.7;
    }
    &:active {
      transform: translate(2px, 2px);
      box-shadow: none;
    }
  }

  &__mark {
    padding: 0;
    margin-top: 12px;
  }

  &__mark {
    display: flex;
    justify-content: center;
  }

  &__markItem {
    list-style: none;
    width: 12px;
    height: 12px;
    background: #ddd;
    border-radius: 3px;
    margin-right: 5px;

    &--visible {
      background: #ccc;
    }
  }
}
</style>
