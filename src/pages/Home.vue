<template>
  <v-container fluid class="fill-height bg-surface">
    <v-row justify="center" align="center">
      <v-col cols="12" md="8" lg="6">
        <v-card color="surface-container-high" class="mx-auto">
          <v-card-text class="pa-8 pa-md-12">
            <v-row align="center">
              <v-col cols="12" md="auto" class="text-center">
                <v-avatar size="160" rounded="lg">
                  <v-img src="pfp.webp" alt="profile picture" />
                </v-avatar>
              </v-col>

              <v-col cols="12" md="">
                <div :class="$vuetify.display.mdAndUp ? '' : 'text-center'">
                  <h1 class="text-h2 text-md-h1 font-weight-bold mb-3">
                    Hey, I'm <span class="climate-font">Nyx</span>
                  </h1>
                  <p class="text-h6 text-medium-emphasis mb-4">
                    Polish open-source software engineer
                  </p>

                  <div class="mb-6">
                    <h2 class="text-high-emphasis mb-3">Languages</h2>
                    <div class="d-flex flex-wrap ga-2" :class="$vuetify.display.mdAndUp ? '' : 'justify-center'">
                      <v-chip class="lang-chip" color="primary" variant="elevated">TypeScript</v-chip>
                      <v-chip class="lang-chip" color="secondary" variant="elevated">Python</v-chip>
                      <v-chip class="lang-chip" color="tertiary" variant="elevated">HTML</v-chip>
                      <v-chip class="lang-chip" color="primary" variant="elevated">CSS</v-chip>
                      <v-chip class="lang-chip" color="secondary" variant="elevated">Kotlin</v-chip>
                      <v-chip class="lang-chip" color="tertiary" variant="elevated">Dart</v-chip>
                      <v-chip class="lang-chip" color="primary" variant="elevated">Go</v-chip>
                    </div>
                  </div>

                  <div class="d-flex ga-3 flex-wrap" :class="$vuetify.display.mdAndUp ? '' : 'justify-center'">
                    <v-btn href="https://github.com/nyxiereal" target="_blank" variant="flat" prepend-icon="mdi-github"
                      color="secondary-container">
                      GitHub
                    </v-btn>
                    <v-btn href="https://discord.com/users/1242567443742986373" target="_blank" variant="flat"
                      color="secondary-container">
                      <span class="btn-icon" aria-hidden="true">
                        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 126.644 96" width="18" height="18"
                          fill="currentColor" focusable="false" aria-hidden="true">
                          <path
                            d="M81.15,0c-1.2376,2.1973-2.3489,4.4704-3.3591,6.794-9.5975-1.4396-19.3718-1.4396-28.9945,0-.985-2.3236-2.1216-4.5967-3.3591-6.794-9.0166,1.5407-17.8059,4.2431-26.1405,8.0568C2.779,32.5304-1.6914,56.3725.5312,79.8863c9.6732,7.1476,20.5083,12.603,32.0505,16.0884,2.6014-3.4854,4.8998-7.1981,6.8698-11.0623-3.738-1.3891-7.3497-3.1318-10.8098-5.1523.9092-.6567,1.7932-1.3386,2.6519-1.9953,20.281,9.547,43.7696,9.547,64.0758,0,.8587.7072,1.7427,1.3891,2.6519,1.9953-3.4601,2.0457-7.0718,3.7632-10.835,5.1776,1.97,3.8642,4.2683,7.5769,6.8698,11.0623,11.5419-3.4854,22.3769-8.9156,32.0509-16.0631,2.626-27.2771-4.496-50.9172-18.817-71.8548C98.9811,4.2684,90.1918,1.5659,81.1752.0505l-.0252-.0505ZM42.2802,65.4144c-6.2383,0-11.4159-5.6575-11.4159-12.6535s4.9755-12.6788,11.3907-12.6788,11.5169,5.708,11.4159,12.6788c-.101,6.9708-5.026,12.6535-11.3907,12.6535ZM84.3576,65.4144c-6.2637,0-11.3907-5.6575-11.3907-12.6535s4.9755-12.6788,11.3907-12.6788,11.4917,5.708,11.3906,12.6788c-.101,6.9708-5.026,12.6535-11.3906,12.6535Z" />
                        </svg>
                      </span>
                      Discord
                    </v-btn>
                    <v-btn to="/projects" variant="flat" color="primary" prepend-icon="mdi-folder-multiple">
                      Projects
                    </v-btn>
                  </div>
                </div>
              </v-col>
            </v-row>
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script setup lang="ts">
// Material 3 Home page component
</script>

<style scoped>
/* Material 3 compliant styles - no custom backdrop filters or glows */

.btn-icon {
  display: inline-flex;
  align-items: center;
  margin-right: 8px;
}

.btn-icon svg {
  width: 18px;
  height: 18px;
  display: block;
  fill: currentColor;
}
</style>
