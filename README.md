# C 实战练习场（学完课程后的多文件工程模板）

现代 C 工程配置示例：**C23 + CMake 4 + Ninja + clangd + GDB**，VS Code 里直接跑。

## 用法

1. VS Code 打开本文件夹（首次会自动提示选 preset 配置）
2. `Ctrl+Shift+P` → `CMake: Configure`（选 default preset）
3. `F7` 构建，`F5` 调试，右上角 Code Runner 可快速单文件运行

## 组件

- `CMakeLists.txt`：C23 标准、`-Wall -Wextra -Wpedantic`、导出 compile_commands.json
- `CMakePresets.json`：固定 GCC 16 (ucrt64) + Ninja，和 CI 一致
- `.clangd`：clangd 读取 build/ 下的编译数据库，补全/跳转/静态检查
- `.vscode/settings.json`：clangd 格式化、Code Runner 一键运行

## 常用命令

```bash
cmake --preset default          # 配置
cmake --build --preset default  # 构建
./build/demo.exe                # 运行
```

新增源文件：在 `src/` 下加 `.c`，然后 `add_executable` 或在 CMakeLists 里加进 `target_sources`。
