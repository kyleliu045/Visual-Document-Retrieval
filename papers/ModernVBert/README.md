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
