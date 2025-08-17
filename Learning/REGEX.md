# 🔎 Regex Cheat Sheet (PowerShell | Python | Bash/Shell)

Regular Expressions (Regex) let you search, match, and manipulate text patterns.

---

## 🎯 Basic Syntax
| Pattern | Meaning | Example Match |
|---------|---------|---------------|
| `.` | Any single character | `c.t` → `cat`, `cot` |
| `^` | Start of string/line | `^Hello` → `Hello world` |
| `$` | End of string/line | `world$` → `Hello world` |
| `\d` | Digit (0–9) | `\d\d` → `42` |
| `\D` | Non-digit | `\D+` → `abc` |
| `\w` | Word char (a–z, A–Z, 0–9, _) | `\w+` → `file1` |
| `\W` | Non-word char | `\W` → `! @ #` |
| `\s` | Whitespace (space, tab, newline) | `\s+` → `"   "` |
| `\S` | Non-whitespace | `\S+` → `word` |

---

## 🔢 Quantifiers
| Pattern | Meaning | Example |
|---------|---------|---------|
| `*` | 0 or more | `ab*` → `a`, `abb`, `abbbb` |
| `+` | 1 or more | `ab+` → `ab`, `abb` |
| `?` | 0 or 1 | `colou?r` → `color`, `colour` |
| `{n}` | Exactly n | `\d{3}` → `123` |
| `{n,}` | n or more | `\d{2,}` → `42`, `1234` |
| `{n,m}` | Between n and m | `\d{2,4}` → `12`, `1234` |

---

## 📦 Character Classes
| Pattern | Meaning | Example |
|---------|---------|---------|
| `[abc]` | a, b, or c | `[ch]at` → `cat`, `hat` |
| `[^abc]` | NOT a, b, or c | `[^0-9]` → any non-digit |
| `[a-z]` | Range a–z | `[a-z]+` → `hello` |
| `[A-Z]` | Uppercase letters | `[A-Z]{2}` → `AB` |
| `[0-9]` | Digits | `[0-9]{4}` → `2025` |

---

## 🎭 Grouping & Alternation
| Pattern | Meaning | Example |
|---------|---------|---------|
| `(abc)` | Group | `(ha)+` → `hahaha` |
| `|` | OR | `cat|dog` → `cat`, `dog` |
| `(?:...)` | Non-capturing group | `(?:ab)+` → `abab` |
| `(?<name>...)` | Named group (PowerShell & Python) | `(?<year>\d{4})` |

---

## ⚡ Anchors & Boundaries
| Pattern | Meaning | Example |
|---------|---------|---------|
| `\b` | Word boundary | `\bcat\b` → matches `cat` not `cater` |
| `\B` | Not word boundary | `\Bcat` → matches `educate` |

---

## 🧩 Lookaround
| Pattern | Meaning | Example |
|---------|---------|---------|
| `(?=...)` | Positive lookahead | `\d(?=px)` → `20` in `20px` |
| `(?!...)` | Negative lookahead | `\d(?!px)` → `20` in `20kg` |
| `(?<=...)` | Positive lookbehind | `(?<=\$)\d+` → `100` in `$100` |
| `(?<!...)` | Negative lookbehind | `(?<!\$)\d+` → `100` in `EUR100` |

---

## ⚙ Usage Examples

### 🐍 Python
```python
import re
text = "Order ID: 12345"
match = re.search(r"\d+", text)
print(match.group())  # 12345
