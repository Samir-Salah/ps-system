<template>
    <div class="cards">
        <div class="row">
            <div class="col-md-3" :class="activeCard">
                <Card class="card-home" @active="activeBorder" />
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
            active: ""
        };
    },
    components: {
        Card
    },
    methods: {
        activeBorder: function(value) {
            this.active = value;
        }
    },
    computed: {
        activeCard: function() {
            return {
                active: this.active
            };
        }
    }
};
</script>
