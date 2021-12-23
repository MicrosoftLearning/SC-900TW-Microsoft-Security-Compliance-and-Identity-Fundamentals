﻿---
Pre-Demo Setup:
    title: '示範設定'
---

# 預先示範設定：

### 設定第 1 部分 - 兌換 Azure Pass
在此設定工作中，您將使用與 Microsoft 365 租用戶相同的認證兌換 Azure Pass。  這將有助於在 Microsoft 365 和 Azure 之間移動時取得更順暢無礙的體驗。

1. 如果您有任何已開啟的瀏覽器視窗，建議您關閉所有瀏覽器。

1. 按右鍵 Microsoft Edge 圖示，然後選取**新的 InPrivate 視窗**以開啟新的 In-Private 瀏覽器工作階段。其他 

1. 在網址列輸入 **www.microsoftazurepass.com**

1. 選取**開始**按鈕以開始使用。

    1. 在登入視窗中輸入電子郵件 **admin@WWLxZZZZZZ.onmicrosoft.com** (其中 ZZZZZZ 是您的實驗託管提供者提供的唯一租用戶 ID)，然後選取**下一步**。
    1. 輸入應由您的實驗託管提供者提供的管理員密碼。請選取**登入**。如果提示保持登入狀態時，請選取**是**。
    1. 如果已列出正確的電子郵件地址，請選取**確認 Microsoft 帳戶**。
    1. 在推廣優惠代碼方塊中輸入推廣優惠代碼，然後按一下**索取推廣優惠代碼**。  
    1. 在「您的個人資料」頁面，保留所有預設資訊，選取**本人同意訂閱協議、優惠詳細資訊和隱私權聲明。**然後選取**登入**。
    1. 如果問卷視窗已開啟，您可以選取透過選取 **X** 將其關閉，或者視需要作出回應並選取**提交**。

1. 啟動帳戶可能需要幾分鐘的時間。  啟動後，會將您導向 Azure 入口網站首頁。歡迎使用 Microsoft Azure 視窗將開啟，請選取**稍後再說**。您可能會看到快顯視窗「使用個人化建議最佳化雲端工作負載」，請選取視窗右上角的 **X**。

1. 持續開啟 Azure 入口網站首頁的瀏覽器索引標籤，您將在下一個示範中返回。

### 設定第 2 部分 - 啟用 Microsoft 365 稽核記錄
在此設定工作中，您將在 Microsoft 365 中啟用稽核記錄功能。  儘管文件表明預設情況下會啟用稽核記錄，但大多數實驗租用戶並未啟用此功能，並且可能需要幾個小時才會生效。  啟用此功能是有效益的，因為 Microsoft 365 使用稽核記錄來獲取原則和分析洞察中識別的使用者洞察和活動。

1. 開啟 Microsoft Edge。在網址列輸入 **admin.microsoft.com**。

1. 登入管理員認證。
    1. 在登入視窗中輸入 **admin@WWLxZZZZZZ.onmicrosoft.com** (其中 ZZZZZZ 是您的實驗託管提供者提供的唯一租用戶 ID)，然後選取**下一步**。
    1. 輸入應由您的實驗託管提供者提供的管理員密碼。請選取**登入**。
    1. 當提示保持登入狀態時，請選取**是**。這將帶您前往 Microsoft 365 系統管理中心頁面。

1. 從 Microsoft 365 系統管理中心的左側導覽窗格中，選取**顯示全部**。

1. 在系統管理中心下，請選取**合規性**。  全新瀏覽器頁面將開啟前往至 Microsoft 365 合規性的歡迎頁面。  

1. 從 Microsoft 365 系統管理中心的左側導覽面板中，選取**顯示全部**。

1. 從左側導覽面板的解決方案下，選取**稽核**。  請注意：還可以透過 Microsoft 365 Defender 首頁存取稽核功能。

1. 驗證是否已選取**搜尋**索引標籤 (已畫底線)。

1. 一旦進入稽核頁面後，請稍等 2-3 分鐘。  如果未啟用稽核，您將在頁面頂部看到藍色列，上面寫著開始記錄使用者和管理活動。  請選取**開始記錄使用者和管理活動**。  啟用稽核後，藍色列則會消失。  如果藍色列不存在，則表示已啟用稽核，無需進一步動作。

1. 從左側導覽面板中選取**首頁**，退回 Microsoft 365 合規性中心的首頁。

### 回顧

在此設定工作中，您已使用與 Microsoft 365 租用戶相同的認證兌換 Azure Pass。  您也啟用了 Microsoft 365 中的稽核記錄功能。

