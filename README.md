## Install
```bash
npm install --save vue-facebook-login-component
```

## Usage
To use the component in your template, simply import and register with your component.

### Script
```js
import VFBLogin from 'vue-facebook-login-component'

// OR, use cherry-pick export (better consistency)
import { VFBLogin } from 'vue-facebook-login-component'

export default {
  components: {
    VFBLogin
  }
}
```

### Template
```html
<v-facebook-login app-id="966242223397117"></v-facebook-login>
```

## Props
<div id="props-table-wrap" class="docs-table-wrap">

| Name          | Type   | Default                | Note |
|---------------|--------|------------------------|------|
| value         | Object | `{ connected: false }` | **Scope-component prop**.<br><br>Used for one-way V-model.
| app-id        | String | None                   | **Scope-component prop**.<br><br>**Required prop**.
| version 	    | String | `'v3.1'`               | **Scope-component prop**.<br><br>See [Facebook Docs](https://developers.facebook.com/docs/apps/changelog/) for available values.
| options       | Object | `{}`                   | **Scope-component prop**.<br><br>See [Facebook Docs](https://developers.facebook.com/docs/javascript/reference/FB.init/) for available values.<br><br>**Properties should be camel-case**.
| login-options | Object | `{ scope: 'email' }`   | **Scope-component prop**.<br><br>See [Facebook Docs](https://developers.facebook.com/docs/reference/javascript/FB.login/) for available values.<br><br>**Properties should be camel-case**.
| button-style  | Object | `{}`                   | **Properties should be camel-case.**
| loader-style  | Object | `{}`                   | **Properties should be camel-case.**
| token-style   | Object | `{}`                   | **Properties should be camel-case.**
| text-style    | Object | `{}`                   | **Properties should be camel-case.**

</div>

## Slots
<div id="slots-table-wrap" class="docs-table-wrap">

| Name    | Default                   |
|---------|-------------------------- |
| login   | `'Log in to Facebook'`    |
| logout  | `'Log out from Facebook'` |
| working | `'Please wait...'`        |

</div>

## Events
<div id="events-table-wrap" class="docs-table-wrap">

| Name               | Payload            | Description                                          | Note |
|--------------------|--------------------|------------------------------------------------------|------|
| sdk-init           | (sdk[Object])      | Returns an object with <br> a Facebook SDK instance. | **Scope-component event**
| login              | (response[Object]) | User attempted login.                                | **Scope-component event**.
| logout             | (response[Object]) | User attempted logout.                               | **Scope-component event**.
| connect            | Boolean            | User is connected.                                   | **Scope-component event**.
| click              | None               | &nbsp;                                               | **Scope-component event**.

</div>

## Scope component (Advanced Customization)
If props, slots and events do not satisfy your customization needs, you can use an underlying component called `v-fb-login-scope`. This component uses the render prop (known as "scoped-slot" in Vue) approach for composition. This means, it does not render **any** html or css, hence it has no added-value on its own. It only exposes a scoped-slot with attributes and methods that are committed as API.

### Props/Events
Refer to the [tables](#props-table-wrap) above for scope-component **specific** props/events.

### Scoped-Slot Scope (Attributes and Methods)
<div id="scope-table-wrap" class="docs-table-wrap">

| Name         | Type     | Description                                                |
|--------------|----------|------------------------------------------------------------|
| login        | Function | Login handler.                                             |
| logout       | Function | Logout handler.                                            |
| toggleLogin  | Function | Toggles login/logout.                                      |
| working      | Boolean  | SDK-initialization/login/logout is currently taking place. |
| connected    | Boolean  | User is logged in.                                         |
| disconnected | Boolean  | User is logged out.                                        |
| enabled      | Boolean  | Button is enabled.                                         |
| disabled     | Boolean  | Button is disabled.                                        |

</div>

### Scope component example (for a full example see [source](https://github.com/adi518/vue-facebook-login-component/blob/master/src/components/FBLogin.vue)).

```html
<template>
  <v-facebook-login-scope>
    <button slot-scope="scope">
      <!-- Compose HTML/CSS here, otherwise nothing will be rendered! -->
    </button>
  </v-facebook-login-scope>
</template>

<script>
import { VFBLoginScope } from 'vue-facebook-login-component'

export default {
  components: {
    VFBLoginScope
  }
}
</script>
```

## Development
Fork, clone and use the following scripts.

For component:
```bash
npm start
```
For documentation (includes a demo):
```bash
npm run docs
```

## Support
Please open an [issue](https://github.com/adi518/vue-facebook-login-component/issues) for support.

## License
Copyright (c) 2018 by [MIT](https://opensource.org/licenses/MIT)