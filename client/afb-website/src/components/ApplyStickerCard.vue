<template>
    <div class="discountCard row py-5">

        <!-- sticker image -->
        <div class="discountFrame col-xs-12 col-sm-12 col-md-12 col-lg-4 d-flex">
            <div class="mx-auto">
                <img class="stickerImage" v-bind:src="content.image">
            </div>
        </div>

        <!-- the card content -->
        <div class="discountContent col-xs-12 col-sm-12 col-md-12 col-lg-8">
            <div class="applySticker">

                <!-- header -->
                <span 
                    :class="{stickerEnlarge: enlargeFont}" 
                    class="sticker-h" 
                    v-html="content.header"
                >
                </span>
                <br>

                <!-- paragraph -->
                <p 
                    :class="{stickerEnlarge: enlargeFont}" 
                    class="textParagraphs"
                >
                    {{ content.paragraph }}
                </p>
                <br>
                <br>
                <DynamicButton :enlargeFont="enlargeFont" v-bind:buttonInfo="{ color: '#CC3E16', text: content.button.text , destination: content.button.url, isUrl: true }"/>
            </div>
        </div>
    </div>
</template>

<script>
import DynamicButton from '@/components/DynamicButton.vue'

// This components receives props that were parsed from the Wordpress API. 
// See About.vue to see how the contents were parsed

// Components that uses it:
//  - About.vue

export default {
    name: 'ApplyStickerCard',
    props: ['content', 'enlargeFont'],
    components: {
        DynamicButton
    },
    computed: {
        buttonText: function() {
            return this.content.headerText
        }
    }
}
</script>

<style scoped>
.discountCard {
    box-shadow: -2.5px 2px 4px 0 rgba(0, 0, 0, 0.15);
    margin-left: auto;
    margin-right: auto;
    background-color:white;
}

.sticker-h >>> h3 {
    font-size: calc(18px + 1vw);
}

.textParagraphs {
    font-size: calc(10px + .8vw);
    font-family: 'DDINRegular';
}

.stickerEnlarge >>> h3 { /* on enlarge button */
    font-size: calc(30px + 1vw);
}

.stickerEnlarge.textParagraphs { /* on enlarge button */
    font-size: calc(15px + .8vw);
}

.discountContent {
    margin-top: auto;
    margin-bottom: auto;
}

.stickerImage {
    width: 100%;
}

@media(max-width: 992px) {
    .discountFrame {
        margin-bottom: 20px;
    }
}

</style>


