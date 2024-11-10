<template>
  <main class="mainContainer">
    <p class="header">This course includes:</p>
    <ul>
      <li
        v-for="(icon, idx) in icons"
        :key="idx"
        class="listItem"
      >
        <div class="listItemIcon">
          <v-icon>{{ icon }}</v-icon>  <!-- Use Vuetify's v-icon component -->
        </div>
        <div class="itemText">
          <span class="black">{{ itemsText[idx] }}</span>
        </div>
      </li>
    </ul>
  </main>
</template>

<script>
export default {
  props: {
    details: Object
  },
  data() {
    const { content_length_video: seconds, num_additional_assets: downloadable } = this.details;
    
    const icons = [
      'mdi-video',              // for on-demand video
      'mdi-file-document',      // for article
      'mdi-download',           // for downloadable resources
      'mdi-infinity',           // for full lifetime access
      'mdi-cellphone',          // for mobile and TV access
      'mdi-certificate'         // for certificate of completion
    ];

    const itemsText = [
      `${parseInt(seconds / 60 / 60)} hours on-demand video`,
      '1 article',
      `${downloadable} downloadable resources`,
      'Full lifetime access',
      'Access on mobile and TV',
      'Certificate of completion'
    ];

    return { icons, itemsText };
  }
};
</script>

<style scoped>
.header {
  font-weight: 700;
  font-size: 25px;
}

.black {
  color: #1c1d1f;
}

.listItem {
  padding: 0 0 0 1rem;
}

.itemText {
  margin-left: -1rem;
}
</style>


<!-- <template>
    <main class="mainContainer">
      <p class="header">This course includes:</p>
      <ul>
        <li
          v-for="(icon, idx) in icons"
          :key="idx"
          class="listItem"
        >
          <div class="listItemIcon">{{ icon }}</div>
          <div class="itemText">
            <span class="black">{{ itemsText[idx] }}</span>
          </div>
        </li>
      </ul>
    </main>
  </template>
  
  <script>
  import { 
    AllInclusive, 
    Download, 
    EmojiEvents, 
    InsertDriveFile, 
    OndemandVideo, 
    StayCurrentPortrait 
  } from '@mui/icons-material';
  
  export default {
    props: {
      details: Object
    },
    data() {
      const { content_length_video: seconds, num_additional_assets: downloadable } = this.details;
      
      // Update icons to use Vue components instead of JSX-like elements
      const icons = [
        OndemandVideo,
        InsertDriveFile,
        Download,
        AllInclusive,
        StayCurrentPortrait,
        EmojiEvents
      ];
  
      const itemsText = [
        `${parseInt(seconds / 60 / 60)} hours on-demand video`,
        '1 article',
        `${downloadable} downloadable resources`,
        'Full lifetime access',
        'Access on mobile and TV',
        'Certificate of completion'
      ];
  
      return { icons, itemsText };
    }
  };
  </script>
  
  <style scoped>
  /* Add your styles here */
  .header {
    font-weight: 700;
    font-size: 25px;
  }
  
  .black {
    color: #1c1d1f;
  }
  
  .listItem {
    padding: 0 0 0 1rem;
  }
  
  .itemText {
    margin-left: -1rem;
  }
  </style>
   -->