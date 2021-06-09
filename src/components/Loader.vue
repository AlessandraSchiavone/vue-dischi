<template>
  <div class="loader">
    <svg width="58" height="58" viewBox="0 0 58 58" xmlns="http://www.w3.org/2000/svg">
        <g fill="none" fill-rule="evenodd">
            <g transform="translate(2 1)" stroke="#FFF" stroke-width="1.5">
                <circle cx="42.601" cy="11.462" r="5" fill-opacity="1" fill="#fff">
                    <animate attributeName="fill-opacity"
                        begin="0s" dur="1.3s"
                        values="1;0;0;0;0;0;0;0" calcMode="linear"
                        repeatCount="indefinite" />
                </circle>
                <circle cx="49.063" cy="27.063" r="5" fill-opacity="0" fill="#fff">
                    <animate attributeName="fill-opacity"
                        begin="0s" dur="1.3s"
                        values="0;1;0;0;0;0;0;0" calcMode="linear"
                        repeatCount="indefinite" />
                </circle>
                <circle cx="42.601" cy="42.663" r="5" fill-opacity="0" fill="#fff">
                    <animate attributeName="fill-opacity"
                        begin="0s" dur="1.3s"
                        values="0;0;1;0;0;0;0;0" calcMode="linear"
                        repeatCount="indefinite" />
                </circle>
                <circle cx="27" cy="49.125" r="5" fill-opacity="0" fill="#fff">
                    <animate attributeName="fill-opacity"
                        begin="0s" dur="1.3s"
                        values="0;0;0;1;0;0;0;0" calcMode="linear"
                        repeatCount="indefinite" />
                </circle>
                <circle cx="11.399" cy="42.663" r="5" fill-opacity="0" fill="#fff">
                    <animate attributeName="fill-opacity"
                        begin="0s" dur="1.3s"
                        values="0;0;0;0;1;0;0;0" calcMode="linear"
                        repeatCount="indefinite" />
                </circle>
                <circle cx="4.938" cy="27.063" r="5" fill-opacity="0" fill="#fff">
                    <animate attributeName="fill-opacity"
                        begin="0s" dur="1.3s"
                        values="0;0;0;0;0;1;0;0" calcMode="linear"
                        repeatCount="indefinite" />
                </circle>
                <circle cx="11.399" cy="11.462" r="5" fill-opacity="0" fill="#fff">
                    <animate attributeName="fill-opacity"
                        begin="0s" dur="1.3s"
                        values="0;0;0;0;0;0;1;0" calcMode="linear"
                        repeatCount="indefinite" />
                </circle>
                <circle cx="27" cy="5" r="5" fill-opacity="0" fill="#fff">
                    <animate attributeName="fill-opacity"
                        begin="0s" dur="1.3s"
                        values="0;0;0;0;0;0;0;1" calcMode="linear"
                        repeatCount="indefinite" />
                </circle>
            </g>
        </g>
    </svg>
    <div class="text">Loading...</div>
  </div>
</template>

<script>
export default {
    name: "Loader"
}

</script>

<style lang="scss" scoped>
    @import '../style/variables';
    .loader {
        text-align: center;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background-color: $bg-color;
        .text {
            color:$text-color;
            text-shadow: 1px 1px 1px;
            font-size: 32px;
            text-transform: uppercase;
            letter-spacing: 4px;
        }
        svg{
            margin:50px 0px;
        }
    }
    
</style>