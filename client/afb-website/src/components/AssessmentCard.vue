<template>
    <div class="col-lg-6 d-flex pl-0">
        <div class="paddingSection testBoxes">
            <!-- header -->
            <span 
                :class="{assessmentEnlarge: enlargeFont}" 
                class="testTextHeaders" 
                v-html="content.headerHTML"
            ></span>
            <hr class="testHeaderLine">
            <br>
            
            <!-- paragraph -->
            <p 
                :class="{assessmentEnlarge: enlargeFont}" 
                class="textParagraphs" v-html="content.paragraph"
            ></p>
            <br>
            <br>
            
            <!-- DynamicButton component that leads to the 'resources' route -->
            <DynamicButton :enlargeFont="enlargeFont" v-bind:buttonInfo="{ color: '#CC3E16', text:buttonText, destination:'/' + content.route, isUrl: false }"/>
        </div>
    </div>
</template>

<script>
import DynamicButton from '@/components/DynamicButton.vue'

// This components receives props that were parsed from the WordPress API
// See About.vue to see how the contents were parsed

// Components that use it
//  - About.vue
//  - AssessmentSelection.vue

export default {
    name: 'AssessmentCard',
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
.paddingSection {
    padding-left: 5%;
    padding-right: 5%;
    padding-top: 3%;
    padding-bottom: 3%;
}

.testBoxes {
  box-shadow: -2.5px 2px 4px 0 rgba(0, 0, 0, 0.15);
  background-color: #ffffff;
}

.testTextHeaders >>> h4 {
    font-size: calc(18px + 1vw);
}

.assessmentEnlarge >>> h4 { /* on enlarge button */
    font-size: calc(30px + 1vw);
}

.assessmentEnlarge.textParagraphs { /* on enlarge button */
    font-size: calc(15px + 0.8vw);
}

@media (max-width: 992px) {
    .testBoxes {
        margin-top: 10px;
    }
}

.textParagraphs {
    font-family: 'DDINRegular';
    font-size: calc(10px + .8vw);
}
</style>


