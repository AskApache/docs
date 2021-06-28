# cycle

`cycle(values, position)` is a Twig function to cycle on an array of values:

```twig
{% set start_year = date() | date('Y') %}
{% set end_year = start_year + 5 %}

{% for year in start_year..end_year %}
    {{ cycle(['odd', 'even'], loop.index0) }}
{% endfor %}
```

The array can contain any number of values:

```twig
{% set fruits = ['apple', 'orange', 'citrus'] %}

{% for i in 0..10 %}
    {{ cycle(fruits, i) }}
{% endfor %}
```

## Arguments

- position: The cycle position

Source: [Twig](https://twig.symfony.com/cycle)