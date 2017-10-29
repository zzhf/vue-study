<template>
    <transition name="dc-alert-fade">
        <div class="dc-alert" :class="[ typeClass ]" v-show="visible">
            <i class="dc-alert-icon" v-if="showIcon"></i>
            <div class="dc-alert-content">
                <span class="dc-alert-title" v-if="title">{{ title }}</span>
                <slot>
                    <p class="dc-alert-description" v-if="description">{{ description }}</p>
                </slot>
                <i class="dc-alert-closebtn" v-show="closable" @click="click"></i>
            </div>
        </div>
    </transition>
</template>

<script>
    export default {
        name: 'DcAlert',

        props: {
            title: {
                type: String,
                default: ''
            },
            description: {
                type: String,
                default: ''
            },
            visible: {
                type: Boolean,
                default: false
            },
            showIcon: {
                type: Boolean,
                default: true
            },
            closable: {
                type: Boolean,
                default: true
            }
        },

        data() {
            return {
            }
        },

        methods: {
            close() {
                this.visible = false;
                this.$emit('close');
            }
        }
    }
</script>