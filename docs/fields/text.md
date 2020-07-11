---
title: Text field
---
Text field
==========

Simple text-input, for single-line fields.

## Basic Configuration:

```yaml
        name:
            type: text
```

## Example usage in templates:

```twig
{{ record.name }}
```

## Options:

The field has a few options to change the appearance and functionality of the
field.

* `class` Can be set to either of the:
  * `narrow` to make the field less wide
  * `large` to make both the field and the font larger
* `allow_twig` can be set to true or false to control if twig may be used in the
  field
* `pattern` Use this to validate the field against a certain pattern.
* `placeholder` Placeholder text inside the input control.

## Input Sanitisation

All content in this field type will be sanitised before it gets inserted into
the database. This means that only 'whitelisted' HTML like `<b>` and
`<img src="…">` is kept, while things like `<embed>` and `<script>` are scrubbed
from the field before being stored. As a site-implementor you can control the
whitelisted tags and attributes using the following section in `config.yaml`:

```yaml
htmlcleaner:
    allowed_tags: [ div, span, p, br, hr, s, u, strong, em, i, b, li, ul, ol, …, … ]
    allowed_attributes: [ id, class, style, name, value, href, src, alt, title, …, … ]
```

By design, you can _not_ disable the sanitation entirely. If you need to allow
the editors to insert unfiltered HTML or javascript, use a `type: textarea`
field instead.

