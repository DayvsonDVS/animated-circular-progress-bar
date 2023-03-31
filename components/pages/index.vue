<template>
  <div class="container">
    <div class="box">
      <div class="shadow"></div>
      <div class="content">
        <div class="percent" data-text="Html" style="--num: 85">
          <div class="dot"></div>

          <svg>
            <circle cx="70" cy="70" r="70"></circle>
            <circle cx="70" cy="70" r="70"></circle>
          </svg>
        </div>

        <div class="number">
          <h2>85<span>%</span></h2>
        </div>
      </div>
    </div>

    <div class="box">
      <div class="shadow"></div>
      <div class="content">
        <div class="percent" data-text="CSS" style="--num: 90">
          <div class="dot"></div>
          <svg>
            <circle cx="70" cy="70" r="70"></circle>
            <circle cx="70" cy="70" r="70"></circle>
          </svg>
        </div>

        <div class="number">
          <h2>90<span>%</span></h2>
        </div>
      </div>
    </div>

    <div class="box">
      <div class="shadow"></div>
      <div class="content">
        <div class="percent" data-text="JS" style="--num: 70">
          <div class="dot"></div>
          <svg>
            <circle cx="70" cy="70" r="70"></circle>
            <circle cx="70" cy="70" r="70"></circle>
          </svg>
        </div>

        <div class="number">
          <h2>70<span>%</span></h2>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import 'assets/scss/main.scss'
</script>

<style scoped lang="scss">
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 80px 100px;
  flex-wrap: wrap;
  .box {
    position: relative;
    width: 240px;
    height: 250px;
    display: flex;
    justify-content: center;
    align-items: center;
    &::before {
      content: '';
      position: absolute;
      top: 0;
      left: 0;
      width: 20px;
      height: 100%;
      background: linear-gradient(#fff, #fff, #e3e3e3);
      filter: blur(1px);
      z-index: 1;
    }
    &::after {
      content: '';
      position: absolute;
      top: 1px;
      right: -1px;
      width: 20px;
      height: 100%;
      background: #9d9d9d;
      filter: blur(1px);
      z-index: 1;
    }
    .content {
      position: relative;
      width: 100%;
      height: 100%;
      background: linear-gradient(#dbdae1, #a3aaba);
      box-shadow: 5px 5px 5px rgba(0, 0, 0, 0.1),
        15px 15px 15px rgba(0, 0, 0, 0.1), 20px 20px 20px rgba(0, 0, 0, 0.1),
        50px 50px 50px rgba(0, 0, 0, 0.1), inset 3px 3px 2px #fff;
      display: flex;
      justify-content: center;
      align-items: center;
      flex-direction: column;
      .number {
        position: relative;
        inset: 0;
        opacity: 0;
        animation: fadeIn 1s linear forwards;
        animation-delay: 2.5s;
        h2 {
          font-size: 2.5em;
          color: #555;
          display: flex;
          align-items: center;
          span {
            font-weight: 300;
            font-size: 0.5em;
            margin-left: 5px;
          }
        }
      }
      .percent {
        position: relative;
        width: 150px;
        height: 150px;
        .dot {
          position: absolute;
          inset: 5px;
          z-index: 10;
          animation: animateDot 2s linear forwards;
          @keyframes animateDot {
            0% {
              transform: rotate(0deg);
            }
            100% {
              transform: rotate(calc(3.6deg * var(--num)));
            }
          }
          &::before {
            content: '';
            position: absolute;
            top: -7px;
            left: 50%;
            transform: translateX(-50%);
            width: 14px;
            height: 14px;
            background: #555;
            border-radius: 50%;
          }
        }
        svg {
          position: relative;
          width: 150px;
          height: 150px;
          transform: rotate(270deg);
          circle {
            width: 100%;
            height: 100%;
            fill: transparent;
            stroke-width: 3;
            stroke: rgba(0, 0, 0, 0.05);
            transform: translate(5px, 5px);
            &:nth-child(2) {
              stroke: #555;
              stroke-dasharray: 440;
              stroke-dashoffset: calc(440 - (440 * var(--num)) / 100);
              opacity: 0;
              animation: fadeIn 7s linear forwards;
              @keyframes fadeIn {
                0% {
                  opacity: 0;
                }
                100% {
                  opacity: 1;
                }
              }
            }
          }
        }
        &::before {
          content: attr(data-text);
          position: absolute;
          inset: 20px;
          background: #555;
          border-radius: 50%;
          display: flex;
          justify-content: center;
          align-items: center;
          color: #fff;
          font-size: 1.75em;
          letter-spacing: 0.1em;
          text-transform: uppercase;
        }
      }
    }
    .shadow {
      position: absolute;
      width: 100%;
      height: 100%;
      background: #eee;
      &::before {
        content: '';
        position: absolute;
        top: 0;
        left: calc(100% + 5px);
        width: 100%;
        height: 200%;
        background: linear-gradient(rgba(0, 0, 0, 0.075), transparent);
        transform: skew(45deg);
      }
      &::after {
        content: '';
        position: absolute;
        bottom: -200%;
        left: calc(100% + 15px);
        width: 100%;
        height: 200%;
        background: linear-gradient(rgba(0, 0, 0, 0.075), transparent);
        transform: skew(45deg);
      }
    }
  }
}
</style>
