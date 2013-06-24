---
layout: post
title: Intent Flags 和 Activity Launch Modes
---

### Intent.FLAG_ACTIVITY_CLEAR_TASK
只能和 FLAG_ACTIVITY_NEW_TASK 结合使用。会 activity 原来的栈，并启动新的栈，成为新栈的 root activity???

### FLAG_ACTIVITY_RESET_TASK_IF_NEEDED
设置此 flag，要么在一个新的 task 中启动 activity，要么将一个已存在的 task 放到顶部。...?
