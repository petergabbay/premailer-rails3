# Premailer Rails 3 README

This gem is a no config solution for the wonderful
[Premailer gem](https://github.com/alexdunae/premailer) to be used with Rails 3.
It uses interceptors which were introduced in Rails 3 and tweaks all mails which
are `deliver`ed and adds a plain text part to them and inlines all CSS rules
into the HTML part.

By default it inlines all the CSS files that are linked to in the HTML:

```html
<link type='text/css' ... />
```

Don't worry about the host in the CSS URL since this will be ignored.

If no CSS file is linked to in the HTML it will try to load a default CSS file
`email.css`.

Every CSS file (including the default `email.css`) is loaded from within the
app. The retrieval of the file depends on your assets configuration:

* Rails 3.1 asset pipeline: It will load the compiled version of the CSS asset
  which is normally located in `app/assets/stylesheets/`.

* Classic static assets: It will try to load the CSS file located in
  `public/stylesheets/`

* [Hassle](https://github.com/pedro/hassle): It will try to load the
  compiled CSS file located in the default Hassle location
  `tmp/hassle/stylesheets/`

## Installation

Simply add the gem to your Gemfile in your Rails project:

    gem 'premailer-rails3'

That's it!
