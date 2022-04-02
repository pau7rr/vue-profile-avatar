#vue-profile-avatar

![Banner](/images/banner.png?raw=true)

An minimalist avatar component for Vue 3.

- Colors decided by initial of username.
- You can customize all colors.

## Installation

`npm install vue-profile-avatar`

// or

`yarn add vue-profile-avatar`

## Usage

### ES6
```js

import Avatar from 'vue-profile-avatar'

export default {
  ...
  components: {
    ProfileAvatar
  },
  ...
}
```
Then:

```html
<ProfileAvatar username="Lorem Ipsum"></ProfileAvatar>
```
## Configuration

### Component props

##### `username`
- Type: String
- Description: Username required for getting background and text color.
- Required: true

##### `size`
- Type: String
- Description: Size of the avatar. Can be `s`, `m`, or `l`.
- Default: `s`
- Required: false

##### `border`
- Type: Boolean
- Description: false if you don't want border.
- Default: true
- Required: false

##### `bgColor`
- Type: ColorHex
- Description: Custom background color.
- Required: false

##### `borderColor`
- Type: ColorHex
- Description: Custom border color.
- Required: false

##### `textColor`
- Type: ColorHex
- Description: Custom text color.
- Required: false

##### `colorType`
- Type: Stirng
- Description: Type of palette colors for your avatars. Can be `normal`, `pastel`, or `brownie`.
- Default: `normal`
- Required: false