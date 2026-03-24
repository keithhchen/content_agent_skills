# screenshot-to-structured eval

## Test 1: test_table.png（表格截图 → CSV）

**类型判断**：表格 ✅

**期望输出**：
```csv
Account,Type,Likes
BrandA,Product,1200
UserB,Travel,3500
```

**实际提取**：
```csv
Account,Type,Likes
BrandA,Product,1200
UserB,Travel,3500
```

**结果**：✅ 完全匹配

---

## Test 2: test_chat.png（聊天截图 → Markdown）

**类型判断**：线性文字（聊天记录）✅

**期望输出**：
```markdown
**Alice**: Hey, have you tried the new SIM card?
**Bob**: Yes! It works great at Narita.
**Alice**: How long did pickup take?
**Bob**: About 3 minutes, super fast.
**Alice**: Nice, ordering one now.
```

**实际提取**：
```markdown
**Alice**: Hey, have you tried the new SIM card?
**Bob**: Yes! It works great at Narita.
**Alice**: How long did pickup take?
**Bob**: About 3 minutes, super fast.
**Alice**: Nice, ordering one now.
```

**结果**：✅ 完全匹配

---

## Test 3: test_list.png（列表截图 → Markdown）

**类型判断**：线性文字（编号列表）✅

**期望输出**：
```markdown
1. Download Google Maps
2. Install Suica app
3. Set up eSIM before flight
4. Save hotel address offline
```

**实际提取**：
```markdown
1. Download Google Maps
2. Install Suica app
3. Set up eSIM before flight
4. Save hotel address offline
```

**结果**：✅ 完全匹配

---

## 总结

| 测试 | 类型判断 | 内容提取 | 结果 |
|------|---------|---------|------|
| 表格截图 | ✅ | ✅ | ✅ |
| 聊天截图 | ✅ | ✅ | ✅ |
| 列表截图 | ✅ | ✅ | ✅ |

**3/3 通过**
