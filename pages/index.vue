<template>
  <div>
    <section class="section">
      <div class="buttonWrapper">
        <div class="">Shifts</div>
        <b-button size="is-small" type="is-dark" @click="addShift()"
          >ADD SHIFT</b-button
        >
      </div>
      <div v-for="(vacancy, index) in vacancies" :key="index">
        <div class="card mb-3">
          <header class="card-header">
            <p class="card-header-title">{{ vacancy.title }}</p>
            <a href="#" class="card-header-icon" aria-label="more options">
              <span @click="toggleDrawer()">
                <b-icon icon="home"> edit</b-icon>
              </span>
            </a>
          </header>
          <div class="card-content">
            <div class="content">
              <p>{{ vacancy.description }}</p>
              <p class="subtitle">Dates</p>
              <b-table
                :narrowed="true"
                :data="vacancy.dates.data"
                :columns="vacancy.dates.columns"
              ></b-table>
            </div>
          </div>
        </div>
      </div>
    </section>
    <div class="sidebar-page">
      <section class="sidebar-layout">
        <b-sidebar
          type="is-light"
          v-model="openDrawer"
          :right="true"
          :fullheight="true"
        >
          <div class="p-1">
            <div class="block">
              <b-field label="Title">
                <b-input size="is-small" v-model="vacancyObj.title"></b-input>
              </b-field>
              <b-field label="Description">
                <b-input
                  size="is-small"
                  v-model="vacancyObj.description"
                ></b-input>
              </b-field>
              <b-field label="Dates">
                <b-datepicker
                  placeholder="Click to select..."
                  v-model="datesArr"
                  multiple
                  icon="calendar-today"
                  size="is-small"
                >
                </b-datepicker>
              </b-field>
              <div
                v-for="(date, index) in datesArr"
                :key="index"
                class="card mb-3"
              >
                <header class="card-header">
                  <p>{{ date }}</p>
                  <a
                    href="#"
                    class="card-header-icon"
                    aria-label="more options"
                  >
                    <span @click="toggleDrawer()">
                      <b-icon icon="close"></b-icon>
                    </span>
                  </a>
                </header>
                <div class="card-content">
                  <div class="content"></div>
                </div>
              </div>
            </div>
          </div>
        </b-sidebar>
      </section>
    </div>
  </div>
</template>

<script>
import Card from "~/components/Card";

export default {
  name: "HomePage",

  components: {
    Card,
  },
  data() {
    return {
      openDrawer: false,
      typeDrawer: "",
      vacancies: [
        {
          title: "title",
          description: "description",
          dates: {
            data: [
              {
                date: "2016-10-15 13:43:27",
                start_time: "Jesse",
                end_time: "Simmons",
                price: "800",
                type: "Male",
              },
              {
                date: "2016-10-15 13:43:27",
                start_time: "Jesse",
                end_time: "Simmons",
                price: "800",
                type: "Male",
              },
              {
                date: "2016-10-15 13:43:27",
                start_time: "Jesse",
                end_time: "Simmons",
                price: "800",
                type: "Male",
              },
            ],
            columns: [
              {
                field: "date",
                label: "",
                width: "200",
                numeric: true,
                centered: true,
              },
              {
                field: "start_time",
                label: "",
                width: "200",
                numeric: true,
                centered: true,
              },
              {
                field: "end_time",
                label: "",
                width: "200",
                numeric: true,
                centered: true,
              },
              {
                field: "type",
                label: "",
                width: "200",
              },
              {
                field: "price",
                label: "",
                numeric: true,
                centered: true,
              },
            ],
          },
        },
      ],
      datesArr: [],
      datesObj: {
        date: "",
        start_time: "",
        end_time: "",
        price: "",
        type: "",
      },
      vacancyObj: {
        title: "",
        description: "",
        dates: {
          data: [],
          columns: [
            {
              field: "date",
              label: "",
              width: "200",
              numeric: true,
              centered: true,
            },
            {
              field: "start_time",
              label: "",
              width: "200",
              numeric: true,
              centered: true,
            },
            {
              field: "end_time",
              label: "",
              width: "200",
              numeric: true,
              centered: true,
            },
            {
              field: "type",
              label: "",
              width: "200",
            },
            {
              field: "price",
              label: "",
              numeric: true,
              centered: true,
            },
          ],
        },
      },
    };
  },
  methods: {
    addShift() {
      this.openDrawer = !this.openDrawer;
      this.typeDrawer = "add";
    },
    toggleDrawer() {
      this.openDrawer = !this.openDrawer;
      this.typeDrawer = "edit";
    },
  },
};
</script>

<style scoped>
.mb-3 {
  margin-bottom: 12px;
}
.p-1 {
  padding: 1em;
}
.buttonWrapper {
  display: flex;
  justify-content: space-between;
  padding: 12px 0px;
}
</style>