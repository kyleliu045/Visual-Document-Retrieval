# ModernVBERT: Towards Smaller Visual Document Retrievers

> **💡 Meta Information**
>
> * **Venue:** `arXiv 2025` 
> * **Paper Type:** Model & Architecture / Empirical Study
> * **Links:** [Paper (arXiv)](https://arxiv.org/abs/2510.01149) | [Code & Models](https://huggingface.co/ModernVBERT)
> * **Institutions:** Illuin Technology, EPFL, Centrale Supélec (Paris-Saclay), Equall.ai
>
> **🏷️ Domains & Tasks**
> * `Visual Document Retrieval (VDR)` `Vision-Language Models (VLMs)` `Retrieval-Augmented Generation (RAG)`
> * **Core Tasks:** Document Retrieval, Modality Alignment, Contrastive Learning

### 📌 Citation
```text
Teiletche, P., Macé, Q., Conti, M., Loison, A., Viaud, G., Colombo, P., & Faysse, M. (2025). ModernVBERT: Towards Smaller Visual Document Retrievers. arXiv preprint arXiv:2510.01149.
```

### 📝 Abstract: The Paradigm Shift in Visual Document Retrieval (摘要：視覺文件檢索的典範轉移)

#### 1. Background & Motivation (背景與動機)
* **The RAG Era:** 隨著檢索增強生成 (RAG) 系統的普及，從大型文件庫中精準提取資訊已成為現代 AI 最核心的工業應用之一。
* **The Shift to Vision (轉向視覺檢索):** 傳統的神經文件檢索幾乎完全依賴「純文字 (Text Space)」，這通常需要繁瑣且易錯的 OCR 前處理。如今，直接以頁面截圖作為輸入的**視覺文件檢索 (Visual Document Retrieval, VDR)** 模型正快速崛起，因為它們在建立索引的延遲與整體效能上具備顯著優勢。
* **Current Status Quo (業界現狀):** 目前業界最主流的 VDR 作法，是直接將大型的「視覺-語言解碼器 (Vision-Language Decoders，即生成式模型)」改裝並重新利用為嵌入模型 (Embedding Models)。

#### 2. The Bottleneck (現狀的痛點)
* 作者一針見血地指出，直接拿「生成式模型」來改裝做檢索，雖然在開發上極具成本效益 (Cost-efficient)，但這種架構天生的限制，實際上已經成為了**限制檢索效能的天花板 (Bottlenecks retrieval performance)**。

#### 3. Methodology & Core Investigations (研究方法與核心探討)
為了打破上述瓶頸，作者並非盲目擴大模型，而是退回原點，透過嚴謹的**控制變因實驗 (Controlled experiments)** 重新審視了整個訓練流程，建立了一套優化 VDR 模型的原則性配方 (Principled recipe)。實驗量化了以下四大決定效能的核心因素：
1. **注意力遮罩機制 (Attention masking)**
2. **影像解析度 (Image resolution)**
3. **模態對齊的數據策略 (Modality alignment data regimes)**
4. **以延遲交互為中心的對比學習目標 (Late interaction centered contrastive objectives)**

#### 4. The Solution: ModernVBERT (最終成果：小而美的霸主)
* **Model Profile:** 基於實驗得出的強大洞見，團隊開發並開源了 **ModernVBERT**——一個參數僅有 2.5 億 (250M-parameter) 的精簡視覺-語言編碼器 (Vision-Language Encoder)。
* **Giant Slayer:** 在文件檢索任務上進行微調後，這個超小模型的效能，成功超越了近期發表且體積比它大上 10 倍的大型模型。
* **Engineering Impact (工程與商業價值):** 憑藉其極小的體積與 Encoder 架構，ModernVBERT 能夠直接在便宜的 CPU 硬體上進行高效推論 (Efficient inference)，在維持頂尖效能的同時，大幅度降低了系統的檢索延遲與企業營運成本。

### 🌐 The Foundation of Modern Search (現代搜尋的基石：神經資訊檢索)

#### 1. The Core Value of IR (資訊檢索的核心價值)
* **Definition (核心定義):** 能夠在龐大的文件集合中快速定位特定資訊，是當今數位系統的核心基礎建設 (core building block)。
* **Applications (應用場景):** 這項關鍵能力支撐了非常廣泛的應用場景，包含網頁搜尋 (web search)、虛擬助理 (virtual assistants) 以及企業知識管理 (enterprise knowledge management)。

#### 2. The Rise of Dense Retrievers (密集檢索器的絕對主力地位)
* **The "De Facto Backbone" (業界標準):** 神經資訊檢索 (Neural IR) 模型，特別是其中的 **Dense Retrievers (密集檢索器)**，已經成為了現代搜尋系統中「事實上的骨幹 (de facto backbone)」。
* **Why Dense Retrievers? (為何成為主流？):** 作者點出了 Dense Retrievers 之所以能稱霸業界的兩個關鍵優勢：
    1. **Strong semantic matching (強大的語意匹配能力):** 模型能夠真正理解文字背後的語意，而不僅僅是傳統的字面關鍵字比對。
    2. **Good scalability properties (良好的擴展性屬性):** 具備優異的擴充彈性，能夠高效處理並檢索海量級別的數據庫。

### 🚀 The Catalyst: RAG and the Retrieval Bottleneck (催化劑：RAG 帶來的挑戰與檢索瓶頸)

#### 1. The RAG Amplifier (RAG 架構的推波助瀾)
* **Trend Amplification (趨勢放大):** 檢索增強生成 (Retrieval-Augmented Generation, RAG) 的廣泛採用，進一步放大了產業界對高效檢索系統的依賴。
* **Mechanism (運作機制):** 在 RAG 架構中，檢索器 (Retriever) 負責從茫茫大海中挑選出一小撮最相關的文件，以此來提供上下文，引導下游的生成模型 (Generator) 產出最終答案。

#### 2. The First-Stage Retrieval Bottleneck (第一階段檢索的致命瓶頸)
在這樣的系統中，第一階段的「檢索模組 (First-stage retrieval module)」是公認的系統咽喉，主要體現在兩個維度：
* **Quality Upper-bound (品質天花板):** 檢索器的**「召回率 (Recall)」**直接決定了最終生成答案品質的上限。如果 Retriever 沒能把包含正確答案的文件找出來，後端的 Generator 再聰明也無法憑空捏造正確解答（甚至會引發幻覺）。
* **Efficiency & Cost (效率與成本):** 檢索過程的**「延遲 (Latency)」**與**「建立索引的成本 (Indexing costs)」**，在很大程度上驅動了整個搜尋系統的總體運作效率。

#### 3. The Key Lever for Industrial Deployment (工業落地的關鍵槓桿)
* **Conclusion (核心結論):** 基於上述痛點，優化文件檢索是讓工業級 RAG 部署變得更精準、更具成本效益的**關鍵槓桿 (Key lever)**。
* **Complex Scenarios (複雜應用場景):** 這項優化對於那些冗長、結構複雜的文件（例如：**PDF、科學文獻 (Scientific articles) 與商業報告 (Reports)**）尤為迫切且重要。

### 📜 The Paradigm Shift: From Text to Visual Document Retrieval (從純文字到視覺文件檢索)

#### 1. The Traditional Text-Based Pipeline & Limitations (傳統純文字檢索與其痛點)
過去，處理 PDF 或掃描檔的檢索系統完全受限於**純文字空間 (Text space)**。這需要一條極度繁重的預處理流水線：
* **Pipeline (處理流程):** 必須先經過 **OCR (光學字元辨識)** $\to$ **版面分析 (Layout analysis)** $\to$ **啟發式段落分割 (Heuristic passage segmentation)**，最後才將萃取出的文字送入神經編碼器 (Neural encoder) 轉成向量。
* **Limitations (三大致命痛點):**
    1. **Brittle and Slow (脆弱且緩慢):** OCR 與版面解析的過程不僅運算耗時，且面對稍微複雜的排版就容易崩潰。
    2. **Loss of Visual Elements (視覺資訊遺失):** 複雜的視覺元素（如：**表格 Tables、圖表 Figures、特殊排版 Typography**）在轉換為純文字時往往被嚴重破壞。
    3. **Error Propagation (錯誤傳播):** 在預處理階段產生的任何辨識錯誤或偏差，都會被無情地「傳播 (propagated)」給後端的檢索器，大幅降低準確度。

#### 2. The Solution: Visual Document Retrieval (解決方案：視覺文件檢索的崛起)
為了克服上述痛點，**視覺文件檢索 (VDR)** 成為了極具吸引力的替代方案。它的核心運作邏輯發生了根本性的改變：
* **Direct Image Input (直接輸入影像):** 不再依賴預先擷取的純文字，VDR 模型直接將**「完整的頁面截圖 (Page screenshots)」**作為輸入。
* **Visual Matching (視覺語意比對):** 給定使用者的檢索詞 (Query)，模型會直接計算檢索詞與「基於影像的文件表徵 (Image-based representations)」之間的相似度。

#### 3. The Advantages of VDR (VDR 的四大核心優勢)
相較於傳統方法，作者總結了 VDR 帶來的決定性好處：
* **Simpler Pipeline (極簡的端到端流程):** 徹底跳過 OCR 與版面解析步驟，降低系統複雜度。
* **Reduced Latency (降低索引延遲):** 大幅減少了文件入庫、建立索引所需的處理時間。
* **Exploiting Visual Cues (完整保留視覺線索):** 能夠完美捕捉並利用傳統純文字會流失的豐富資訊（例如**排版 Layout、圖表 Figures 與字體 Fonts**）。
* **Strong Performance (強悍的實戰效能):** 在如 ViDoRe 這類視覺元素豐富的基準測試 (Visually rich benchmarks) 上，展現了極具競爭力的表現。

### ⚠️ The Limits of Generative VLM Repurposing (生成式 VLM 轉作檢索模型的侷限性與近期發展)

#### 1. The Status Quo: Cost-Efficient but Suboptimal (業界現狀：低成本的「改裝車」)
* **Current Approach (主流作法):** 目前大多數的視覺文件檢索 (VDR) 系統，都是透過「事後對比微調 (Post-hoc contrastive fine-tuning)」，將現成的大型「生成式視覺-語言解碼器 (Generative Vision-Language Decoders)」直接改裝成檢索編碼器 (Retrieval encoders)。
* **The Trade-off (效能妥協):** 雖然這種拿現成模型改裝的做法極具成本效益 (Cost-efficient)，但這項設計決策實際上嚴重卡死了檢索的效能與效率 (Bottlenecks retrieval performance and efficiency)。

#### 2. The Architecture Mismatch (核心痛點：架構與目標的嚴重錯位)
作者指出，生成模型的天生設計並不適合檢索任務。這在純文字模型中早已被證實為次優解 (Suboptimal)，放到視覺模型上依然是個問題：
* **Mismatched Designs (四大錯位):** 生成模型的四大核心預設——**模型大小 (Model sizes)、注意力模式 (Attention patterns)、影像解析度 (Image resolutions)、訓練目標 (Training objectives)**——都是為了「生成文字 (Generative use cases)」而設計，根本沒有針對「檢索匹配」進行最佳化。

#### 3. The Scaling Law Myth (打破參數迷思：縮放定律的差異)
* **Less Pronounced Scaling (不適用的縮放定律):** 在生成模型中「參數越大越聰明」的縮放趨勢 (Scaling trends)，在嵌入/檢索模型 (Embedding models) 上其實並不明顯。
* **Small is Beautiful (小模型的潛力):** 雖然效能與模型大小有一定關聯，但只要架構正確，**小模型依然能夠達到非常強悍的檢索效能 (Strong retrieval performance remains attainable with small models)**。這也是 ModernVBERT 得以用 250M 小參數逆襲大模型的理論基礎。

#### 4. Recent Industry Interventions (近期業界的優化嘗試)
面對上述生成式模型的瓶頸，近期視覺檢索領域的各家研究紛紛祭出了不同的手段來提升效能：
1. **大力出奇蹟:** 擴增對比學習的數據量與運算預算 (Scaling contrastive data and compute budget)。
2. **修改底層機制:** 改變注意力遮罩的設計 (Modifying the attention mask)。
3. **提升視覺精細度:** 提高輸入影像的解析度 (Increasing image resolutions)。
4. **增加資料多樣性:** 引入更多元化的任務與資料來源 (Introducing more diverse tasks and data sources)。

### 🎯 The Core Objective & Central Question (核心研究目標與關鍵叩問)

#### 1. Systematically Disentangling Design Choices (系統化解開設計的迷霧)
* **The Goal (研究目標):** 面對業界各種零散的優化嘗試，本作試圖將這些努力「集中化 (Centralize)」，並有系統地「解開 (Disentangle)」在視覺檢索器訓練中，各項核心設計決策所帶來的真實影響。
* **The Method (研究方法):** 透過涵蓋從「語言模型預訓練 (Language model pretraining)」到「多階段、特定領域微調 (Multi-stage, domain-specific fine-tuning)」的**嚴格控制變因實驗 (Controlled experiments)**。
* **The Central Question (核心叩問):** 所有的實驗都是為了回答一個最根本的問題：
  > **"Which design choices best boost performance in modern visual document retrievers?"**
  > （在現代視覺文件檢索器中，究竟是哪些設計選擇最能有效提升效能？）

### 🏆 The Core Contributions (論文的兩大核心貢獻)

#### Contribution 1: Revisiting Core Assumptions (打破常規：重新審視視覺檢索設計)
作者透過系統性的實驗，推翻並修正了幾個關於訓練 VDR 模型的重要假設：
* **The True Value of Token-level Objectives (詞元級目標的真諦):** 實驗證明，詞元級別的訓練目標不單單只是產生更強的「影像嵌入 (Image embeddings)」，它真正的價值在於深度強化**「影像與文字詞元之間的對齊 (Image-text token alignment)」**。
* **Bidirectional > Causal (雙向注意力勝出):** 證實了「因果注意力 (Causal attention)」在文件檢索中是次優的 (Suboptimal)。特別是在多向量 (Multi-vector) 的設定下，採用**雙向遮罩 (Bidirectional masking)** 能帶來顯著的效能改善。

* **Holistic Pipeline (不可忽視的訓練細節):** 在訓練管線中，**影像解析度 (Image resolution)** 與**資料混合比例 (Data mixes)** 等參數絕對不能被忽略，它們是左右最終效能的關鍵。

#### Contribution 2: The Birth of ModernVBERT (ModernVBERT 的誕生：從零打造的檢索專武)
基於上述的第一點洞見，研究團隊開發並開源了全新的視覺檢索模型：
* **ModernVBERT (基礎模型):** 一個極度輕量、僅有 **2.5 億參數 (250M)** 的多模態編碼器 (Multimodal encoder)。它透過掩碼語言模型 (MLM) 的目標，將預訓練的語言 Encoder 與視覺 Encoder 完美融合對齊。
* **ColModernVBERT (檢索特化變體):** 這是專為文件檢索任務微調 (Fine-tuned) 的進階版本。
* **The Milestone (里程碑意義):** 儘管體積嬌小且訓練預算有限，ColModernVBERT 在標準的視覺文件檢索基準測試中，竟然**追平了比它大上 10 倍 (10x larger) 的大型模型**！
* **Conclusion (結論):** 這項成果強而有力地證明了：「從零開始、專為檢索量身打造模型 (Designing a retrieval-focused model from the ground up)」，遠比盲目拿生成式大模型來改裝有效得多。
