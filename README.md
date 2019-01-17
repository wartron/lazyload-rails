## Lazyload-Rails [![Build Status](https://travis-ci.org/jassa/lazyload-rails.png)](https://travis-ci.org/jassa/lazyload-rails)

This project integrates the jQuery Lazy Load Plugin
for Rails `image_tag` helpers

### What's jQuery Lazy Load?

From the project page:

*Lazy Load is a jQuery plugin written in JavaScript. It delays loading of images in long web pages. Images outside of viewport (visible part of web page) won't be loaded before user scrolls to them. This is opposite of image preloading.*

*Using Lazy Load on long web pages containing many large images makes the page load faster. Browser will be in ready state after loading visible images. In some cases it can also help to reduce server load.*

See [example](http://backbonejs.org/#examples) (scroll down to see images load)

## Documentation

### Features

* Add `lazy: true` option to Rails `image_tag` helpers to render lazyload-friendly img tags.
* Simple (really). That's pretty much it.

### Example

```erb
<%= image_tag "kittenz.png", alt: "OMG a cat!", lazy: true %>
```

Equals:

```html
<img alt="OMG a cat!" data-original="/images/kittenz.png" src="http://www.appelsiini.net/projects/lazyload/img/grey.gif">
```

## Install

Add this line to your application's Gemfile:

```ruby
gem "lazyload-rails"
```

Download the [jQuery v2 Lazy Load Plugin](https://rawgit.com/tuupola/jquery_lazyload/2.x/lazyload.js)
into your `vendor/assets/javascripts` directory and include it however you prefer.

And in your JavaScript code do:

```javascript
$("img.lazyload").lazyload();
```

Lazy Load can be customized, [see more options](http://www.appelsiini.net/projects/lazyload)

*__Important__: Remember that the Lazy Load Plugin depends on jQuery.*

## Configuration

By default, a 1x1 grey gif is used as placeholder (from [http://appelsiini.net/projects/lazyload/img/grey.gif](http://www.appelsiini.net/projects/lazyload/img/grey.gif)). This can be easily customized:

```ruby
# config/initializers/lazyload.rb
Lazyload::Rails.configure do |config|
  config.placeholder = "/public/img/grey.gif"
end
```

## License

Lazyload-Rails is released under the [MIT License](http://www.opensource.org/licenses/MIT).
