<template>
  <div>
    <SfTopBar>
      <template #center>
        <p style="margin-right: 5px;">Download our application.</p>
        <SfButton class="sf-button--text">Find out more</SfButton>
      </template>
    </SfTopBar>
    <sf-header
      :title="title"
      :logo="logo"
      :active-icon="activeIcon"
      :search-placeholder="searchPlaceholder"
      :search-value="searchValue"
      :cart-icon="cartIcon"
      :wishlist-icon="wishlistIcon"
      :is-sticky="isSticky"
      :account-icon="accountIcon"
      :cart-items-qty="cartItemsQty"
      :class="customClass"
      @click:cart="console.log('@click:cart')"
      @click:wishlist="console.log('@click:wishlist')"
      @click:account="console.log('@click:account')"
      @change:search="searchValue = $event"
    >
      <template #search>
        <SfSearchBar
          :class="'customClass'"
          :placeholder="searchPlaceholder"
          aria-label="Search"
          v-model="searchValue"
        />
      </template>
      <template #navigation>
        <SfHeaderNavigationItem v-for="item in navigation" :key="item">
          <SfLink href="#">{{ item }}</SfLink>
        </SfHeaderNavigationItem>
      </template>
    </sf-header>
    <Nuxt />
    <div style="max-width: 1240px; margin: auto;">
      <SfCallToAction
        :title="cta.title"
        :description="cta.description"
        :button-text="cta.buttonText"
        :image="cta.image"
        :background="cta.background"
      />
    </div>
    <SfFooter :column="column" :multiple="multiple">
      <SfFooterColumn
        v-for="column in columns"
        :key="column.title"
        :title="column.title"
      >
        <SfList v-if="column.items">
          <SfListItem v-for="item in column.items" :key="item">
            <SfMenuItem :label="item" />
          </SfListItem>
        </SfList>
        <div v-else :style="{ display: 'flex' }">
          <SfImage
            v-for="picture in column.pictures"
            :key="picture"
            width="12"
            height="12"
            :src="'/assets/storybook/SfFooter/' + picture + '.svg'"
            :style="{ margin: '0 1.5rem 0 0' }"
          />
        </div>
      </SfFooterColumn>
    </SfFooter>
    <SfBottomNavigation :class="customClass1">
      <SfBottomNavigationItem
        :icon="icon"
        :label="label"
        :icon-active="iconActive"
        :is-active="currentIcon === iconActive"
        @click="currentIcon = iconActive"
      />
      <SfBottomNavigationItem
        v-for="(item, key) in items"
        :key="key"
        :icon="item.icon"
        :icon-active="item.iconActive"
        :label="item.label"
        icon-size="20px"
        :is-active="currentIcon === item.iconActive"
        @click="currentIcon = item.iconActive"
      />
      <SfBottomNavigationItem label="Basket" icon="add_to_cart" is-floating />
    </SfBottomNavigation>
  </div>
</template>

<script>
import {
  SfTopBar,
  SfLink,
  SfButton,
  SfHeader,
  SfIcon,
  SfBar,
  SfImage,
  SfBottomNavigation,
  SfFooter,
  SfMenuItem,
  SfList,
  SfCallToAction,
  SfSearchBar,
} from '@storefront-ui/vue'
export default {
  components: {
    SfTopBar,
    SfButton,
    SfHeader,
    SfLink,
    SfIcon,
    SfBar,
    SfImage,
    SfBottomNavigation,
    SfFooter,
    SfMenuItem,
    SfList,
    SfCallToAction,
    SfSearchBar,
  },
  data() {
    return {
      isMobile: true,
      navigation: ['women', 'man', 'kids', 'more'],
      searchValue: '',
      title: 'Storefront UI',
      logo: '/logo.svg',
      activeIcon: 'account',
      isSticky: false,
      searchPlaceholder: 'Search for items',
      menuIcon: 'list',
      cartIcon: 'empty_cart',
      wishlistIcon: 'heart',
      accountIcon: 'profile',
      cartItemsQty: '12',
      customClass: 'sf-header--multiline sf-header--has-mobile-search',
      customClass1: 'remove-desktop',
      // logo: {
      //   mobile: { url: '/assets/logo.svg' },
      //   desktop: { url: '/assets/logo.svg' },
      // },
      items: [
        { icon: 'menu', iconActive: '', label: 'Menu' },
        { icon: 'heart', iconActive: 'heart_fill', label: 'Heart' },
        { icon: 'profile', iconActive: 'profile_fill', label: 'Profile' },
      ],
      currentIcon: 'heart_fill',
      label: 'Home',
      icon: 'home',
      iconActive: 'home_fill',
      //ffff

      columns: [
        {
          title: 'About us',
          items: ['Who we are', 'Quality in the details', 'Customer Reviews'],
        },
        {
          title: 'Departments',
          items: ['Women fashion', 'Men fashion', 'Kidswear', 'Home'],
        },
        {
          title: 'Help',
          items: ['Customer service', 'Size guide', 'Contact us'],
        },
        { title: 'Payment & delivery', items: ['Purchase terms', 'Guarantee'] },
        {
          title: 'Social',
          pictures: ['facebook', 'pinterest', 'twitter', 'youtube'],
        },
      ],
      column: 4,
      multiple: false,
      cta: {
        title: 'Subscribe to Newsletters',
        description:
          'Be aware of upcoming sales and events. Receive gifts and special offers!',
        buttonText: 'Subscribe',
        image: 'assets/storybook/Home/newsletter.jpg',
        background: '#e1e3e2',
      },
    }
  },
}
</script>

<style lang="scss">
@import '@storefront-ui/vue/styles.scss';
:root {
  @include generate-color-variants(--_c-green-primary, #1d1f22);
  @include assign-color-variants(--c-primary, --_c-green-primary);
}

body {
  margin: 0;
  padding: 0;
}

* {
  box-sizing: border-box;
}

.top-logo {
  background: #ffffff;
  width: 100%;
  padding: 15px;
}

@media only screen and (max-width: 1023px) {
  .remove-mobile {
    display: none;
  }
}

@media only screen and (min-width: 1024px) {
  .remove-desktop {
    display: none;
  }
}
</style>
