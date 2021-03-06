## Live example

::: danger
DEPRECATED, use [autocomplete](/examples/autocomplete.html) component instead.
:::

<eg-base>
  <eg-place-default />
</eg-base>

## Source code

```html
<body>
  <div id="root">
    <h1>Test</h1> "Singapore" should appear in the text box on page load. No errors in console.
    <gmap-place-input default-place="Singapore" @place_changed="updatePlace">
    </gmap-place-input>
    {{place && place.lat}}, {{place && place.lng}},
  </div>

  <script src="https://cdnjs.cloudflare.com/ajax/libs/vue/2.6.11/vue.js"></script>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/lodash.js/4.16.4/lodash.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/gmap-vue@1.2.2/dist/gmap-vue.min.js"></script>

  <script>
    Vue.use(GmapVue, {
      load: {
        key: 'AIzaSyDf43lPdwlF98RCBsJOFNKOkoEjkwxb5Sc',
        libraries: 'places'
      },
      // Demonstrating how we can customize the name of the components
      installComponents: true,
    });

    document.addEventListener('DOMContentLoaded', function() {
      new Vue({
        el: '#root',
        data: {
          place: null
        },
        methods: {
          updatePlace(what) {
            this.place = {
              lat: what.geometry.location.lat(),
              lng: what.geometry.location.lng()
            };
          }
        }
      });
    });
  </script>
</body>
```
