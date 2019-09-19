# { Today I Learned }

## 9/19/2019

* if you use React snippets for VS Code... `RFAC` is the snippet for creating a functional component (using the arrow syntax)



## 7/25/2019

* not new but good to remember

```javascript
const errorStyle = 'font-weight: bold; font-size: 32px; color: red; text-shadow: 1px 1px 0px black, 1px -1px 0px black, -1px 1px 0px black, -1px -1px 0px black;'

console.error('%c Gasp!', consoleStyle, error)

console.info('%c Barely worth a mention, this.', 'color: blue; font-size: 12px')

console.clear()
console.assert(buckeye > wolverine) // true
console.table(anArray)
```

* use browser sync for a quick work
* installed globally

```
$browser-sync start --server --files '*.css, *.html, *.js' --browser firefox"
```


## 5/2/2019

* Using React.Children to add props to child elements

```javascript
const newChildren = React.Children.map(this.props.children, (child) => {
  return React.cloneElement(child, {
    isActive: this.state.value === child.props.value
  })
})

```


## 4/19/2019

- How to submit a form after preventing it from submitting

```javascript
e.preventDefault();
const { target } = e;
const formSubmitCallback = () => target.parentElement.submit();
```

## 4/11/2019

- properties for keeping font widths the same for 'skinny' vs 'wide' numbers

```css
p {
  font-feature-settings: 'tnum';
  font-variant-numeric: tabular-nums;
}
```

## 3/22/2019

- couple tips I've known for a while but nice to capture on the page

### Add a color to VS Code Title Bar

- great idea from Wes Bos, color the title bar based on project, frontend vs backend, etc.
- create a folder `.vscode` in the project (make sure to uncomment .gitignore)
- add a file `settings.json` to the folder
- add some customizations:

```javascript
{
  "workbench.colorCustomizations": {
    "titleBar.activeBackground": "#2ecc40",
    "titleBar.inactiveBackground": "#3d9970"
  }
}
```

### Add a link to a MD file

[Today I Learned](https://www.github.com/erickbennett/til.git)

```markdown
[Today I Learned](https://www.github.com/erickbennett/til.git)
```

## 3/15/2019

### Render Props

```javascript
// creating -> see hooks example

// implementing
<Toggle>{({ on, toggle }) => <Fancy on={on} toggle={toggle} />}</Toggle>
```

### Hooks

```javascript
import { useState } from 'react';

const Toggle = ({ children }) => {
  const [isToggled, setToggle] = useState(false);
  return children({ isToggled, setToggle });
};

export default Toggle;
```

## 3/7/2019

### Launch a specific browser with create-react-app

- package.json

```javascript
"scripts": {
    "start": "BROWSER='Firefox Developer Edition' react-scripts start"
}
```

## 3/6/2019

### React Testing

- Adding a data property to an element is a useful way to aid unit testing

```javascript
<Link to={ROUTE_DETAIL} data-testid="detail-link" />
```

### Gay Hendrick's genius move

1. Any time you **notice** any sort of unhappiness in you...
2. Ask, **what am I trying to control** that is not in my power to control
3. Sometimes you get an immediate **insight**, if not spend time thoughtfully wondering
4. Formally declare it outside of your control; let it go, let it be. Now, **think of a positive action you have control over and take it**

## 3/5/2019

### TIL

TIL is a quick way to capture learning without the time of a blog.

### Parkinson's Law

Parkinson's law of triviality _is an observation about the human tendency to devote a great deal of time to unimportant details while crucial matters go unattended._

### Using React for Presentations

- a React project for creating presentations
- [Spectacle](https://github.com/FormidableLabs/spectacle) on Github
