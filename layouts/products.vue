<template>
    <div>
        <div class="min-h-screen font-sans antialiased relative">
            <div class="relative">
                <div
                    class="absolute top-0 left-0 w-full h-[125vh] sm:h-[225vh] lg:h-[125vh] cover-gradient-2 sm:cover-gradient"
                ></div>
                <Header></Header>
            </div>
            <div>
                <slot/>
            </div>
        </div>
    </div>
    <div>
        <slot/>
    </div>
</template>
<script setup lang="ts">
</script>
