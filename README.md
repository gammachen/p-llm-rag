# 天龙八部RAG问答系统

## 系统依赖安装说明

您遇到的错误表明系统缺少必要的依赖包。请按以下步骤安装：

**1. 安装核心依赖包：**

```
flask
flask-session
numpy
torch
faiss-cpu
sentence-transformers
transformers
Pillow
opencv-python
pytesseract
pdf2image
moviepy
```

**2. 安装OCR相关依赖包：**

```
sudo apt-get install tesseract-ocr
```

**3. 安装视频处理相关依赖包：**

```
sudo apt-get install ffmpeg
```

**4. 安装Python库：**

```
pip install -r requirements.txt
```

**5. 安装OCR语言包（可选）：**

```
sudo apt-get install tesseract-ocr-chi-sim
```

```
# 天龙八部RAG问答系统

这是一个基于RAG（检索增强生成）技术的问答系统，专门针对《天龙八部》小说内容以及其他非结构化数据进行智能问答。系统支持多种RAG模式和多模态数据处理。

## 功能特点

### 三种RAG模式

1. **基本RAG模式**：将非结构化数据通过Embedding Model进行向量化，存储到向量数据库中。查询时，系统构建提示并传递给LLM。
   - 优点：提高数据检索的准确性，减少LLM的计算负担

2. **带记忆的RAG模式**：用户提出问题后，问题和回答都存储到长时记忆数据库中。后续查询会考虑之前的对话历史。
   - 优点：提供持续的上下文记忆，改善用户体验

3. **带缓存的RAG模式**：用户问题向量化后，从cache中查询类似的问题和答案。如果没有命中，则与LLM交互，并将回答存储到Cache中。
   - 优点：提高响应速度，减少重复计算

### 多模态数据处理

系统支持处理以下类型的非结构化数据：

- **文本**：小说、文章等纯文本内容
- **PDF**：通过OCR提取文本内容
- **图片**：通过OCR提取图片中的文字信息
- **视频**：提取关键帧并识别其中的文字内容

### 多轮对话

系统支持多轮对话，能够记住之前的交互历史，提供连贯的对话体验。

## 技术架构

- **前端**：HTML/CSS/JavaScript
- **后端**：Flask
- **向量嵌入**：Sentence-Transformers
- **向量数据库**：FAISS
- **语言模型**：Qwen1.5-0.5B-Chat
- **OCR处理**：pytesseract
- **PDF处理**：pdf2image
- **视频处理**：OpenCV, moviepy

## 项目结构

```
/
├── app.py                 # 主应用入口
├── flask_app/             # Flask应用目录
│   ├── app.py             # Flask应用主文件
│   └── rag_implementation.py  # RAG实现逻辑
├── templates/             # HTML模板
│   └── index.html         # 主页面
├── static/                # 静态资源
│   ├── images/            # 图片资源
│   ├── videos/            # 视频资源
│   └── uploads/           # 用户上传文件
└── tian_long_ba_bu.txt    # 天龙八部小说文本
```

## 使用方法

1. 启动应用：

```bash
python flask_app/app.py
```

2. 在浏览器中访问：`http://localhost:5000`

3. 在界面上选择RAG模式、检索类型和文件类型（如适用）

4. 输入问题并点击发送

5. 查看系统返回的回答和相关检索结果

6. 可以通过上传功能添加新的文档到知识库

## 非结构化数据说明

非结构化数据是指没有预定义数据模型或不符合预定义数据模型的信息，通常是文本重的人类语言、音频、视频、图片等。与结构化数据（如数据库表）不同，非结构化数据不能轻易地被传统程序处理。

在本系统中：

- 文本文件（如小说）是最基本的非结构化数据
- 图片中的文字需要通过OCR技术提取
- PDF文件需要先转换为图像，再通过OCR提取文本
- 视频需要提取关键帧，然后应用OCR技术

## 依赖库

```
flask
flask-session
numpy
torch
faiss-cpu
sentence-transformers
transformers
Pillow
opencv-python
pytesseract
pdf2image
moviepy
```

## 注意事项

- 首次运行时，系统会自动加载《天龙八部》小说文本并构建向量索引，可能需要一些时间
- 处理大型文件（特别是视频）可能需要较长时间
- OCR识别的准确性取决于图像质量
- 系统响应速度受限于硬件性能和模型大小# p-llm-rag
# p-llm-rag
