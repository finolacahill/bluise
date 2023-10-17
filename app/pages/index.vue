<template>
  <section class="home">
    <div class="py-24 md:py-36 mx-auto flex flex-wrap flex-col md:flex-row items-center">
      <div class="flex flex-col w-full xl:w-3/5 justify-center lg:items-start overflow-y-hidden">
        <div v-html="$md.render(welcomeText)" class="home__welcome markdown" />
      </div>
      <div class="flex flex-col w-full xl:w-2/5">
        <img
          alt="Hero"
          class="rounded shadow-xl"
          src='images/uploads/IMG_873F1B136C54-1.jpeg'
        />
      </div>
    </div>
  </section>
</template>

<script lang="ts">
import { Component, Vue } from 'nuxt-property-decorator';
import settings from '@/content/settings/general.json';

@Component({
  transition() {
    return 'slide-left';
  },
})
export default class Home extends Vue {
  welcomeText = settings.welcomeText;
  isSignedUp = false;

  async asyncData({ app }) {
    const pageTitle = 'Finola Cahill Writer & Musician'; // Replace with your page title
    const pageDescription = 'Finola Cahill is an Irish poet, writer and musician from Co. Mayo in the west of Ireland. She is a member of Pembroke with Ellen Quinn Banville'; // Replace with your meta description
    
    // Set meta tags dynamically
    app.head = {
      title: pageTitle,
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: pageDescription,
        },
        // Add more meta tags if needed
      ],
    };

    return {
      // Your asyncData logic if any
    };
  }
}
</script>

<style lang="scss" scoped>
/* Your component-specific styles */
</style>
