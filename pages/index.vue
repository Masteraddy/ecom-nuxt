<template>
  <div style="background: #f8f8f8;">
    <SfHero :style="{ maxWidth: '1240px', margin: 'auto' }">
      <template v-for="item in banners">
        <SfHeroItem
          :class="item.class"
          :title="item.title"
          :key="item.slot"
          :subtitle="item.subtitle"
          :button-text="item.buttonText"
          :image="item.image"
          :background="item.background"
        />
      </template>
      <!-- <SfHeroItem
        title="Colorful summer dresses are already in store"
        subtitle="Summer Collection 2019"
        button-text="Learn more"
        image="/assets/storybook/SfHero/hero.png"
        background="#FCE4EC"
      /> -->
    </SfHero>
    <SfHeading
      :class="customClass"
      :level="level"
      :title="'Explore the Exclusiveness'"
      :subtitle="subtitle"
      :style="{ padding: '1rem' }"
    />
    <SfCarousel :style="{ maxWidth: '1240px', margin: 'auto' }">
      <template v-for="item in 8">
        <SfProductCard
          :key="item"
          :style="{ margin: '5px' }"
          :badge-label="badgeLabel"
          :badge-color="badgeColor"
          :title="title"
          :link="link"
          :link-tag="linkTag"
          :score-rating="scoreRating"
          :max-rating="maxRating"
          :reviews-count="reviewsCount"
          :regular-price="regularPrice"
          :special-price="specialPrice"
          :wishlist-icon="wishlistIcon"
          :is-on-wishlist-icon="isOnWishlistIcon"
          :is-on-wishlist="isOnWishlist"
          :show-add-to-cart-button="showAddToCartButton"
          :add-to-cart-disabled="addToCartDisabled"
          :is-added-to-cart="isAddedToCart"
          @click:is-added-to-cart="alert('@click:is-added-to-cart')"
          @click:wishlist="alert('@click:wishlist')"
          @click:reviews="alert('@click:reviews')"
        >
          <template #image>
            <SfImage :src="image" :alt="title" :lazy="lazy" />
          </template>
        </SfProductCard>
      </template>
    </SfCarousel>
    <div
      :style="{
        maxWidth: '1240px',
        margin: 'auto',
        marginTop: '1.5rem',
        marginBottom: '1.5rem',
        display: 'grid',
        gridGap: '5px',
        gridTemplateColumns: 'repeat(auto-fit, minmax(216px, 1fr))',
      }"
    >
      <template v-for="item in banners">
        <SfBanner
          :style="item.style"
          :key="item.slot"
          :title="item.title"
          :subtitle="item.subtitle"
          :description="item.description"
          :button-text="item.buttonText"
          image="item.image"
          :background="item.background"
          :class="item.class"
        />
      </template>
    </div>
    <SfHeading
      :class="customClass"
      :level="level"
      :title="'Explore Xclusiveness'"
      :subtitle="subtitle"
      :style="{ padding: '1rem' }"
    />
    <div class="homeproducts">
      <template v-for="item in 10">
        <SfProductCard
          :class="productClass"
          :key="item"
          :badge-label="badgeLabel"
          :badge-color="badgeColor"
          :title="title"
          :link="link"
          :link-tag="linkTag"
          :score-rating="scoreRating"
          :max-rating="maxRating"
          :reviews-count="reviewsCount"
          :regular-price="regularPrice"
          :special-price="specialPrice"
          :wishlist-icon="wishlistIcon"
          :is-on-wishlist-icon="isOnWishlistIcon"
          :is-on-wishlist="isOnWishlist"
          :show-add-to-cart-button="showAddToCartButton"
          :add-to-cart-disabled="addToCartDisabled"
          :is-added-to-cart="isAddedToCart"
          @click:is-added-to-cart="alert('@click:is-added-to-cart')"
          @click:wishlist="alert('@click:wishlist')"
          @click:reviews="alert('@click:reviews')"
        >
          <template #image>
            <SfImage :src="image" :alt="title" :lazy="lazy" />
          </template>
        </SfProductCard>
      </template>
    </div>
    <div style="margin: 1rem;"></div>
    <!-- Categories -->
  </div>
</template>
<script>
import {
  SfHero,
  SfBanner,
  SfBannerGrid,
  SfHeading,
  SfProductCard,
  SfImage,
  SfCarousel,
} from '@storefront-ui/vue'
export default {
  components: {
    SfHero,
    SfBanner,
    SfBannerGrid,
    SfHeading,
    SfProductCard,
    SfImage,
    SfCarousel,
  },
  data() {
    return {
      // title: 'Colorful summer dresses are already in store',
      subtitle: '# Summer Collection 2019',
      // buttonText: 'Learn more',
      // image: {
      //   mobile: '/assets/storybook/SfHero/hero.png',
      //   desktop: '/assets/storybook/SfHero/hero.png',
      // },
      // background: '#ECEFF1',
      customClass: '',
      level: 2,

      image: '/product-white.png',
      imageWidth: 216,
      imageHeight: 326,
      badgeLabel: '-50%',
      badgeColor: 'color-primary',
      title: 'Cotton Sweater',
      link: '',
      linkTag: '',
      scoreRating: 4,
      maxRating: 5,
      reviewsCount: 7,
      regularPrice: '$10.99',
      specialPrice: '$5.09',
      wishlistIcon: 'heart',
      isOnWishlistIcon: 'heart_fill',
      isOnWishlist: false,
      showAddToCartButton: true,
      isAddedToCart: false,
      addToCartDisabled: false,
      productClass: 'productit',
      lazy: true,

      banners: [
        {
          slot: 'banner-A',
          subtitle: 'Dresses',
          title: 'Cocktail & Party',
          description:
            "Find stunning women's cocktail dresses and party dresses. Stand out in lace and metallic cocktail dresses from all your favorite brands.",
          buttonText: 'Shop now',
          image: '/assets/storybook/Home/bannerF.jpg',
          class: 'sf-banner--slim',
          background: '#ECEFF1',
        },
        {
          slot: 'banner-B',
          subtitle: 'Dresses',
          title: 'Linen Dresses',
          description:
            "Find stunning women's cocktail dresses and party dresses. Stand out in lace and metallic cocktail dresses from all your favorite brands.",
          buttonText: 'Shop now',
          image: '/assets/storybook/Home/bannerE.jpg',
          class: 'sf-banner--slim',
          background: '#ECEFF1',
          // style: 'padding-right: 20%',
        },
      ],
      bannerGrid: 1,
    }
  },
}
</script>

<style lang="scss" scoped>
$image-width: 100%;
.productit {
  max-width: 100%;
}

.homeproducts {
  max-width: 1024px;
  margin-top: 1.5rem;
  margin-bottom: 2rem;
  margin: auto;
  display: grid;
  grid-gap: 5px;
  grid-template-columns: repeat(auto-fit, minmax(170px, 1fr));
  justify-content: center;
}
</style>
