# react-native-lightbox

## Installation

```
npm install --save react-native-lightbox
```

**This module requires React Native 0.11 or later**

## Usage

`navigator` property is optional but recommended on iOS, see next section for `Navigator` configuration.

```js
var createReactClass = require('create-react-class');
var Lightbox = require('react-native-lightbox');

var LightboxView = createReactClass({
  render: function() {
    return (
      <Lightbox navigator={this.props.navigator}>
        <Image
          style={{ height: 300 }}
          source={{ uri: 'http://knittingisawesome.com/wp-content/uploads/2012/12/cat-wearing-a-reindeer-hat1.jpg' }}
        />
      </Lightbox>
    );
  },
});
```

### Navigator setup/Android support

For android support you must pass a reference to a `Navigator` since it does not yet have the `Modal` component and is not on the official todo list. See the `Example` project for a complete example.

```js
var createReactClass = require('create-react-class');

var MyApp = createReactClass({
  renderScene: function(route, navigator) {
    var Component = route.component;

    return (
      <Component navigator={navigator} route={route} {...route.passProps} />
    );
  },

  render: function() {
    return (
      <Navigator
        ref="navigator"
        style={{ flex: 1 }}
        renderScene={this.renderScene}
        initialRoute={{
          component: LightboxView,
        }}
      />
    );
  }
});
```

## Properties

| Prop | Type | Description |
|---|---|---|
|**`activeProps`**|`object`|Optional set of props applied to the content component when in lightbox mode. Usable for applying custom styles or higher resolution image source.|
|**`renderHeader(close)`**|`function`|Custom header instead of default with X button|
|**`renderContent`**|`function`|Custom lightbox content instead of default child content|
|**`onClose`**|`function`|Triggered when lightbox is closed|
|**`onOpen`**|`function`|Triggered when lightbox is opened|
|**`underlayColor`**|`string`|Color of touchable background, defaults to `black`|
|**`backgroundColor`**|`string`|Color of lightbox background, defaults to `black`|
|**`swipeToDismiss`**|`bool`|Enables gestures to dismiss the fullscreen mode by swiping up or down, defaults to `true`.|
|**`pinchToZoom`**|`bool`|Enables pinch to zoom functionality on the fullscreen content, defaults to `true`.|
|**`springConfig`**|`object`|[`Animated.spring`](https://facebook.github.io/react-native/docs/animations.html) configuration, defaults to `{ tension: 30, friction: 7 }`.|

## Demo

![Demo](https://cloud.githubusercontent.com/assets/378279/9074360/16eac5d6-3b09-11e5-90af-a69980e9f4be.gif)

## Example

Check full example in the `Example` folder.

## License

[MIT License](http://opensource.org/licenses/mit-license.html). © Joel Arvidsson
