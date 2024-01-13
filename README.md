# Django Bookmarks

A Django app that lets users create bookmarks to Django model instances

# Installation

Install `django-bookmarks` using your favourite package manager.

Add `django_bookmarks` to your Django projects `INSTALLED_APPS`:
```
...
'django_bookmarks',
...
```

Include `django_bookmarks.urls` in your URL dispatcher:
```
...
path("bookmarks"/, include("django_bookmarks.urls")),
...
```

Django Bookmarks adds two routes below where you include the app:
* `/` is a view that lists all bookmarks of the user accessing it
* `/togglebookmark/<content_type_id>/<object_id>` below is a view to add or remove a bookmark to the model instance for the user accessing it

Django Bookmarks ships the `django_bookmarks` templatetags library, which currently consists of the templatetag `toggle_bookmark`.
The `toggle_bookmark` templatetag takes the model instance as argument and adds a `bookmark` link that to your template. This bookmark link displayes
a bookmark symbol that is either white, if the model instance *is not* bookmarked or yellow, if the model instance *is* bookmarked. Clicking the link
toggles the bookmarking state of the model instance for the logged in user.
If you have [htmx](htmx.org/) included in your web application, the bookmarking link uses htmx to update the bookmark symbol, otherwise the link
redirects to the page where you came from.
