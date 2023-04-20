<template>
    <Layout>
        <template #header>
            <Header></Header>
        </template>
        <template #resume>
            <Resume
                :dateLabel="'Mes économies'"
                :label="label"
                :totalAmount="1000000"
                :amount="amount"
            >
                <template #graphic>
                    <Graphic :amounts="amounts"/>
                </template>
                <template #action>
                    <Action @create="create"/>
                </template>
            </Resume>
        </template>
        <template #movements>
            <Movements
                :movements="movements"
                @remove="remove"
            />
        </template>
    </Layout>
</template>

<script>
import Layout from './Layout.vue';
import Header from './Header.vue';
import Resume from './Resume/Index.vue';
import Action from './Action.vue';
import Movements from './Movements/Index.vue';
import Graphic from './Resume/Graphic.vue';
import { computed } from '@vue/reactivity';
import { remove } from '@vue/shared';

export default {
    components: {
    Layout,
    Header,
    Resume,
    Action,
    Movements,
    Graphic
},
    data() {
        return {
            label: null,
            amount: null,
            // amounts: [100, 200, 500, 200, -400, -600, -300, 0, 300, 500],
            movements: [{
                id: 0,
                title: "Mouvement 1",
                description: "Lorem ipsul dolor sit amet",
                amount: 100,
                time: new Date("04-13-2023")
            }, {
                id: 1,
                title: "Mouvement 2",
                description: "Lorem ipsul dolor sit amet",
                amount: 200,
                time: new Date("04-14-2023")
            }, {
                id: 2,
                title: "Mouvement 3",
                description: "Lorem ipsul dolor sit amet",
                amount: 500,
                time: new Date("04-15-2023")
            }, {
                id: 3,
                title: "Mouvement 4",
                description: "Lorem ipsul dolor sit amet",
                amount: 200,
                time: new Date("04-16-2023")
            }, {
                id: 4,
                title: "Mouvement 5",
                description: "Lorem ipsul dolor sit amet",
                amount: -400,
                time: new Date("04-17-2023")
            }, {
                id: 5,
                title: "Mouvement 6",
                description: "Lorem ipsul dolor sit amet",
                amount: -600,
                time: new Date("04-18-2023")
            }, {
                id: 6,
                title: "Mouvement 7",
                description: "Lorem ipsul dolor sit amet",
                amount: -300,
                time: new Date("04-19-2023")
            }, {
                id: 7,
                title: "Mouvement 8",
                description: "Lorem ipsul dolor sit amet",
                amount: 100,
                time: new Date("04-20-2023")
            }, {
                id: 8,
                title: "Mouvement 9",
                description: "Lorem ipsul dolor sit amet",
                amount: 300,
                time: new Date("03-20-2023")
            }, {
                id: 9,
                title: "Mouvement 10",
                description: "Lorem ipsul dolor sit amet",
                amount: 500,
                time: new Date("03-20-2023")
            }]
        }
    },
    computed: {
        amounts() {
            const lasDays = this.movements
                .filter(m => {
                    const today = new Date();
                    const oldDate = today.setDate(today.getDate() - 30);
                    
                    return m.time > oldDate;
                })
                .map(m => m.amount);

            return lasDays.map((m, i) => {

                const lastMovements = lasDays.slice(0, i);

                return lastMovements.reduce((suma, movement) => {

                    return suma + movement

                }, 0);
            });
        }
    },
    methods: {
        create(movement) {
            this.movements.push(movement);
        },
        remove(id) {
            const index = this.movements.findIndex(m => m.id === id);
            this.movements.splice(index, 1);
        }
    }
};
</script>