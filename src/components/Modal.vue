<template>
    <div>
        <div>
            <b-button v-b-modal.modal-xl variant="primary">xl modal</b-button>
            <b-modal id="modal-xl" size="xl" title="Extra Large Modal">Hello Extra Large Modal!</b-modal>
        </div>
    </div>
</template>

<script>
    export default {
        methods: {
            showModal() {
                this.$refs['my-modal'].show()
            },
            hideModal() {
                this.$refs['my-modal'].hide()
            },
            toggleModal() {
                // We pass the ID of the button that we want to return focus to
                // when the modal has hidden
                this.$refs['my-modal'].toggle('#toggle-btn')
            }
        }
    }
</script>