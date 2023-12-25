<div class="blinking"></div>
<style lang="scss">
    .blinking {
        background-color: $third-color;
        width: 8px;
        height: 20px;
        margin-top: 2px;
        margin-left: 10px;
        animation: alternate-reverse infinite blinking 500ms;
    }
    @keyframes blinking {
        from {
            background-color: transparent;
        }
        to {
            background-color: $third-color;
        }
    }
</style>