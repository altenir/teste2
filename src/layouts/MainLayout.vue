<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="leftDrawerOpen = !leftDrawerOpen"
        />

        <q-toolbar-title> Gama API-W </q-toolbar-title>

        <!-- div>
          <q-badge color="warning">
            GRUPO
          </q-badge><br>
          <q-badge color="warning">
            NOME
          </q-badge>
        </div -->
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      bordered
      content-class="bg-grey-11"
    >
      <q-list>
        <q-list class="q-ma-sm rounded-borders">
          <q-list class="no-border">
            <q-item clickable>
              <q-item-section>
                <img
                  style="margin: auto"
                  alt="Logo Uatizapi"
                  src="~assets/logo-kohaku-180x180.png"
                />
              </q-item-section>
            </q-item>
          </q-list>
        </q-list>

        <!-- ######### -->
        <!-- CADASTROS -->
        <!-- ######### -->
        <q-list bordered class="q-ma-sm rounded-borders bg-grey-2 text-grey-10">
          <q-expansion-item
            :content-inset-level="0.1"
            expand-separator
            class="bg-grey-2"
            icon="view_list"
            label="Principal"
            caption=""
            default-opened
          >
            <div class="">
              <q-list dense class="rounded-borders">
                <q-separator />
                <q-item clickable>
                  <q-item-section> Dashboard </q-item-section>
                </q-item>
                <q-separator />
                <q-item clickable to="/instance">
                  <q-item-section> Instâncias </q-item-section>
                </q-item>
                <q-separator />
                <q-item clickable>
                  <q-item-section> Dados da Conta </q-item-section>
                </q-item>
                <q-separator />
                <q-item clickable>
                  <q-item-section> Usuário da API </q-item-section>
                </q-item>
                <q-separator />
                <q-item clickable to="/webhooks-receive">
                  <q-item-section> Webhooks Recebidos </q-item-section>
                </q-item>
              </q-list>
            </div>
          </q-expansion-item>
        </q-list>

        <!-- ######### -->
        <!-- ENVIO DE TESTE -->
        <!-- ######### -->
        <q-list bordered class="q-ma-sm rounded-borders bg-grey-2 text-grey-10">
          <q-expansion-item
            :content-inset-level="0.1"
            expand-separator
            class="bg-grey-2"
            icon="bug_report"
            label="Teste"
            caption=""
            default-opened
          >
            <div class="">
              <q-list dense class="rounded-borders">
                <q-separator />
                <q-item clickable to="/contract">
                  <q-item-section> Templates para envio </q-item-section>
                </q-item>
              </q-list>
            </div>
          </q-expansion-item>
        </q-list>

        <!-- ######### -->
        <!-- AJUDA -->
        <!-- ######### -->
        <q-list bordered class="q-ma-sm rounded-borders bg-grey-2 text-grey-10">
          <q-expansion-item
            :content-inset-level="0.1"
            expand-separator
            class="bg-grey-2"
            icon="help"
            label="Ajuda"
            caption=""
            default-opened
          >
            <div class="">
              <q-list dense class="rounded-borders">
                <q-separator />
                <q-item clickable to="/contract">
                  <q-item-section> Documentação </q-item-section>
                </q-item>
                <q-separator />
                <q-item clickable>
                  <q-item-section> Suporte </q-item-section>
                </q-item>
              </q-list>
            </div>
          </q-expansion-item>
        </q-list>

        <!-- ############# -->
        <!-- CONFIGURAÇÕES -->
        <!-- ############# -->
        <q-list bordered class="q-ma-sm rounded-borders bg-grey-2 text-grey-10">
          <q-expansion-item
            class="rounded-borders bg-grey-2"
            :content-inset-level="0.1"
            expand-separator
            icon="settings"
            label="Administração"
            caption=""
            default-opened
          >
            <div class="">
              <q-list dense class="rounded-borders">
                <q-separator />
                <q-item clickable>
                  <q-item-section> Adm Instâncias </q-item-section>
                </q-item>
                <q-separator />
                <q-item clickable to="/users">
                  <q-item-section> Usuários </q-item-section>
                </q-item>
                <q-separator />
                <q-item clickable>
                  <q-item-section> Grupos </q-item-section>
                </q-item>
                <q-separator />
                <q-item clickable>
                  <q-item-section> Módulos </q-item-section>
                </q-item>
                <q-separator />
                <q-item clickable>
                  <q-item-section> Permissões </q-item-section>
                </q-item>
                <q-separator />
                <q-item clickable>
                  <q-item-section> Opções </q-item-section>
                </q-item>
              </q-list>
            </div>
          </q-expansion-item>
        </q-list>

        <q-item
          clickable
          class="q-ma-sm rounded-borders bg-grey-2 text-grey-10"
          @click="openSobre"
        >
          <q-item-section avatar>
            <q-icon name="sms" color="text-primary" />
          </q-item-section>
          <q-item-section>
            <q-item-label><span class="">Sobre</span></q-item-label>
          </q-item-section>
        </q-item>

        <q-item
          clickable
          class="q-ma-sm rounded-borders bg-grey-2 text-grey-10"
          @click="onLogout"
        >
          <q-item-section avatar>
            <q-icon name="exit_to_app" color="text-primary" />
          </q-item-section>
          <q-item-section>
            <q-item-label><span class="">Sair</span></q-item-label>
          </q-item-section>
        </q-item>
      </q-list>
    </q-drawer>

    <q-dialog v-model="sobre">
      <q-card>
        <q-card-section>
          <div
            class="text-subtitle2 text-center"
            style="font-family: 'exninja'; font-size: 2em"
          >
            KOHAKU
          </div>
        </q-card-section>
        <q-card-section class="q-pt-none">
          <div class="text-center">
            <div>v.0.0.1</div>
          </div>

          <div class="row">
            <div class="col-12 col-md-12">
              <q-banner
                rounded
                inline-actions
                class="text-dark text-center bg-yellow q-ma-sm"
              >
                Desenvolvimento/Suporte<br />
                <div
                  class="q-ma-sm"
                  style="font-family: 'exninja'; font-size: 2em"
                >
                  GAMADEVBR
                </div>
                <br />
                <div class="text-left">
                  <q-icon
                    style="font-size: 2em"
                    name="email"
                  />&nbsp;contato@gamadev.com.br
                </div>
                <br />
                <div class="text-left">
                  <q-icon
                    style="font-size: 2em"
                    name="question_answer"
                  />&nbsp;(91) 99296-0196
                </div>
                <br />
              </q-banner>
            </div>
          </div>
        </q-card-section>
        <q-card-actions align="right">
          <q-btn
            class="q-ma-md"
            label="fechar"
            color="grey-8"
            v-close-popup
          ></q-btn>
        </q-card-actions>
      </q-card>
    </q-dialog>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<style>
/* body {
  background-color: var(--q-color-secondary) !important;
} */
.q-item.q-router-link--active,
.q-item--active {
  color: var(--q-color-accent) !important;
  background-color: var(--q-color-secondary) !important;
}
</style>

<script>
// import EssentialLink from 'components/EssentialLink.vue'

const linksData = [
  {
    title: "Docs",
    caption: "quasar.dev",
    icon: "school",
    link: "#/business",
  },
];

export default {
  name: "MainLayout",
  // components: { EssentialLink },
  data() {
    return {
      sobre: false,
      logado: {},
      leftDrawerOpen: false,
      essentialLinks: linksData,
    };
  },
  async mounted() {
    console.log(process.env.MINHA_VAR);
  },
  computed: {
    onGetLogout() {
      return this.getLogout.staLogout;
    },
  },
  methods: {
    openSobre() {
      this.sobre = true;
    },
  },
};
</script>
