# HTML
HTML is divided into Basics, Intermediate, and Advanced throughout the course, but I'll write it all in one place.

## HTML Basics
- **Void Elements :** no end tag.
	```html
	<br>
	<img>
	```
- **Semantic Tags :** more accessibility, better for text-to-speech.
	```html
	<strong>	makes text bold
	<em>		emphasize, makes text italic
	```
- **Opening links in new tab :** The anchor tag's `href` specifies the destination, while `target` specifies where it opens. Default is the current tab (`_self`). Use `_blank` to open in a new tab:
	```html
	<a href="https://www.theodinproject.com/about" target="_blank" rel="noopener noreferrer">About The Odin Project</a>
	```
	The `noopener` attribute prevents the new page from accessing the original page. The `noreferrer` attribute hides referrer information, preventing the new page from knowing where the link came from. It also includes the `noopener` behavior, preventing [tabnabbing](https://owasp.org/www-community/attacks/Reverse_Tabnabbing).
