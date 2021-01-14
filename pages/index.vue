<template>
<v-container  class="main" >
<v-row class="mr-4"  >
  <h1 >ذهن افزار</h1>
  <v-spacer></v-spacer>
  <div
        class="pa-4 text-center white rounded-r-xl"
  >
  <v-icon>mdi-cog</v-icon>
  </div>
</v-row>
<v-form>
    <v-container>
      <v-row>
        <v-col
          cols="12"
          class="mx-auto"
        >
            <v-text-field
            solo
            flat
            dense
            rounded
            single-line
            hide-details
            clearable
            name="search"
            label="جست و جو"
          ></v-text-field>
        </v-col>
      </v-row>
            </v-container>
</v-form>
      <v-row class="mt-6">

        <v-col cols="12" sm="12" md="10" class="mx-auto">
          <h2 class="mb-4">فروشگاه گیاهان</h2>
   <v-slide-group
      multiple
      show-arrows
    >
      <v-slide-item
        v-for="item in items"
        :key="item.number"
      >
     <v-card class="mx-1" width="250" height="200">
       <v-col cols="4" class="float-right">
          <img
            :src=item.src
            width="100"
            height="200"
          >
       </v-col>
       <v-col cols="5"  class="float-left ml-10"> 
        <v-row><h3 class="teal--text mb-12 mt-2">{{item.name}}</h3></v-row>
        <v-row><h5 class="mb-10">{{item.description}}</h5></v-row>
        <v-row><span>{{item.number}} گیاه</span></v-row>
       </v-col>
     </v-card>
      </v-slide-item>
    </v-slide-group>
  </v-col>
    </v-row>
   <v-row class="mt-6">

        <v-col cols="12" sm="12" md="10" class="mx-auto">
          <h2 class="mb-4">گیاهان شما</h2>
   <v-slide-group
      multiple
      show-arrows
    >
      <v-slide-item
        v-for="item in items"
        :key="item.number"
      >
     <v-card class="mx-1" width="200" height="340">
      
          <v-img
            :src=item.src
            width="200"
            height="200"
          >
            <v-btn v-if="item.like" icon @click="changeLike(item)">
            <v-icon  color="red">
               mdi-heart
            </v-icon>
            </v-btn>
            <v-btn icon  v-if="!item.like" @click="changeLike(item)">
            <v-icon  color="red">
              mdi-heart-outline
            </v-icon>
            </v-btn>
          </v-img>
       
       <v-card-text > 
        <v-row><h3 class="teal--text mb-12 mt-2">{{item.name}}</h3></v-row>
        <v-row><span>{{item.number}} گیاه</span></v-row>
      </v-card-text>
     </v-card>
      </v-slide-item>
    </v-slide-group>
  </v-col>
    </v-row>
    <!-- <v-card class="mx-6" width="200" height="340">
      
          <v-img
            :src=item.src
            width="200"
            height="200"
          >
            <v-btn v-if="item.like" icon @click="changeLike(item)">
            <v-icon  color="red">
               mdi-heart
            </v-icon>
            </v-btn>
            <v-btn icon  v-if="!item.like" @click="changeLike(item)">
            <v-icon  color="red">
              mdi-heart-outline
            </v-icon>
            </v-btn>
          </v-img>
       
       <v-card-text > 
        <v-row><h3 class="teal--text mb-12 mt-2">{{item.name}}</h3></v-row>
        <v-row><span>{{item.number}} گیاه</span></v-row>
      </v-card-text>
     </v-card> -->
       <v-row class="mt-6">

        <v-col cols="12" sm="12" md="10" class="mx-auto">
          <h2 class="mb-4">یادآوری ها</h2>
   <v-data-iterator
      :items="data"
      :items-per-page.sync="itemsPerPage"
      hide-default-footer
    >
      <template v-slot:default="props">
          <v-row>
            <v-col
              v-for="(item, index) in props.items"
              :key="index"
              cols="12"
              sm="6"
              md="6"    
            
            >
              <v-card   elevation="2" class="my-1 rounded-lg" tile color="white" height="100">
               <v-col cols="6" class="float-right">
                 <v-row class="mb-6 mt-3 mr-2 ">
                    <h3 class=" teal--text">
                      {{ item.name}}
                    </h3>
                </v-row>
                <v-row class="mr-2">
                    <span class="font-weight-bolder body-1 ">
                      {{ item.time}}
                    </span>
                </v-row>
                </v-col>
                <v-col >
                  <v-btn :color=item.color dark class="float-left mt-3" fab   elevation="0"
                    ><v-icon>{{item.icon}}</v-icon></v-btn
                  >
                </v-col>
              </v-card>
            </v-col>
          </v-row>
        </template>
    </v-data-iterator>
           <v-row>
            <v-col
               cols="12"
              sm="6"
              md="6"  
            >
              <v-card   elevation="2" class="my-1 rounded-lg" tile color="amber darken-2" height="100">
               <v-col cols="8" class="float-right">
                 <v-row class="mb-6 mt-3 mr-2 ">
                    <h3 class="white--text">
                      افزودن یادآوری
                    </h3>
                </v-row>
                <v-row class="mr-2">
                    <span class="font-weight-bolder body-1 white--text">
                      تعویض خاک , آب دادن 
                    </span>
                </v-row>
                </v-col>
                <v-col >
                  <v-btn color="grey lighten-1"  dark class="float-left mt-3" fab   elevation="0"
                    ><v-icon>mdi-timer-outline</v-icon></v-btn
                  >
                </v-col>
              </v-card>
            </v-col>
          </v-row>
  </v-col>
    </v-row>
     <v-row class="mt-6">

        <v-col cols="12" sm="12" md="10" class="mx-auto">
          <h2 class="mb-4"> محصولات فروشگاه</h2>
    <v-data-iterator
      :items="items"
      :items-per-page.sync="itemsPerPage"
      hide-default-footer
    >
      <template v-slot:default="props">
          <v-row>
            <v-col
              v-for="(item, index) in props.items"
              :key="index"
              cols="6"
              md="3"    
              sm="3"
            
            >
                 <v-card class="mx-1" width="280" height="420">
      
          <v-img
            :src=item.src
            width="280"
            height="280"
          >
            <v-btn v-if="item.like" icon @click="changeLike(item)">
            <v-icon  color="red">
               mdi-heart
            </v-icon>
            </v-btn>
            <v-btn icon  v-if="!item.like" @click="changeLike(item)">
            <v-icon  color="red">
              mdi-heart-outline
            </v-icon>
            </v-btn>
          </v-img>
       
       <v-card-text > 
        <v-row class="justify-center"><h3 class="teal--text mb-5 mt-2 ">{{item.name}}</h3></v-row>
        <v-row class="justify-center mb-5">
       <v-rating
          v-model="item.rate"
          color="yellow darken-3"
          background-color="grey darken-1"
          empty-icon="$ratingFull"
          half-increments
          small
        ></v-rating>
           <span class="grey--text mr-2 mt-2">
        ({{ item.rate }})
      </span>
        </v-row>
        <v-row class="mx-2">
          <v-icon color="teal darken-3">
            mdi-bag-checked
          </v-icon>
          <v-spacer></v-spacer>
          <span class="green--text text--lighten-1">{{item.cost}}</span>
        </v-row>
      </v-card-text>
     </v-card>
            </v-col>
          </v-row>
        </template>
    </v-data-iterator>
  </v-col>
    </v-row>
     <v-row class="mt-6">

        <v-col cols="12" sm="12" md="10" class="mx-auto">
          <h2 class="mb-4">یادآوری ها</h2>
   <v-data-iterator
      :items="webinars"
      :items-per-page.sync="itemsPerPage"
      hide-default-footer
      class="mb-12"
    >
      <template v-slot:default="props">
          <v-row>
            <v-col
              v-for="(item, index) in props.items"
              :key="index"
              cols="12"
              sm="6"
              md="6"    
            >
              <v-card   elevation="2" class="my-1 rounded-lg" tile color="white" height="100">
                <v-row>
                <v-col cols="2" class="mr-2">
                    <v-img
                      src="/v.png"
                      width="48"
                     class="rounded-pill elevation-3 mt-3"
                     >
                    </v-img>
                </v-col>
               <v-col cols="6">
                 <v-row class="mb-6 mr-2  mt-1">
                    <h3 class=" teal--text">
                      {{ item.name}}
                    </h3>
                </v-row>
                <v-row class="mr-2">
                    <span class="font-weight-bolder ">
                      {{ item.time}}
                    </span>
                </v-row>
                </v-col>
                <v-spacer></v-spacer>
                 <v-col class="float-left ml-0 " cols="3"><v-icon color="yellow">mdi-star</v-icon> 
                           <span class="grey--text">
        ({{ item.rate }})
      </span></v-col>
        
              </v-row>
    
              </v-card>
            </v-col>
          </v-row>
        </template>
    </v-data-iterator>

  </v-col>
    </v-row>
     <v-bottom-navigation app :fixed="!fixMenueCheck" :absolute="fixMenueCheck" class="rounded-lg mt-6 overflow-y-auto" height="70"  >
    <v-btn value="recent">

      <v-icon color="teal" large>mdi-home</v-icon>
    </v-btn>
 <v-btn value="recent">
      

      <v-icon large>mdi-timer-outline</v-icon>
    </v-btn>
     <v-btn value="recent" class="rounded-pill" color="teal">
      

      <v-icon large color="white">mdi-cart-outline</v-icon>
    </v-btn>
    <v-btn value="favorites">
      

      <v-icon large>mdi-book-open</v-icon>
    </v-btn>

    <v-btn value="nearby">

      <v-icon large>mdi-infinity</v-icon>
    </v-btn>
  </v-bottom-navigation>
</v-container>
</template>

<script>
  export default {
data: () => ({
      model: null,
      items: [
        {
          src: "/plants.jpeg",
          name: 'گیاهان آپارتمانی',
          description: 'مناسب نگه داری در آپارتمان',
          number: 24,
          like:true,
          rate:2,
          cost:"20000"
        },
        {
           src: "/plants.jpeg",
          name: 'گیاهان آپارتمانی',
          description: 'مناسب نگه داری در آپارتمان',
          number: 25,
          like:false,
          rate:4.5,
          cost:"20000"
        },
        {
           src: "/plants.jpeg",
          name: 'گیاهان آپارتمانی',
          description: 'مناسب نگه داری در آپارتمان',
          number: 26,
          like:false,
          rate:3,
           cost:"20000"
        },
        {
         src: "/plants.jpeg",
          name: 'گیاهان آپارتمانی',
          description: 'مناسب نگه داری در آپارتمان',
          number: 27,
          like:true,
          rate:1,
           cost:"20000"
        },
        {
          src: "/plants.jpeg",
          name: 'گیاهان آپارتمانی',
          description: 'مناسب نگه داری در آپارتمان',
          number: 28,
          like:true,
          rate:3,
           cost:"20000"
        },
        {
          src: "/plants.jpeg",
          name: 'گیاهان آپارتمانی',
          description: 'مناسب نگه داری در آپارتمان',
          number: 29,
          like:false,
          rate:2.5,
           cost:"20000"
        },
        {
           src: "/plants.jpeg",
          name: 'گیاهان آپارتمانی',
          description: 'مناسب نگه داری در آپارتمان',
          number: 30,
          like:true,
          rate:5,
           cost:"20000"
        }
      ],
        itemsPerPage: 4,
      data: [
        {
          name: 'تعویض خاک گیاه',
          color: 'orange',
          time: '2day',
          icon: 'mdi-refresh'
        },
        {
          name: 'آب دادن به گیاه',
          color: 'blue',
          time: '8hour',
          icon: 'mdi-water'
        },
      ],
      webinars: [
        {
          name: 'مهندس پروین نعمتی',
          time: '  روز سشنبه تاریخ ۱۲/۷/۷ ساعت ۹ ',
          rate: '۴.۵'
        },
        {
          name: 'وبینار آبیاری گیاه',
           time: '  روز سشنبه تاریخ ۱۲/۷/۷ ساعت ۹ ',
          rate: '۳.۵۶'
        },
      ],
       fixMenueCheck:false
    }),
    methods:{
      changeLike(item){
        item.like=!item.like
      },
    }
  }
</script>
<style>
.main{
  background-color:#EEEEEE;
  max-width: 100% !important;
}

</style>

