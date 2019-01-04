<template>
    <div>
        <div ref="dragBox">
            <slot></slot>
            <div class="yd-pullrefresh-dragtip" ref="dragTip"
                 v-show="touches.isDraging"
                 :class="dragTip.animationTiming"
                 :style="{ 'transform': 'translate3d(0, ' + dragTip.translate + 'px, 0)' }"
            >
                <span class="yd-pullrefresh-dragtip-icon">
                    <i :class="dragTip.loadingIcon"
                       :style="{ 'transform': 'rotate(' + dragTip.iconRotate + 'deg)' }"></i>
                    {{dragTip.statusText}}
                </span>
            </div>
        </div>
        <div class="yd-pullrefresh-draghelp" v-if="showHelpTag" @click="showHelpTag = false">
            <div><span>下拉更新</span></div>
        </div>
    </div>
</template>

<script type="text/babel">
    import {isColor} from '../../../utils/assist';

    export default {
        name: 'yd-demos',
        props: {
            title: String,
            fixed: Boolean,
            bgcolor: {
                validator(value) {
                    if(!value) return true;
                    return isColor(value);
                },
                default: '#FFF'
            },
            color: {
                validator(value) {
                    if(!value) return true;
                    return isColor(value);
                },
                default: '#5C5C5C'
            },
            borderColor: {
                validator(value) {
                    if(!value) return true;
                    return isColor(value);
                },
                default: '#E4E4E4'
            },
            fontsize: {
                validator(value) {
                    return /^(\.|\d+\.)?\d+(px|rem)$/.test(value);
                },
                default: '.3rem'
            },
            height: {
                validator(value) {
                    return /^(\.|\d+\.)?\d+(px|rem)$/.test(value);
                },
                default: '1rem'
            }
        },
        computed: {
            classes() {
                return this.fixed ? 'yd-demos-fixed' : '';
            }
        }
    }
</script>

<style lang="less">
    @import '../../../styles/components/demos.less';
</style>
