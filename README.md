# hw1_M11423042

**資料夾(資料前處理)**：內有三個檔案，分別是訓練集資料重複值刪除(adult_data_duplicate.ipynb)及測試集資料重複值刪除(adult_test_duplicates.ipynb)及訓練集缺失值補植(adult_data_missing_value.ipynb)
  
  ● adult_data_duplicate.ipynb：偵測訓練集的重複值筆數並刪減(重複筆數僅留一筆)。
  
  ● adult_test_duplicates.ipynb：偵測測試集的重複值筆數並刪減(重複筆數僅留一筆)。
  
  ● adult_data_missing_value.ipynb：偵測訓練集的缺失值，如？或空白，統計後依變數型態採取不同方式做補值(數值型欄位以中位數；類別型欄位以眾數/Unknown)。

**資料夾(實驗二)**：內有十二個檔案，分別是C4.5混淆矩陣圖(CM_C45.png)及C5.0混淆矩陣圖(CM_C50.png)及CART混淆矩陣圖(CM_CART.png)及ID3混淆矩陣圖(CM_ID3.png)及C4.5決策樹圖(Tree_C45.png)及C5.0決策樹圖(Tree_C50.png)及CART決策樹圖(Tree_CART.png)及ID3決策樹圖(Tree_ID3.png)及ID3、C4.5、CART訓練模型(dm_decision_tree_ID3.C4.5.CART.ipynb)及C5.0訓練模型(dm_decision_tree_C5.0.ipynb)及ID3、C4.5、CART預測結果(Test_Predictions_ID3.C4.5.CART.xlsx)及C5.0預測結果(Test_Predictions_C5.0.xlsx)

**CM_為混淆矩陣圖*

**Tree_為三層決策樹圖*

  ● dm_decision_tree_C5.0.ipynb：使用前處理後的Adult資料集進行訓練、測試C5.0決策樹分類器。

  ● dm_decision_tree_ID3.C4.5.CART.ipynb：使用前處理後的Adult資料集進行訓練、測試ID3、C4.5、CART決策樹分類器。

  ● Test_Predictions_ID3.C4.5.CART.xlsx：整理各類演算法(ID3、C4.5、CART)的預測結果。

  ● Test_Predictions_C5.0.xlsx：整理C5.0的預測結果。


**資料夾(實驗三)**：：內有四個檔案，分別是Large決策樹圖(Large_tree_d10_l64.png)、Medium決策樹圖(Medium_tree_d6_l16.png)、Small決策樹圖(Small_tree_d3_l16.png)、採用Cost-Complexity Pruning和CART之模型(dm_post_pruning_decision_tree_finalver.ipynb)
  
  ● dm_post_pruning_decision_tree_finalver.ipynb：透過Grid Search，比較不同樹深度與葉節點數的組合表現，並利用Elbow Method找出模型複雜度與準確率的平衡點，選出三組代表模型（Small、Medium、Large），最後在測試集上評估其準確率。

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





