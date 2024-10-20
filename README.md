# Product-Classification-for-EE5327701

## 需求安裝

首先，請安裝必要的套件，這些套件列在 `requirements.txt` 中。使用以下指令安裝所有必要的依賴：

```bash
pip install -r requirements.txt
```

## 修改資料與來源

根據需要，請修改程式中的資料集來源。預設會從 Hugging Face 資料集加載產品名稱。你可以將其改為使用自己的資料。

**預設程式碼：**

```python
p_names = load_dataset(p_name_dataset, split="train")['product_name']
```

**修改後的程式碼：**

將上面的程式碼改成你自己的資料，具體可以是從文件或其他來源加載產品名稱。

```python
# 例如：從一個本地 CSV 檔案中加載產品名稱
import pandas as pd
p_names = pd.read_csv('你的資料集.csv')['product_name']
```

## 執行程式並取得分類結果

在程式中，將 `categories` 和 `p_names` 傳入 `get_category()` 函數以取得分類結果。具體的函數使用方法如下：

```python
categories = ['category1', 'category2', 'category3']  # 這裡是你的分類標籤
# 將產品名稱和分類標籤傳入 get_category 函數，並可選擇 top_k 參數
results = get_category(categories, p_names, top_k=3)
```

你可以通過設定 `top_k` 來取得前 `n` 個最相關的類別。

## 儲存結果

將分類結果保存為 CSV 檔案。文件會以學號(若有英文請以大寫為主)命名:

```python
df = pd.DataFrame(results)
df.to_csv('你的學號_categories.csv', index=False, encoding='utf-8-sig')
```

## 完整流程總結

1. 安裝必要的套件：`pip install -r requirements.txt`
2. 修改資料來源，將預設的 `p_names` 改為你的資料集。
3. 使用 `get_category()` 函數進行分類，並設定 `top_k` 取得最相關的類別。
4. 保存結果到名為 `你的學號_categories.csv` 的檔案中。
