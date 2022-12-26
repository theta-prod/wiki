# [Tutorial] If we need build a controled gpt model

- **Metadata** : `type: Tutoial` `scope: System, Solution` 
- **Techs Need** : `docker` `git`
- **Status**: `on-going`
<br/><br/>

## ✨ You should already know
- docker/ docker-compose
- git

👩‍💻 👨‍💻

## ✨ About the wiki
- `Situation:` 當學生在寫新提案時，常常沒有適合的範本來學習模仿，因此造成極大的負擔
- `Target:` 在學生編寫新提案時，產生相對應的範本來給學生參考
- `Index:`

| Sub title | decription | memo |
| ------ | ------ | ------ |
| 整體規劃 | 包含執行流程、技術架構和服務流程的規劃 | - |
| 模型選擇 | 基底模型的選擇 | InstructGPT, PPO |
| 資料蒐集 | 建置穩定從網路上蒐集資料的方法 | Python, Crontab, browser-driver |
| 資料標註與前處理 | 標註資料的方法建置 | NER, Classfication等標註方式 |
| 模型與知識管理 | 模型的訓練與上傳管理 | Transformers, ELK |
| 產品應用與管理 | 提取與使用模型的方法 | Restful API, Pipeline |


## ✨ Sessions

---
<br>

### **整體規劃**
> 包含執行流程、技術架構和服務流程的規劃

####  📝 系統架構
> 架構我們包含五個部分，模型架構選擇、資料蒐集、資料標註與前處理、模型與知識管理和產品應用與管理。

| - | decription | tech |
| ------ | ------ | ------ |
| 模型選擇 | 透過GPT2與情緒模型來模擬訓練InstructGPT | InstructGPT, PPO |
| 資料蒐集 | 透過CrawLab和Selenium來操作瀏覽器蒐集資料 | Python, Crontab, browser-driver |
| 資料標註與前處理 | 透過doccano來進行標註資料 | NER, Classfication等標註方式 |
| 模型與知識管理 | 透過hungingface與ELK來管理模型與資料 | Transformers, ELK |
| 產品應用與管理 | 透過hungingface與FastAPI來提取與使用模型 | Restful API, Pipeline |

- 流程歸納
1. 網路資源(網頁) -> CrawLab和Selenium進行爬蟲 -> 原始數據
2. 原始數據 -> 在ELK內儲存資料 -> 原始數據資料庫
3. 原始數據資料庫 -> 使用doccano標註資料 -> 已標註數據資料庫
4. 已標註數據資料庫 -> 使用 Transformers 進行模型訓練與上傳 -> 模型資料庫
5. 模型資料庫 -> 提取模型並使用FastAPI提供服務 -> Restful API

### **模型架構選擇**
這是預期目標是在內容生成的部分，因此我們使用開源的GPT2的中文版本模型
與[InstructGPT]("https://arxiv.org/abs/2203.02155")所介紹的流程。
![image](https://cdn.openai.com/chatgpt/draft-20221129c/ChatGPT_Diagram.svg)
其中主旨為使用`短文與長文對應`來製作`內容擴展`的模型，並建立`情緒模型`作為`獎勵模型`來加以控制。

### **資料蒐集**
資料蒐集我們有使用`IBM`提供的[Apply design thinking to AI](https://www.ibm.com/design/thinking/page/courses/AI_Essentials) 課程中
的[AI Essentials: Data](https://www.ibm.com/design/thinking/page/toolkit/activity/ai-essentials-data) 工具進行分析，將需要的資料區根據其中不同的性質來使用不同流程進行管理。
為了在網路上蒐集到更多真實的資料，我們要建置一個`資料蒐集系統`，該系統含有網頁操作、資料暫存和任務排程系統。


### **資料標註與前處理**

根據上面所述，我們總共會產生三個模型，分別是作為基底的`擴寫模型`、作為獎勵模型的`情緒模型`，
與最終產物 – `特定情緒偏好擴寫模型`。因此我們使用`人工方式`標註`情緒資料`、再之組合標題、摘要
與內文的組合作為`擴寫範本`。
這邊我們需要有個平台來協助標註資料，[doccano](https://github.com/doccano/doccano) 是一個
供人類使用的開源註釋工具。它可以創建用於情感分析、命名實體識別、文本摘要等的標記數據。

### **模型與知識管理**

在這流程中我們需要一個有規範的`資料管理流程`，在這流程中我們選擇用[ELK](https://www.elastic.co/what-is/elk-stack) 
的框架，該框架包含資料庫、資料分析圖像化和內容搜尋等相關內容m在ELK提供中心化的內容功能，協助發現資料蒐集與應用程式中的問題。
ELK提供中心化的內容功能，協助發現資料蒐集與應用程式中的問題，它讓用戶能在一個平台上搜尋與監控所有文字內容，也讓內容搜尋與監控變得輕而易舉。
除了資料管理以外，我們使用`Hugging Face`作為模型管理的平台，Hugging Face開發使用機器學習構建應用的標準程序。
最著名的是其為自然語言處理應用程序構建的Transformers模組，以及允許用戶共享機器學習模型和數據集的平台。


### **產品應用與管理**
當模型完成並上架[Transformers資料庫](https://huggingface.co/docs/transformers/main_classes/pipelines)，我們透過Hugging Face提供的Pipeline作為引用介面，Pipeline是使用模型進行推理的一種非常簡單的方法。
Pipeline是從Transformers資料庫中抽取出模型，提供專用於建置網路服務的 API，包括命名實體識別、內容生成、情感分析、特徵提取和問答。
搭配[FastAPI](https://fastapi.tiangolo.com/) 作為服務提供的介面，FastAPI是用於在Python中開發RESTful API的Web框架。
FastAPI基於Pydantic和類型提示，以驗證，序列化和反序列化數據，並自動生成OpenAPI文檔。
它完全支持異步編程，並且可以與Gunicorn和ASGI服務器一起運行以用於Uvicorn和Hypercorn等產品。
