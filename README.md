# vue-bottom-sheet

## props

```js
  id: {
    type: String,
    default: "bottom-sheet"
  },
  modalClass: {
    type: String,
    default: ""
  },
  modalStyle: {
    type: String,
    default: ""
  }
}
```

## useage

### template

```html
<template>
  <a href="#bottom-sheet">CLICK</a>

  <bottom-sheet>
    <iframe
      width="100%"
      height="800px"
      src="https://www.youtube.com/embed/IvUU8joBb1Q"
      frameborder="0"
      allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture"
      allowfullscreen
    ></iframe>
  </bottom-sheet>
</template>
```

### js

```js
import BottomSheet from "./BottomSheet";

export default {
  components: {
    BottomSheet
  }
};
```
