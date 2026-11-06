# 十篇論文逐篇介紹

[回首頁](README.md) · [看文獻比較與研究方向](comparison_and_direction.md)

整理主題：**視覺語言模型的幻覺、工具核驗與 AI Agent**。日期：2026-11-07。

每篇使用相同順序：**摘要 → 目的 → 方法 → 成果 → 和目前研究的關係**。「摘要」是中文白話改寫；「成果」來自原論文；最後一項是本整理的分析建議。

## 文獻導覽

| 期刊論文 | 會議論文 |
|---|---|
| [J1 Woodpecker：用工具檢查答案](#j1) | [C1 POPE：檢查模型有沒有說出不存在的物件](#c1) |
| [J2 多模態大模型：認識模型與評估](#j2) | [C2 HallusionBench：看模型會不會依照圖片改答案](#c2) |
| [J3 自主 Agent：認識決策與回饋](#j3) | [C3 VCD：用原圖與擾動圖的差異調整回答](#c3) |
| [J4 工具學習：何時用、選哪個、怎麼用](#j4) | [C4 ViperGPT：把視覺問題變成程式](#c4) |
| [J5 幻覺理解：整理錯誤的可能成因](#j5) | [C5 REVERSE：生成中發現問題，再回頭修正](#c5) |

---

## 五篇期刊論文

<a id="j1"></a>

### J1｜Woodpecker：用工具幫模型檢查答案

**完整題名：** [Woodpecker: hallucination correction for multimodal large language models](https://link.springer.com/article/10.1007/s11432-024-4251-x)

**作者／發表：** Shukang Yin 等，Science China Information Sciences，2024。**類型：原創方法。**

**摘要**

模型描述圖片時，可能把不存在的東西說得很肯定。這篇先從原答案找出需要查證的內容，再找視覺工具提供證據，最後修正原答案。

**本篇目的**

不重新訓練原本的看圖模型，也能改善回答中的幻覺。

**研究方法**

流程分成五步：找物件概念、產生問題、視覺核驗、整理證據、修正答案。原作用到文字模型、物件偵測器與視覺問答模型。

**呈現成果**

Table 4 中，MiniGPT-4 在 POPE Random 的正確率由 **54.67% 提高至 85.33%**，增加 **30.66 個百分點**。但這項評估只抽 **50 張圖、每圖六題**，不能直接當成我們 500 張圖的比較結果。

**重要性與研究關係**

出版社頁面顯示 **210 次引用**。它直接示範外部核驗，值得作為相關方法；但五階段、多模型也增加工作量。對目前題目較有用的是「如何查證、如何記錄修正與錯改」。

**查證位置：** [正式全文](https://www.sciengine.com/parse/pdf/1674-733X/1C1C4934294B4349B90D92A376E027F1.pdf)，§3、§4.1、Tables 4、7。引用數來源與日期見[紀錄](sources_and_checks.md#citation-counts)。

<a id="j2"></a>

### J2｜多模態大模型綜述：先弄清楚模型怎麼看圖

**完整題名：** [A survey on multimodal large language models](https://pmc.ncbi.nlm.nih.gov/articles/PMC11645129/)

**作者／發表：** Shukang Yin 等，National Science Review，2024。**類型：綜述。**

**摘要**

這篇整理能同時處理圖片與文字的大模型，包括模型怎麼接起來、用什麼資料訓練，以及如何評估回答。

**本篇目的**

讓讀者掌握多模態大模型的基本架構、研究路線與尚未解決的問題。

**研究方法**

把既有研究整理成架構、訓練與資料、評估、能力擴充等面向，也介紹幻覺、示例學習與視覺工具推理。

**呈現成果**

提供模型、資料與評估的分類，說明幻覺可涉及物件存在、屬性或關係。成果是研究地圖；本文沒有提出一個新模型，再報告它提高多少正確率。

**重要性與研究關係**

本輪未核實引用數，依其背景價值選入。它能幫助說清楚 InternVL 類模型和工具系統的關係，也提醒我們：POPE 評的只是其中一部分能力。

**查證位置：** 正式全文的 Architecture、Evaluation、Multimodal hallucination、LLM-aided visual reasoning。

<a id="j3"></a>

### J3｜自主 Agent 綜述：從回答問題走向採取行動

**完整題名：** [A survey on large language model based autonomous agents](https://link.springer.com/article/10.1007/s11704-024-40231-1)

**作者／發表：** Lei Wang 等，Frontiers of Computer Science，2024。**類型：綜述。**

**摘要**

Agent 可以依任務安排步驟、使用工具，再根據回饋調整行動。這篇整理這類系統的建構、應用與評估。

**本篇目的**

用共同的分類方式比較不同 Agent，讓研究者看懂各系統的差異。

**研究方法**

從角色設定、記憶、規劃與行動整理架構，再討論能力取得、應用及評估方法。

**呈現成果**

提供架構與評估分類，指出提示不穩、幻覺和多次呼叫成本等挑戰。它沒有用同一台機器重新測試所有系統，也沒有給出新視覺模型的準確率。

**重要性與研究關係**

出版社頁面顯示 **2,516 次引用**。可用來說明本研究的決策、工具與回饋設計。這些分類面向不表示小題目一定要把四大模組全部做齊。

**查證位置：** [正式全文](https://link.springer.com/content/pdf/10.1007/s11704-024-40231-1.pdf)，§2、Tables 1–3、§6。引用數見[紀錄](sources_and_checks.md#citation-counts)。

<a id="j4"></a>

### J4｜工具學習綜述：先問「有沒有必要用工具」

**完整題名：** [LLM-Based Agents for Tool Learning: A Survey](https://link.springer.com/article/10.1007/s41019-025-00296-9)

**作者／發表：** Weikai Xu 等，Data Science and Engineering，2025。**類型：綜述。**

**摘要**

模型有了工具，還要知道何時使用、選哪個，以及怎麼正確操作。這篇整理工具學習的方法、資料集與評估指標。

**本篇目的**

說清楚工具使用的不同問題，並比較既有解法。

**研究方法**

把研究分成工具檢索、規劃、環境互動與評估，也區分需要訓練和免訓練的方法。

**呈現成果**

整理工具基準及任務完成、規劃、工具選擇等指標。§2.1 指出許多基準預設一定需要工具，較少獨立評估「是否值得呼叫」。這是問題定位，還不是本研究具有新穎性的證明。

**重要性與研究關係**

出版社頁面顯示 **84 次引用**。對目前題目最有用的是把範圍縮至「何時核驗」，先固定工具，避免同時處理大量工具檢索與複雜規劃。

**查證位置：** [正式全文](https://link.springer.com/content/pdf/10.1007/s41019-025-00296-9.pdf)，§2.1、§4、§7。引用數見[紀錄](sources_and_checks.md#citation-counts)。

<a id="j5"></a>

### J5｜幻覺理解綜述：從成因看模型為什麼說錯

**完整題名：** [Understanding Hallucinations in Large Visual and Language Models](https://doi.org/10.1145/3811409)

**作者／發表：** Zheng Yi Ho、Siyuan Liang、Dacheng Tao，ACM Computing Surveys，2026。**類型：綜述。**

> **閱讀版本：** 正式期刊的題錄、摘要及部分可見段落已核對；逐篇精讀使用相關作者預印本。完整正式版尚未讀完，兩個版本的頁碼與內容不可混用。

**摘要**

這篇從資料、模型架構、生成過程、訓練與評估等面向，整理文字與視覺模型產生幻覺的可能原因。

**本篇目的**

讓不同任務的幻覺研究能放在共同框架下討論，並連結到較具體的成因。

**研究方法**

採文獻綜合與概念分類，從模型、觀察者、世界與輸入四個層次分析問題，再對照模型生命週期。

**呈現成果**

提出分類框架並整理共通與模態特有的問題。這類成果能幫助界定錯誤，並非一個已校準、可以直接套到 POPE 的幻覺偵測器。

**重要性與研究關係**

本輪未核實引用數。2026 年正式綜述顯示這個主題仍有研究整理，但不能據此宣稱熱門程度排名。對本研究的用途，是區分「物件說錯」與其他錯誤，避免把改善範圍寫得太大。

**查證位置：** 正式版摘要及可見 §§3.4、7–9；相關預印本 [arXiv:2510.00034v1](https://arxiv.org/abs/2510.00034v1) §§3–6。詳見[版本紀錄](sources_and_checks.md#reading-status)。

---

## 五篇會議論文

<a id="c1"></a>

### C1｜POPE：用簡單問題檢查物件幻覺

**完整題名：** [Evaluating Object Hallucination in Large Vision-Language Models](https://aclanthology.org/2023.emnlp-main.20/)

**作者／發表：** Yifan Li 等，EMNLP 2023。**類型：評測基準。**

**摘要**

模型有時會把常見、或容易一起出現的物件想像進圖片。POPE 直接問「圖中有沒有某物件」，讓這類錯誤較容易量測。

**本篇目的**

建立較穩定、容易比較的物件存在性評估方式。

**研究方法**

採用存在與不存在物件各半的問答，並用隨機、常見、易共現三種方式挑選負例。COCO 主實驗為 **500 張圖，每圖六題**。

**呈現成果**

原作顯示負例越容易讓模型產生聯想，表現越差；其指定提示實驗中，POPE 也比自由描述的評估更穩定。它提出的是測量方式，沒有直接改善模型。

**重要性與研究關係**

Woodpecker、VCD 與 REVERSE 都使用 POPE 作評估或分析，具有後續採用證據。我們已有重現成果，最適合作固定起點；結論限於物件存在性。

**查證位置：** [正式全文](https://aclanthology.org/2023.emnlp-main.20.pdf)，§5、Tables 3–6、§7。

<a id="c2"></a>

### C2｜HallusionBench：圖片改了，答案會跟著改嗎？

**完整題名：** [HallusionBench: An Advanced Diagnostic Suite for Entangled Language Hallucination and Visual Illusion in Large Vision-Language Models](https://openaccess.thecvf.com/content/CVPR2024/html/Guan_HallusionBench_An_Advanced_Diagnostic_Suite_for_Entangled_Language_Hallucination_and_CVPR_2024_paper.html)

**作者／發表：** Tianrui Guan 等，CVPR 2024。**類型：診斷基準。**

**摘要**

模型可能知道某張著名圖片的答案，卻沒真的看現在這張圖。這篇用原圖、修改圖與部分無圖條件，檢查模型是否依據眼前證據回答。

**本篇目的**

分析語言知識、視覺誤判與跨條件回答不一致的問題。

**研究方法**

建立 **346 張圖、1,129 筆問答、455 個控制組**，並分別計算單題、同圖與同問題組的正確率。

**呈現成果**

Table 2 中，GPT-4V 經 GPT-4 輔助評分的 qAcc 為 **28.79%**；單題整體正確率為 **65.28%**。差距表示整組全答對比單題答對更嚴格，兩者不能當同一指標。

**重要性與研究關係**

它的貢獻是成組控制與一致性診斷。我們已有重現，可作背景；一般物件偵測器無法處理其中所有幾何、地圖與文字題型。

**查證位置：** [正式全文](https://openaccess.thecvf.com/content/CVPR2024/papers/Guan_HallusionBench_An_Advanced_Diagnostic_Suite_for_Entangled_Language_Hallucination_and_CVPR_2024_paper.pdf)，§3、Eqs.2–5、Table 2。

<a id="c3"></a>

### C3｜VCD：利用原圖與擾動圖的預測差異

**完整題名：** [Mitigating Object Hallucinations in Large Vision-Language Models through Visual Contrastive Decoding](https://openaccess.thecvf.com/content/CVPR2024/html/Leng_Mitigating_Object_Hallucinations_in_Large_Vision-Language_Models_through_Visual_Contrastive_CVPR_2024_paper.html)

**作者／發表：** Sicong Leng 等，CVPR 2024。**類型：推論方法。**

**摘要**

同一個模型分別看原圖和加噪音的圖，再利用預測差異調整輸出，降低不受圖片支持的回答。

**本篇目的**

不用重新訓練，也不另外加入專家模型，改善物件幻覺。

**研究方法**

在逐字生成時比較兩個視覺條件的輸出分數，並限制候選字詞，避免產生過於不合理的答案。

**呈現成果**

Table 1 中，LLaVA-1.5 在 COCO Random 的 F1 由 **81.33% 提高至 87.16%**。這是原作取樣式解碼設定下的結果；補充材料另有 greedy 對照，不能直接拿主表比較我們的歷史分數。

**重要性與研究關係**

它是 Woodpecker、REVERSE 等後續研究比較的相關方法。可作免訓練對照候選，但兩路推論仍有額外成本，接到 InternVL3 的接口也要先確認。

**查證位置：** [正式全文](https://openaccess.thecvf.com/content/CVPR2024/papers/Leng_Mitigating_Object_Hallucinations_in_Large_Vision-Language_Models_through_Visual_Contrastive_CVPR_2024_paper.pdf)，§3–4、Table 1；補充 Table 7。

<a id="c4"></a>

### C4｜ViperGPT：把看圖問題拆成程式步驟

**完整題名：** [ViperGPT: Visual Inference via Python Execution for Reasoning](https://openaccess.thecvf.com/content/ICCV2023/html/Suris_ViperGPT_Visual_Inference_via_Python_Execution_for_Reasoning_ICCV_2023_paper.html)

**作者／發表：** Dídac Surís、Sachit Menon、Carl Vondrick，ICCV 2023。**類型：視覺推理系統。**

**摘要**

系統先將問題轉成 Python 程式，再呼叫找物件、比較位置、回答局部問題等工具，組合出答案。

**本篇目的**

把複合視覺問題拆成可以執行、可以查看中間結果的步驟。

**研究方法**

提供工具介面給程式生成模型，再由直譯器執行。原作使用多種視覺工具與語言模型，不同測試採用不同工具組合。

**呈現成果**

Table 1 的 RefCOCO、RefCOCO+ testA，零樣本結果分別為 **72.0% 與 67.0%**，依原表 IoU 評估條件呈現。結果支持指定任務下的工具組合能力，不代表所有工具輸出都正確。

**重要性與研究關係**

J3 將它列入工具型 Agent 相關研究。適合學習如何記錄中間證據；完整系統的模型與接口較多，目前可先借用設計概念。

**查證位置：** [正式全文](https://openaccess.thecvf.com/content/ICCV2023/papers/Suris_ViperGPT_Visual_Inference_via_Python_Execution_for_Reasoning_ICCV_2023_paper.pdf)，§3–4、Table 1、Fig.7；補充 A–B。

<a id="c5"></a>

### C5｜REVERSE：發現可疑內容後回頭修正

**完整題名：** [Generate, but Verify: Reducing Hallucination in Vision-Language Models with Retrospective Resampling](https://proceedings.neurips.cc/paper_files/paper/2025/hash/5eff08bd064f0cdd92182cdf6fd06b99-Abstract-Conference.html)

**作者／發表：** Tsung-Han Wu 等，NeurIPS 2025。**類型：訓練結合生成修正。**

**摘要**

模型一邊生成，一邊判斷片語是否可疑；發現問題後，退回前面的位置重新產生，嘗試修正回答。

**本篇目的**

把幻覺偵測與修正能力一起放進模型，減少對外部驗證流程的依賴。

**研究方法**

使用約 **130 萬筆半合成資料**訓練特殊標記與驗證能力，再於推論時回溯、重新取樣及改寫。

**呈現成果**

原作在開放描述等測試有改善，也做了方法消融；但 §5 與附錄 D 說明，**POPE 這類判別式任務沒有明顯改善**。開放回答的收益不能直接搬到二元問答。

**重要性與研究關係**

這篇 2025 年研究顯示驗證與回溯仍有新方法，也比較既有減幻覺方法。但它需要訓練，與目前固定模型、控制工程量的範圍不符，較適合作相關工作。

**查證位置：** [正式全文](https://proceedings.neurips.cc/paper_files/paper/2025/file/5eff08bd064f0cdd92182cdf6fd06b99-Paper-Conference.pdf)，§3、§5、Table 4、Tables A.1–2。

---

## 讀完後怎麼使用這份清單

先用五篇期刊建立背景與問題分類，再用五篇會議論文說明「怎麼量測、別人怎麼改善、我們的差異在哪裡」。引用數只作其中一項依據；原作樣本、比較方式與限制同樣重要。

下一份：[文獻比較與研究方向](comparison_and_direction.md)。
