<template>
  <section class="page" :class="page.slug">
    <div class="flex flex-col md:flex-row items-center">
      <div class="md:w-2/3 px-4 md:pr-8">
        <h1 class="page__title text-lg md:text-xl lg:text-4xl xl:text-6xl text-center py-8 md:py-16">
          {{ page.title }}
        </h1>

        <div v-html="$md.render(page.content)" class="page__content markdown pt-4 md:pt-6 md:pb-24" />
      </div>

      <img
        v-if="page.featuredImage"
        :src="page.featuredImage"
        alt="Featured Image"
        class="md:h-74 md:ml-4 rounded-md align-middle"
      />
    </div>
  </section>
</template>

<script lang="ts">
import { Component, Vue } from 'nuxt-property-decorator';
import { MetaInfo } from 'vue-meta';

interface Page {
  title: string;
  seoDescription: string;
  featuredImage?: string;
  content: string;
}

@Component({
  transition(to, from) {
    if (!from) {
      return 'slide-left';
    }
    return 'slide-right';
  }
})
export default class PageTemplate extends Vue {
  page: Page = {
    title: '',
    seoDescription: '',
    content: ''
  };

  head(): MetaInfo {
    return {
      title: this.page.title,
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: this.page.seoDescription
        },
        {
          hid: 'og:image',
          name: 'og:image',
          content: this.page.featuredImage || ''
        }
      ]
    };
  }

  async asyncData({ params, payload }): Promise<{ page: Page }> {
    try {
      const page = require(`@/content/pages/${params.page}.json`);
      return { page };
    } catch (error) {
      throw new Error('Page not found');
    }
  }
}
</script>

<style scoped>
/* Add your custom styles here */
</style>
