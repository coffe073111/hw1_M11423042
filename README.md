# hw1_M11423042

資料夾(資料前處理):內有三個檔案，分別是訓練集資料重複值刪除(adult_data_duplicate.ipynb)及測試集資料重複值刪除(adult_test_duplicates.ipynb)及訓練集缺失值補植(adult_data_missing_value.ipynb)
  
  ● adult_data_duplicate.ipynb：偵測訓練集的重複值筆數並刪減(重複筆數僅留一筆)。
  
  ● adult_test_duplicates.ipynb：偵測測試集的重複值筆數並刪減(重複筆數僅留一筆)。
  
  ● adult_data_missing_value.ipynb：偵測訓練集的缺失值，如？或空白，統計後依變數型態採取不同方式做補值(數值型欄位以中位數；類別型欄位以眾數/Unknown)。




  
  ● dm_post_pruning_decision_tree_finalver.ipynb:透過Grid Search，比較不同樹深度與葉節點數的組合表現，並利用Elbow Method找出模型複雜度與準確率的平衡點，選出三組代表模型（Small、Medium、Large），最後在測試集上評估其準確率。
