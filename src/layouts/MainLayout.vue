<template>
  <q-layout view="lhr lpR lFr">
    <q-header reveal elevated class="bg-primary text-white" height-hint="98">
      <q-toolbar>
        <q-toolbar-title> Movie Trend Plus+ </q-toolbar-title>
        <q-space />
        <q-separator />
      </q-toolbar>
      <q-tabs align="left">
        <q-route-tab to="/" label="Home" />
        <q-route-tab to="/day" label="Trending Today" />
        <q-route-tab to="/week" label="Trending this Week" />
        <q-route-tab to="/top" label="Top Rated" />
      </q-tabs>
    </q-header>

    <q-page-container class="bg-dark text-white">
      <router-view />
    </q-page-container>
  </q-layout>
</template>
