<div align="center">
    <h1>react-tooltip-z</h1>
    <a href="https://github.com/delpikye-v/react-tooltip">react-tooltip-z</a>
    <br />
    <br />
    <b><a href="https://codesandbox.io/s/react-tooltip-0bspg">LIVE EXAMPLE</a>
    </b>
</div>

---

#### Desciption

It is wrap the tooltip for the element. (Cusomize tooltip - `html/css/complex`)

Append the tooltip outside the root (`portal element`).

---
### Usage

Install the package

```js
npm install --save react-tooltip-z
```

Import the module in the place you want to use:
```js
import { Tooltip } from "react-tooltip-z";
// import { Tooltip, useTooltipContext } from "react-tooltip-z";

```

#### Snippet

###### simple
```js
// const [content, setContent] = useState('This is simple tooltip')
<Tooltip
    tooltipContent={'This is simple tooltip'}
    placement="bottom"
>
    <button>this is children</button>
</Tooltip>

```

<br />

###### simple `jsx/component`

```js
function myClick() {}

<Tooltip
    tooltipContent={<b>This is jsx<br /> Tooltip</b>} // or Component
    tooltipClassName="my-class"
    placement="right"
    trigger="click"
    handleClick={() => alert('event active')} // myClick()
>
	<button>this is children</button>
</Tooltip>
```

<br />

###### simple `manual` (with api)

```js
// here is the sample, please update it exactly with your source

const [sync, setSync] = useState(false)
// fetch api // do something
fetchApi() {
    if (sync) {
        setSync(false)
        return
    }

    fetch('api').then(....).then(rs => {
        setTodo(todo)
        setSync(true)
    }) 
}

<Tooltip 
    tooltipContent={<div>{todo.title}e<br />fds</div>}
    trigger="manual"
    placement='right'
    showSync={sync} // manual simple
>
	<button>Tooltip of todo</button>
</Tooltip>

<button onClick={fetchApi}>Fetch</button>
```

<br />

##### More complex (with api + useTooltipContext)

```js
// here is the sample, please update it exactly with your source

import { Tooltip, useTooltipContext } from "react-tooltip-z";

// ListData.js
<ul>
    {
        post.map(item => {
            return (
                <Tooltip
                    tagName="li"  // wrap all child
                    trigger="manual" 
                    placement="right"

                    // exact html prop & more...
                    style={{ color: red }} 
                >
                    <ListDataItem {...} />
                </Tooltip>
            )
        })
    }
</ul>

// ListDataItem.js (children)
// use TooltipContext to update tooltip
const { showTooltip, hideTooltip, isShow, tooltipId} = useTooltipContext()

// do something and show tooltip
fetchApi() {
    showTooltip('tooltip data after fetch.')
}

<div
    onClick={fetchApi}
    onMouseLeave={hideTooltip}
>
    This is list data item index.
</div>

```

<br />

---


#### props

| props            	| type                  		| desciption                                                         		|
|-------------------|-------------------------------|---------------------------------------------------------------------------|
| tagName          	| String                		| If you wrap all children component,  use this                      		|
| tooltipClassName 	| String                		|                                                                    		|
| tooltipContent   	| `String`/`Component`/ `jsx`   | Tooltip data                                                   			|
| placement        	| `top`/`right`/`left`/`bottom` | it relies on the element's height,  width and position to display 		|
| trigger          	| `hover`/`click`/`manual`    	| Default `hover`                                                 			|
| delayShow         | Number (`250`) minisecond   	| Time delay show tooltip                                    				|
| limitWidth        | Boolean         				| Default: `true` . (Fix `max-width: 200px` / `false`: none)				|
| handleClick      	| function              		| When use event onClick of element(trigger click)         					|
| handleMouseEnter 	| function              		| When use event onMouseEnter of element (trigger hover)   					|
| handleMouseLeave 	| function              		| When use event onMouseLeave of element (trigger hover)              		|
| onShown      		| function 						| Handle after show              											|
| onHidden     		| function 						| Handle after hide              											|
| showSync     		| boolean  						| Simple trigger = manual       											|
| hideIfResize 		| boolean  						| hide tooltip if resize screen  (true)										|
| ...props 			| other	  						| other props exact of elements												|

<br />

#### Note

```js
`showSync`, `useTooltipContext`: use when trigger = `manual`
```

event: `handleClick` (onClick), `handleMouseEnter`(onMouseEnter), `handleMouseLeave` (onMouseLeave)` 

+ Tooltip using `3 function js for trigger`. So if you want to use them, please pass the props function.

+ `placement`: if the position of the tooltip goes beyond the screen. It try will move to the right position to be visible.

 
<br />

#### RUN

<b><a href="https://codesandbox.io/s/react-tooltip-0bspg">LIVE EXAMPLE</a>

<br />

### License

MIT
