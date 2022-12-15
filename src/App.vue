<template>
    <main class="wrapper">
        <div class="container">
            <div class="container__top">
                <List />
                <Inventory />
            </div>
            <div class="container__bottom">
                <Block />
            </div>
        </div>
    </main>
</template>

<style lang="scss">
    @import "./assets/styles/style";
</style>
<script>
    import List from "@/components/list/List";
    import Inventory from "@/components/inventory/Inventory";
    import Block from "@/components/block/Block";
    export default {
        components: {Block, Inventory, List}
    }
</script>