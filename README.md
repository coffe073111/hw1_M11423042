# hw1_M11423042

**資料夾(資料前處理)**：內有三個檔案，分別是訓練集資料重複值刪除(adult_data_duplicate.ipynb)及測試集資料重複值刪除(adult_test_duplicates.ipynb)及訓練集缺失值補植(adult_data_missing_value.ipynb)
  
  ● adult_data_duplicate.ipynb：偵測訓練集的重複值筆數並刪減(重複筆數僅留一筆)。
  
  ● adult_test_duplicates.ipynb：偵測測試集的重複值筆數並刪減(重複筆數僅留一筆)。
  
  ● adult_data_missing_value.ipynb：偵測訓練集的缺失值，如？或空白，統計後依變數型態採取不同方式做補值(數值型欄位以中位數；類別型欄位以眾數/Unknown)。

**資料夾(實驗二)**：內有十個檔案，分別是C4.5混淆矩陣圖(CM_C45.png)及C5.0混淆矩陣圖(C5.0_confusion_matrix.png)及CART混淆矩陣圖(CM_CART.png)及ID3混淆矩陣圖(CM_ID3.png)及C4.5決策樹圖(Tree_C45.png)及C5.0決策樹圖(Tree_C50.png)及CART決策樹圖(Tree_CART.png)及ID3決策樹圖(Tree_ID3.png)及ID3、C4.5、CART訓練模型test_overfiting_ID3.C4.5.CART (2).ipynb)及各類決策樹預測結果(Test_Predictions.xlsx)

**CM_為混淆矩陣圖*

**Tree_為三層決策樹圖*

  ● dm_decision_tree_C5.0.ipynb：使用前處理後的Adult資料集進行訓練、測試C5.0決策樹分類器。

  ● test_overfiting_ID3.C4.5.CART (2).ipynb：使用前處理後的Adult資料集進行訓練、測試ID3、C4.5、CART決策樹分類器。

  ● Test_Predictions.xlsx：整理各類演算法(ID3、C4.5、CART)的預測結果。


**資料夾(實驗三)**：：內有四個檔案，分別是Large決策樹圖(Large_tree_d10_l64.png)、Medium決策樹圖(Medium_tree_d6_l16.png)、Small決策樹圖(Small_tree_d3_l16.png)、採用Cost-Complexity Pruning和CART之模型(dm_post_pruning_decision_tree_finalver.ipynb)
  
  ● dm_post_pruning_decision_tree_finalver.ipynb：透過Grid Search，比較不同樹深度與葉節點數的組合表現，並利用Elbow Method找出模型複雜度與準確率的平衡點，選出三組代表模型（Small、Medium、Large），最後在測試集上評估其準確率。

  ● requirements：環境設定。





