﻿---
title: Lync Server 2013 的 TLS 和 MTLS
TOCTitle: Lync Server 2013 的 TLS 和 MTLS
ms:assetid: b32a5b85-fc82-42dc-a9b2-96400f8cd2b8
ms:mtpsurl: https://technet.microsoft.com/zh-tw/library/Dn481133(v=OCS.15)
ms:contentKeyID: 59679129
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013 的 TLS 和 MTLS

 

_**上次修改主題的時間：** 2013-11-07_

傳輸層安全性 (TLS) 與相互傳輸層安全性 (MTLS) 通訊協定提供網際網路上的加密通訊與端點驗證。Microsoft Lync Server 2013 使用這兩種通訊協定來建立受信任伺服器的網路，並確保經由該網路的所有通訊皆有加密。伺服器之間的所有 SIP 通訊都是透過 MTLS 進行。 用戶端對伺服器的 SIP 通訊則是透過 TLS 進行。

TLS 可讓使用者透過他們的用戶端軟體，驗證所連線的 Lync Server 2013 伺服器。在 TLS 連線中，用戶端會向伺服器要求有效的憑證，若要通過驗證，憑證必須是由同樣受用戶端信任的 CA 核發，而且伺服器的 DNS 名稱必須符合憑證上的 DNS 名稱。如果憑證是有效的，用戶端便可以使用憑證中的公開金鑰來建立一組對稱加密金鑰，以便用於通訊。只有憑證原先的擁有者才能使用其私人金鑰來解密通訊內容。如此所建立的即是受信任的連線，且從此無需再接受其他受信任的伺服器或用戶端盤查。在此環境下，搭配 Web 服務使用的安全通訊端層 (SSL) 可以如 TLS 類型一般產生關聯。

伺服器對伺服器的連線依賴 MTLS 進行相互驗證。在 MTLS 連線中，產生訊息和接收訊息的伺服器會從雙方信任的 CA 來交換憑證。憑證會向彼此證明身分。在 Lync Server 2013 部署中，由企業 CA 發出的憑證只要還在有效期限內，且未遭發出憑證的 CA 撤銷，所有內部用戶端和伺服器就會認定該憑證有效，因為 Active Directory 網域的所有成員皆信任該網域的企業 CA。而在同盟案例中，同盟的雙方都必須信任發行的 CA。每一個合作夥伴可以視需要使用不同的 CA，但該 CA 也必須受到對方合作夥伴的信任。Edge Server 的受信任的根 CA 中若有合作夥伴的根 CA 憑證，或是雙方使用受雙方信任的第三方 CA 時，最容易建立此信任。

TLS 和 MTLS 可協助避免竊聽和攔截式攻擊。在攔截式攻擊中，攻擊者會在兩個網路實體不知情的情況下，透過攻擊者的電腦重新路由雙方之間的通訊。受信任伺服器 (僅限 拓撲產生器 中指定者) 的 TLS 和 Lync Server 2013 規格可部分減緩應用程式層級的攔截式攻擊風險，方法是在兩個端點之間使用公開金鑰密碼編譯來進行端對端的加密。因此，攻擊者需擁有含有相對應私密金鑰的有效且受信任的憑證，且該憑證是發給用戶端通訊目標的服務名稱，才能將通訊解密。然而，您還是必須遵循您網路基礎架構的最佳安全性措施 (在此案例中為公司 DNS)。Lync Server 2013 會假設 DNS 伺服器會以網域控制站和通用類別目錄受信任的相同方式受到信任，但 DNS 確實會防止攻擊者的伺服器成功回應向假名發出皂要求，針對 DNS 挾持攻擊提供一層保護。

下方圖表詳細說明 Lync Server 2013 如何使用 MTLS 來建立受信任伺服器的網路。

**Lync Server 網路中受信任的連線**

![MTLS 的使用](images/Dn481133.437749da-c372-4f0d-ac72-ccfd5191696b(OCS.15).jpg "MTLS 的使用")

