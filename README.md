# React Preload
[![npm version](https://badge.fury.io/js/react-preloaded.svg)](http://badge.fury.io/js/react-preloaded)

A React component to preload images. It renders a passed component during the loader phase, and renders it's children once the images have been successfully fetched.

This repository was forked from [Sam Bernard](https://github.com/sambernard/react-preload).


## Installation

### npm

```bash
npm install react-preloaded --save
```

## Usage

```javascript
var Preload = require('react-preloaded').Preload;
```

```javascript
var loadingIndicator = (<div>Loading...</div>)
var images = [];

<Preload
  loadingIndicator={loadingIndicator}
  images={images}
  autoResolveDelay={3000}
  onError={this._handleImageLoadError}
  onSuccess={this._handleImageLoadSuccess}
  resolveOnError={true}
  mountChildren={true}
  >
	{/* content to be rendered once loading is complete*/}
</Preload>
```

## Prop types

```javascript
   propTypes: {
		//Rendered on success
		children: PropTypes.element.isRequired,

		//Rendered during load
		loadingIndicator: PropTypes.node.isRequired,

		//Array of image urls to be preloaded
		images: PropTypes.array,

		//If set, the preloader will automatically show
		//the children content after this amount of time
		autoResolveDelay: PropTypes.number,

		//Error callback. Is passed the error
		onError: PropTypes.func,

		//Success callback
		onSuccess: PropTypes.func,

		//Whether or not we should still show the content
		//even if there is a preloading error
		resolveOnError: PropTypes.bool

        //Whether or not we should mount the child content after
        //images have finished loading (or after autoResolveDelay)
        mountChildren: PropTypes.bool
    }
```

## Additional Details

This module also exposes `ImageCache` and `ImageHelper` which can be used to preload images
directly, and can be accessed via `require('react-preloaded').ImageCache` and
`require('react-preloaded').ImageHelper` respectively.

## License

[MIT][mit-license]

[mit-license]: ./LICENSE
