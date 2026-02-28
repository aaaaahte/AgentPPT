# AgentPPT

**用自然语言创建和编辑 PPT，让 Agent 帮你做幻灯片。**

AgentPPT 是一个基于大模型 Agent 的 PPT 创建与编辑工具。输入主题或编辑指令，Agent 自动生成或修改演示文稿；编辑时提供类似 Cursor 的交互：实时预览、同意/取消单次修改、多版本保存与恢复。

---

## ✨ 功能特性

### PPT 创建

- **主题驱动**：输入主题，Agent 自动生成大纲与各页内容
- **辅助材料**：支持上传与主题相关的文档（如 Word）辅助生成
- **双模式**：
  - **无模板模式**：由 Agent 自由排版与生成
  - **有模板模式**：上传或选择模板，Agent 在占位符内填充内容，保留版式

### PPT 编辑

- **自然语言编辑**：用文字描述修改意图（如「把第三页标题改成 XXX」），Agent 理解并执行
- **实时预览**：缩略图列表 + 当前页大图，修改后即时刷新
- **同意 / 取消**：满意则确认保存，不满意则一键回退到修改前
- **多版本管理**：保存多个版本（版本 1 / 2 / 3 …），可随时恢复到任意版本

### 规划中

- 流式分步预览、当前页在线编辑、更丰富的版式与动画支持等，见 [技术设计文档](docs/TECHNICAL_DESIGN.md#7-后续演进方向)

---

## 🛠 技术栈

| 层级     | 技术 |
|----------|------|
| 后端     | Python 3.10+ · FastAPI · LangChain · python-pptx |
| 前端     | Vue 3 · TypeScript |
| 大模型   | 通过环境变量配置 API Key，支持接入常见 LLM API |

---

## 📦 快速开始

### 环境要求

- Python 3.10+
- Node.js 18+（用于前端开发与构建）
- 大模型 API Key（如 OpenAI、Claude、国产大模型等，由后端统一配置）

### 配置

在项目根目录或运行环境中配置环境变量，例如：

```bash
# 必填：大模型 API 相关（变量名依实际后端实现为准）
export OPENAI_API_KEY="your-api-key"
# 或
export ANTHROPIC_API_KEY="your-api-key"
```

具体支持的变量名见后端说明或 `.env.example`（若项目提供）。

### 安装与运行

```bash
# 克隆仓库
git clone https://github.com/your-username/AgentPPT.git
cd AgentPPT

# 后端
cd backend
pip install -r requirements.txt
uvicorn main:app --reload

# 前端（另开终端）
cd frontend
npm install
npm run dev
```

访问前端开发地址（如 `http://localhost:5173`）即可使用。生产部署时可将前端构建为静态资源，由后端或 Nginx 等托管。

> 说明：若仓库尚未包含完整后端/前端目录，可先参考 [技术设计文档](docs/TECHNICAL_DESIGN.md) 了解架构与接口约定。

---

## 📁 项目结构（示意）

```
AgentPPT/
├── backend/          # FastAPI 后端，LangChain Agent，python-pptx 服务
├── frontend/         # Vue 3 + TypeScript 前端
├── docs/             # 设计文档
│   └── TECHNICAL_DESIGN.md
└── README.md
```

实际结构以仓库为准，详细模块划分见 [技术设计文档](docs/TECHNICAL_DESIGN.md)。

---

## 📄 文档

- [技术设计文档](docs/TECHNICAL_DESIGN.md)：功能范围、架构、接口与流程、编辑指令设计、后续演进等

---

## 📜 开源协议

具体协议以仓库为准。

---

## 🤝 参与贡献

欢迎提交 Issue 与 Pull Request。开发前建议先阅读 [技术设计文档](docs/TECHNICAL_DESIGN.md) 以了解整体设计。
