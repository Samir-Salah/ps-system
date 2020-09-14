<template>
    <div class="cards">
        <div class="row">
            <div class="col-md-3 col">
                <Card class="card-home"/>
            </div>
        </div>
    </div>
</template>

<script>
import Card from "@/components/Card.vue";

export default {
    name: "Home",
    components: {
        Card
    }
};
</script>
