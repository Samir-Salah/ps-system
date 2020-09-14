<template>
    <div class="side-panel">
        <div class="side-header">
            <div class="side-header-image container">
                <img src="@/images/user.png" alt="" />
            </div>
            <div class="side-header-username container">
                Welcome,
                <span>{{ userName }}</span>
            </div>
        </div>
        <div class="side-content">
            <ul class="side-list-items list-unstyled">
                <router-link to="/" tag="a" exact>
                    <li>
                        <img src="@/images/ps.png" alt="" /> Home( playstation )
                    </li>
                </router-link>
                <router-link to="/about" tag="a">
                    <li><img src="@/images/cafe.png" alt="" /> Cafe Shop</li>
                </router-link>
                <router-link to="/" tag="a">
                    <li><img src="@/images/report.png" alt="" /> Reports</li>
                </router-link>
            </ul>
        </div>
    </div>
</template>

<script>
export default {
    name: "SideBar",
    data: function() {
        return {
            userName: "User Name"
        };
    }
};
</script>
