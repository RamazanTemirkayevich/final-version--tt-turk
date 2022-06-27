<template>
    <div class="modal-images">
        <div class="modal-images__box">
            <slot />
        </div>
    </div>
</template>

<style lang="scss" scoped>
@media (min-width: 320px) {
    .modal-images {
        position: fixed;
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
        z-index: 99;
        background-color: rgba(0, 0, 0, 0.2);
        
        display: flex;
        align-items: center;
        justify-content: center;
        padding: 35px 10px;

        &__box {
            width: 1193px;
            height: 839px;
            background: #FFFFFF;
            border-radius: 15px;
        }
    }
}
</style>