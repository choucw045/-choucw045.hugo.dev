---
title: "VS Code Debugger for Rust Setup Notes."
date: 2022-06-16T03:50:53+08:00
# draft: true
toc: false
image: ""
tags: ["rust"]
categories: ["develop"]
---

## Instructions

1. Install extensions below:
```
rust-analyzer (rust-lang.rust-analyzer)
Microsoft C++ (ms-vscode.cpptools) (for Windows)
CodeLLDB (vadimcn.vscode-lldb) (for Unix-like OS)
```

2. Add breakpoints
3. Press Debug button | launch ```rust-analyzer: debug```


## Problems I encountered

### launch.json not automatically created
After a correct installing, ```launch.json``` should be created at the first time running debugger.

If VS Code warned that you didn't have a corresponding debugger extension, the reason might be that you installed a C++ extension not compatitive to your OS.

### Can't add breakpoints

Enable this option in VS Code preference: ```Debug: Allow breakpoints everywhere```.

### Program executed correctly but didn't hit the breakpoint

Current workspace path might contain a symbolic link, while rust compiler will replace symbolic link as real path, thus the breakpoints are missed. Detailed information can be found in reference [1].

There are two ways to handle this situation:
1. Open folder by real path
2. Insert corresponding ```sourceMap``` section in ```launch.json```.
```
{
  "type": "lldb",
  ...
  "sourceMap": {
    "<original-path>": "<symlinked-path>"
  }
}
```


## References
[1] https://blog.dbrgn.ch/2020/12/20/rust-vscode-lldb-breakpoints-not-working/