---
name: excel-to-csv
description: |
  将 Excel 文件（.xlsx/.xls）转换为 CSV。当用户提供 Excel 文件并需要转为 CSV 时触发。
  也处理用户只需要 Excel 中特定列/sheet 的情况。
  关键词：excel、xlsx、转csv、导出csv、表格转换。
---

# Excel → CSV

## 做什么

把 `.xlsx` / `.xls` 文件转成 `.csv`，保留用户需要的列和 sheet。

## 流程

1. 读取 Excel 文件，列出所有 sheet 名称和每个 sheet 的列名
2. 问用户：要哪些 sheet？要哪些列？（如果用户已经说清楚了就不问）
3. 转换并保存为 CSV，默认保存在同目录下，文件名为 `{原文件名}.csv`
4. 如果多个 sheet，每个 sheet 一个 CSV：`{原文件名}_{sheet名}.csv`

## 实现

用 Python pandas。一行能解决的事不要写十行。

```python
import pandas as pd

df = pd.read_excel("input.xlsx", sheet_name="Sheet1")
# 如果用户指定了列
df = df[["列A", "列B", "列C"]]
df.to_csv("output.csv", index=False, encoding="utf-8-sig")
```

`utf-8-sig` 编码确保中文在 Excel 中打开不乱码。

## 边界情况

- 合并单元格 → pandas 会自动 ffill，提醒用户检查
- 日期列 → 保持 ISO 格式 `YYYY-MM-DD`，不要变成 Excel 序列号
- 空行/空列 → 默认去掉，除非用户说保留
