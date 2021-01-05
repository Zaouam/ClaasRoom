<template v-slot:activator="{ on, attrs }">
  <v-app>
    <v-card

        style="position: sticky;
   top: 0;
   border-radius: 0;
   z-index: 2;"
    >
      <v-toolbar  color="#1E90FF" dark>
        <v-app-bar-nav-icon></v-app-bar-nav-icon>
        <v-toolbar-side-icon>
          <v-img class="mr-3" height="56px" src="@/assets/loogo.png" width="56px">
          </v-img>
        </v-toolbar-side-icon>
        <v-toolbar-title>ClassRoom</v-toolbar-title>

        <v-spacer></v-spacer>
        <v-text-field v-model="search" placeholder="search" />

        <v-btn icon>
          <v-icon>mdi-magnify</v-icon>
        </v-btn>

        <v-menu
            bottom
            min-width="200px"
            rounded
            offset-y
        >
          <template v-slot:activator="{ on }">
            <v-btn
                icon
                x-large
                v-on="on"
            >
              <v-avatar
                  color="#0086b3"
                  size="48"
              >
                <span class="white--text headline">{{ user.initials }}</span>
              </v-avatar>
            </v-btn>
          </template>
          <v-card>
            <v-list-item-content  class="justify-center">
              <div  class="mx-auto text-center">
                <v-avatar
                    color="#0086b3"
                >
                  <span class="white--text headline">{{ user.initials }}</span>
                </v-avatar>
                <h3>{{ user.fullName }}</h3>
                <p class="caption mt-1">
                  {{ user.email }}
                </p>
                <v-divider class="my-3"></v-divider>
                <v-btn
                    depressed
                    rounded
                    text
                >
                  Edit Account
                </v-btn>
                <v-divider class="my-3"></v-divider>
                <v-btn
                    depressed
                    rounded
                    text
                >
                  Disconnect
                </v-btn>
              </div>
            </v-list-item-content>
          </v-card>
        </v-menu>

        <v-btn
                icon>
          <v-icon>mdi-dots-vertical</v-icon>
        </v-btn>


      </v-toolbar>

    </v-card>

    <v-main>
      <HelloWorld :items="resultQuery" />
    </v-main>
    <v-footer
        dark
        padless
    >
      <v-card
          class="flex"
          flat
          tile
      >


        <v-card-text class="py-2 white--text text-center">
          {{ new Date().getFullYear() }} — <strong>by Anis</strong>
        </v-card-text>
      </v-card>
    </v-footer>
  </v-app>

</template>

<script>
import HelloWorld from './components/HelloWorld';

export default {
  name: 'App',

  components: {
    HelloWorld,
  },

  data: () => ({
    search: '',
    items: [
      {
        color: '#1F7087',
        title: 'JAVA',
        artist: 'Mme Hela Bel Haj',
        route: '/About'
      },
      {
        color: '#33ccff',
        title: 'IHM',
        artist: 'Mr Mounir Zrigui',
      },
      {
        color: '#00ace6',
        title: 'IA',
        artist: 'Mr Mounir Zrigui',
      }, {
        color: '#007399',
        title: 'Multimedia',
        artist: 'Mr Samir Belaid',
      }, {
        color: '#0086b3',
        title: 'Tech Web',
        artist: 'Mme Sihem Loukil',
      }, {
        color: '#004d66',
        title: 'Syst Repartis',
        artist: 'Mr El Ayeb',
      }, {
        color: '#00394d',
        title: 'Adm Systeme',
        artist: 'Mr Mazigh',
      }, {
        color: '#002633',
        title: 'Réseaux',
        artist: 'Ons',
      }, {
        color: '#00ace6',
        title: 'Sécurité',
        artist: 'Mr Daldoul',
      },

    ],
    Sitems: [
      {title: 'Click Me'},
      {title: 'Click Me'},
      {title: 'Click Me'},
      {title: 'Click Me 2'},
    ],
    user: {
      initials: 'Az',
      fullName: 'Anis Zaouam',
      email: 'aniszaouam5@gmail.com',
    },
  }),
  methods: {

ite:function(item){
  console.log(item)
  return this.items.filter((item)=>{
    return item.title.match((this.search))
  })
}

},
computed:{

  resultQuery() {
    if (this.search) {
      return this.items.filter(item => {
        return this.search
            .toLowerCase()
            .split(" ")
            .every(v => item.title.toLowerCase().includes(v));
      });
    } else {
      return this.items;
    }
  }
}
}

</script>
