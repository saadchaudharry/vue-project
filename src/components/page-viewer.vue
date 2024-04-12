<template>

    <div class="container">
        <h1>{{ page.heading }}</h1>
        <h3>{{ page.subHeading }}</h3>
    </div>

</template>

<script>
import { ref } from 'vue';

export default {
  name: 'page-viewer',
  props: ['page']
}
</script>

<style></style>