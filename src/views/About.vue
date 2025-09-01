<script setup>
import { computed } from "vue"

const data = [
  { month: "Jan", value: 30 },
  { month: "Feb", value: 45 },
  { month: "Mar", value: 60 },
  { month: "Apr", value: 40 },
  { month: "May", value: 70 },
  { month: "Jun", value: 55 }
]

const width = 500
const height = 250
const chartHeight = 200
const chartWidth = 440
const max = Math.max(...data.map(d => d.value))

// Skala X dan Y
const xScale = (i) => 40 + (i * (chartWidth / (data.length - 1)))
const yScale = (v) => chartHeight - (v / max) * 160 + 20

// Buat path line
const linePath = computed(() => {
  return data.map((d, i) => {
    const x = xScale(i)
    const y = yScale(d.value)
    return (i === 0 ? `M ${x},${y}` : `L ${x},${y}`)
  }).join(" ")
})

// Buat area path
const areaPath = computed(() => {
  let path = data.map((d, i) => {
    const x = xScale(i)
    const y = yScale(d.value)
    return (i === 0 ? `M ${x},${y}` : `L ${x},${y}`)
  }).join(" ")
  // tutup area ke bawah
  path += ` L ${xScale(data.length - 1)},${chartHeight+20} L 40,${chartHeight+20} Z`
  return path
})

// Pie Chart
// Hitung total
const total = data.reduce((sum, d) => sum + d.value, 0)

// Fungsi konversi derajat → koordinat
const polarToCartesian = (cx, cy, r, angle) => {
  const rad = (angle - 90) * Math.PI / 180
  return {
    x: cx + r * Math.cos(rad),
    y: cy + r * Math.sin(rad)
  }
}

// Buat arc untuk setiap slice pie
const slices = computed(() => {
  let startAngle = 0
  return data.map(d => {
    const angle = (d.value / total) * 360
    const endAngle = startAngle + angle
    const largeArc = angle > 180 ? 1 : 0

    const start = polarToCartesian(150, 150, 100, startAngle)
    const end = polarToCartesian(150, 150, 100, endAngle)

    const pathData = [
      `M 150,150`,
      `L ${start.x},${start.y}`,
      `A 100,100 0 ${largeArc} 1 ${end.x},${end.y}`,
      `Z`
    ].join(" ")

    startAngle = endAngle

    return {
      path: pathData,
      value: d.value,
      label: d.month
    }
  })
})
</script>

<template>
  <main class="chart-container">
    <div class="chart-header">
      <h2>Statistik Jumlah Pelanggan per Bulan</h2>
    </div>

    <!-- SVG Chart -->
    <svg class="chart" :width="width" :height="height" viewBox="0 0 500 250">
      <!-- Gradient Area -->
      <defs>
        <linearGradient id="gradient" x1="0" x2="0" y1="0" y2="1">
          <stop offset="0%" stop-color="teal" stop-opacity="0.5"/>
          <stop offset="100%" stop-color="teal" stop-opacity="0"/>
        </linearGradient>
      </defs>

      <!-- Background Grid -->
      <g v-for="i in 5" :key="i">
        <line
          x1="40" :y1="i*40" x2="480" :y2="i*40"
          stroke="#ddd" stroke-width="1" stroke-dasharray="4 2"
        />
      </g>

      <!-- Area under line -->
      <path :d="areaPath" fill="url(#gradient)" />

      <!-- Line -->
      <path :d="linePath" fill="none" stroke="teal" stroke-width="3" />

      <!-- Data points -->
      <g v-for="(item, index) in data" :key="index">
        <circle
          :cx="xScale(index)"
          :cy="yScale(item.value)"
          r="5"
          class="chart-point"
        />
        <!-- Value text -->
        <text
          :x="xScale(index)"
          :y="yScale(item.value) - 10"
          class="chart-value"
        >
          {{ item.value }}
        </text>
        <!-- Month label -->
        <text
          :x="xScale(index)"
          y="240"
          class="chart-label"
        >
          {{ item.month }}
        </text>
      </g>
    </svg>
  </main>
  <main class="pie-chart-page">
    <div class="chart-container">
      <h2>Pie Chart Jumlah Pelanggan per Bulan</h2>
      <svg width="300" height="300">
        <g v-for="(slice, index) in slices" :key="index">
          <path
            :d="slice.path"
            :fill="['#4dc9f6','#f67019','#f53794','#537bc4','#acc236','#166a8f'][index % 6]"
            stroke="white"
            stroke-width="2"
          />
        </g>
      </svg>

      <ul class="legend">
        <li v-for="(item, index) in data" :key="index">
          <span
            class="color-box"
            :style="{ backgroundColor: ['#4dc9f6','#f67019','#f53794','#537bc4','#acc236','#166a8f'][index % 6] }"
          ></span>
          {{ item.month }} - {{ item.value }}
        </li>
      </ul>
    </div>
  </main>
</template>

<style scoped>
.chart-container {
  padding: 1rem 2rem;
  text-align: center;
  color: var(--dark-alt, #333);
}

.chart-header h2 {
  font-size: 1.4rem;
  font-weight: 600;
  margin-bottom: 1.5rem;
}

.chart {
  max-width: 100%;
}

.chart-point {
  fill: white;
  stroke: teal;
  stroke-width: 2;
}

.chart-value {
  text-anchor: middle;
  font-size: 12px;
  fill: black;
  font-weight: bold;
}

.chart-label {
  text-anchor: middle;
  font-size: 12px;
  fill: #333;
}

/* pie chart */
.pie-chart-page {
  padding: 1rem 5rem;
  text-align: center;
}

.chart-container {
  display: inline-block;
}

.legend {
  list-style: none;
  padding: 0;
  margin-top: 1rem;
  text-align: left;
}

.legend li {
  margin: 0.3rem 0;
  display: flex;
  align-items: center;
  font-size: 14px;
}

.color-box {
  display: inline-block;
  width: 16px;
  height: 16px;
  margin-right: 8px;
  border-radius: 3px;
}
</style>
