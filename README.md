# React Image Timeline

An image-centric timeline component for React.js. View chronological events in a pleasant way.

![screenshot](https://github.com/aaron9000/react-image-timeline/blob/master/src/assets/screenshot.png)

***Updated for React 16***

### Features
- Responsive & mobile-friendly
- Easily customized
- Lightweight (only CSS and SVG)
- Only 20kb
- ***Zero*** extra dependencies

### View Example 
http://aaron9000.github.io/react-image-timeline/


### Add to Existing Project
- `npm install react-image-timeline --save`

### Usage
```js
import ReactDOM from 'react-dom';
import Timeline from 'react-image-timeline';
require('react-image-timeline/dist/timeline.css');

ReactDOM.render(<Timeline events={events} />, document.getElementById('root'));
```


#### Props
|                      Key |                     Type |                 Required
|--------------------------|--------------------------|--------------------------|
|                  events  |        array of "Event"  |                required  |
|            reverseOrder  |                 boolean  |                          |
|        customStartLabel  |               component  |                          |
|          customEndLabel  |               component  |                          | 
|            customHeader  |               component  |                          |
|         customImageBody  |               component  |                          |
|          customTextBody  |               component  |                          |
|            customFooter  |               component  |                          |

### Event
|                      Key |                     Type |                 Required|
|--------------------------|--------------------------|--------------------------|
|                    date  |                    date  |                required  |
|                   title  |                  string  |                required  |
|                imageUrl  |                  string  |                required  |
|                    text  |                  string  |                required  |
|                 onClick  |                function  |                          |
|              buttonText  |                  string  |                          |
|                  extras  |                  object  |                          |


or

```js
{
    date: Date.parse("2013-09-27"),
    text: "Sed leo elit, pellentesque sit amet congue quis, ornare nec lorem.",
    title: "Cairo, Egypt",
    imageUrl: "http://github.com/aaron9000/react-image-timeline/src/assets/egypt.jpg"
}
```

### Customization

#### Event Metadata
To pass extra data into custom components, use the `extras` field on the `event` model.

#### Custom Styles
To customize the timeline styles, add CSS to override [timeline.css](https://github.com/aaron9000/react-image-timeline/blob/master/lib/timeline.css).

#### Custom Dot Pattern
The dots are defined in CSS using a [base64-encoded image](https://www.base64-image.de/). Encode a new image and override the corresponding CSS class.

#### Custom Components
For more advanced customization, you can pass in custom components to replace the defaults. Custom components will be passed an `event` model in props.
```js

// A custom header to replace the default
const CustomHeader = (props) => {

    // The corresponding "event" model
    const {title, extras} = props.event;
    
    // Custom data payload
    const {customField} = extras;

    // Use your own CSS
    return <div className="custom-header">
        <h1>{title}</h1>
        <p>{customField}</p>
    </div>;
};

ReactDOM.render(<Timeline events={events} customHeader={CustomHeader}/>, document.getElementById('root'));
```

#### Run Example Project
```
*clone repository*
npm install
npm run start
```
Then, visit [localhost:3000/example](http://localhost:3000/example) in your browser.

#### Run Tests
```
npm run test
```

#### Build & Run Example Locally
```
npm run build
cd build && python -m SimpleHTTPServer 8000
open http://localhost:8000
```