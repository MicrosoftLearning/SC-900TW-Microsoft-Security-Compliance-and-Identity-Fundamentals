﻿---
lab:
    title: '探索 Microsoft Defender for Cloud'
    module: '單元 3，第 2 課：描述 Microsoft 安全性解決方案的功能：描述 Azure 的安全管理功能'
---

# 實驗：探索 Microsoft Defender for Cloud

## 實驗案例
在此實驗中，您將會探索 Microsoft Defender for Cloud，並了解如何利用 Azure 安全分數來改善組織的安全性狀態。

**預估時間**：30 分鐘

#### 工作 1：在此工作中，您將會完成 Microsoft Defender for Cloud 的導覽。
1.	開啟 Microsoft Edge。在網址列輸入 **portal.azure.com**。

1. 登入管理員認證。
    1. 在登入視窗中輸入 **admin@WWLxZZZZZZ.onmicrosoft.com** (其中 ZZZZZZ 是您的實驗託管提供者提供的唯一租用戶 ID)，然後選取**下一步**。
    1. 輸入應由您的實驗託管提供者提供的管理員密碼。請選取**登入**。
    1. 當提示保持登入狀態時，請選取**是**。

1. 在螢幕左上角的 Microsoft Azure 旁邊，選取 「顯示入口網站功能表」 圖示 (三條水平線，又稱為漢堡圖示)，接著從左側導覽面板的 「我的最愛」 底下選取 「**Microsoft Defender for Cloud**」。  如果該選項未列於 「我的最愛」，請在搜尋方塊中輸入 **Microsoft Defender for Cloud**，然後從結果清單中選取 「**Microsoft Defender for Cloud**」。

1. 留意 Microsoft Defender for Cloud 概觀頁面上顯示的資訊。  

1. 頁面最上方可能會顯示藍色的資訊方塊，告知您可能正在檢視有限的資訊。  請選取**按一下此處**。
    1. 請確保您取得全租用戶的可見性，指派您自己所需的角色。  請選取**安全性管理員**，接著請選取頁面底部的**取得存取權**。
    1. 您可能會看到訊息：根管理群組不存在。  系統將會根據描述為您建立群組。  最久可能需要 15 分鐘才會完成 (但通常更快)。  授與存取權後，選取頁面左上角 「取得權限」 上方的 「**Microsoft Defender for Cloud**」，接著重新整理 Microsoft Defender for Cloud 概觀頁面。

1. 頁面最上方顯示的資訊包含 Azure 訂用帳戶數、已評估資源數、作用中建議數，以及任何安全性警示。  頁面主畫面有一些卡片，代表 「安全分數」、「法規合規性」、「深入解析」、「Azure Defender」 等等。  

1. 請在頁面上方選取**已評估的資源**   (請注意，這相當於在 Microsoft Defender for Cloud 首頁的左側導覽面板上選取 「詳細目錄」)。
    1. 這會將您導覽至 「**詳細目錄**」 頁面，該頁面會顯示您的 Azure Pass 訂用帳戶。  請選取 **Azure Pass – 贊助**。
    1. 「資源健康狀態」 頁面會提供一份建議清單。  在可用的清單上，選取**應有多位擁有者被指派至您的訂用帳戶**。
    1. 選取 「補救步驟」 旁的下拉式箭頭。請注意提供的詳細補救步驟以及採取動作的選項。  
    1. 選取螢幕左上角的 「**Microsoft Defender for Cloud**」，返回 Microsoft Defender for Cloud 概觀頁面。

1. 選取頁面最上方的 「**作用中建議**」   (請注意，這相當於在 Microsoft Defender for Cloud 首頁的左側導覽面板上選取 「建議」)。
    1. 建議頁面會顯示 「安全分數」 儀表板。
    1. 「安全分數」 儀表板下方有控制措施清單。每個安全性控制措施代表應降低的安全性風險，也包含與該控制措施有關的最高分數、目前分數、可能提高的分數以及資源健康狀態的資訊。  
    1. 選取其中一個控制措施，例如**啟用 MFA**。  選取其中一個子項目，例如**應在具有訂用帳戶擁有者權限的帳戶上啟用 MFA**。  在開啟的頁面中，您會看到描述項、補救步驟以及受影響的資源。請選取螢幕右上角的 **X** 離開此頁面。
    1. 請選取螢幕右上角的 **X** 離開建議頁面，退回概覽頁面。

1. 在主頁面中選取 「**法規合規性**」。「法規合規性」 頁面提供合規性控制措施清單。  在每個控制措施下方有一組以 Azure 安全性效能評定為基礎的評量，為您提供在 Azure 上保護雲端解決方案的建議。
    1. 選取 **IM.** (**身分管理**)，然後選取 「**IM-6 使用增強式驗證控制項**」。  此清單會顯示有助於改善合規狀態的客戶責任動作。
    1. 選取螢幕右上角的 「**X**」 關閉頁面，返回 Microsoft Defender for Cloud 概觀頁面。 
    1. 將 Microsoft Defender for Cloud 概觀頁面維持開啟，以便您在下一個工作中使用。


#### 工作 2：在此工作中，您將會瀏覽 Azure 安全分數及探索可改善安全分數的建議。 

1. 在 Microsoft Defender for Cloud 概觀頁面中選取 「**安全分數**」 卡片。
1. 選取 **Azure Pass – 贊助**。  請注意您的安全分數。
1. 在建議頁面中選取 「**實作安全性最佳做法**」，展開清單。請注意，資源健全狀態會呈現為紅色。
1. 選取 「**應有一個以上擁有者指派至您的訂用帳戶**」，此項目會顯示紅色的資源健全狀態。 
1. 在 「**受影響資源**」 下方，確認狀況不良的資源已確實選取或加上底線，然後選取畫面上列出的 Azure 訂用帳戶。
1. 在存取控制 (IAM) 頁面上方，請選取 **+ 新增**，接著在下拉式功能表選取 **新增角色指派**。
    1. 在頁面左側選取 「**擁有者**」 (這應該會是列出的第一個項目)，使該列以灰色醒目提示，然後在頁面底部選取 「**下一步**」。
    1. 選取 「成員」 旁邊的 「**+ 選取成員**」。 
    1. 在螢幕右側開啟的 「選取成員」 視窗中，選取 「**Alex Wilber**」，然後按頁面底部的 「**選取**」。  
    1. 在 「新增角色指派」 頁面中，確認 Alex Wilber 列示為成員，接著在按下 「**檢閱 + 指派**」 後選取 「**下一步**」。
    1. 狀態更新最久可能需要 24 小時，完成後，您的安全分數也會一併更新，同時也會滿足 「管理存取與權限」 群組中的所有項目。
    1. 在頁面左上角的 Azure Pass 上方選取 「**Microsoft Defender for Cloud**」，返回 Microsoft Defender for Cloud 概觀頁面。
1. 讓此頁面維持開啟狀態，以供下一個工作使用。


#### 工作 3：  複習一下，Microsoft Defender for Cloud 提供兩種模式：一種不具備增強的安全性功能 (免費)，另一種透過 Microsoft Defender for Cloud 計畫提供增強的安全性功能。在此工作中，您會了解如何啟用/停用各種 Microsoft Defender for Cloud 計畫。

1.	在 Microsoft Defender for Cloud 概觀頁面中，選取左側導覽面板的 「**環境設定**」。
1. 選取 「租用戶根群組」 旁邊的大於 **>** 符號，加以展開 (請勿直接選取 「租用戶根群組」，這麼做會導向其他頁面)，然後選取 「**Azure Pass - 贊助**」。
1.	在 Defender 計畫頁面，您可以選取 「啟用全部」 或選取個別 Defender 計畫。保留原有的設定，將所有計畫設為關閉。
1.	您現在可以關閉瀏覽器索引標籤，結束 Azure 入口網站。


#### 回顧
在此實驗中，您已了解 Microsoft Defender for Cloud，以並清楚如何利用 Azure 安全分數來改善組織的安全性狀態。