<script type="text/ecmascript-6">
    export default {
        data(){
            return {}
        },

        created() {
            document.addEventListener('keydown', this.handleEscape);
            document.body.classList.add('overflow-hidden');
        },


        destroyed() {
            document.removeEventListener('keydown', this.handleEscape);
            document.body.classList.remove('overflow-hidden');
        },


        methods: {
            handleEscape(e) {
                e.stopPropagation();

                if (e.keyCode == 27) {
                    this.close();
                }
            },


            /**
             * Close the modal.
             */
            close() {
                this.$emit('close');
            },
        }
    }
</script>

<template>
    <transition name="modal">
        <div class="z-30 fixed pin overflow-y-scroll modal-mask" @click="close">
            <div class="bg-white rounded shadow-lg max-w-md mx-auto my-10 p-5 modal-container" @click.stop>
                <slot/>
            </div>
        </div>
    </transition>
</template>