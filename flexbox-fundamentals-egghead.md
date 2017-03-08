#Flexbox Fundamentals (Egghead)
---

###What will `display: flex` do?
It will convert the container into a block level element and will affect the layout of its children.

To make the flex container an inline element, but still be able to display contents using flexbox, you can use `display: inline-flex`

###What is the default value of `flexbox-direction`?
`row`. 

Flexbox containers have a property called `flexbox-direction` which defaults to `row`. It will make child elements align horizontally. To align them vertically, set its value to `column`.

`flexbox-direction` is very useful in responsive design. For example you can change nav menu items from horizontal on big screens to vertical on small screens.


###Other than `row` and `column`, what other values can you give to `flexbox-direction`?
`row-reverse` and `column-reverse`. They will reverse the respective layouts.

###Which property decides the order in which children are displayed inside flexbox container?
`order` property of children elements.

`order` defaults to `0`. And when multiple children have same order value, they appear in the order in which they are defined in DOM.

Negative values are also allowed. If all elements have default order value(`0`), then setting one element's order value to `-1` will pull it at the top.

###Which property affects the way children are aligned (along the direction in which content is flowing ?
`justify-content`.

###What is the default value of `justify-content`?
`flex-start`. 

In vertically aligned layout, they will bunch up to the top. If you set it to `flex-end` they will bunch together at the bottom. And `center` will align them to the center.

###What does `justify-content: space-between` do?
It sticks first item at the top, last at the bottom, and rest of the children spaced evenly in between.

There is also `space-around` option which distributes the space evenly b/w items (including first and last)

###Which property affects the space perpendicular to the flex direction?
`align-items`.

Default value is `stretch`. You can also set it to `flex-start`, `flex-end`, `center` or `baseline`.

###How can you change alignment of one child individually?
Using `align-self` on that particular child.

It defaults to `auto`, which means do whatever `align-items` says.

###Which 3 properties can be used to set sizes of flexbox children elements?

- flex-grow
- flex-shrink
- flex-basis

These are applied to individual children and not to the container.

You should use flex-basis to set size in direction of flexbox and not give width/height to individual children.

###What is the use of `flex-grow`?
- It decides how the extra space is divided up by the children.
- Its default value is `0`, which means none of the children will grow beyond the `flex-basis`.
- If there are 2 children and one has `flex-grow: 1` then it will take 100% of the extra space. If both have `flex-grow` set to 1, both will take 1/2 of extra space.
- If `flex-basis` is not defined, then `flex-grow` will define the size of children elements.

###What is the default value of `flex-shrink`?
`1`. It means all children shrink the same amount from their basis values.

Flex shrink decides what should happen when their is deficit in the combined `flex-basis` values.

###What will `flex-shrink: 0` do?
It will cause the container width to overflow. (if total `flex-basis` is more than available container space.)

###What will `flex: 1` do?

- `flex` property is a shorthand for setting `flex-grow`, `flex-shrink` and `flex-basis`.
- `flex: 1` will apply below settings:
	- `flex-grow: 1`
	- `flex-shrink: 1`
	- `flex-basis: 0`
- That will make all the children the same size, and all grow to use all the space.

###How can we prevent overflowing of children elements?
- Using `flex-wrap: wrap`. Default value is `nowrap`.
- Using `flex-wrap: wrap-reverse` will reverse the flow. 
- Using `align-content` property with multi-line content will help you easily space around content.


