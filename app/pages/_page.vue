<template>
  <section class="page" :class="page.slug">
    <div class="flex flex-col md:flex-row items-center">
      <div class="md:w-2/3 px-4 md:pr-8">
        <h1 class="page__title text-lg md:text-xl lg:text-4xl xl:text-6xl text-center py-8 md:py-16">
          {{ page.title }}
        </h1>

        <div v-html="$md.render(page.content)" class="page__content markdown pt-4 md:pt-6 md:pb-24" />
      </div>

      <img v-if="page.featuredImage" :src="page.featuredImage" alt="Featured Image" class="md:w-1/3 mx-auto my-4 md:my-0 rounded-md" />
    </div>
  </section>
</template>

<script lang="ts">
import { Component, Vue } from 'nuxt-property-decorator';
import { MetaInfo } from 'vue-meta';

// Define the Page interface here
interface Page {
  title: string;
  seoDescription: string;
  featuredImage?: string; // Make featuredImage optional
  content: string;
}

@Component({
  // ...existing component options...
})
export default class PageTemplate extends Vue {
  page!: Page;

  async asyncData({ params, payload }): Promise<{ page: Page }> {
    // ...existing asyncData function...
  }
}
</script>

<style scoped>
/* Add your custom styles here */
</style>
