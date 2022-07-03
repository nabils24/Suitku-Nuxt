<template>
  <div class="bg">
    <v-row
      justify="center"
      align="center"
      color="primary"
      class="d-flex pa-md-11 mx-lg-auto"
    >
      <v-card
        color="primary"
        width="375px"
        justify="center"
        align="center"
        height="300px"
        elevation="10"
        class="pa-4 text-center primary text-no-wrap rounded-b-xl"
      >
        <v-card-title class="justify-center font-weight-bold">{{
          namaGame
        }}</v-card-title>
        <v-card-subtitle v-show="hasilsub" class="font-weight-bold"
          >Hasil Permainan Adalah</v-card-subtitle
        >
        <v-row class="pa-3 justify-center">
          <v-btn class="me-5" @click="dialogs = true">
            {{ profileGame.namePlayer }}
          </v-btn>
          <v-btn> Bot Nabil </v-btn>
        </v-row>
        <v-row class="pa-3 justify-center">
          <v-text class="textpilih me-8">
            {{ gamesOption.playerPick }}
          </v-text>
          <v-text class="textpilih" v-if="option"> VS </v-text>
          <v-text class="textpilih ms-7">
            {{ gamesOption.botPick }}
          </v-text>
        </v-row>
        <v-text class="textpilih font-weight-bold">{{ gamesOption.winner }}</v-text>
      </v-card>
    </v-row>
    <v-row class="pa-md-6 justify-space-around" align="center" justify="center">
      <v-hover v-slot="{ hover }">
        <v-card
          color="primary"
          width="300px"
          justify="center"
          align="center"
          height="275px"
          class="card"
          elevation="10"
          @click="setplayerPick('✊🏼')"
        >
          <v-expand-transition>
            <div
              v-if="hover"
              class="
                d-flex
                transition-fast-in-fast-out
                black
                darken-2
                v-card--reveal
                text-h2
                white--text
              "
              style="height: 100%"
            >
              {{ namaObject1 }}
            </div>
          </v-expand-transition>
          <v-card-title class="justify-center"></v-card-title>
          <v-text class="textBt">✊🏼</v-text>
        </v-card>
      </v-hover>

      <v-hover v-slot="{ hover }">
        <v-card
          color="primary"
          width="300px"
          justify="center"
          align="center"
          height="275px"
          class="card"
          elevation="10"
          @click="setplayerPick('✌🏼')"
        >
          <v-expand-transition>
            <div
              v-if="hover"
              class="
                d-flex
                transition-fast-in-fast-out
                black
                darken-2
                v-card--reveal
                text-h2
                white--text
              "
              style="height: 100%"
            >
              {{ namaObject2 }}
            </div>
          </v-expand-transition>
          <v-card-title class="justify-center"></v-card-title>
          <v-text class="textBt">✌🏼</v-text>
        </v-card>
      </v-hover>
      <v-hover v-slot="{ hover }">
        <v-card
          color="primary"
          width="300px"
          justify="center"
          align="center"
          height="275px"
          class="card"
          elevation="10"
          @click="setplayerPick('🖐🏼')"
        >
          <v-expand-transition>
            <div
              v-if="hover"
              class="
                d-flex
                transition-fast-out-fast-out
                black
                darken-2
                v-card--reveal
                text-h2
                white--text
              "
              style="height: 100%"
            >
              {{ namaObject3 }}
            </div>
          </v-expand-transition>
          <v-card-title class="justify-center"></v-card-title>
          <v-text class="textBt">🖐🏼</v-text>
        </v-card>
      </v-hover>
    </v-row>
    <v-row justify="center">
      <v-dialog v-model="dialogs" persistent max-width="600px">
        <v-card>
          <v-card-title>
            <span class="text-h5">Ubah nama kamu</span>
          </v-card-title>
          <v-card-text>
            <v-container>
              <v-row>
                <v-col cols="12">
                  <v-text-field
                    label="Nama*"
                    required
                    v-model="nama"
                  ></v-text-field>
                </v-col>
              </v-row>
            </v-container>
            <small>*Pastikan Namamu tidak lebih dari 6 kata</small>
          </v-card-text>
          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn color="blue darken-1" text @click="dialogs = false">
              Gajadi
            </v-btn>
            <v-btn color="blue darken-1" text @click="setplayernamekuh(nama)">
              Simpan
            </v-btn>
          </v-card-actions>
        </v-card>
      </v-dialog>
    </v-row>
  </div>
</template>

<script>
export default {
  name: "IndexPage",
  data() {
    return {
      namaGame: "SuitKu",
      namaObject1: "Batu",
      namaObject2: "Gunting",
      namaObject3: "Kertas",
      hasilsub: false,
      dialogs: false,
      nama: "",
      option: false,

      profileGame: {
        namePlayer: "Player",
        nameBot: "Bot",
      },
      gamesOption: {
        playerPick: "",
        botPick: "",
        winner: "",
      },
    };
  },
  methods: {
    setBotpick() {
      const pilihan = ["✊🏼", "✌🏼", "🖐🏼"];
      const generate = pilihan[Math.floor(Math.random() * pilihan.length)];
      this.gamesOption.botPick = generate;
    },
    setplayerPick(pick) {
      this.gamesOption.playerPick = pick;
      this.option = true;
      this.setBotpick();
      this.winnerCalculation();
    },
    winnerCalculation() {
      const nameplayer = this.profileGame.namePlayer;
      if (
        this.gamesOption.botPick == "🖐🏼" &&
        this.gamesOption.playerPick == "✌🏼"
      ) {
        this.gamesOption.winner = nameplayer + " win";
      } else if (
        this.gamesOption.botPick == "🖐🏼" &&
        this.gamesOption.playerPick == "✊🏼"
      ) {
        this.gamesOption.winner = "Bot Win";
      } else if (
        this.gamesOption.botPick == "✌🏼" &&
        this.gamesOption.playerPick == "🖐🏼"
      ) {
        this.gamesOption.winner = "Bot Win";
      } else if (
        this.gamesOption.botPick == "✌🏼" &&
        this.gamesOption.playerPick == "✊🏼"
      ) {
        this.gamesOption.winner = nameplayer + " win";
      } else if (
        this.gamesOption.botPick == "✊🏼" &&
        this.gamesOption.playerPick == "🖐🏼"
      ) {
        this.gamesOption.winner = nameplayer + " win";
      } else if (
        this.gamesOption.botPick == "✊🏼" &&
        this.gamesOption.playerPick == "✌🏼"
      ) {
        this.gamesOption.winner = "Bot Win";
      } else {
        this.gamesOption.winner = "SERI!";
      }
    },
    setplayernamekuh(names) {
      this.profileGame.namePlayer = names;

      if (this.profileGame.namePlayer.length > 6) {
        this.profileGame.namePlayer = "Player";
        this.dialogs = false;
        this.nama = "";
      } else {
        this.profileGame.namePlayer = names;
        this.dialogs = false;
      }
    },
  },
};
</script>
<style  scoped>
.textBt {
  font-size: 115px;
}
.textpilih {
  font-size: 45px;
}
.v-card--reveal {
  align-items: center;
  bottom: 0;
  justify-content: center;
  opacity: 1;
  position: absolute;
  width: 100%;
  cursor: pointer;
}
</style>
