# trim

`trim(characterMask = null, side = "both")` is a Twig filter to strip whitespace (or other characters) from the
beginning and end of a string.

```twig
{{ '  I like Twig.  '|trim }}

{# outputs 'I like Twig.' #}

{{ '  I like Twig.'|trim('.') }}

{# outputs '  I like Twig' #}

{{ '  I like Twig.  '|trim(side='left') }}

{# outputs 'I like Twig.  ' #}

{{ '  I like Twig.  '|trim(' ', 'right') }}

{# outputs '  I like Twig.' #}
```

<p class="note"><strong>Note:</strong> Internally, Twig uses the PHP trim, ltrim, and rtrim functions.</p>

## Arguments

- `character_mask`: The characters to strip
- `side`: The default is to strip from the left and the right (`both`) sides, but `left` and `right` will strip from
  either the left side or right side only
