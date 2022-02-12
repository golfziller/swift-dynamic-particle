
  <template>
  <div class="">
    <vs-navbar
      shadow
      fixed
      square
      center-collapsed
      v-model="active"
      class="navbar-custom"
    >
      <template #left>
        <div class="box-left">
          <img src="@/assets/img/sentenance_logo.png" width="150px" />
          <span class="material-icons-outlined burger" @click="onClickSlide">
            menu
          </span>
        </div>
      </template>
      <template #right>
        <vs-avatar badge circle size="35" success class="icon-space">
          <span class="material-icons-outlined"> notifications </span>
        </vs-avatar>
        <vs-avatar badge circle size="35" warn class="icon-space">
          <span class="material-icons-outlined"> chat_bubble_outline </span>
        </vs-avatar>
        <span class="show-name icon-space">Hi, Admin</span>
        <vs-avatar circle size="35">
          <template #text> A </template>
        </vs-avatar>
      </template>
    </vs-navbar>
    <vs-sidebar
      v-model="active"
      :open="activeSidebar"
      square
      class="slide-bar-custom"
    >
      <vs-sidebar-item id="home">
        <template #icon>
          <span class="material-icons"> home </span>
        </template>
        Overview
      </vs-sidebar-item>
      <vs-sidebar-item id="report">
        <template #icon>
          <span class="material-icons"> list_alt </span>
        </template>
        Report
      </vs-sidebar-item>
      <vs-sidebar-item id="map">
        <template #icon>
          <span class="material-icons"> map </span>
        </template>
        Map
      </vs-sidebar-item>
      <vs-sidebar-item id="Location">
        <template #icon>
          <span class="material-icons"> location_on </span>
        </template>
        Location
      </vs-sidebar-item>

      <vs-sidebar-group>
        <template #header>
          <vs-sidebar-item arrow> Device Management </vs-sidebar-item>
        </template>

        <vs-sidebar-item id="sensor">
          <template #icon>
            <i class="material-icons">stacked_bar_chart</i>
          </template>
          Sensor
        </vs-sidebar-item>
        <vs-sidebar-item id="gateway">
          <template #icon>
            <i class="material-icons">mediation</i>
          </template>
          Gateway
        </vs-sidebar-item>
        <vs-sidebar-item id="camera">
          <template #icon>
            <i class="material-icons">camera</i>
          </template>
          camera
        </vs-sidebar-item>
      </vs-sidebar-group>
      <vs-sidebar-group>
        <template #header>
          <vs-sidebar-item arrow> Manage work </vs-sidebar-item>
        </template>

        <vs-sidebar-item id="workManage">
          <template #icon>
            <i class="material-icons">work</i>
          </template>
          Work Management
        </vs-sidebar-item>
        <vs-sidebar-item id="workStatus">
          <template #icon>
            <i class="material-icons">wysiwyg</i>
          </template>
          Work Status
        </vs-sidebar-item>
      </vs-sidebar-group>
      <vs-sidebar-group>
        <template #header>
          <vs-sidebar-item arrow> Setting </vs-sidebar-item>
        </template>

        <vs-sidebar-item id="alert">
          <template #icon>
            <i class="material-icons">error_outline</i>
          </template>
          Alert
        </vs-sidebar-item>
        <vs-sidebar-item id="network">
          <template #icon>
            <i class="material-icons">cell_wifi</i>
          </template>
          Network
        </vs-sidebar-item>
        <vs-sidebar-item id="locationSetting">
          <template #icon>
            <i class="material-icons">my_location</i>
          </template>
          Location Setting
        </vs-sidebar-item>
        <vs-sidebar-item id="user">
          <template #icon>
            <i class="material-icons">person</i>
          </template>
          User
        </vs-sidebar-item>
        <vs-sidebar-item id="permission">
          <template #icon>
            <i class="material-icons">person_search</i>
          </template>
          Permission Setting
        </vs-sidebar-item>
      </vs-sidebar-group>

      <template #footer>
        <div class="logOut">
          <vs-button danger  block> <span class="material-icons-outlined"> logout </span
          ><span class="text-icon">Logout</span> </vs-button>
         
        </div>
      </template>
    </vs-sidebar>
    <div :class="`page ${!activeSidebar ? 'page-slide-left' : ''} `">
      <nuxt></nuxt>
    </div>
  </div>
</template>
  <script>
export default {
  data: () => ({
    active: "home",
    activeSidebar: true,
  }),
  methods: {
    onClickSlide() {
      this.activeSidebar = !this.activeSidebar;
    },
  },
};
</script>
<style scoped>
.page {
  margin-top: 50px;
  margin-left: 260px;
  padding: 15px;;
  transition: 0.3s;
}
.logOut {
  display: flex;
  align-items: center;
  justify-content: flex-end;
  color: red;
  width: 100%;
}
.show-name {
  color: white;
  font-size: 12px;
}
.icon-space {
  margin-left: 5px;
  margin-right: 5px;
}
.box-left {
  display: flex;
  justify-content: space-between;
  width: 260px;
}
.page-slide-left {
  margin-left: 0px;
  transition: 0.5s;
}
.burger {
  cursor: pointer;
  display: flex;
  align-items: center;
}
.navbar-custom {
  z-index: 20000;
  background-color: #85827e;
}
.slide-bar-custom {
  z-index: 12000;
  padding-top: 100px;
  /* //border-right: 4px solid #d2faec; */
}
.vs-sidebar__item.hasIcon.active {
  color: green;
}
.vs-sidebar__item.active:after {
  background-color: green;
}
.vs-sidebar__footer {
  background-color: green!important;
}
</style>
