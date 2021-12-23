﻿---
Demo:
    title: 'Azure 原則'
    module: '單元 4，第 5 課：描述 Microsoft 合規性解決方案的功能：描述 Azure 原則'
---


# 示範：Azure 原則

### 示範案例
在本示範中，您將逐步了解設定 Azure 原則的流程，以及此原則的影響。

#### 示範第 1 部分：建立一個原則以要求資源群組上的標籤 (顯示從範本建立原則的步驟)

1. 開啟 Microsoft Edge。在網址列輸入 **portal.microsoft.com**。  您應該已經登入，若無則請用管理員認證登入。

1. 請在頁面上方寫著 Microsoft Azure 旁邊的藍色列搜尋方塊中輸入 **policy**，並從搜尋結果中選取**原則**。

1. 您現在位於 「原則」 概覽頁面。注意在儀表板中的可用資訊。

1. 在左側導覽面板的 「製作」 下方，選取**作業**。  您將會看到已有一個原則設定，選取 **ASC 預設**。  檢閱描述欄位。注意：描述欄位會參照「Azure 資訊安全中心」(已重新命名為 Microsoft Defender for Cloud)。  選取頁面右上角的 **X**，返回 「原則指派」 頁面。

1. 請在頁面上方選取**指派原則**。

1. 指派原則精靈將啟動，引導管理員進行指派原則的流程。  選取 「原則」 定義欄位旁邊的**省略符號**。  提供可用的原則定義清單。  

1. 在搜尋列輸入**標籤**。

1. 在搜尋結果中選取**需要資源群組標籤** (可能需要往下捲動)，再按一下**選取**。  注意：此原則的功用是拒絕建立任何不符合要求的新資源群組。  

1. 請注意預設指派的名稱。  保留該名稱，並在頁面下方選取**下一步**。

1. 在 「標籤」 名稱欄位輸入**環境** (資源群組將需要環境標籤)，再選取**下一步**。  

1. 在 「補救」 索引標籤中閱讀描述項，請勿變更設定。選取**下一步**

1. 在非合規性訊息中，輸入**需要環境標籤**，再選取**下一步**。請注意：若資源群組在原則指派前建立且沒有環境標籤，將出現此非合規性原因的訊息。  如果在建立原則後建立資源群組，如果沒有環境標籤，資源群組的建立會遭到拒絕。

1. 檢閱原則指派情形，接著選取 「建立」。  如果未立即出現原則，請選取**重新整理**。備註：原則可能需要長達 30 分鐘才會生效。

1. 選取螢幕右上角的 「**X**」，離開 「原則指派」 頁面。

1. 您現在在 Azure 服務首頁。  保持此頁面開啟，將會在下一個工作中使用。

#### 示範第 2 部分：  建立無標籤的資源群組，再加上標籤進行修正，展示原則的影響。

1. 在頁面上方的 「Azure 服務」 字樣下方選取**資源群組**。如果未列出選項，請在搜尋列中輸入 「資源群組」 後，在該處選取。

1. 請在頁面左上角選取 **+ 建立**。

1. 在 「建立資源群組」 的 「基本」 索引標籤中，讓 「訂閱」 欄位維持原本的設定，亦即 「Azure Pass - 贊助」。

1. 在 「資源群組」 欄位中輸入 **SC900-Labs**。

1. 將 「區域」 設定保持預設狀態，再選取**下一步：標籤**

1. 標籤名稱與值的欄位保持空白。  請勿填寫，再選取**審閱 + 建立**。

1. 您將會看到通過的驗證 (標籤名稱與值不是精靈的必要欄位)，再選取**建立**。

1. 您會看到螢幕上方出現失敗訊息：「無法建立資源群組。檢視錯誤詳細資料。」  選取**檢視錯誤詳細資料**。未達成部分 Azure 原則的條件，因此資源群組建立是基於非合規性原因而遭到封鎖。備註：如果您沒有看到失敗訊息，並且已建立資源群組，這是因為原則尚未生效。  前往 「原則」 頁面，找到您在先前的工作中建立的原則。原則生效後，您就會看到該資源不符合規範。  詳細資料頁面將顯示非合規性訊息。

1. 錯誤摘要會顯示錯誤類型，指出「原則不允許資源『SC900-Labs』」。  請選取螢幕右上角的 **X** 關閉此視窗。

1. 在建立資源群組的視窗，選取 **<上一頁**。

1. 您已回到建立資源群組的標籤頁面。  在 「名稱」 欄位中輸入「環境」，在 「值」 欄位輸入 **SC900-Labs** 後，選取 「**下一步：檢閱 + 建立 >**」。

1. 驗證標籤並選取**建立**。

1. 您將會看到列出的資源群組。  因為資源群組提供標籤，所以滿足部分 Azure 原則的條件。  資源群組符合原則的規範。

#### 回顧

在本示範中，您已了解設定 Azure 原則的流程，以及此原則的影響。