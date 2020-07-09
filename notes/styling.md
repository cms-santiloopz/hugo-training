# Styling


### sass/scss
To include sass/scss in your project, use Hugo Pipes, like so.
```html

	{{ $scss := resources.Get "styles.scss" }}

	{{ $style := $scss | resources.ToCSS }}

	<link rel="stylesheet" type="text/css" href="{{ $style.Permalink }}">
```