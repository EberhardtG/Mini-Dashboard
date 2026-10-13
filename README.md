

# **Task Dashboard — FastAPI Mini API Integration**

A lightweight, interactive dashboard that connects to the *mini_api.py* FastAPI backend and displays live task data. This project demonstrates core frontend–backend integration skills: fetching API data, rendering dynamic UI elements, submitting POST requests, and maintaining a responsive dashboard experience.

This assignment mirrors the structure of real dashboards you’ll build in Streamlit and full-stack applications later in the program.

---

## 🚀 **Features**

### **📊 Live Task Statistics**
Fetched directly from `/stats`:
- **Total tasks**
- **Completed tasks**
- **Pending tasks**

### **📋 Task List**
Fetched from `/tasks`:
- Displays every task with its current status  
- Status icons:
  - ✔ Done  
  - ⏳ Pending  

### **➕ Add New Tasks**
- Input field + Add button  
- Sends a POST request to `/tasks`  
- Automatically refreshes the dashboard after adding

### **🔄 Refresh Dashboard**
- Re-fetches both tasks and stats  
- Updates the “Last Updated” timestamp  
- Ensures the UI always reflects the backend state

### **⏱ Last Updated Timestamp**
- Uses `new Date().toLocaleTimeString()`  
- Updates every time the dashboard refreshes

### **⚠ Error Handling**
- Displays user-friendly error messages  
- Logs technical errors to the console for debugging

---

## 🧠 **How It Works**

### **1. API Integration**
All data comes from the FastAPI mini API running locally:

```
http://localhost:8000
```

Endpoints used:
- `GET /tasks` — fetch all tasks  
- `POST /tasks` — add a new task  
- `GET /stats` — fetch summary statistics  

### **2. Core Functions**

#### **loadTasks()**
- Fetches all tasks  
- Clears the existing list  
- Renders each task with its status  

#### **loadStats()**
- Fetches total/done/pending counts  
- Updates the stats bar  

#### **addTask()**
- Reads input  
- Sends POST request  
- Clears input  
- Refreshes tasks + stats  

#### **refreshAll()**
- Calls both load functions  
- Updates timestamp  
- Used by the Refresh button and page load  

### **3. Event Listeners**
- Add button → `addTask()`  
- Refresh button → `refreshAll()`  
- Page load → `refreshAll()`  

---

## 📂 **Project Structure**

```
dashboard.html
└── Contains HTML, CSS, and JavaScript for the dashboard UI
mini_api.py
└── FastAPI backend providing /tasks and /stats endpoints
```

---

## 🛠️ **Tech Stack**

- **HTML** — structure  
- **CSS** — layout and styling  
- **JavaScript** — API calls, DOM updates, event handling  
- **FastAPI** — backend API  
- **JSON** — data format  

---

## 🧩 **Design Decisions**

- **Single source of truth:**  
  All task data comes from the API, not from local state.

- **Separation of concerns:**  
  `loadTasks()` handles rendering tasks,  
  `loadStats()` handles statistics,  
  `addTask()` handles POST requests,  
  `refreshAll()` orchestrates updates.

- **Immediate UI feedback:**  
  After adding a task, the dashboard refreshes automatically.

- **Clear error messaging:**  
  Errors are shown in the UI and logged for debugging.

- **Simple, readable layout:**  
  Designed for clarity and ease of use.

---

## 📦 **Prerequisites**

Before opening `dashboard.html`, ensure the FastAPI mini API is running:

```bash
uvicorn mini_api:app --reload
```

---

## ▶️ **Usage**

1. Start the FastAPI server  
2. Open `dashboard.html` in your browser  
3. View live stats and tasks  
4. Add new tasks  
5. Refresh the dashboard anytime  

---

## ✔️ **Assignment Requirements — Completed**

| Requirement | Status |
|------------|--------|
| Stats bar using `/stats` | ✔ Done |
| Task list using `/tasks` | ✔ Done |
| Add form POSTing to `/tasks` | ✔ Done |
| Refresh button | ✔ Done |
| Last updated timestamp | ✔ Done |
| Uses fetch + response.ok + try/catch | ✔ Done |
| Calls refreshAll() on page load | ✔ Done |

