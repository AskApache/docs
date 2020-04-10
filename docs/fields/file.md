---
title: File field
---
File field
==========

Simple file upload/select field.

## Basic Configuration:

```yaml
        attachment:
            type: file
```

## Example usage in templates:

```twig
{{ asset(record.attachment, 'files') }}
```

## Options:

The field has a few options to change the appearance and functionality of the
field.

* `extensions` Allows you to restrict users to only be able to upload files
  with certain file extensions
* `upload` Allows you to upload files for this field into a specified directory
  so they remain grouped. This directory will be created in `{%web%}/files/`

```yaml
        attachment:
            type: file
            extensions: [ png, pdf ]
            upload: portfolio
```
