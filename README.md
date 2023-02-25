# Platform Icons Vue Component

## Icons
Icons can be included with the `<PlatformIcon />` component and passing in the name of the icon through the `icon` prop, such as:

```
<PlatformIcon icon="rocket" />
```

## Sizes
By default, icons will be the size of relative text. Icons can be resized by passing in a size to the `size` prop:

```
<PlatformIcon icon="rocket" size="xl" />
```

## Color
By default, icons will be set to the current text color, however colors can be changed by passing colors or CSS custom properties into the `color` prop. CSS classes can also be added to the `<PlatformIcon />` component.

```
<PlatformIcon icon="rocket" color="red" />
```