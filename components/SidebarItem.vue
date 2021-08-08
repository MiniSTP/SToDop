<template>
    <div class="sidebar-item" :class="{ action: action, select: select }">
        <svg class="sidebar-item-icon" :width="size" :height="size" :viewBox="viewBox">
            <g v-if="paths !== null">
                <path v-for="p in paths" :key="p.index" :d="p.path" :opacity="p.opacity | 1" />
            </g>
        </svg>
        <span class="sidebar-item-name">{{ name }}</span>
        <span v-if="count !== 0" class="sidebar-item-counter">{{ count }}</span>
        <svg v-if="action" class="sidebar-item-action" width="15" height="3">
            <path d="M1.5 3a1.5 1.5 0 1 1 0-3 1.5 1.5 0 0 1 0 3zm6 0a1.5 1.5 0 1 1 0-3 1.5 1.5 0 0 1 0 3zm6 0a1.5 1.5 0 1 1 0-3 1.5 1.5 0 0 1 0 3z"/>
        </svg>
    </div>
</template>

<script>
export default {
    name: "SidebarItem",
    props: {
        select: {
            type: Boolean,
            default: false
        },
        action: {
            type: Boolean,
            default: true
        },
        name: {
            type: String,
            default: "Sample"
        },
        count: {
            type: Number,
            default: 0
        },
        size: {
            type: Number,
            default: 24
        },
        paths: {
            type: Array,
            default: () => []
        }
    },
    computed: {
        viewBox() {
            return "0 0 " + this.size + " " + this.size;
        }
    }
}
</script>

<style scoped>
.sidebar-item {
    display: flex;
    width: 100%;
    height: 40px;
    flex-direction: row;
    align-items: center;
}
.sidebar-item-name {
    flex-grow: 1;
}
.sidebar-item-action {
    display: none;
}
.sidebar-item:hover .sidebar-item-action {
    display: block;
}
.sidebar-item.action:hover .sidebar-item-counter {
    display: none;
}
span {
    display: flex;
    align-items: center;
    padding-bottom: 1px;
}
</style>