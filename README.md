# AI Agent 影像辨識｜文獻整理與研究方向

**核心問題：小型視覺語言模型看圖回答時，能不能透過有限次檢查，少說錯一些？**

本專案從 InternVL3-2B 的 POPE 與 HallusionBench 重現經驗出發，整理 **5 篇期刊論文＋5 篇會議論文**，用白話說明各篇在研究什麼、怎麼做，以及成果能支持哪些結論。

更新日期：**2026-11-07**。

## 先看這兩份

| 文件 | 內容 | 適合什麼時候看 |
|---|---|---|
| [① 十篇論文逐篇介紹](paper_notes.md) | 每篇的摘要、目的、方法、成果、重要性，以及和目前研究的關係 | 準備文獻報告、和教授討論 |
| [② 文獻比較與研究方向](comparison_and_direction.md) | 把各方法放在一起比較，說明基線、可做範圍與必要實驗 | 決定題目、控制工作量 |

## 已整理的五篇期刊

| 論文 | 期刊／年份 | 類型 | 重要性依據 |
|---|---|---|---|
| [Woodpecker](paper_notes.md#j1) | Science China Information Sciences，2024 | 原創方法 | 出版社頁面顯示 **210 次引用**；直接研究工具核驗與幻覺修正 |
| [多模態大模型綜述](paper_notes.md#j2) | National Science Review，2024 | 綜述 | 整理架構、訓練、資料與評估，適合建立背景 |
| [自主 Agent 綜述](paper_notes.md#j3) | Frontiers of Computer Science，2024 | 綜述 | 出版社頁面顯示 **2,516 次引用**；提供 Agent 架構與評估的比較方式 |
| [工具學習綜述](paper_notes.md#j4) | Data Science and Engineering，2025 | 綜述 | 出版社頁面顯示 **84 次引用**；直接討論何時用工具、如何選工具 |
| [幻覺理解綜述](paper_notes.md#j5) | ACM Computing Surveys，2026 | 綜述 | 提供較新的成因分類；正式版閱讀狀態另有說明 |

引用數是 **2026-11-07 讀到的 Springer Nature 出版社頁面快照**，不是 Google Scholar 數字。其他篇未核實到的引用數沒有填成零。各篇的來源與查詢紀錄見[參考資料與查證紀錄](sources_and_checks.md)。

五篇期刊中有四篇綜述；綜述的成果是整理知識與提出分類，不能當成四個新的實驗方法。因此另整理 POPE、HallusionBench、VCD、ViperGPT、REVERSE 五篇會議論文，補足基準、方法與系統比較。

## 目前的研究判斷

先固定 **InternVL3-2B＋COCO POPE**，把問題限制在「圖中是否存在某個物件」，候選改法最多一個。先確認檢查答案本身有沒有淨收益，再考慮何時啟動檢查。

這是根據文獻與現有重現經驗提出的研究建議；新方法的效果與新穎性仍需驗證。

## 閱讀與資料狀態

- 已完成 **9 篇正式版正文精讀**。
- 第 10 篇 J5 已讀相關作者預印本；另核對正式期刊題錄、摘要與可見段落，完整正式版仍待補齊。
- 「摘要」均為中文白話整理；各篇成果屬於原作者，沒有把它們寫成本專案的新實驗結果。

## 需要查細節時

| 資料 | 用途 |
|---|---|
| [參考資料與查證紀錄](sources_and_checks.md) | 查來源、引用數日期、全文閱讀範圍與版本差異 |
| [文獻資料](papers.json) | 保留題名、作者、年份、出版來源及重要性依據 |
| [BibTeX](bibliography.bib)／[RIS](bibliography.ris) | 匯入 Zotero 等文獻管理工具；含 10 篇目標文獻及另外標示的 J5 預印本來源 |
| [基線設定參考](baseline_reference.json) | 保存先前登錄的模型、題目版本與推論設定；狀態為尚未執行的新基線規格 |

相關重現專案：[POPE](https://github.com/ChenBill900703/pope-internvl3-2b-reproduction)、[HallusionBench](https://github.com/ChenBill900703/HallusionBench-InternVL3-2B-Reproduction)。
