- [Pseudo class vs Pseudo element](#pseudo)
- [CSS grid](#cssgrid)

## Pseudo class vs Pseudo element <a name="pseudo"></a>
- Basically a pseudo-class is a selector that assists in the selection of something that cannot be expressed by a simple selector, for example :hover. A pseudo-element however allows us to create items that do not normally exist in the document tree, for example ```::after```.<br />
- Pseudo-classes select regular elements but under certain conditions, like when their position relative to siblings or when they’re under a particular state.<br />
- Pseudo-elements effectively create new elements that are not specified in the markup of the document and can be manipulated much like a regular element. This introduces huge benefits for creating cool effects with minimal markup, also aiding significantly in keeping the presentation of the document out of the HTML and in CSS where it belongs.<br />

## CSS Grid <a name="cssgrid"></a>
https://www.youtube.com/watch?v=FEnRpy9Xfes<br />
- Flexbox is great for laying out items in one Direction, In Rows.<br />
- CSS Grid allows us to lay out elements in two directions rows & columns independent of each other<br />
- Besides absolute positioning, there is nothing that provides this functionality in CSS without coming out of the flow of the document.<br />
```
/* fallback code written here IE */
.search-results {
	display: flex;
	flex-wrap: wrap;
	... 
}
/* feature queries */
@supports (display: grid) {
	.search-results {
		display: grid;
		grid-gap: 10px;
		/* fr = fraction unit */
		grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
		padding: 10px;
	}
}
/* more fall back media queries stuff goes here */
@media only screen and (min-width: 500px) {
	...
}
```
<br />
- https://codepen.io/brendamarienyc/pen/oZMxOY<br />
- https://open.nytimes.com/bootstrap-to-css-grid-87b3f5f830e4<br />
- https://labs.jensimmons.com/
