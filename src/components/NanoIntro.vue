<template>
  <div class="intro">
    <img class="logo" src="../assets/trynano_full.png" />
    <h3>
      {{ t('nanoIntro.firstSentence') }}
    </h3>
    <i18n-t keypath="nanoIntro.secondSentence.main" tag="h5">
      <strong>{{ t('nanoIntro.secondSentence.whatIsNano') }}</strong>
    </i18n-t>
    <ClickToReveal
      :revealText="t('nanoIntro.revealText')"
      :clickable="true"
      :shouldBoldText="true"
      :sizeFactor="1"
      @revealClicked="handleRevealStepsClicked"
    ></ClickToReveal>
  </div>
</template>

<script>
import { ref } from 'vue';
import { useI18n } from 'vue-i18n';
import ClickToReveal from './common/ClickToReveal.vue';

export default {
  name: 'NanoIntro',
  components: { ClickToReveal },
  emits: ['revealStepsClicked'],
  setup(props, context) {
    const { t } = useI18n({ useScope: 'global' });
    const revealStepsClicked = ref(false);

    const handleRevealStepsClicked = () => {
      revealStepsClicked.value = true;
      context.emit('revealStepsClicked');
    };

    return { t, revealStepsClicked, handleRevealStepsClicked };
  },
};
</script>

<style lang="css" scoped>
.intro {
  margin-bottom: 25px;
}

.logo {
  height: auto;
  width: auto;
  max-width: 300px;
  max-height: 300px;
  padding-bottom: 25px;
}

h3 {
  font-size: 1.2em;
  font-weight: 700;
}

h5 {
  font-size: 0.95em;
  font-weight: 400;
}
</style>
