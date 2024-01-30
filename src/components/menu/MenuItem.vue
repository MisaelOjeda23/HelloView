<template>
    <div class="wrapper">
        <HelloWorld msg="Wow, You did it!" />
        <nav>
            <RouterLink to="">Home</RouterLink>
            <RouterLink to="/about">About</RouterLink>
        </nav>
    </div>
</template>

<script lang="ts" setup>
import type IMenuItem from '@/interface/IMenuItem';

const data = defineProps<IMenuItem>();

</script>