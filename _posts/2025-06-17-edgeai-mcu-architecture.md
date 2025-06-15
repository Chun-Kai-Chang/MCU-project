---
layout: post
title: EdgeAI 回收系統架構說明
date: 2025-06-17
categories: edgeai
author: 張鈞凱
---

本篇說明本專題所設計之 AI-assisted 回收分類系統架構，主要透過 **AMB82-mini** 微控制器，整合多個感測模組與 Google Gemini AI API，實現語音與影像辨識的智慧化回收設備。

---

## 🔧 系統整體架構圖

系統整體如下圖所示，由主控端 AMB82-mini 控制，結合 Vision + RTC + TTS 等模組：

<p align="center">
  <img src="https://github.com/Chun-Kai-Chang/MCU-project/blob/main/assets/img/system-architecture.png?raw=true" width="70%">
</p>

圖中包含模組如下：

- Camera（內建） ➜ 拍照傳送至 Gemini Vision API，回傳辨識結果
- 麥克風 ➜ 錄音後透過 Gemini Speech-to-Text 辨識語音指令
- ILI9341 LCD ➜ 顯示處理結果
- RTC ➜ 提供時間戳記，寫入 SD 卡記錄
- TTS ➜ 回應語音結果
- SD 卡 ➜ 儲存辨識記錄與對應圖片

---

## 🧠 Gemini AI 雲端應用

本系統串接 Google Gemini Vision 與 Gemini Speech 模型：

- **Vision**：用來分析拍攝到的圖像，辨識是否為「瓶子」、「鋁罐」、「紙類」等回收物
- **Speech**：辨識使用者語音指令，例如「這是什麼？」或「儲存照片」

---

## 💬 操作流程摘要

1. 使用者按下觸控或語音觸發
2. 拍照後送至 Vision 模型
3. 同步記錄 RTC 時間，寫入 SD 卡
4. 顯示分類結果於 LCD，播放語音回饋

---

## 📦 小結

EdgeAI 系統融合了 MCU + AI API 的應用，能在嵌入式裝置上實現智慧化分類，是資源回收自動化的一大進步。

