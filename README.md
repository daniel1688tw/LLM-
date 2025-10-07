代碼流程說明請見LLM專題.pdf

程式碼撰寫在Table_to_report.ipynb
data_description.txt 定義表格欄位資訊
set1.csv為一個羽球數據表格(ShuttleSet 羽球數據集)
main.txt 存使用者大綱及說明

1. data_description.txt + main.txt   為了挑選欄位
2. set1.csv -> filtered_set1.csv    把無用的欄位篩掉
3. data_description.txt  ->  filtered_data_description.txt   把無用的欄位篩掉
4. main.txt + filtered_data_description.txt  ->  analyze_response.txt     分析該如何進行接下來的分析數據
5. analyze_response.txt  ->  operations.info.json   根據分析選出可用操作
6. filtered_set1.csv  +  filtered_data_desription.txt  + operations_info.json  ->  operations.json    根據數據欄位資訊與操作，篩選出更適合的操作
7. operations.json  + filtered_set1.csv + main.txt ->  selected_operations.json       操作重要性排序後30%且非三種重要操作把它篩掉
8. 開始建構樹使用BFS  (操作生成 (ContentPlanner)、安全執行 DataFrame 操作 (SafeDataFrameOperator)、樹結構追蹤 (TreeNode / TreeOfReport)、以及 文本生成 (TextGenerator)。)
