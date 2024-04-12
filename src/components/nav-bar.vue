<template>
    <nav class="navbar navbar-expand-lg bg-body-tertiary  " :data-bs-theme="get_theme">
        <div class="container-fluid">
            <a class="navbar-brand" @click.prevent="default_index = 0">Navbar</a>
            <button class="navbar-toggler" type="button" data-bs-toggle="collapse"
                data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false"
                aria-label="Toggle navigation">
                <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse" id="navbarSupportedContent">
                <ul class="navbar-nav me-auto mb-2 mb-lg-0">

                    <li v-for="(item, index) in data_url" :key="index" class="nav-item">
                        <a class="nav-link " :class="{ active: default_index == index }" :href="item.url"
                            @click.prevent="emaitt(index)">
                            {{ item.navTitle }}
                        </a>
                    </li>

                </ul>
                <form class="d-flex" role="search">
                    <button class="btn btn-outline-success"
                        @click.prevent="dark_theme = !dark_theme;">Toggle Theme</button>
                </form>

            </div>
        </div>
    </nav>


</template>

<script>
import { ref,computed } from 'vue';

export default {
    name:'nav-bar',
    props: ['data_url', 'default_index'],
    emits: ['nav-link-clicked'],

    setup(props, { emit }) {
        const dark_theme = ref(1);

        const emaitt = (index) => {
            emit('nav-link-clicked', index);
        };

        const get_theme = computed(() => {
            return dark_theme.value ? 'dark' : 'light'
        })
        return { get_theme, dark_theme, emaitt };

    },
}
</script>

<style></style>