  # CSS

## Selectors
- ### Types of selectors :
	```css
	*{}			/* Universal selector */
	div{}		/* Type selector */
	.class{}	/* Class selector */
	#id{}		/* ID selector */
	```
- ### Chaining selectors :

	Chain selectors without separation to target elements with multiple classes.

	Example:
	```html
	<div>
	  <div class="subsection header">Latest Posts</div>
	  <p class="subsection preview">This is where a preview for a post might go.</p>
	</div>
	```
	```css
	.subsection.header {	/* No space */
	  color: red;
	}
	```
	This targets elements only with both `subsection` and `header` classes.

	You can also chain a class and an ID:
	```css
	.subsection#preview {
	  color: blue;
	}
	```

	- **Limitations**
	Cannot chain more than one type selector (e.g., `divp` is invalid).

- ### Descendant Combinator :
	Uses a space between selectors to indicate a relationship.

	Example:
	```html
	<div class="ancestor">
		<!-- A -->
		<div class="contents">
			<!-- B -->
			<div class="contents"><!-- C --></div>
		</div>
	</div>
	
	<div class="contents"><!-- D --></div>
	```
	```css
	.ancestor .contents {
	  /* some declarations */
	}
	```
	This selects `.contents` elements (B and C) inside `.ancestor`, not D.
	> `.ancestor > .child ` , child combinator, does the same thing

	You can use multiple combinators:
	```css
	.one .two .three .four {
	  /* some declarations */
	}
	```
	This targets `.four` inside `.three`, inside `.two`, inside `.one`. Avoid excessive nesting for clarity and specificity issues.
	> For more info, [refer this](https://www.theodinproject.com/lessons/foundations-intro-to-css#chaining-selectors).


- ### Specificity, the Cascade :

	Sort of like a tie-breaker, when an element has multiple, conflicting declarations targeting it.  
	- Inline style > ID selector > Class Selector > Type selector > Universal selector
	- If specificity is the same, then whichever rule was the _last_ defined is the winner
- ### Inheritance :
	Typography-based properties (`color`, `font-size`, `font-family`, etc.) are usually inherited, while most other properties aren’t.
	
	

## The Box Model


```mermaid
graph LR;
    A[Margin] --> B[Border];
    B --> C[Padding];
    C --> D[Content];
```
- ### Standard Box Model
	Here, if we set `width` and `height`, they are applied to only content box. 
- ### Alternate Box Model
	Here, if we set `width` and `height`, they are applied to the visible box on the page, i.e. `content + padding + border`. 
	```css
	html {
	  box-sizing: border-box;
	}
	*,
	*::before,
	*::after {
	  box-sizing: inherit;
	}
	```
	We use this box model more frequently, because it's easier to work with.
	> For more info, [refer this](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/The_box_model#the_standard_css_box_model).
