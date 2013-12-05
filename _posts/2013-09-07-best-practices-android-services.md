---
layout: post
title: Android 应用开发最佳实践-Services篇
---

+ 应该在 Activity 的 onStart() 和 onStop() 中对 Service 进行 binding 和 unbinding

+ 多数情况下，我们只需要在相同的进程中使用 Service 即 local service，而这种情况下和 bound service 通信只要扩展 Binder class。所以扩展 Binder class 是最常用的方式。

+ 当需要在单独进程中运行 Service 时，优先选用 Messenger 的方式和 bound service 通信，只有在需要多线程的时候才需要使用 AIDL 的方式。（实际上 Messenger 的底层也利用了 AIDL，但是它将所有请求都放到消息队列里了，避免了多线程，因此比 AIDL 更简单）
