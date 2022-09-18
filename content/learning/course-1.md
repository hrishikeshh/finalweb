---
title: "Course 1"
date: 2022-04-03T23:15:00+07:00
slug: course_url_name
category: bioinformatics
summary:
description: 
cover:
  image: ""
  alt: "What is bioinformatics?"
  caption: 
  relative: false
showtoc: true
draft: false

---

## Tables

| Syntax      | Description | Test Text     |
| :---        |    :----:   |          ---: |
| Header      | Title       | Here's this   |
| Paragraph   | Text        | And more      |

```python
result = client.payments.get_payment(
    payment_id = "{{PAYMENT_ID}}"
)

if result.is_success():
    pprint(result.body)
elif result.is_error():
    pprint(result.errors)

```

```javascript
const express = require("express");
const app = express();
const port = 3000;

app.get("/", (req, res) => {
  res.send("Hello World!");
});

app.listen(port, () => {
  console.log(`Example app listening at http://localhost:${port}`);
});
```


```python
class Solution:
    def isPalindrome(self, x: int) -> bool:
        if x<0: return False
        num = str(x)
        f = num[:int(len(num)/2):1]
        s = num[-1:-int(len(num)/2)-1:-1]
        
        if f == s:
            return True
        return False
```