<script setup lang="ts">

const articles = ref([
  {
    title: 'Hydrogen VS Electric Cards',
    desc: 'Will hydrogen-fueled cars ever catch up to EVs?',
    url: '#',
  },
  {
    title: 'The Downsides of AI Artistry',
    desc: 'What are the possible adverse effects of on-demand AI image generation?',
    url: '#',
  },
  {
    title: 'Is VC Funding Drying Up?',
    desc: 'Private funding by VC firms is down 50% YOY. We take a look at what that means.',
    url: '#',
  },
])

const featuredArticles = ref([
  {
    title: 'Reviving Retro PCs',
    desc: 'What happens when old PCs are given modern upgrades?',
    img: '/_nuxt/assets/images/image-retro-pcs.jpg',
    url: '#',
  },
  {
    title: 'Top 10 Laptops of 2022',
    desc: 'Our best picks for various needs and budgets.',
    img: '/_nuxt/assets/images/image-top-laptops.jpg',
    url: '#',
  },
  {
    title: 'The Growth of Gaming',
    desc: 'How the pandemic has sparked fresh opportunities.',
    img: '/_nuxt/assets/images/image-gaming-growth.jpg',
    url: '#',
  },
])

const burgerTriggered = ref(false)

const toggleBurger = () => {
  burgerTriggered.value = !burgerTriggered.value
}



</script>

<template>
  <header class="container mx-auto px-4 mt-7 flex w-full justify-between items-center">
    <iconsLogo />
    <nav class="gap-8 lg:flex hidden ">
      <nuxt-link
        class="hover:text-[var(--secondary)]"
        to="#"
      >Home</nuxt-link>
      <nuxt-link
        class="hover:text-[var(--secondary)]"
        to="#"
      >Popular</nuxt-link>
      <nuxt-link
        class="hover:text-[var(--secondary)]"
        to="#"
      >Trending</nuxt-link>
      <nuxt-link
        class="hover:text-[var(--secondary)]"
        to="#"
      >Categories</nuxt-link>
    </nav>
    <div
      @click="toggleBurger"
      :class="{
        burger: true,
        'burger--active': burgerTriggered
      }"
      class="burger-wrapper"
    >
      <div class="burger-line">
      </div>
    </div>
    <div
      :class="{
        'mobile-nav-wrapper': true,
        'mobile-nav-wrapper--active': burgerTriggered
      }"
      class="mobile-nav-wrapper"
      @click="toggleBurger"
    >
      <div
        :class="{
          'mobile-nav': true,
          'mobile-nav--active': burgerTriggered
        }"
        class="mobile-nav"
        @click.stop
      >
        <nav>
          <nuxt-link to="#">Home</nuxt-link>
          <nuxt-link to="#">Popular</nuxt-link>
          <nuxt-link to="#">Trending</nuxt-link>
          <nuxt-link to="#">Categories</nuxt-link>
        </nav>
      </div>
    </div>
  </header>
  <section class="hero py-9">
    <div class="container mx-auto lg:grid lg:grid-cols-3 lg:gap-4">
      <div class="featured-article px-4 mx-auto pt-7 flex flex-col gap-7 lg:pt-0 items-start lg:col-span-2">
        <picture class="w-full">
          <source
            media="(max-width: 767px)"
            srcset="~/assets/images/image-web-3-mobile.jpg"
          >
          <source
            media="(min-width: 767px)"
            srcset="~/assets/images/image-web-3-desktop.jpg"
          >
          <img
            class="hero__image"
            alt="Web 3.0"
          >
        </picture>
        <div class="hero__content grid grid-cols-1 lg:grid-cols-2 gap-4 lg:items-stretch">
          <a href="#">
            <h2 class="hero__heading text-[40px] font-bold leading-none lg:text-5xl lg:leading-tight">
              The Bright Future of Web 3.0?
            </h2>
          </a>
          <div class="hero__body flex flex-col gap-7 items-start">
            <p class="text-[15px] text-neutral-500 leading-6 ">
              We dive into the next evolution of the web that claims to put the power of the platforms back into the
              hands
              of the people. But is it really fulfilling its promise?
            </p>
            <a
              class="hero__read-more text-[14px] lg:hover:bg-[var(--secondary)] font-bold leading-none tracking-[.5ch] uppercase px-8 py-5 bg-[#F15D51] lg:bg-black text-white font-normal lg:mt-auto"
              href="#"
            >Read More</a>
          </div>
        </div>
      </div>
      <div class="new-articles bg-[#00001A] container px-4 mx-auto py-7 lg:mt-0 mt-10 flex flex-col gap-7 items-start">
        <h2 class="text-4xl text-[var(--action)] font-semibold">
          New
        </h2>
        <ul class="new-articles-list grid grid-cols-1 gap-7">
          <li
            v-for="(article, index) in articles"
            :key="index"
            class="new-article-card text-white flex flex-col gap-3"
          >
            <a
              class="hover:text-[var(--action)]"
              :href="article.url"
            >
              <h3 class="new-article-card__heading text-xl font-extrabold"> {{ article.title }} </h3>
            </a>
            <p class="new-article-card__desc text-neutral-300">{{ article.desc }}</p>
          </li>
        </ul>
      </div>
    </div>
  </section>
  <section class="featured-articles-section">
    <ul
      class="container px-4 mx-auto pt-7 grid grid-cols-1 gap-7 lg:grid-cols-3 items-start featured-articles-list items-stretch"
    >
      <li
        v-for="(article, index) in featuredArticles"
        :key="index"
        class="featured-article-card grid grid-cols-3 gap-4"
      >
        <picture class="col-span-1 object-cover">
          <source :srcset="article.img">

          <img
            class="featured-article-card__image"
            :alt="article.title"
          >
        </picture>
        <div class="featured-article-card__body col-span-2 flex flex-col gap-1 justify-between py-2">
          <div class="featured-article-card__counter text-neutral-400 text-2xl lg:text-4xl font-extrabold">0{{ index + 1
          }}</div>
          <a
            class="hover:text-[var(--secondary)]"
            :href="article.url"
          >
            <h3 class="featured-article-card__heading text-xl font-extrabold"> {{ article.title }} </h3>
          </a>
          <p class="featured-article-card__desc text-neutral-400">{{ article.desc }}</p>
        </div>
      </li>
    </ul>
  </section>
</template>



<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap');


:root {
  --action: #E9AA52;
  --secondary: #F15D51;
}

html {
  scroll-behavior: smooth;
  font-family: 'Inter', sans-serif;
}

.burger {
  &-wrapper {
    width: 40px;
    height: 17px;
    position: relative;
    display: none;
    cursor: pointer;
    z-index: 9999;

    @media (max-width: 768px) {
      display: block;
    }
  }

  &-line {
    width: 100%;
    height: 3px;
    background-color: #000;
    position: absolute;
    top: 50%;
    left: 0;
    transform: translateY(-50%);

    &:before,
    &:after {
      content: "";
      width: 100%;
      height: 3px;
      background-color: #000;
      position: absolute;
      left: 0;
      transition: all 0.3s ease;
    }

    &:before {
      top: -7px;
    }

    &:after {
      top: 7px;
    }
  }

  &--active {
    .burger-line {
      background-color: transparent;

      &:before,
      &:after {
        top: 0;
        background-color: #000;
      }

      &:before {
        transform: rotate(45deg);
      }

      &:after {
        transform: rotate(-45deg);
      }
    }
  }
}



.mobile-nav {
  position: fixed;
  top: 0;
  right: 0;
  width: 70%;
  height: 100vh;
  background-color: #fff;
  z-index: 999;
  transform: translateX(150%);
  transition: all 0.3s ease;

  &-wrapper {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100vh;
    opacity: 0;
    z-index: 999;
    transition: all 0.3s ease;
    background-color: transparent;
    pointer-events: none;



    &--active {
      opacity: 1;
      background-color: rgba(0, 0, 0, 0.5);
      pointer-events: all;

    }

  }


  &--active {
    transform: translateX(0);
  }

  nav {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    height: 100%;

    a {
      margin: 20px 0;
      font-size: 24px;
    }
  }
}

img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.new-article {
  &-card:not(:last-child) {
    padding-bottom: 30px;
    border-bottom: 1px solid #555;
  }


}
</style>