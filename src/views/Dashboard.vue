<template>

    <v-container fill-height="true">
        <v-layout>
            <v-flex
                md12
                lg8>
                    <v-card height="100%">
                        <v-tabs fixed-tabs>
                            <v-tab>
                                {{tabs[0]}}
                            </v-tab>

                            <v-tab>
                                {{tabs[1]}}
                            </v-tab>

                            <v-tab>
                                {{tabs[2]}}
                            </v-tab>

                            <v-tab>
                                {{tabs[3]}}
                            </v-tab>

                            <v-tab-item>
                                <v-card flat>
                                    <v-card-text></v-card-text>
                                </v-card>
                            </v-tab-item>

                            <v-tab-item>
                                <v-card flat>
                                    <v-card
                                        height="288px">

                                    </v-card>
                                    <v-form>
                                        <v-container>
                                            <v-layout row wrap>
                                                <v-flex xs12 style="height:72px;">
                                                    <v-text-field
                                                        v-model="message"
                                                        :append-icon="message ? 'mdi-send' : 'mdi-send'"
                                                        box
                                                        clear-icon="mdi-close-circle"
                                                        clearable
                                                        label="Message"
                                                        type="text"
                                                        class='my-input'
                                                        @click:append="sendMessage"
                                                        @click:clear="clearMessage"
                                                    ></v-text-field>
                                                </v-flex>

                                        </v-layout>
                                        </v-container>
                                    </v-form>
                                </v-card>
                            </v-tab-item>

                            <v-tab-item>
                                <v-card flat>
                                    <v-card-text></v-card-text>
                                </v-card>
                            </v-tab-item> 

                            <v-tab-item>
                                <v-card flat>
                                    <v-card-text></v-card-text>
                                </v-card>
                            </v-tab-item>  

                        </v-tabs>

                        
                    </v-card>
                </v-flex>
        </v-layout>
    </v-container>
</template>

<script>
  export default {
    data: () => ({
      tabs : ['View Resources', 'Chats', 'Live Polls', 'Score'],
      password: 'Password',
      show: false,
      message: 'Hey!',
      marker: true,
      iconIndex: 0,
      icons: [
        'mdi-emoticon',
        'mdi-emoticon-cool',
        'mdi-emoticon-dead',
        'mdi-emoticon-excited',
        'mdi-emoticon-happy',
        'mdi-emoticon-neutral',
        'mdi-emoticon-sad',
        'mdi-emoticon-tongue'
      ]
    }),

    computed: {
      icon () {
        return this.icons[this.iconIndex]
      }
    },

    methods: {
      toggleMarker () {
        this.marker = !this.marker
      },
      sendMessage () {
        this.resetIcon()
        this.clearMessage()
      },
      clearMessage () {
        this.message = ''
      },
      resetIcon () {
        this.iconIndex = 0
      },
      changeIcon () {
        this.iconIndex === this.icons.length - 1
          ? this.iconIndex = 0
          : this.iconIndex++
      }
    }
  }
</script>

<style>
    .my-input .v-input .v-input__slot {
        border-radius: 100px;
    }
</style>
