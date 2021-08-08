<template>
    <div class="sidebar-list" :class="{ expand: expand }" @click="expand = !expand">
        <div class="sidebar-list-header">
            <svg class="sidebar-list-icon-expand" width="16" height="16" viewBox="0 0 16 16">
                <path transform="translate(-266, -17)" d="M280,22.7581818 L279.1564,22 L273.9922,26.506 L273.4414,26.0254545 L273.4444,26.0281818 L268.8562,22.0245455 L268,22.7712727 C269.2678,23.878 272.8084,26.9674545 273.9922,28 C274.8718,27.2330909 274.0144,27.9809091 280,22.7581818"/>
            </svg>
            <span class="sidebar-list-name">{{ name }}</span>
            <button v-if="action" v-show="mouseover">
                <svg width="13" height="13">
                    <path d="M6 6V.5a.5.5 0 0 1 1 0V6h5.5a.5.5 0 1 1 0 1H7v5.5a.5.5 0 1 1-1 0V7H.5a.5.5 0 0 1 0-1H6z" />
                </svg>
            </button>
        </div>
        <div class="sidebar-list-container">
            <span v-if="empty !== ''">{{ empty }}</span>
        </div>
    </div>
</template>

<script>
export default {
    name: "SidebarList",
    props: {
        action: {
            type: Boolean,
            default: true
        },
        name: {
            type: String,
            default: "Sample"
        },
        empty: {
            type: String,
            default: ""
        }
    },
    data() {
        return {
            expand: true,
            mouseover: false
        }
    },
    created() {
        this.$parent.$on("sidebar-mouseover", () => {
            this.mouseover = true;
        })
        this.$parent.$on("sidebar-mouseleave", () => {
            this.mouseover = false;
        })
    }
}
</script>

<style scoped>
.sidebar-list {
    display: flex;
    flex-direction: column;
}
.sidebar-list-header {
    height: 44px;
    display: flex;
    flex-direction: row;
    align-items: center;
}
.sidebar-list-name {
    flex-grow: 1;
}
.sidebar-list-container {
    max-height: 0;
    display: block;
    overflow: hidden;
    transition: 0.4s;
}
.sidebar-list.expand .sidebar-list-container {
    max-height: 100px;
}
.sidebar-list-icon-expand {
    transition: transform 0.4s;
    transform: rotate(-90deg);
}
.sidebar-list.expand .sidebar-list-icon-expand {
    transform: rotate(0deg);
}
</style>