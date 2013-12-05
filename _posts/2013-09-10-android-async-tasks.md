---
layout: post
title: Android 中执行异步任务
---


## 结论

由于人往往容易浮躁，那就先写结论。


### 最概括的结论
+ 将一切（可能）耗时的操作都在非主（UI）线程中异步执行;
+ 尽可能以单线程来执行异步任务以简化实现。


### 具体的结论

耗时操作分为
+ IO（常见，如数据库，网络）
+ CPU（不常见，耗时的运算）

异步执行任务的解决方案
+ AsyncTask
+ CursorLoader
+ AsyncQueryHandler
+ IntentService
+ 自定义 worker Thread

异步执行任务的 Best Practices
+ 对于数据库的访问（以 ContentProvider 的方式）应该使用 CursorLoader 和 AsyncQueryHandler 来异步执行
+ 对于其他需要伴随用户交互界面的耗时操作通常使用 AsyncTask 来异步执行
+ 对于需要在没有用户交互界面的时候进行的耗时操作可以使用 IntentService
+ 在以上方法都不能满足需求的情况下才考虑用自定义的 Thread 来异步执行任务


### 结论背后的细节

异步执行任务方案的细节统计

<table>
    <tr>
        <th>Solution</th>
        <th>Threading</th>
        <th>Thread Name</th>
        <th>Cancel Before Start</th>
        <th>Cancel In Progress</th>
    </tr>
    <tr>
        <td>AsyncTask</td>
        <td>Single (default)</td>
        <td>AsyncTask # (1, 2, 3...)</td>
        <td>true</td>
        <td>true</td>
    </tr>
    <tr>
        <td>CursorLoader</td>
        <td>Multiple</td>
        <td>AsyncTask # (1, 2, 3...)</td>
        <td>true</td>
        <td>true</td>
    </tr>
    <tr>
        <td>AsyncQueryHandler</td>
        <td>Single</td>
        <td>AsyncQueryHandler</td>
        <td>true</td>
        <td>false</td>
    </tr>
    <tr>
        <td>IntentService</td>
        <td>Single (for each service)</td>
        <td>IntentService["name"]</td>
        <td>false</td>
        <td>false</td>
    </tr>
</table>

