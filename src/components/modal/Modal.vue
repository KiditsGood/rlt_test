<template>
    <div :class="{open: modalHandler}" class="modal">
        <div :class="selectedItem" class="modal__block"></div>
        <div class="modal__skeletons">
            <div class="modal__skeletons-item h30"></div>
            <div class="modal__skeletons-item"></div>
            <div class="modal__skeletons-item"></div>
            <div class="modal__skeletons-item"></div>
            <div class="modal__skeletons-item w180"></div>
            <div class="modal__skeletons-item w80"></div>
        </div>
        <button @click="deleteHandler = !deleteHandler" class="modal__button">Удалить предмет</button>
        <div @click="modalHandler = !modalHandler" class="modal__close">
            <span></span>
            <span></span>
        </div>
        <div :class="{open: deleteHandler}" class="modal__hidden">
            <input v-model="countWatcher" type="number" class="modal__hidden-input" placeholder="Введите количество">
            <div class="modal__hidden-buttons">
                <button @click="deleteHandler = !deleteHandler" class="modal__hidden-buttons--item white">Отмена</button>
                <button @click="deleteCount = countWatcher" class="modal__hidden-buttons--item pink">Подтвердить</button>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: "Modal",

        data() {
            return {
                deleteHandler: false,
                countWatcher: ''
            }
        },

        props:{
            selectedItem: String,
            modalHandler: Boolean,
            deleteCount: String
        }
    }
</script>