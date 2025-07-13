# Dynamic Dashboard

A dynamic dashboard built with [Vue 3](https://vuejs.org/) and [Vite](https://vitejs.dev/), using [charts.css](https://chartscss.org/) for beautiful, responsive charts. Easily create dynamic charts by passing data as props to components.

## Features

- ⚡️ Fast development with Vite
- 📊 Dynamic charts using charts.css
- 🧩 Modular Vue 3 components
- 🗂️ Simple data-driven chart rendering

## Usage

### Data Structure

To render a chart, pass an array of objects to the chart component's `data` prop. Each object must have:

- `dataPresentation` (string): The label or value to display.
- `value` (number): The numeric value used to calculate the chart.

**Example:**
```js
const graphData = [
  { value: 30, dataPresentation: "30" },
  { value: 20, dataPresentation: "20" },
  { value: 25, dataPresentation: "25" },
  { value: 15, dataPresentation: "15" },
  { value: 10, dataPresentation: "10" }
];
```
