# D3 Calendar Contributions Map
A [d3.js](https://d3js.org/) map representing time series data. Inspired by Github's contribution chart

![Reusable D3.js Calendar Contributions Chart](example/thumbnail.png)

## Configuration

|Property        | Usage           | Default  | Required |
|:------------- |:-------------|:-----:|:-----:|
| data | Chart data | none | yes |
| selector | DOM selector to attach the chart to | body | no |
| max | Maximum count | max found in data | no |
| startDate | Date to start map at | 1 year ago | no |
| colorRange | Minimum and maximum chart gradient colors | ['#eee', '#c6e48b', '#7bc96f', '#239a3b', '#196127'] | no |
| tooltipEnabled | Option to render a tooltip | true | no |
| tooltipUnit | Unit to render on the tooltip, can be object for pluralization control | 'contributions' | no |
| legendEnabled | Option to render a legend | true | no |
| onClick | callback function on day click events (see example below) | null | no |
| locale | Object to translate every word used, except for tooltipUnit | see below | no |

### Default locale object

```javascript
{
    months: ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec'],
    days: ['S', 'M', 'T', 'W', 'T', 'F', 'S'],
    No: 'No',
    on: 'on',
    Less: 'Less',
    More: 'More'
}
```

## Dependencies

* [d3.js](https://d3js.org/)
* [moment.js](http://momentjs.com/)

## Usage

1: Add d3.js and moment.js

2: Include calendar-contributions-map.js and calendar-contributions-map.css
`<link rel="stylesheet" type="text/css" href="path/tocalendar-contributions-map.css">`
`<script src="path/to/calendar-contributions-map.js"></script>`

3: Format the data so each array item has a `date` and `count` property.
As long as `new Date()` can parse the date string it's ok. Note - there all data should be rolled up into daily bucket granularity.

4: Configure the chart and render it
```javascript
// chart data example
var chartData = [{
  date: valid Javascript date object,
  count: Number
}];
var chart1 = calendarContributionsMap()
              .data(chartData)
              .selector('#chart-one')
              .tooltipEnabled(true)
              .onClick(function (data) {
                console.log('onClick callback. Data:', data);
              });
chart1();  // render the chart
```

### control unit pluralization

```javascript
var chart1 = calendarContributionsMap()
              .data(chartData)
              .tooltipUnit(
                [
                  {min: 0, unit: 'contribution'},
                  {min: 1, max: 1, unit: 'contribution'},
                  {min: 2, max: 'Infinity', unit: 'contributions'}
                ]
              );
chart1();  // render the chart
```

## Pull Requests and issues

...are very welcome!
