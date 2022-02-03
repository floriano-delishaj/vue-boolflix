<template>
    <header>
        <div class="container d-flex justify-content-between align-items-center">
            <h2>BOOLFLIX</h2>
            <div class="search-container d-flex">
                <div class="button d-flex justify-content-center align-items-center p-2"
                    @click="$emit('search', searchInput)"
                >Search</div>
                <input v-model="searchInput"
                    type="text"
                    @keyup.enter="$emit('search', searchInput)"
                />
            </div>
        </div>
    </header>
</template>

<script>
    export default {
        data() {
            return {
                searchInput: '',
            }
        }
    }
</script>

<style lang="scss" scoped>

    @import '@/style/headerContainer.scss';

</style>