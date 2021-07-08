<template>
   <v-card
      rounded
      height="600"
      width="600"
      color="#faf1ea"
      class="mx-auto pa-6 rounded-xl d-flex flex-column"
   >
      <!-- Word Type -->
      <v-row>
         <v-col>
            <h4 class="ml-2">{{ type }}</h4>
         </v-col>
      </v-row>

      <!-- Kana Reading -->
      <v-row v-if="this.clicked1">
         <v-col class="d-flex align-center justify-center mb-n16">
            <h2> {{this.kana}} </h2>
         </v-col>
      </v-row>

      <!-- Kanji / Word -->
      <v-row v-if="!this.clicked2">
         <v-col class="d-flex align-center justify-center mt-n6 mb-6">
            <h1 :class="this.clicked1 ? 'mb-6' : 'mt-12'"> {{this.word}} </h1>
         </v-col>
      </v-row>

      <!-- Word Meaning -->
      <v-row v-if="this.clicked2">
         <v-col class="d-flex align-center justify-center mt-n6 mb-6">
            <h1> {{this.meaning}} </h1>
         </v-col>
      </v-row>

      <!-- Bottom Buttons -->
      <v-row class="d-flex align-end">
         <v-spacer></v-spacer>

         <!-- Hiragana Button -->
         <v-col>
            <v-btn
               elevation=0
               width="200"
               height="85"
               @click="click(0)"
               :class="this.clicked1 ? 'rounded-xl clicked' : 'rounded-xl not-clicked'"
            >
               あ
            </v-btn>
         </v-col>
         <v-spacer></v-spacer>

         <!-- Meaning Button -->
         <v-col>
            <v-btn
               elevation=0
               width="200"
               height="85"
               @click="click(1)"
               :class="this.clicked2 ? 'rounded-xl clicked' : 'rounded-xl not-clicked'"
            >
               <!-- :class="this.clicked[1] ? 'rounded-xl clicked' : 'rounded-xl not-clicked'" -->
               意味
            </v-btn>
         </v-col>
         <v-spacer></v-spacer>
      </v-row>
   </v-card>
</template>

<script>
export default {
   name: 'Flashcard',

   props: ["word", "kana", "meaning", "type", "checked", "clicked1", "clicked2"],

   data: () => ({
      // clicked: [false, false], // doesn't work for some reason
   }),

   methods: {
      click: function(btn) {
         if (!btn) {
            this.clicked1 = !this.clicked1;
            this.clicked2 = false;
            }
         else {
            this.clicked2 = !this.clicked2;
            this.clicked1 = false;
         }
         // this.clicked[btn] = !this.clicked[btn];
         // this.clicked[Math.abs(btn-1)] = false;
      },
      check: function() {
         this.checked = !this.checked;
         this.$emit('newChecked', this.checked);
      }
   }
}
</script>

<style scoped>
   .clicked {
      color:#f7e5dc !important;
      background: #b48b8b !important;
      background-color: #b48b8b !important;
      border-radius:15px !important;
      font-size: 50px !important;
      text-align: center !important;
      text-justify: center !important;
      padding-bottom: 5px !important;
      font-weight: bold;
   }
   .not-clicked {
      border-radius:15px !important;
      font-size: 50px !important;
      text-align: center !important;
      text-justify: center !important;
      padding-bottom: 5px !important;
      font-weight: bold;
      color:#a87272 !important;
      background: #d6b8b8 !important;
      background-color: #d6b8b8 !important;
   }
   h1 {
      font-weight: bold;
      font-size: 70px !important;
      color:#845151 !important;
      text-align: center !important;
      text-justify: center !important;
   }
   h2 {
      font-size: 40px !important;
      color:#8d5a5a !important;
      text-align: center !important;
      text-justify: center !important;
   }
   h4{
      font-weight: bold;
      font-size: 30px !important;
      color:#694646 !important;
   }
</style>