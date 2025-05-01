<script setup>
import { onMounted, ref, computed } from 'vue'
import { useDate } from 'vuetify'

// Calendar setup
const today = ref(new Date())
const events = ref([])
const calendarColors = ['blue', 'indigo', 'deep-purple', 'cyan', 'green', 'orange', 'grey-darken-1']
const names = ['Meeting', 'Holiday', 'PTO', 'Travel', 'Event', 'Birthday', 'Conference', 'Party']

// Mini Calendar Logic
const miniDate = ref(new Date())
const selectedDate = ref(new Date())

const miniMonth = computed(() => miniDate.value.getMonth())
const miniYear = computed(() => miniDate.value.getFullYear())

const miniMonthName = computed(() =>
  new Date(miniYear.value, miniMonth.value).toLocaleString('default', { month: 'long' }),
)

const miniWeekDays = ['Sun', 'Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat']

const miniDaysInMonth = computed(() => {
  return new Date(miniYear.value, miniMonth.value + 1, 0).getDate()
})

const miniFirstDayOfMonth = computed(() => {
  return new Date(miniYear.value, miniMonth.value, 1).getDay()
})

const nextMiniMonth = () => {
  miniDate.value = new Date(miniYear.value, miniMonth.value + 1)
}

const prevMiniMonth = () => {
  miniDate.value = new Date(miniYear.value, miniMonth.value - 1)
}

const selectDate = (day) => {
  selectedDate.value = new Date(miniYear.value, miniMonth.value, day)
}

const isSelectedDate = (day) => {
  const date = new Date(miniYear.value, miniMonth.value, day)
  return date.toDateString() === selectedDate.value.toDateString()
}

const hasEvents = (day) => {
  const date = new Date(miniYear.value, miniMonth.value, day)
  return events.value.some((e) => new Date(e.start).toDateString() === date.toDateString())
}

onMounted(() => {
  // Initialize calendar events
  const adapter = useDate()
  fetchEvents({
    start: adapter.startOfDay(adapter.startOfMonth(today.value)),
    end: adapter.endOfDay(adapter.endOfMonth(today.value)),
  })
})

function fetchEvents({ start, end }) {
  const _events = []
  const min = start
  const max = end
  const days = (max.getTime() - min.getTime()) / 86400000
  const eventCount = rnd(days, days + 20)

  for (let i = 0; i < eventCount; i++) {
    const allDay = rnd(0, 3) === 0
    const firstTimestamp = rnd(min.getTime(), max.getTime())
    const first = new Date(firstTimestamp - (firstTimestamp % 900000))
    const secondTimestamp = rnd(2, allDay ? 288 : 8) * 900000
    const second = new Date(first.getTime() + secondTimestamp)

    _events.push({
      title: names[rnd(0, names.length - 1)],
      start: first,
      end: second,
      color: calendarColors[rnd(0, calendarColors.length - 1)],
      allDay, // Fixed: was incorrectly set to !allDay
    })
  }

  events.value = _events
}

function rnd(a, b) {
  return Math.floor((b - a + 1) * Math.random()) + a
}
</script>

<template>
  <!-- Mini Calendar -->
  <v-card class="mt-4" elevation="2">
    <v-card-title class="d-flex justify-space-between align-center">
      <v-btn icon @click="prevMiniMonth" density="comfortable">
        <v-icon>mdi-chevron-left</v-icon>
      </v-btn>
      <span class="text-subtitle-1">{{ miniMonthName }} {{ miniYear }}</span>
      <v-btn icon @click="nextMiniMonth" density="comfortable">
        <v-icon>mdi-chevron-right</v-icon>
      </v-btn>
    </v-card-title>

    <v-card-text>
      <v-row dense class="text-caption font-weight-bold text-center">
        <v-col v-for="day in miniWeekDays" :key="day" cols="1.714">
          <!-- Fixed: cols="12/7" to cols="1.714" -->
          {{ day }}
        </v-col>
      </v-row>

      <v-row dense class="mt-1">
        <!-- Empty spaces for first day offset -->
        <v-col v-for="n in miniFirstDayOfMonth" :key="'empty-' + n" cols="1.714"></v-col>
        <!-- Fixed: cols value -->

        <!-- Calendar days -->
        <v-col v-for="day in miniDaysInMonth" :key="day" cols="1.714" class="pa-1">
          <!-- Fixed: cols value -->
          <v-btn
            :color="isSelectedDate(day) ? 'primary' : ''"
            :variant="isSelectedDate(day) ? 'flat' : 'text'"
            icon
            density="comfortable"
            size="small"
            @click="selectDate(day)"
          >
            {{ day }}
            <v-badge
              v-if="hasEvents(day) && !isSelectedDate(day)"
              color="primary"
              dot
              location="bottom"
            ></v-badge>
          </v-btn>
        </v-col>
      </v-row>
    </v-card-text>

    <v-divider></v-divider>

    <!-- Selected date information -->
    <v-card-text v-if="selectedDate">
      <v-row no-gutters>
        <v-col cols="auto" class="mr-2">
          <v-icon color="primary">mdi-calendar</v-icon>
        </v-col>
        <v-col>
          <div class="text-subtitle-2 font-weight-medium">
            {{
              selectedDate.toLocaleDateString(undefined, {
                weekday: 'long',
                month: 'long',
                day: 'numeric',
              })
            }}
          </div>
          <div class="text-caption">
            {{
              events.filter((e) => new Date(e.start).toDateString() === selectedDate.toDateString())
                .length
            }}
            events
          </div>
        </v-col>
      </v-row>
    </v-card-text>
  </v-card>
</template>
