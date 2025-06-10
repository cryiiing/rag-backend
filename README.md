# 智能文档问答后端 (Document QA Backend)

这是一个基于 LangChain、FAISS、阿里云灵积和深度求索模型的本地文档智能问答系统后端。用户可以提供本地文档（PDF, DOCX, TXT），系统会构建一个知识库，并通过命令行进行交互式问答。

## ✨ 功能特性

- **多格式支持**: 支持 PDF, DOCX, 和 TXT 格式的文档。
- **国产模型驱动**: 使用阿里云灵积 `text-embedding-v3` 进行文本向量化，使用 `deepseek-chat` 模型进行对话生成，兼顾性能与成本。
- **本地化知识库**: 知识库存储在本地
- **对话式交互**: 支持多轮对话，能够理解上下文。
- **来源可追溯**: 回答时会附上参考的源文档信息。

## 📁 项目结构

```
doc-qa-backend/
├── src/
│   └── main.py         # 核心后端逻辑
├── .env                # 环境变量模板
├── README.md           # 项目说明
└── requirements.txt    # Python依赖
```

## 🚀 快速开始

### 1. 克隆项目

```bash
git clone https://github.com/your-username/doc-qa-backend.git
cd doc-qa-backend
```

### 2. 创建并激活虚拟环境

推荐使用 `conda` 或 `venv` 创建独立的Python环境。

```bash
# 使用 conda
conda create -n docqa python=3.11 -y
conda activate docqa
```

### 3. 安装依赖

```bash
pip install -r requirements.txt
```

### 4. 配置环境变量

复制 `.env.example` 文件并重命名为 `.env`。

```bash
cp .env.example .env
```

然后，编辑 `.env` 文件，填入你自己的 API 密钥。

```env
DASHSCOPE_API_KEY="sk-your-dashscope-key"
DEEPSEEK_API_KEY="sk-your-deepseek-key"
```

### 5. 修改文件路径并运行

打开 `src/main.py` 文件，在 `if __name__ == "__main__":` 部分，修改 `file_paths` 列表，指向你本地的文档路径。

```python
# src/main.py

# ...
if __name__ == "__main__":
    file_paths = [
        "path/to/your/document1.pdf",
        "path/to/your/document2.docx",
    ]
    # ...
```

最后，运行主程序：

```bash
python src/main.py
```

程序会开始处理文档并进入交互式问答模式。
