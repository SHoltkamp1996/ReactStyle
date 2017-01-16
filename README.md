# React-Style-Guid
There are some basic rules you have to consider
* Only one React componentper per file.
    * But multiple Stateless or Pure components are allowed in one file.
* Use JSX syntax when writing React component 

## Project structure
* This is a possible structure for an Project with `React` als `alt.js`.

```
..
src
|-actions
  |-configAction.js
|-components
  |-configs
    |-admin
      |-SettingsAccordion.jsx
    |-user
      |-FavoriteAccordion.jsx
|-Intro.jsx
|-Intro.scss
|-sources
  |-UserSource.js
|-stores
  |-UserStore.js
|-utils
|-alt.js
|-Index.js
|-Index.css
...
  
```
## Naming 
* **Filename**: Use PascalCase for filenames  `ChaynsUser.jsx`
* **ReferenctNaming**: PascalCase for React components, camelCase for their instances.

```jsx
import  ChaynsUser from './ChaynsUser';

const chaynsUserItem = <ChaynsUser />;
```

* **ComponentNaming**:  Use the filename as the component name. You can use a `index.jsx` if the directory name has the same name as the component. **Better** rename the directory. 

```jsx
import  ChaynsUser from './ChaynsUser';
```

* **Properties** Don't use DOM component propertie names for different purpose e.g. don't use style or className with your own definition.

```jsx
import SchoolClass from './SchoolClass';

<SchoolClass schoolClassName ="Science-Laboratory" />
```

## Component 
* Declar your React component with `extends React.Component`.
* Keep your render function short and clean.
* You can use stateless components to minimize your render function. Especially if you can use the stateless components multiple times.

```jsx
export default class Tapp extends React.Component {
    render(){
        return(
            <div className="tapp">
                <!--Set your intro text-->
                <div className="tapp__intro">
                    <h1>My Tapp</h1>
                    This is a new Tapp
                </div>
                <Accordion />
            </div>
        )
    }
}
``` 

### Component structure

#### extends React.Component
 1. static methods
 2. constructor
 3.  getChildContext
 4.  componentWillMount
 5.  componentDidMount
 6.  componentWillReceiveProps
 7.  shouldComponentUpdate
 8.  componentWillUpdate
 9.  componentDidUpdate
 10. omponentWillUnmount
 11. eventHandlers like `onClickUserPicture()`, `onChangeUserName()`
 12. getter for render like `getUACGroup()`
 13. render

#### React.createClass
 1. displayName
 2. propTypes
 3. contextTypes
 4. childContextTypes
 5. mixins
 6. statics
 7. defaultProps
 8. getDefaultProps
 9. getInitialState
 10. getChildContext
 11. componentWillMount
 12. componentDidMount
 13. componentWillReceiveProps
 14. shouldComponentUpdate
 15. componentWillUpdate
 16. componentDidUpdate
 17. componentWillUnmount
 18. eventHandlers like `onClickUserPicture()`, `onChangeUserName()`
 19. getter for render like `getUACGroup()`
 20. render

## propTypes
* PropTypes will help you to ceep your code clean and structured
* Always define defaultProps for all non-required props.

```jsx
import React, { PropTypes } from 'react'

const propTypes ={
    userId: PropTypes.number.isRequired,
    firstName: PropTypes.string.isRequired,
    greeting: PropTypes.string
};

const defaultProps= {
    greeting: 'Hello, '
};

class User extends React.Component{

    render(){
        <div id={this.props.userId}>
            {this.props.greeting + this.props.firstName}
        </div>
    }
}

User.propTypes = propTypes;
User.defaultProps = defaultProps;

export default  User
```

## Alignment 
* Use this alignmentstyles for your components.

```jsx
<User
    userName = "Max Mustermann"
    userId={123456789}
/>
```
```jsx
//only one Property
<Order id="1234567891011" />
```
```jsx
//children
<User
    userName = "Max Mustermann"
    userId={123456789}
>
    <Orders />
</User>

```

## Quotes
* Use single quotes (') for JavaScript and double quotes (") for JSX. 

```jsx
<User
   userName = "Max Mustermann"
   userId={123456789}
   style = {{margin: '10px'}}
/>
```

## Spacing
* Use a single space for self-closing tags.
 
```jsx
 <Order />
```
* Don't use spaces in your curly braces.

```jsx
<Order element={currentOrder} />
```

## Properties
* Always use camelCase for your prop names.

```jsx
<User
    userName = "Max Mustermann"
    userId={123456789}
/>
```
* Leave out the values when the prop is expelicity `true`.

```jsx
<User hidden />
```

* Always include an alt prop on `<img>` tags. 
* Don't use words like "image", "photo" or "picture" in `<img>` alt props.
* Don't use `accessKey`.
* Use unique IDs as `key`.

## Refs
* Use ref callbacks.

```jsx
<User ref={(ref) => {this.userRef = ref}} />
```

## Parentheses
* Wrap JSX in parentheses when they span more then one line.

```jsx
render(){
    return(
        <div>
            <User
                userName = "Max Mustermann"
                userId={123456789}
                style = {{margin: '10px'}}
            />
        </div>
    )
}
```
```jsx
render(){
    return ( <Order>{ItemName}</Order> )
}
```

## Tags
* Use self-close tags when the tag has no child.
* If the component has multi-line properties, set the closing tag in a new line.

```jsx
<div className="tapp" />
```
```jsx
<div 
    className = "tapp"
    style = {{overflow : "hidden"}} 
/>
```

## Methods
* Use arrow functions if possible and useful.
* Bind event handlers for the render methods in the constructor.

```jsx
export default class extends React.Component {
    constructor(props) {
        super(props);

        this.onClickStar = this.onClickStar.bind(this);
    }

    onClickStar() {
        // do something
    }

    render() {
        return <Star onClick={this.onClickStar} />
    }
}
```
* Don't use underscore prefix. JacaScript has no private method, so it makes less sense. 

## Chayns with React
* By using chayns you have to be sure chayns is ready. Therefor put the `ReactDOM.render` in your `chayns.ready`.

```jsx
chayns.ready.then(function resolved() {

    ReactDOM.render(
            <div className='tapp'>
                <Intro />
            </div>,
            document.querySelector('#app')
    );
        
    console.log('chayns is ready, environment is loaded', chayns.env);
}).catch(function rejected() {
    console.log('no chayns environment found');
}).then(function always() {
    console.log('Will always be executed');
});
```


### Source
* Our StyleGuid based on [Airbnb React-StyleGuid](https://github.com/airbnb/javascript/tree/master/react)
