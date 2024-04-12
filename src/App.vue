<template>
  <div>
    <nav-bar 
             :data_url="dataUrl" 
             :default_index="defaultIndex" 
             @nav-link-clicked="handleNavLinkClick" 
      />
    <page-viewer :page="dataUrl[defaultIndex]" />
  </div>
</template>

<script>
import { ref } from 'vue';
import NavBar from './components/nav-bar.vue';
import PageViewer from './components/page-viewer.vue';

export default {
  name:'App',
  components: {
    NavBar,
    PageViewer,
  },
  setup() {
    const defaultIndex = ref(0);
    const dataUrl = ref([
      {
        heading: 'Main Section 1',
        subHeading: 'Subsection A',
        navTitle: 'Nav Title A',
        url: 'https://example.com/pageA'
      },
      {
        heading: 'Main Section 2',
        subHeading: 'Subsection B',
        navTitle: 'Nav Title B',
        url: 'https://example.com/pageB'
      },
      {
        heading: 'Main Section 3',
        subHeading: 'Subsection C',
        navTitle: 'Nav Title C',
        url: 'https://example.com/pageC'
      }
    ]);

    const handleNavLinkClick = (index) => {
      defaultIndex.value = index;
    };

    return { dataUrl, defaultIndex, handleNavLinkClick };
  }
}
</script>

<style scoped></style>
