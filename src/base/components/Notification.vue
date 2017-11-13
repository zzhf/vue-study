<template>
    <transition name="fade">
        <div 
            class="dc-notification"
            v-show="visible"
            :style="{top: top ? top + 'px' : 'auto'}"
            @mouseenter="clearTimer"
            @mouseleave="startTimer"
            @click="click"
            >
            <i 
                class="dc-notification-icon"
                :class="[typeClass, iconClass]"
                v-if="type || iconClass"
            >
            </i>
            <div 
                class="dc-notification-group"
                :class="{'is-with-icon': typeClass || iconClass}"
            >
                <h2 class="dc-notification-title" v-text="title"></h2>
                <div class="el-notification-content"><slot>{{ message }}</slot></div>
                <div class="dc-notification-closeBtn dc-icon-close" @click.stop="close"></div>
            </div>
        </div>
    </transition>
</template>

<script>
    const typeMap = {
        success: 'circle-check',
        info: 'information',
        warning: 'waring',
        error: 'circle-cross'
    }

    export  default {
        data() {

        },
        watch: {
            closed(newVal) {
                if (newVal) {
                    this.visible = false;
                    this.$el.addEventListener('transitionend', this.destroyElement);
                }
            }
        },
        methods: {
            destroyElement() {
                this.$el.removeEventListener('transitionend', this.destroyElement);
                this.$destroy(true);
                this.$el.parentNode.removeChild(this.$el);
            },

            click() {
                if (typeof this.onClick === 'function') {
                    this.onClick();
                }
            },

            clearTimer() {
                clearTimeout(this.timer);
            },

            startTimer() {
                if (this.duration > 0) {
                    this.timer = setTimeout(() => {
                        if (!this.closed) {
                            this.closed();
                        }
                    })
                }
            }
        }
    }
</script>