# YAML (YML) Complete Notes

## What is YAML?

YAML (YAML Ain't Markup Language) is a human-readable data serialization language commonly used for:

* Configuration files
* CI/CD pipelines
* Docker Compose
* Kubernetes manifests
* Application settings

### Basic Rules

* Uses **indentation** (spaces, not tabs)
* Key-value pairs use `:`
* Indentation defines hierarchy
* Comments start with `#`

Example:

```yaml
chai_type: masala_chai
temperature: hot
servings: 2
brewing_time: 5
```

---

# 1. Nested Objects

Use indentation to create child properties.

```yaml
chai_recipe:
  base: black_tea
  milk: whole_milk

chai_recipe_two:
  base: black_tea
  milk: whole_milk
```

Result:

```json
{
  "chai_recipe": {
    "base": "black_tea",
    "milk": "whole_milk"
  }
}
```

---

# 2. String Data Types

## Single Line Strings

Strings can be written with or without quotes.

```yaml
chai_name: Masala Chai
description: "Chai with cardamom, ginger"
tagline: 'The best chai in town'
```

---

## Multi-Line Strings

### Literal Style (`|`)

Preserves line breaks exactly.

```yaml
brewing_instruction: |
  boil water
  add tea leaves
  add milk
```

Output:

```text
boil water
add tea leaves
add milk
```

---

### Folded Style (`>`)

Converts line breaks into spaces.

```yaml
brewing_instruction_two: >
  boil water
  add tea leaves
  add milk
```

Output:

```text
boil water add tea leaves add milk
```

---

# 3. Number Data Types

```yaml
cups_per_day: 3
cups_per_day_two: 0xFF22FF
```

Examples:

* Integer → `3`
* Hexadecimal → `0xFF22FF`

---

# 4. Boolean Values

YAML supports several boolean representations.

```yaml
is_hot: true
add_sugar: yes
add_salt: no
is_instant: off
is_consent: on
```

Equivalent values:

| True | False |
| ---- | ----- |
| true | false |
| yes  | no    |
| on   | off   |

---

# 5. Null Values

Both represent `null`.

```yaml
sweetner: null
alternative_milk: ~
```

---

# 6. Date and Time

```yaml
morning_brew: 2025-01-15
local_time: 2025-01-15 08:30:01
```

Examples:

* Date → `2025-01-15`
* DateTime → `2025-01-15 08:30:01`

---

# 7. Arrays / Lists

## Block Style List

```yaml
spices:
  - ginger
  - cloves
  - black_pepper
  - true
  - 200
```

---

## Inline Style List

```yaml
spices: [cardamom, ginger, cloves]

steeping_times: [3, 2, 1]
```

---

# 8. List of Lists / Nested Lists

```yaml
chai_categories:
  - name: Traditional
    varieties:
      - Masala Chai
      - Ginger Chai
      - Cardamom Chai

  - name: Modern
    varieties:
      - Vanilla Chai
      - Chocolate Chai
```

---

# 9. Dictionaries (Objects)

```yaml
masala_chai:
  ingredients:
    tea: black_tea

    liquid:
      water: 200ml
      milk: 100ml

    spices:
      ginger: 1_inch
      cinnamon: 1_stick

  preparation:
    method: simmer
    duration: 5_minutes
```

---

# 10. List of Dictionaries

```yaml
chai_menu:
  - name: Masala Chai
    price: 30
    size: regular

  - name: Ginger Chai
    price: 30
    size: regular
```

Result:

```json
[
  {
    "name": "Masala Chai",
    "price": 30
  },
  {
    "name": "Ginger Chai",
    "price": 30
  }
]
```

---

# 11. Anchors and Aliases

Useful for avoiding repeated configuration.

## Create an Anchor

```yaml
default_chai_base: &default_base
  tea: black_tea
  water: 200ml
  brewing_time: 5
```

---

## Reuse Using Alias

```yaml
morning_chai:
  <<: *default_base
  milk: 100ml

evening_chai:
  <<: *default_base
  milk: 200ml
```

Equivalent to:

```yaml
morning_chai:
  tea: black_tea
  water: 200ml
  brewing_time: 5
  milk: 100ml
```

---

# 12. Type Conversion

Convert values explicitly.

## Convert to String

```yaml
zip_code: !!str 12345
```

Result:

```yaml
"12345"
```

---

## Convert to Integer

```yaml
count: !!int "123"
```

Result:

```yaml
123
```

---

# 13. Sets

A set contains unique values.

```yaml
unique_spices: !!set
  ? cardamom
  ? ginger
  ? cloves
```

Equivalent to:

```text
{cardamom, ginger, cloves}
```

No duplicate values are allowed.

---

# YAML Cheat Sheet

| Type               | Example          |
| ------------------ | ---------------- |
| String             | `name: chai`     |
| Integer            | `count: 5`       |
| Boolean            | `is_hot: true`   |
| Null               | `value: null`    |
| Date               | `2025-01-15`     |
| List               | `- ginger`       |
| Inline List        | `[a, b, c]`      |
| Object             | `tea: black_tea` |
| Nested Object      | Indented values  |
| Anchor             | `&default`       |
| Alias              | `*default`       |
| String Conversion  | `!!str 123`      |
| Integer Conversion | `!!int "123"`    |
| Set                | `!!set`          |

---

# Best Practices

✅ Use spaces instead of tabs

✅ Keep indentation consistent (2 spaces recommended)

✅ Use meaningful key names

✅ Use anchors for repeated configurations

✅ Prefer block-style lists for readability

❌ Avoid mixing tabs and spaces

❌ Don't over-nest structures

❌ Don't duplicate configuration unnecessarily

---

# Summary

YAML supports:

* Key-value pairs
* Strings
* Numbers
* Booleans
* Null values
* Dates & Times
* Lists
* Dictionaries (Objects)
* Nested structures
* Anchors & Aliases
* Type conversion
* Sets

It is widely used in modern DevOps and cloud-native tools such as Docker, Kubernetes, GitHub Actions, GitLab CI/CD, and many application configuration files.

---

# ⭐ Support

If this repository helps you learn YML(YAML), consider giving it a ⭐ on GitHub.

It helps more developers discover the project.

Happy Learning! 🚀
