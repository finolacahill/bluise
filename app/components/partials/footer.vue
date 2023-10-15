<template>
  <footer class="footer -mx-4 md:mx-0">
    <div class="container mx-auto pb-6 flex justify-center">
      <a href="https://www.instagram.com/fifinolala">
        <img src="images/uploads/instagram.png" alt="Instagram" class="icon" />
      </a>
      <a href="https://twitter.com/finolala">
        <img src="images/uploads/twitter.png" alt="Twitter" class="icon" />
      </a>
      <a href="https://open.spotify.com/album/47eIpq5u7jcVrBio0zWlAg?si=zVQqXWTsQ_mEbHmp-1o2AQ">
        <img src="images/uploads/spotify.png" alt="Spotify" class="icon" />
      </a>
      
    </div>
  </footer>
</template>

<script lang="ts">
import { Component, Vue } from 'nuxt-property-decorator';

@Component
export default class Footer extends Vue {}
</script>

<style lang="scss">
.footer {
  background-color: #01050a;
}

.icon {
  width: 24px; /* Adjust the width as needed */
  height: 24px; /* Adjust the height as needed */
  margin: 0 10px; /* Adjust the margin between icons as needed */
}
</style>
