<template>
  <div class="m-header">
    <a-heading
        :heading-text="headingText"
        heading-type="h1"
        class="heading"
    />
    <div class="game-control">
      <a-button
          @buttonClicked="toggleGameStatus"
          :disabled="gameStatus === endStatus"
      >
        {{ buttonTitle }}
      </a-button>
    </div>
  </div>
</template>

<script>
import { mapActions, mapState } from "vuex";
import { GAME_STATUS_CONTINUE, GAME_STATUS_END, GAME_STATUS_PAUSE, GAME_STATUS_PLAY } from "@/constants/constants";
import AHeading from "@/components/atoms/a-heading";
import AButton from "@/components/atoms/a-button";

export default {
  name: 'MHeader',
  components: {
    AButton,
    AHeading
  },
  computed: {
    ...mapState(['gameStatus']),
    endStatus () {
      return GAME_STATUS_END
    },
    headingText () {
      return 'Welcome to Teeter Totter!'
    },
    buttonTitle () {
      return this.gameStatus === GAME_STATUS_PAUSE ? GAME_STATUS_CONTINUE : GAME_STATUS_PAUSE
    }
  },
  methods: {
    ...mapActions(['startGame', 'setGameStatus']),
    toggleGameStatus () {
      this.setGameStatus(this.gameStatus === GAME_STATUS_PAUSE ? GAME_STATUS_PLAY : GAME_STATUS_PAUSE)
    }
  }
}
</script>

<style lang="scss" scoped>
@import "src/css/variables";

.heading {
  margin-bottom: $spacer-base;
}

.game-control {
  margin-bottom: $spacer-base;
}
</style>
