# Programming Best Practices

General
-------

* These are not to be blindly followed; strive to understand these and ask
  when in doubt.
* Don't duplicate the functionality of a built-in library.
* Don't swallow exceptions or "fail silently."
* Don't write code that guesses at future functionality.
* Exceptions should be exceptional.
* [Keep the code simple].

[Keep the code simple]: http://www.readability.com/~/ko2aqda2

Email
-----

* Use [SendGrid] or [Amazon SES] to deliver email in staging and production
  environments.

[Amazon SES]: http://robots.thoughtbot.com/post/3105121049/delivering-email-with-amazon-ses-in-a-rails-3-app
[SendGrid]: https://devcenter.heroku.com/articles/sendgrid

Web
---

* Avoid a Flash of Unstyled Text, even when no cache is available.
* Avoid rendering delays caused by synchronous loading.
* Use https instead of http when linking to assets.

HTML
----

* Don't use a reset button for forms.
* Prefer cancel links to cancel buttons.
* Use `<button>` tags over `<a>` tags for actions.

CSS
---

* Use Scss.
* Use [Autoprefixer][autoprefixer] to generate vendor prefixes based on the
  project-specific browser support that is needed.

[autoprefixer]: https://github.com/postcss/autoprefixer

Scss
----

* Prefer `overflow: auto` to `overflow: scroll`, because `scroll` will always
  display scrollbars outside of OS X, even when content fits in the container.
* Prefer mixins to `@extend`.

jQuery
-------
* Prefer use of data-attribute selectors.


Browsers
--------

* Avoid supporting versions of Internet Explorer before IE10.
