<template>

  <div :class="bemm()">
    <div :class="bemm('container')">

      <h1 :class="bemm('first-name')"><span>.mt</span>
        <ul :class="bemm('letters')">
          <li :class="bemm('letter')" v-for="char in splitIntoChars('Tig')">
            {{ char }}
          </li>
        </ul>
      </h1>
      <h2 :class="bemm('last-name')">
        <ul :class="bemm('letters')">
          <li :class="bemm('letter')" v-for="char in splitIntoChars('van Diepen')">
            {{ char }}
          </li>
        </ul>
      </h2>
    </div>
  </div>
</template>

<script lang="ts" setup>
import { useBemm, splitIntoChars } from "@/utils";
const bemm = useBemm('intro');
</script>


<style lang="scss">
.intro {
  height: 100vh;
  background-color: var(--background);
  width: 100vw;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;

  &__first-name {
    font-weight: bold;
    line-height: 1;
    display: inline-block;
    font-size: 1em;
    position: relative;


    span {
      --round: calc(var(--border-radius) / 2);
      position: absolute;
      padding: .25em .25em;
      transform: translate(75%, -75%);
      right: 0;
      top: 0;
      border-radius: var(--round) var(--round) var(--round) 0;
      background-color: var(--secondary);
      font-weight: 500;
      font-size: .5em;
      color: var(--background);
      animation: popAndSlide .5s 1s ease-out forwards;
      opacity: 0;

    }
  }

  @keyframes popAndSlide {
  0% {
    transform: translateY(-300%) translateX(-100%);
    opacity: 0;
    scale: 0.8;
  }

  30% {
    transform: translate(85%, -65%);
    opacity: 1;
    scale: 1.1;
  }

  45% {
    transform: translate(65%, -85%) rotate(-5deg);
    scale: 0.95;
  }

  60% {
    transform: translate(85%, -65%) rotate(4deg);
    scale: 1.05;
  }

  75% {
    transform: translate(70%, -80%) rotate(-3deg);
    scale: 0.98;
  }

  90% {
    transform: translate(78%, -72%) rotate(2deg);
    scale: 1.02;
  }

  100% {
    transform: translate(75%, -75%) rotate(-5deg);
    scale: 1;
    opacity: 1;
  }
}



  &__last-name {
    --extra-delay: 1.5s;
    font-size: 1em;
    line-height: 1;
    display: inline-block;
    border-radius: calc(var(--border-radius) / 2);
    font-weight: 200;
  }

  &__container {
    font-size: clamp(1.5em, 6vw, 5em);
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: row;
  }

  &__letters {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: row;
  }

  &__letter {
    opacity: 0;
    min-width: .25em;
    animation: fallDown .5s var(--delay, .5s) ease-out forwards;

    @for $i from 1 through 10 {
      &:nth-child(#{$i}) {
        --delay: calc((#{$i} * .1s) + var(--extra-delay, 0s));
      }
    }
  }

  @keyframes fallDown {
    0% {
      transform: translateY(-50%);
      opacity: 0;
    }

    25% {
      transform: translateY(10%);
      opacity: 0.5;
    }

    50% {
      transform: translateY(-5%);
      opacity: 0.75;
    }

    75% {
      transform: translateY(2%);
      opacity: 0.9;
    }

    100% {
      transform: translateY(0);
      opacity: 1;

    }
  }

}
</style>
