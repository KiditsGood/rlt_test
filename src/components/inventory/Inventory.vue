<template>
    <div class="inventory">
        <div class="inventory__hole"
             v-for="hole in holes.slice(1)"
             @drop='onDrop($event, hole)'
             @dragover.prevent @dragenter.prevent
        >

            <div v-if="items.filter(item => item.hole === hole.id).length > 0">
                <div class="item"
                     :class="item.color"
                     v-for="item in items.filter(item => item.hole === hole.id)"
                     draggable="true"
                     :key="item.id"
                     @dragstart="startDrag($event, item)"
                     @click="modalOpen = !modalOpen; currentColor = item.color;"
                     v-show="item.count > 0"
                >
                    {{item.title}}
                    <p class="item__count">{{ item.count }}</p>
                </div>
            </div>
            <div v-else>{{hole.title}}</div>
        </div>
        <Modal :modal-handler="modalOpen" :selected-item="currentColor"/>
    </div>
</template>

<script>
    import Modal from "@/components/modal/Modal";
    export default {
        name: "Inventory",
        components: {Modal},
        data() {
            return {
                holes: [
                    {
                        id: 0,
                        title: ''
                    },
                    {
                        id: 1,
                        title: '',
                        type: 'single'
                    },
                    {
                        id: 2,
                        title: '',
                        type: 'single'
                    },
                    {
                        id: 3,
                        title: '',
                        type: 'single'
                    },
                    {
                        id: 4,
                        title: '',
                        type: 'single'
                    },
                    {
                        id: 5,
                        title: '',
                        type: 'single'
                    },
                    {
                        id: 6,
                        title: '',
                        type: 'single'
                    },
                    {
                        id: 7,
                        title: '',
                        type: 'single'
                    },
                    {
                        id: 8,
                        title: '',
                        type: 'single'
                    },
                    {
                        id: 9,
                        title: '',
                        type: 'single'
                    },
                    {
                        id: 10,
                        title: '',
                        type: 'single'
                    },
                    {
                        id: 11,
                        title: '',
                        type: 'single'
                    },
                    {
                        id: 12,
                        title: '',
                        type: 'single'
                    },
                    {
                        id: 13,
                        title: '',
                        type: 'single'
                    },
                    {
                        id: 14,
                        title: '',
                        type: 'single'
                    },
                    {
                        id: 15,
                        title: '',
                        type: 'single'
                    },
                    {
                        id: 16,
                        title: '',
                        type: 'single'
                    },
                    {
                        id: 17,
                        title: '',
                        type: 'single'
                    },
                    {
                        id: 18,
                        title: '',
                        type: 'single'
                    },
                    {
                        id: 19,
                        title: '',
                        type: 'single'
                    },
                    {
                        id: 20,
                        title: '',
                        type: 'single'
                    },
                    {
                        id: 21,
                        title: '',
                        type: 'single'
                    },
                    {
                        id: 22,
                        title: '',
                        type: 'single'
                    },
                    {
                        id: 23,
                        title: '',
                        type: 'single'
                    },
                    {
                        id: 24,
                        title: '',
                        type: 'single'
                    },
                    {
                        id: 25,
                        title: '',
                        type: 'single'
                    }
                ],
                items: [
                    {
                        id: 0,
                        title: '',
                        hole: 1,
                        color: 'green',
                        count: 4
                    },
                    {
                        id: 1,
                        title: '',
                        hole: 2,
                        color: 'yellow',
                        count: 2
                    },
                    {
                        id: 2,
                        title: '',
                        hole: 3,
                        color: 'purple',
                        count: 5
                    }],
                modalOpen: false,
                currentColor: ''
            };
        },
        methods: {
            startDrag: (evt, item) => {
                evt.dataTransfer.dropEffect = 'move'
                evt.dataTransfer.effectAllowed = 'move'
                evt.dataTransfer.setData('itemID', item.id)
            },
            onDrop (evt, hole) {
                const itemID = evt.dataTransfer.getData('itemID')
                const item = this.items.find(item => item.id == itemID)

                if (hole.type && hole.type === 'single') {
                    let otheritem = this.items.find(i => i.hole === hole.id)

                    if (otheritem)
                        otheritem.hole = item.hole
                }
                item.hole = hole.id
            }
        }
    }
</script>