# react-hexgrid

![Build Status](https://img.shields.io/travis/Hellenic/react-hexgrid.svg)
![Coverage](https://img.shields.io/coveralls/Hellenic/react-hexgrid.svg)
![Downloads](https://img.shields.io/npm/dm/react-hexgrid.svg)
![Downloads](https://img.shields.io/npm/dt/react-hexgrid.svg)
![npm version](https://img.shields.io/npm/v/react-hexgrid.svg)
![dependencies](https://img.shields.io/david/Hellenic/react-hexgrid.svg)
![dev dependencies](https://img.shields.io/david/dev/Hellenic/react-hexgrid.svg)
![License](https://img.shields.io/npm/l/react-hexgrid.svg)

Interactive hexagon grids with React bindings

With inspiration from
[http://www.redblobgames.com/grids/hexagons](http://www.redblobgames.com/grids/hexagons).

## Getting Started

Install it via npm:

```shell
npm install --save react-hexgrid
```

## Example

```javascript
import { HexGrid } from 'react-hexgrid';
import './App.css';

class App extends Component {
  constructor(props) {
    super(props);
    let boardConfig = {
      width: 800, height: 800,
      layout: { width: 10, height: 10, flat: true, spacing: 1.1 },
      origin: { x: 0, y: 0 },
      map: 'hexagon',
      mapProps: [ 2 ]
    }
    let grid = HexGrid.generate(boardConfig);
    this.state = { grid, config: boardConfig };
  }
  render() {
    let { grid, config } = this.state;

    return (
      <div className="App">
        <HexGrid width={config.width} height={config.height} hexagons={grid.hexagons} layout={grid.layout} />
      </div>
    );
  }
}
```
Will look something like this (custom CSS applied):
![HexGrid image](https://raw.githubusercontent.com/Hellenic/react-hexgrid/master/HexGrid.png "HexGrid")

## Configurations

```javascript
{
    width: 1000, // Width of the viewbox
    height: 800, // Height of the viewbox
    layout: { // Settings on how the tiles looks like
        width: 8, // Width of a single tile
        height: 8, // Height of a single tile
        flat: false, // Defines is the tile pointy one or a flat one
        spacing: 1.1 // Spacing between the tiles
    },
    origin: { // Defines the offset for the grid. Depending on the grid type, you might need to adjust this
        x: 0,
        y: 0
    },
    map: 'hexagon', // Grid type (see GridGenerator.js)
                    // Possible values: hexagon, triangle, parallelogram, rectangle, orientedRectangle
    mapProps: [ 3 ] // Properties for the grid type (depends on the grid type)  (see GridGenerator.js)
                    // * 'hexagon': [ radius: Number ]
                    // * 'triangle': [ size: Number ]
                    // * 'parallelogram': [ q1: Number, q2: Number, r1: Number, r1: Number ]
                    // * 'rectangle': [ width: Number, height: Number ]
                    // * 'orientedRectangle': [ width: Number, height: Number ]
}
```

## Exposed classes

{ HexGrid, Hex, Layout, HexUtils }

## Examples

See examples folder.
1. [basic-board](https://github.com/Hellenic/react-hexgrid/tree/master/examples/basic-board)- Just simple render of HexGrid
1. [grid-types](https://github.com/Hellenic/react-hexgrid/tree/master/examples/grid-types) - All the different grid types and their configurations
1. [tile-events](https://github.com/Hellenic/react-hexgrid/tree/master/examples/tile-events) - HexGrid with action functions passed down. Just logs to console when different events are triggered.
1. [pathfinding](https://github.com/Hellenic/react-hexgrid/tree/master/examples/pathfinding) - HexGrid with pathfinding from center of the grid to mouse.

## License

MIT
