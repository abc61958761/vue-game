<template>
  <v-container>
    <!-- ===== 特價區 ===== -->
    <div>
      <v-carousel
        cycle
        height="400"
        hide-delimiter-background
        show-arrows-on-hover
      >
        <v-carousel-item
          v-for="(slide, i) in slides"
          :key="i"
        >
          <v-sheet
            :color="colors[i]"
            height="100%"
          >
            <v-row
              class="fill-height"
              align="center"
              justify="center"
            >
              <div class="display-3">{{ slide }} Slide</div>
            </v-row>
          </v-sheet>
        </v-carousel-item>
      </v-carousel>
    </div>

    <!-- == 遊戲精選 == -->
    <div class="game-selection">
      <div class="game-selection-wrapper">
        <div class="game-selection-title">
          <h1>根據您玩過的遊戲</h1>
        </div>
        <div class="game-selection-content">
          <v-card tile raised flat v-for="(gameSelection, index) in gameSelectionList" :key="index">
            <v-img width="300px" :src="gameSelection.src"></v-img>
            <v-card-actions>
              <div class="price-list">
                <div>
                  <span class="discount">-50</span>
                  <span class="original-price">＄300</span>
                  <span class="special-offer">＄300</span>
                </div>
              </div>
            </v-card-actions>
          </v-card>
        </div>
      </div>
    </div>

    <!-- 遊戲推薦 -->
    <div>

    </div>

    <!-- 遊戲列表 -->
    <div class="list-card">
      <div class="list-card-wrapper" v-for="(game, index) in gameList" :key="index">
        <div class="list-card-content">
          <div class="list-card-content-title">
            <h1>{{game.title}}</h1>
            <h4></h4>
          </div>
          <div class="list-card-content-images">
            <div class="list-card-content-image" v-for="(image, index) in game.images" :key="index">
              <template v-if="index === 0">
                <v-img  class="first" :src="image.src"></v-img>
                <div class="game-detail elevation-4">
                  <h4>{{game.title}}</h4>
                  <h6>發行日期：</h6>
                  <v-carousel
                    class="mb-2"
                    touchless
                    interval="1000"
                    cycle
                    height="200"
                    hide-delimiter-background
                    show-arrows-on-hover
                    :show-arrows="false"
                    hide-delimiters
                  >
                  <v-carousel-item
                      v-for="(item,i) in game.images"
                      :key="i"
                      :src="item.src"
                    ></v-carousel-item>
                  </v-carousel>
                  <v-card outlined>
                    <v-list-item two-line dense>
                      <v-list-item-content>
                        <v-list-item-title>使用評論</v-list-item-title>
                        <v-list-item-subtitle>極度好評</v-list-item-subtitle>
                      </v-list-item-content>
                    </v-list-item>
                  </v-card>
                </div>
              </template>
              <v-img v-else :src="image.src"></v-img>
            </div>
          </div>

          <div class="price-list">
            <div>
              <span class="discount">-50</span>
              <span class="original-price">＄300</span>
              <span class="special-offer">＄300</span>
            </div>
          </div>
        </div>
        <div class="list-card-action">
          <div class="desktop">
            <v-btn small outlined color="#fffbbe">造訪產品頁面</v-btn>
            <v-btn small outlined color="#fffbbe" class="ml-6">新增至願望清單</v-btn>
            <v-btn small outlined color="#fffbbe" class="ml-2">加入購物車</v-btn>
            <v-btn small color="#fffbbe" class="end">尋找更多</v-btn>
          </div>
          <div class="mobile">
            <v-btn icon>
              <v-icon>mdi-dialpad</v-icon>
            </v-btn>
            <v-btn icon>
              <v-icon>mdi-heart</v-icon>
            </v-btn>
            <v-btn icon>
              <v-icon>mdi-thumb-up</v-icon>
            </v-btn>
            <v-btn icon class="end">
              <v-icon>mdi-format-list-bulleted-square</v-icon>
            </v-btn>
          </div>
        </div>
      </div>
    </div>
  </v-container>
</template>

<script>
  export default {
    name: 'HelloWorld',

    data: () => ({
      colors: [
          'indigo',
          'warning',
          'pink darken-2',
          'red lighten-1',
          'deep-purple accent-4',
        ],
        slides: [
          'First',
          'Second',
          'Third',
          'Fourth',
          'Fifth',
        ],
        gameList: [{
          title: "超級雞馬",
          images: [{
            src: require('@/assets/ultimate_chicken_horse/ultimate_chicken_horse_1.jpeg')
          }, {
            src: require('@/assets/ultimate_chicken_horse/ultimate_chicken_horse_2.jpeg')
          }, {
            src: require('@/assets/ultimate_chicken_horse/ultimate_chicken_horse_3.jpeg')
          }, {
            src: require('@/assets/ultimate_chicken_horse/ultimate_chicken_horse_4.jpeg')
          }]
        }, {
          title: "超級雞馬",
          images: [{
            src: require('@/assets/ultimate_chicken_horse/ultimate_chicken_horse_1.jpeg')
          }, {
            src: require('@/assets/ultimate_chicken_horse/ultimate_chicken_horse_2.jpeg')
          }, {
            src: require('@/assets/ultimate_chicken_horse/ultimate_chicken_horse_3.jpeg')
          }, {
            src: require('@/assets/ultimate_chicken_horse/ultimate_chicken_horse_4.jpeg')
          }]
        }],
        gameSelectionList: [{
          price: {
            discount: 30,
            originalPrice: 400
          },
          src: require('@/assets/game_selection/game_selection_1.jpeg')
        }, {
          price: {
            discount: 60,
            originalPrice: 30
          },
          src: require('@/assets/game_selection/game_selection_2.jpeg')
        }, {
          price: {
            discount: 75,
            originalPrice: 800
          },
          src: require('@/assets/game_selection/game_selection_3.jpeg')
        }, {
          price: {
            discount: 50,
            originalPrice: 5000
          },
          src: require('@/assets/game_selection/game_selection_4.jpeg')
        }, {
          price: {
            discount: 10,
            originalPrice: 200
          },
          src: require('@/assets/game_selection/game_selection_5.jpeg')
        }]
    }),
  }
</script>
<style lang="scss">
.list-card {
  .list-card-wrapper {
    display: flex;
    flex-direction: column;
    background: #162a51;
    margin-bottom: 16px;
    color: #ffffff;

    .list-card-content {
      display: flex;
      flex-direction: column;
      padding: 0 8px;
      position: relative;

      .list-card-content-images {
        display: flex;
        align-items: center;
        overflow: scroll;
        margin-bottom: 4px;

        > div {
          display: flex;
        }

        .list-card-content-image {
          display: flex;
          transition: transform .2s;
          &:not(:first-child):hover {
            transform: scale(1.1);
            z-index: 999;
            box-shadow: 0px 2px 4px -1px rgba(0, 0, 0, 0.2), 0px 4px 5px 0px rgba(0, 0, 0, 0.14), 0px 1px 10px 0px rgba(0, 0, 0, 0.12);
          }

          & .first {
            padding: 16px;

            &:hover + .game-detail{
              visibility: visible;
              opacity: 1;
            }
          }
        }
      }
    }

    .list-card-action {
      display: flex;
      height: 56px;
      align-items: center;
      padding: 0 8px;
      position: relative;
      .end {
        position: absolute;
        right: 8px;
      }
    }
  }
}
.price-list {
  display: flex;
  background: #000029;
  justify-content: flex-end;
  align-items: center;
  height: 28px;
  padding-right: 8px;
  span {
    padding: 0 4px;
  }
  .discount {
    background: #efc88d;
    display: inline-flex;
    color: black;
    align-items: center;
    height: 28px;
  }
  .original-price {
    color: #ffffff;
    text-decoration:line-through;
  }
  .special-offer {
    color: #ffffff;
  }
}

.game-selection-wrapper {
  display: flex;
  .game-selection-title {
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .game-selection-content {
    display: flex;
    flex-wrap: wrap;
  }
}

.game-detail {
  visibility: hidden;
  width: 300px;
  left: 350px;
  background: #ffffff;
  z-index: 999;
  position: absolute;
  transition: opacity 0.3s;
  opacity: 0;
  color: black;
  padding: 8px;
}

@media screen and (max-width:480px) {
  .game-detail {
    display: none;
  }
  .desktop {
    display: none;
  }
  .mobile {
    display: block;

    button .v-icon{
      color: #ffffff !important;
    }
  }
}
@media screen and (min-width:481px) {
  .desktop {
    display: block;
  }
  .mobile {
    display: none;
  }
}
</style>
