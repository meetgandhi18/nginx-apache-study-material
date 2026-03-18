# 📘 Regular Expressions (Regex)

## 📌 What is Regex?
Regular Expressions (Regex) are used to **find patterns within text**.

---

## 🎯 Uses
- Validate text
- Search within text
- Extract data

---

## 🧱 Syntax
```
/pattern/
```

---

## 🔎 Basic Example
Pattern:
```
/bob/
```
Text:
```
bob is here. bob is good.
```
Output:
```
bob
```

---

## 🌍 Global Flag
Pattern:
```
/bob/g
```
Text:
```
bob is here. bob is good.
```
Output:
```
bob
bob
```

---

## 🔗 OR Operator
Pattern:
```
/Bob|Alice/g
```
Text:
```
Bob and Alice are friends
```
Output:
```
Bob
Alice
```

---

## 👥 Grouping
Pattern:
```
/(Bob|Alice) Jones/g
```
Text:
```
Bob Jones, Alice Jones, John Jones
```
Output:
```
Bob Jones
Alice Jones
```

---

## ❓ Optional (0 or 1)
Pattern:
```
/colou?r/g
```
Text:
```
color colour colouur
```
Output:
```
color
colour
```

---

## ⭐ Zero or Many (*)
Pattern:
```
/colou?r*/g
```
Text:
```
color colour colouur colorrrr colo
```
Output:
```
color
colour
colou
colorrrr
colo
```

---

## ➕ One or Many (+)
Pattern:
```
/colou?r+/g
```
Text:
```
color colour colorrrr colou
```
Output:
```
color
colour
colorrrr
```

---

## 🔢 Count {min,max}
Pattern:
```
/colou?r{1,6}/g
```
Text:
```
color colour colouur colouuuur colorrrrrr
```
Output:
```
color
colour
colorrrrrr
```

---

## 🔐 Escape Special characters
Pattern:
```
/colors\?/g
```
Text:
```
colors? colors
```
Output:
```
colors?
```

---

## 🔢 Digits
Pattern:
```
/\d/g
```
Text:
```
a1b2c3
```
Output:
```
1 2 3
```

---

## 🔤 Words
Pattern:
```
/\w+/g
```
Text:
```
hello i am meet
```
Output:
```
hello
i
am
meet
```

---

## 🚫 Not a digit
Pattern:
```
/\D+/g
```
Text:
```
123 hello 456 meet 01-02-2003
```
Output:
```
 hello 
 meet
 - -
```

---

## 📦 Character Set
Pattern:
```
/[A-Z]/g
```
Text:
```
aBcdE
```
Output:
```
B
E
```

---

## 🚫 Negation
Pattern:
```
/[^LBC]/g
```
Text:
```
BALL CAT
```
Output:
```
A
A

A
T
```

---

## 🧠 Summary

| Symbol | Meaning |
|--------|--------|
| . | Any character |
| ^ | Start OR negation |
| $ | End |
| * | 0+ |
| + | 1+ |
| ? | Optional |
| {} | Count |
| [] | Set |
| () | Group |
| \ | Escape |
| | | OR |

---

## 🚀 Example
Pattern:
```
/^[A-Za-z0-9_]+$/
```
Text:
```
meet_123
meet@123
```
Output:
```
meet_123 ✅
meet@123 ❌
```
