<script lang="ts">
  import "carbon-components-svelte/css/white.css";
  import Location from "carbon-icons-svelte/lib/Location.svelte";
  import Rain from "carbon-icons-svelte/lib/Rain.svelte";
  import Temperature from "carbon-icons-svelte/lib/Temperature.svelte";
  import ChartClusterBar from "carbon-icons-svelte/lib/ChartClusterBar.svelte";
  import DeliveryTruck from "carbon-icons-svelte/lib/DeliveryTruck.svelte";
  import ChartLineSmooth from "carbon-icons-svelte/lib/ChartLineSmooth.svelte";
  import AddFilled from "carbon-icons-svelte/lib/AddFilled.svelte";
  import MapBoundaryVegetation from "carbon-icons-svelte/lib/MapBoundaryVegetation.svelte";

  import {
    TreeView,
    SideNav,
    Header,
    SideNavMenu,
    SideNavItems,
    SideNavMenuItem,
    SideNavDivider,
    SideNavLink,
  } from "carbon-components-svelte";

  let activeId = "";
  let selectedIds = [];
  let expandedIds = [1];
  let children = [
    {
      id: 0,
      icon: Location,
      text: "Gatton",
      children: [
        {
          id: 300,
          text: "Rainfall",
          icon: Rain,
          children: [
            { id: "300.1", icon: ChartClusterBar, text: "Annual" },
            { id: "300.2", icon: ChartClusterBar, text: "Summer" },
            { id: "300.3", icon: ChartClusterBar, text: "Winter" },
            { id: "300.4", icon: ChartClusterBar, text: "Autumn" },
            { id: "300.5", icon: ChartClusterBar, text: "Spring" },
          ],
        },
        {
          id: 20,
          text: "Northern Beef",
          icon: DeliveryTruck,
          children: [
            {
              id: 30,
              text: "Rainfall",
              icon: Rain,
              children: [
                { id: "30.1", icon: ChartClusterBar, text: "Wet Season" },
                { id: "30.2", icon: ChartClusterBar, text: "Dry Season" },
              ],
            },
            {
              id: 40,
              text: "Temperature",
              icon: Temperature,
              children: [
                {
                  id: 40.1,
                  icon: ChartClusterBar,
                  text: "Limited pasture growth",
                },
                { id: 40.2, icon: ChartClusterBar, text: "Annual Heatwaves" },
              ],
            },
          ],
        },
        { id: 50, icon: DeliveryTruck, text: "Southern Sheep" },
        { id: 60, icon: ChartLineSmooth, text: "Seasonal Forecast" },
        { id: 70, icon: MapBoundaryVegetation, text: "Natural Capital" },
      ],
    },
    {
      id: 1,
      text: "Blackbutt",
      icon: Location,
      children: [
        {
          id: 2,
          text: "Northern Beef",
          icon: DeliveryTruck,
          children: [
            {
              id: 3,
              text: "Rainfall",
              icon: Rain,
              children: [
                { id: "3.1", icon: ChartClusterBar, text: "Wet Season" },
                { id: "3.2", icon: ChartClusterBar, text: "Dry Season" },
              ],
            },
            {
              id: 4,
              text: "Temperature",
              icon: Temperature,
              children: [
                {
                  id: 4.1,
                  icon: ChartClusterBar,
                  text: "Limited pasture growth",
                },
                { id: 4.2, icon: ChartClusterBar, text: "Annual Heatwaves" },
              ],
            },
          ],
        },
        { id: 5, icon: DeliveryTruck, text: "Southern Sheep" },
        { id: 6, icon: ChartLineSmooth, text: "Seasonal Forecast" },
        { id: 7, icon: MapBoundaryVegetation, text: "Natural Capital" },
      ],
    },
    {
      id: -1,
      icon: AddFilled,
      text: "Add location",
    },
  ];
</script>

<SideNav isOpen={true}>
  <TreeView
    labelText="Locations"
    {children}
    bind:activeId
    bind:selectedIds
    {expandedIds}
    on:select={({ detail }) => console.log("select", detail)}
    on:toggle={({ detail }) => console.log("toggle", detail)}
    on:focus={({ detail }) => console.log("focus", detail)}
  />
</SideNav>

<div>Active node id: {activeId}</div>
<div>Selected ids: {JSON.stringify(selectedIds)}</div>

<style>
  div {
    margin-top: var(--cds-spacing-05);
  }
</style>
