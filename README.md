# React Waypoint

[![npm version](https://badge.fury.io/js/react-waypoint.svg)](http://badge.fury.io/js/react-waypoint)
[![bower version](https://badge.fury.io/bo/react-waypoint.svg)](http://badge.fury.io/bo/react-waypoint)
[![Build Status](https://travis-ci.org/brigade/react-waypoint.svg?branch=master)](https://travis-ci.org/brigade/react-waypoint)

A React component to execute a function whenever you scroll to an element. Works
in all containers that can scroll, including the window.

React Waypoint can be used to build features like lazy loading content, infinite
scroll, or docking elements to the viewport on scroll.

Inspired by [Waypoints][waypoints], except this little library grooves the
[React][react] way.

## Demo
![Demo of React Waypoint in action](https://raw.github.com/brigade/react-waypoint/master/react-waypoint-demo.gif)

[View demo page][demo-page]

[waypoints]: https://github.com/imakewebthings/waypoints
[react]: https://github.com/facebook/react
[demo-page]: http://brigade.github.io/react-waypoint/

## Installation

### npm

```bash
npm install react-waypoint --save
```

### Bower

```bash
bower install react-waypoint --save
```

## Usage

```javascript
var Waypoint = require('react-waypoint');
```

```javascript
<Waypoint
  onEnter={this._handleWaypointEnter}
  onLeave={this._handleWaypointLeave}
  threshold={0.2}
/>
```

### Example: [JSFiddle Example][jsfiddle-example]

[jsfiddle-example]: http://jsfiddle.net/L4z5wcx0/7/

## Prop types

```javascript
  propTypes: {

    /**
     * Function called when waypoint enters viewport
     * Both parameters will be null if the waypoint is in the
     * viewport on initial mount.
     *
     * @param {Event|null} event
     * @param {'above'|'below'|null} from
     */
    onEnter: PropTypes.func,

    /**
     * Function called when waypoint leaves viewport
     *
     * @param {Event|null} event
     * @param {'above'|'below'} to
     */
    onLeave: PropTypes.func,

    /**
     * Threshold - a percentage of the height of the visible
     * part of the scrollable parent (e.g. 0.1)
     */
    threshold: PropTypes.number
  },
```

## Limitations

In this component we make a few assumptions that we believe are generally safe,
but in some situations might present limitations.

- We determine the scrollable-ness of a node by inspecting its computed
  overflow-y or overflow property and nothing else. This could mean that a
  container with this style but that does not actually currently scroll will be
  considered when performing visibility calculations.
- We assume that waypoint is rendered within at most one scrollable container.
  If you render a waypoint in multiple nested scrollable containers, the
  visibility calculations will likely not be accurate.
- We also base the visibility calculations on the scroll position of the
  scrollable container (or `window` if no scrollable container is found). This
  means that if your scrollable container has a height that is greater than the
  window, it might trigger `onEnter` unexpectedly.

## Credits

Credit to [trotzig][trotzig-github] and [lencioni][lencioni-github] for writing
this component, and the [Brigade team][brigade-github] for open sourcing it.

Thanks to the creator of the original Waypoints library,
[imakewebthings][imakewebthings-github].

[lencioni-github]: https://github.com/lencioni
[trotzig-github]: https://github.com/trotzig
[brigade-github]: https://github.com/brigade/
[imakewebthings-github]: https://github.com/imakewebthings

## License

[MIT][mit-license]

[mit-license]: ./LICENSE
