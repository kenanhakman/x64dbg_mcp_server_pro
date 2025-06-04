# x64dbg_mcp_server_pro

🔧 A powerful MCP (Message Command Protocol) server that enables remote debugging of Windows executables via [x64dbg](https://x64dbg.com) — directly from Visual Studio Code using [CLine](https://marketplace.visualstudio.com/items?itemName=saoudrizwan.claude-dev) and [RooCode](https://marketplace.visualstudio.com/items?itemName=RooVeterinaryInc.roo-cline).

---

## 📌 Overview

`x64dbg_mcp_server_pro` bridges the gap between your development environment and low-level debugging by providing a communication server that speaks the **MCP protocol** used by VSCode extensions like CLine and RooCode.

This tool allows users to remotely control an x64dbg session, inspect memory, set breakpoints, manipulate registers, and automate analysis — all without leaving the editor.

---

## ✨ Features

### 🔄 Debug Session Management
- `start_debug_session`, `stop_debug_session`, `attach_to_process`, `detach_debugger`, `is_debugging`
- Full control over debug session lifecycle

### 🐞 Execution Control
- `continue_execution`, `pause_execution`, `step_into`, `step_over`, `step_out`, `execute_command`
- Seamless step-by-step navigation and code execution

### 💾 Memory Inspection & Manipulation
- `read_memory`, `write_memory`, `get_memory_info`, `get_memory_map`, `memset_memory`
- Word/DWord/QWord access: `read_word`, `read_dword`, `read_qword`

### 🧱 Memory Management
- `virtual_alloc`, `virtual_free`, `virtual_protect`, `virtual_query`

### 🔍 Breakpoint Handling
- `set_breakpoint`, `remove_breakpoint`, `toggle_breakpoint`, `list_breakpoints`
- Advanced: `set_hardware_breakpoint`, `set_memory_breakpoint`, `remove_hardware_breakpoint`, `remove_memory_breakpoint`

### 🧠 Registers and Symbols
- `get_registers`, `set_register`, `get_symbol_at`, `disassemble`, `assemble`

### 🏷 Comments & Labels
- `set_comment`, `remove_comment`, `get_comment_at`
- `set_label`, `remove_label`, `get_label_at`

### 🛠 Utility & Status
- `get_server_status`, `get_help`, `hide_debugger`

---

## 🚀 Getting Started

📚 API Reference
The following MCP commands are supported:

Kopyala
Düzenle
is_debugging, start_debug_session, attach_to_process, detach_debugger, stop_debug_session,
continue_execution, pause_execution, step_into, step_over, step_out, execute_command,
read_memory, write_memory, get_memory_info, get_memory_map, memset_memory,
read_word, read_dword, read_qword,
virtual_alloc, virtual_free, virtual_protect, virtual_query,
set_breakpoint, remove_breakpoint, toggle_breakpoint, list_breakpoints,
set_hardware_breakpoint, remove_hardware_breakpoint, set_memory_breakpoint, remove_memory_breakpoint,
get_registers, set_register, get_symbol_at, disassemble, assemble,
set_label, remove_label, get_label_at,
set_comment, remove_comment, get_comment_at,
hide_debugger, get_server_status, get_help
Use the get_help command for detailed info on each command and parameters.

### 1. Clone this repo
---

## ⚙️ Configuration Instructions (VSCode + RooCode / CLine)

1. **Unzip** the archive you downloaded.
2. **Move** the extracted folder to: /username/
3. **Edit your RooCode or CLine `.json` config file** in VSCode (usually in your workspace or extension settings):

```json
{
  "mcpServers": {
    "x64dbg": {
      "disabled": false,
      "transportType": "stdio",
      "command": "python",
      "args": [
        "C:\\Users\\<your_username>\\x64dbg_MCP_server_pro\\x64dbg_mcp_server_pro.py",
        "--x64dbg-server",
        "http://127.0.0.1:8888/",
        "--transport",
        "stdio"
      ],
      "autoApprove": []
    }
  }
}
