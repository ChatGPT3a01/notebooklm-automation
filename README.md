# NotebookLM 自動化 Web GUI

透過網頁介面，用自然語言控制 Google NotebookLM。

## 功能特色

- 📚 筆記本管理（建立、刪除、重命名）
- 📎 來源匯入（URL、YouTube、PDF）
- 🎙️ 內容生成（Podcast、影片、簡報、測驗、閃卡、心智圖等）
- 🔍 智慧問答（對文件提問）
- 📥 下載匯出

## 系統需求

| 項目 | 需求 |
|------|------|
| Python | 3.9 以上 |
| 作業系統 | Windows / macOS / Linux |
| 瀏覽器 | Chromium（自動安裝） |
| Google 帳號 | 需要登入 NotebookLM |

## 安裝步驟

### 1. 下載專案

```bash
git clone https://github.com/ChatGPT3a01/notebooklm-automation.git
cd notebooklm-automation
```

或直接下載 ZIP：點擊上方綠色「Code」按鈕 → Download ZIP → 解壓縮

### 2. 安裝依賴

```bash
pip install -r requirements.txt
playwright install chromium
```

> 這會自動安裝 Flask、notebooklm-py 等所有必要套件。
> Chromium 下載約 200MB，請確保網路穩定。

### 3. Google 帳號登入

```bash
notebooklm login
```

執行後會開啟瀏覽器，完成 Google 帳號登入後，在終端機按 Enter 確認。

### 4. 啟動應用程式

```bash
python app.py
```

### 5. 開啟瀏覽器

訪問 http://localhost:5000

## 使用方式

### 自然語言指令範例

**筆記本管理：**
- 「列出我所有的筆記本」
- 「建立一個叫做『AI研究』的筆記本」

**來源匯入：**
- 「新增這個網址 https://example.com」
- 「加入這個 YouTube 影片」

**內容生成：**
- 「幫我生成 Podcast」
- 「製作心智圖」
- 「生成 10 題測驗」

## 專案結構

```
notebooklm-automation/
├── app.py                # Flask 主程式
├── config.py             # Flask 設定
├── config.json           # 使用者設定
├── requirements.txt      # Python 依賴
├── routes/               # API 路由
│   ├── auth.py          # 認證
│   ├── notebooks.py     # 筆記本管理
│   ├── sources.py       # 來源管理
│   ├── artifacts.py     # 工件管理
│   ├── settings.py      # 設定
│   └── execute.py       # 自然語言執行
├── services/             # 業務邏輯
│   ├── notebooklm_service.py  # CLI 封裝
│   ├── nlp_parser.py          # 自然語言解析
│   ├── config_manager.py      # 設定管理
│   └── task_manager.py        # 背景任務
├── static/               # 靜態資源
│   ├── css/
│   ├── js/
│   └── images/
└── templates/            # HTML 模板
    ├── base.html
    ├── splash.html
    ├── index.html
    ├── features.html
    └── settings.html
```

## 部署選項

### 本機使用
```bash
python app.py
```

### 區域網路分享
其他電腦訪問：`http://你的IP:5000`

### Windows 正式部署 (Waitress)
```bash
pip install waitress
python -c "from waitress import serve; from app import create_app; serve(create_app(), host='0.0.0.0', port=5000)"
```

### Linux/macOS 正式部署 (Gunicorn)
```bash
pip install gunicorn
gunicorn -w 4 -b 0.0.0.0:5000 "app:create_app()"
```

## 常見問題

**Q: 登入狀態失效？**
重新執行 `notebooklm login`

**Q: 生成 Podcast 很久沒反應？**
Podcast 生成需要 2-5 分鐘，檢查右側「任務狀態」欄位

**Q: 無法遠端存取？**
確認 `app.run(host='0.0.0.0')` 並開放防火牆 5000 port

## 授權

MIT License

---

❣️ Powered by 阿亮老師
