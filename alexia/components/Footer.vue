<template>
<div class="flex justify-between text-white bg-blu p-6 items-center">
    <div class="logo color h-full flex justify-center">
        <img src="../public/white_logo.svg" alt="" class="w-60">
    </div>
    <div class="flex gap-4">
        <div class="flexflex-col">
            <a class="flex items-center" href="https://www.youtube.com/watch?v=ABfQuZqq8wg">
                <PhArrowUpLeft :size="35"></PhArrowUpLeft>
                <h3>
                    EMAIL
                </h3>
            </a>
            <a class="flex items-center" href="https://www.youtube.com/watch?v=ABfQuZqq8wg">
                <PhArrowUpLeft :size="35"></PhArrowUpLeft>
                <h3>
                    INSTAGRAM
                </h3>
            </a>
            <a class="flex items-center" href="https://www.youtube.com/watch?v=ABfQuZqq8wg">
                <PhArrowUpLeft :size="35"></PhArrowUpLeft>
                <h3>
                    BEHANCE
                </h3>
            </a>
            <a class="flex items-center" href="https://www.youtube.com/watch?v=ABfQuZqq8wg">
                <PhArrowUpLeft :size="35"></PhArrowUpLeft>
                <h3>
                    LINKEDIN
                </h3>
            </a>
        </div>
        <div class="date">
            /25
        </div>
    </div>
</div>
</template>


<script setup>
    import { PhArrowUpLeft } from "@phosphor-icons/vue";
</script>


<style lang="sass" scoped>

</style>