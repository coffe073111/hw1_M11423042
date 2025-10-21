# hw1_M11423042

###  資料前處理

內含三個 `.ipynb` 檔案，負責資料清理與補值處理。

| 檔名 | 功能說明 |
|------|-----------|
| **adult_data_duplicate.ipynb** | 偵測並移除訓練集中的重複筆數（僅保留一筆）。 |
| **adult_test_duplicates.ipynb** | 偵測並移除測試集中的重複筆數（僅保留一筆）。 |
| **adult_data_missing_value.ipynb** | 偵測訓練集缺失值（如 `?` 或空白），並依變數型態補植：<br>・數值型欄位 → 以中位數補值<br>・類別型欄位 → 以眾數或 `Unknown` 補值。 |

---

###  實驗一

共十二個檔案，包含各演算法的決策樹圖、混淆矩陣圖與預測結果。

####  圖像檔案
| 類別 | 檔名 | 說明 |
|------|------|------|
| 混淆矩陣圖 | `CM_ID3.png`, `CM_C45.png`, `CM_C50.png`, `CM_CART.png` | 各演算法在測試集的分類結果視覺化。 |
| 決策樹圖 | `Tree_ID3.png`, `Tree_C45.png`, `Tree_C50.png`, `Tree_CART.png` | 各模型的三層決策樹結構。 |

> 🔸 `CM_` 開頭 → 混淆矩陣圖  
> 🔸 `Tree_` 開頭 → 三層決策樹圖  

####  程式與結果檔案
| 檔名 | 功能說明 |
|------|-----------|
| **dm_decision_tree_ID3.C4.5.CART.ipynb** | 使用前處理後資料集訓練並測試 **ID3、C4.5、CART** 決策樹分類器。 |
| **dm_decision_tree_C5.0.ipynb** | 使用前處理後資料集訓練並測試 **C5.0** 決策樹分類器。 |
| **Test_Predictions_ID3.C4.5.CART.xlsx** | 彙整 ID3、C4.5、CART 模型的測試集預測結果。 |
| **Test_Predictions_C5.0.xlsx** | 彙整 C5.0 模型的測試集預測結果。 |

---

###  實驗二

共四個檔案，探討 **CART 決策樹** 之 **後剪枝 (Cost-Complexity Pruning)** 與模型複雜度。

| 檔名 | 功能說明 |
|------|-----------|
| **dm_post_pruning_decision_tree_finalver.ipynb** | 透過 **Grid Search** 比較不同樹深度與葉節點數的組合，並以 **Elbow Method** 尋找模型複雜度與準確率的平衡點。選出三組代表模型（Small、Medium、Large），最後於測試集進行評估。 |
| **Small_tree_d3_l16.png** | 小型模型（樹深度=3，葉節點=16）之決策樹圖。 |
| **Medium_tree_d6_l16.png** | 中型模型（樹深度=6，葉節點=16）之決策樹圖。 |
| **Large_tree_d10_l64.png** | 大型模型（樹深度=10，葉節點=64）之決策樹圖。 |

---

###  環境設定

  ● requirements：環境設定。




# hw1_M11423042

[![Made with Jupyter](https://img.shields.io/badge/Made%20with-Jupyter-orange)](#)
[![scikit-learn](https://img.shields.io/badge/ML-scikit--learn-informational)](#)

> 以 **Adult** 資料集為例，完成資料前處理、四種決策樹模型（ID3 / C4.5 / C5.0 / CART）的訓練與可視化，並在實驗三以 **Cost-Complexity Pruning** 進行後修剪與模型選擇。

---

## 目錄（Table of Contents） <a id="toc"></a>
- [專案結構](#structure)
- [資料前處理](#preprocessing)
- [實驗二：決策樹與混淆矩陣](#exp2)
- [實驗三：後修剪與模型挑選](#exp3)
- [環境與執行方式](#env)
- [命名規則](#naming)

---

## 專案結構 <a id="structure"></a>

```text
.
├─ 資料夾(資料前處理)/
│  ├─ adult_data_duplicate.ipynb
│  ├─ adult_test_duplicates.ipynb
│  └─ adult_data_missing_value.ipynb
├─ 資料夾(實驗二)/
│  ├─ CM_C45.png  CM_C50.png  CM_CART.png  CM_ID3.png
│  ├─ Tree_C45.png  Tree_C50.png  Tree_CART.png  Tree_ID3.png
│  ├─ dm_decision_tree_ID3.C4.5.CART.ipynb
│  ├─ dm_decision_tree_C5.0.ipynb
│  ├─ Test_Predictions_ID3.C4.5.CART.xlsx
│  └─ Test_Predictions_C5.0.xlsx
├─ 資料夾(實驗三)/
│  ├─ Large_tree_d10_l64.png
│  ├─ Medium_tree_d6_l16.png
│  ├─ Small_tree_d3_l16.png
│  └─ dm_post_pruning_decision_tree_finalver.ipynb
└─ requirements.txt（或 requirements/）

資料前處理 <a id="preprocessing"></a>

清理重複值、處理缺失值，並輸出乾淨資料供後續實驗使用。

檔名	說明
adult_data_duplicate.ipynb	偵測並刪除 訓練集 重複列（每組重複僅保留一筆）。
adult_test_duplicates.ipynb	偵測並刪除 測試集 重複列（每組重複僅保留一筆）。
adult_data_missing_value.ipynb	偵測 訓練集 缺失值（含 ?、空白等），數值欄以 中位數 補值；類別欄以 眾數 / Unknown 補值。
<details open> <summary><b>補值與重複值處理重點</b></summary>

缺失值統一規則（剔除空白、? 等異常記號再統計）。

數值欄（如年齡、工時）以 Median 對抗極端值；類別欄以 Mode/Unknown 保持可解釋性。

重複列以 完整列比對 為準，保留第一筆。

</details>

↑ 回到目錄

實驗二：決策樹與混淆矩陣 <a id="exp2"></a>

訓練 ID3 / C4.5 / C5.0 / CART，輸出三層決策樹圖與混淆矩陣圖，並整理測試集預測結果。

Notebook

dm_decision_tree_ID3.C4.5.CART.ipynb：訓練/測試 ID3、C4.5、CART。

dm_decision_tree_C5.0.ipynb：訓練/測試 C5.0。

成果圖（依實際路徑調整）

混淆矩陣	決策樹（3層）

	


	


	


	

預測匯出

Test_Predictions_ID3.C4.5.CART.xlsx：ID3/C4.5/CART 測試集預測彙整。

Test_Predictions_C5.0.xlsx：C5.0 測試集預測彙整。

CM_*.png 為 混淆矩陣圖；Tree_*.png 為 三層決策樹圖。

↑ 回到目錄

實驗三：後修剪與模型挑選 <a id="exp3"></a>

以 Grid Search 比較不同 max_depth × max_leaf_nodes 組合，利用 Elbow Method 在模型複雜度與準確率之間取得平衡，選出 Small / Medium / Large 代表模型，並在測試集評估。

Notebook

dm_post_pruning_decision_tree_finalver.ipynb：採用 CART + Cost-Complexity Pruning 的完整流程。

代表模型圖

Small_tree_d3_l16.png

Medium_tree_d6_l16.png

Large_tree_d10_l64.png

↑ 回到目錄





