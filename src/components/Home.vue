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
                    graphic
                </template>
                <template #action>
                    <Action/>
                </template>
            </Resume>
        </template>
        <template #movements>
            <Movements
                :movements="movements"
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

export default {
    components: {
        Layout,
        Header,
        Resume,
        Action,
        Movements,
    },
    data() {
        return {
            label: null,
            amount: null,
            movements: [{
                id: 0,
                title: "Mouvement 1",
                description: "Lorem ipsul dolor sit amet",
                amount: 1000,
            }, {
                id: 1,
                title: "Mouvement 2",
                description: "Lorem ipsul dolor sit amet",
                amount: -1000,
            }, {
                id: 2,
                title: "Mouvement 3",
                description: "Lorem ipsul dolor sit amet",
                amount: 1000,
            }, {
                id: 3,
                title: "Mouvement 4",
                description: "Lorem ipsul dolor sit amet",
                amount: 1000,
            }, {
                id: 4,
                title: "Mouvement 5",
                description: "Lorem ipsul dolor sit amet",
                amount: 1000,
            }, {
                id: 5,
                title: "Mouvement 6",
                description: "Lorem ipsul dolor sit amet",
                amount: 1000,
            }, {
                id: 6,
                title: "Mouvement 7",
                description: "Lorem ipsul dolor sit amet",
                amount: 1000,
            }, {
                id: 7,
                title: "Mouvement 8",
                description: "Lorem ipsul dolor sit amet",
                amount: 1000,
            }, {
                id: 8,
                title: "Mouvement 9",
                description: "Lorem ipsul dolor sit amet",
                amount: 1000,
            }]
        }
    }
};
</script>