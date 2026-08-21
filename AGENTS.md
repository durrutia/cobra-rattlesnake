# Agent Guidelines for Cobra RattleSnake

## Apostrophes & Smart Quotes

**Always use straight apostrophes (`'`) in source markdown files.** Never use typographic/curly apostrophes (`'`) or HTML entities (`&apos;`).

### Why

- Jekyll's kramdown converter has a "smart quotes" feature that automatically converts straight quotes to typographic ones in the generated HTML
- This causes rendering issues where `don't` becomes `don't` (with a curly apostrophe) which can display incorrectly on some platforms
- The site config now disables smart quotes globally via `kramdown.smart_quotes: ["apos", "apos", "quot", "quot"]`

### Correct

```markdown
Farid doesn't make sauce. He settles scores.
Taiwan's night markets inspire us.
```

### Incorrect

```markdown
Farid doesn't make sauce. He settles scores.   # curly apostrophe
Farid doesn&apos;t make sauce.                  # HTML entity
```

### Verification

After changes, verify the generated HTML uses straight apostrophes:

```bash
grep -rn "’" _site/  # should return nothing
```

### Config Reference

The `_config.yml` contains:

```yaml
kramdown:
  smart_quotes: ["apos", "apos", "quot", "quot"]
  input: GFM
```

This forces kramdown to output `&apos;` (which renders as straight `'` in HTML) instead of `&rsquo;` (curly `'`).