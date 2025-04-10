<script setup lang="ts">
import WelcomeItem from './WelcomeItem.vue'
import DocumentationIcon from './icons/IconDocumentation.vue'
import ToolingIcon from './icons/IconTooling.vue'
import IconSupport from '@/components/icons/IconSupport.vue'

</script>

<template>
  <WelcomeItem>
    <template #icon>
      <ToolingIcon />
    </template>
    <template #heading>Presentation</template>
    The crystal ball, a timeless symbol of divination and mystery, holds a powerful allure.  More than just a polished sphere of glass or quartz, it represents the human desire to peer beyond the veil of the present, to glimpse the shadowy outlines of the future.  Its smooth surface, often reflecting the surroundings in distorted, fragmented images, mirrors the uncertain and ambiguous nature of prophecy itself.
  </WelcomeItem>

  <WelcomeItem>
    <template #icon>
      <DocumentationIcon />
    </template>
    <template #heading>History</template>

    Historically, crystal balls haven't always been associated with fortune telling.  Ancient cultures used polished stones for various purposes, from ritualistic offerings to simple decorative objects.  The association with divination likely emerged later, fueled by the belief that the orb's reflective properties allowed the seer to focus their intuition and receive visions.  The mesmerizing quality of the sphere, particularly in low light, could easily induce a trance-like state, lending credence to the perceived revelations.

  </WelcomeItem>

  <WelcomeItem>
    <template #icon>
      <IconSupport />
    </template>
    <template #heading>Support</template>

    Today, crystal balls remain a popular symbol in fiction, often portraying a romanticized version of foresight.  From the mystical pronouncements of fictional seers to the more theatrical performances of stage magicians, the crystal ball continues to evoke a sense of wonder and intrigue.  However, the inherent ambiguity of its supposed powers remains:  Is it a genuine window to the future, or merely a reflection of the seer's own subconscious and the observer's inherent biases? The answer, like the visions within the ball itself, remains elusive, a testament to the enduring power of mystery and the human desire to know what lies ahead.

  </WelcomeItem>


</template>
