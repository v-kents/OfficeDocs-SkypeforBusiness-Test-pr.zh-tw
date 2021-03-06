﻿---
title: Lync Server 2013：指派位置原則範圍
TOCTitle: 指派位置原則範圍
ms:assetid: e4c66517-c593-4253-b900-7b4dd8bddf2f
ms:mtpsurl: https://technet.microsoft.com/zh-tw/library/JJ205360(v=OCS.15)
ms:contentKeyID: 49292619
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 在 Lync Server 2013 中指派位置原則範圍

 

_**上次修改主題的時間：** 2012-06-06_

如同其他 Lync Server 原則，位置原則可從多種領域等級指派：全域、網站與使用者。但是使用者層級位置原則的領域會與其他 Lync Server 原則的操作方式有些許不同。個別使用者位置原則不只可套用到端點物件 (例如使用者與公共區域電話連絡人物件)，也可套用到 Lync Server 網站。網站是地理位置對應的用戶端子網路群組 (但不一定是整個中央網站或分支網站的所有子網路)。所有連接到網站子網站的用戶端會自動挑出指派到網站的位置原則。若將使用者層級位置原則同時指派到使用者與網站，網站位置原則會優於個別使用者原則設定。

各網站皆有指派的位置原則，且各原則都會接受指派不同的 PSTN 使用方式、通知 URI 與會議 URI 值。

> [!NOTE]  
> 此特殊原則領域行為方式的用處在於，若一個 Office 網站集區的使用者主伺服器瀏覽其他網站且需撥打緊急電話，系統將可套用適用該網站的 E9-1-1 通話路由設定，不論使用者指派的集區或網站為何。


