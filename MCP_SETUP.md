# MCP Server Configuration Guide for HexTrackr

## 🔧 **VS Code MCP Server Setup**

### **Required MCP Servers**
1. **Memory** - Project context and state persistence
2. **Playwright** - Browser automation and UI testing
3. **Context7** - Enhanced context management
4. **Sequential Thinking** - Complex problem solving

### **Memory Server Configuration**

#### **Centralized Storage Path**
- **Location**: `/Volumes/DATA/GitHub/server-memory/`
- **Purpose**: Shared memory across all projects and sessions
- **Benefits**: Persistent context, cross-project learning

#### **VS Code Settings (settings.json)**
```json
{
  "mcp.servers": {
    "memory": {
      "command": "mcp-memory-server",
      "args": ["--storage-path", "/Volumes/DATA/GitHub/server-memory/"],
      "env": {
        "MEMORY_STORAGE_PATH": "/Volumes/DATA/GitHub/server-memory/"
      }
    },
    "playwright": {
      "command": "mcp-playwright-server"
    },
    "sequential-thinking": {
      "command": "mcp-sequential-thinking-server"
    }
  }
}
```

### **Setup Commands**
```bash
# Create centralized memory directory
mkdir -p /Volumes/DATA/GitHub/server-memory

# Verify directory exists
ls -la /Volumes/DATA/GitHub/server-memory/

# Test memory server (if accessible via CLI)
echo "HexTrackr project initialized" > /Volumes/DATA/GitHub/server-memory/project-init.txt
```

### **Troubleshooting**

#### **Memory Server Path Issues**
```bash
# Check if directory exists
ls -la /Volumes/DATA/GitHub/server-memory/

# Recreate if missing
mkdir -p /Volumes/DATA/GitHub/server-memory/

# Check permissions
chmod 755 /Volumes/DATA/GitHub/server-memory/
```

#### **VS Code MCP Issues**
1. **Restart MCP Servers**: Command Palette → "MCP: Restart Servers"
2. **Check Configuration**: Settings → Search "MCP" → Verify server paths
3. **View Logs**: Check VS Code output panel for MCP server logs
4. **Reinstall**: Disable and re-enable MCP extension if needed

### **Verification Steps**
```bash
# 1. Directory structure check
ls -la /Volumes/DATA/GitHub/server-memory/

# 2. VS Code MCP status
# Open Command Palette (Cmd+Shift+P)
# Type: MCP: Show Server Status

# 3. Test memory functionality
# Try mcp_memory_create_entities in chat

# 4. Test other MCP servers
# Playwright: mcp_playwright_browser_navigate
# Sequential: mcp_sequentialthi_sequentialthinking
```

### **Project-Specific Memory Usage**

#### **HexTrackr Context Storage**
The Memory MCP should store:
- Current development phase and sprint status
- Completed features and pending tasks
- Architecture decisions and design patterns
- User preferences and workflow standards
- Git workflow and commit message patterns

#### **Cross-Session Continuity**
When starting new chat sessions, AI assistants should:
1. Load project context from memory
2. Verify current development phase
3. Check for pending tasks or blockers
4. Understand established patterns and standards

---

**Important**: User must configure VS Code MCP settings manually. AI assistants can only verify functionality and provide troubleshooting guidance.
