<template>
    <div class="card">
    <b-button v-b-modal.modal-xl variant="transparent">
        <div class="card__title">
            <div class="card__title--question">
                <h3>{{question}}</h3>
            </div>
            <div class="card__title--category">
                <small>{{category}}</small>
            </div>
        </div>
    </b-button>
        <b-modal id="modal-xl" size="xl" title="Extra Large Modal">
            {{answer}}
        </b-modal>
    </div>
</template>
<script>
    export default {
        name: 'CardQuestion',
        props: ['question', 'category', 'answer'],
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
<style lang="scss">
    .card {
        padding: 20px;
        width: 400px;
        display: flex;
        flex-direction: column;
        align-items: flex-start;
        box-shadow: 0 0 10px #00000020;
        border-radius: 8px;
        cursor: pointer;
        &:hover {
            transition: 0.3s;
            box-shadow: 0 0 10px #00000060;
        }
        &__title {
            width: 100%;
            &--question {
                display: flex;
                flex-direction: column;
                align-items: flex-start;
                h3 {
                    text-align: left;
                    color: cadetblue;
                    padding: 0;
                    margin: 0;
                }
            }
            &--category {
                display: flex;
                flex-direction: column;
                align-items: flex-start;
                small {
                    text-align: left;
                    padding: 0;
                    margin: 0;
                }
            }
        }
        &__answer {
            display: flex;
            flex-direction: column;
            align-items: flex-start;
            p {
                text-align: left;
                font-size: 0.9em;
            }
        }
    }
</style>