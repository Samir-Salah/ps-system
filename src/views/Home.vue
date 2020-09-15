<template>
    <div class="cards">
        <div class="row">
            <div
                class="col-sm-12 col-md-6 col-lg-4 col-xl-3"
                v-for="(card, index) in noOfCards"
                :key="index"
            >
                <Card class="card-home" />
            </div>
        </div>
    </div>
</template>

<script>
import Card from "@/components/Card.vue";

export default {
    name: "Home",
    data: function() {
        return {
            noOfCards: 8
        };
    },
    components: {
        Card
    }
};
</script>
