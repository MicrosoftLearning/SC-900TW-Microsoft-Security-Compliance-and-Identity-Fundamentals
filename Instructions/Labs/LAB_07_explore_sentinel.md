---
lab:
    title: '探索 Microsoft Sentinel'
    module: '單元 3，第 3 課：描述 Microsoft 安全性解決方案的功能：描述 Microsoft Sentinel 的安全性功能'
---


# 實驗：探索 Microsoft Sentinel 

## 實驗案例
在本實驗中，您將逐步說明 Microsoft Sentinel 執行個體的建立流程。  您也會設定權限，確保您能順暢存取即將部署以支援 Microsoft Sentinel 的資源。  完成基本設定後，您會逐步介紹將 Microsoft Sentinel 連線至資料來源的步驟，並使用內建的分析功能，取得任何可疑內容的通知，最後您還會探索自動化功能。  

  

**預估時間**：30-45 分鐘

#### 工作 1：  建立 Microsoft Sentinel 執行個體。

1. 開啟 Microsoft Edge。在網址列輸入 **portal.azure.com**。

2. 登入管理員認證。
    1. 在登入視窗中輸入 **admin@WWLxZZZZZZ.onmicrosoft.com** (其中 ZZZZZZ 是您的實驗託管提供者提供的唯一租用戶 ID)，然後選取**下一步**。
    
    1. 輸入應由您的實驗託管提供者提供的管理員密碼。請選取**登入**。
    1. 當提示保持登入狀態時，請選取**是**。

3. 在螢幕左上角的 Microsoft Azure 旁邊，請選取 「顯示入口網站功能表」 圖示 (三條水平線，又稱為漢堡圖示)，接著選取**所有服務**。  

4. 在篩選服務方塊中輸入 **Microsoft Sentinel**，然後從清單中選取 「**Microsoft Sentinel**」。

5. 在 Microsoft Sentinel 頁面上選取 「**建立 Microsoft Sentinel**」。

6. 在 「新增 Microsoft Sentinel 到工作區」 頁面上選取 「**建立新工作區**」。

7. 在建立 Log Analytics 工作區的基本索引標籤中，輸入以下內容：
    1. 訂用帳戶：  **Azure Pass – 贊助**
   
    1. 資源群組：請選取**建立新的**，並輸入名稱 **SC900-ResourceGroup**，然後選取**確定**。
    1. 名稱：**SC900-LogAnalytics-workspace**。
    1. 區域：**美國西部** (保留預設值)
    1. 請選取**下一步：定價層 >**

8. 對於定價層，保留預設值設定：**隨用隨付 (每 GB 2018)**，然後選取**下一步**：**標記 >**。

9. 對於標記，您可以將其留為空白，然後選取**檢閱 + 建立**。

10. 驗證您所輸入的資訊，然後選取**建立**。

11. 如果您未看到已列出的新工作區，請選取**重新整理**，然後選取**新增**。

12. 新增工作區後，畫面上會隨即顯示 Microsoft Sentinel | 最新消息和指南頁面。  請注意開始使用頁面上所列出的三個步驟。

13. 請保持此頁面開啟，您將在下個工作中使用它。

#### 工作 2：  建立 Microsoft Sentinel 執行個體後，您需要確保為支援 Microsoft Sentinel 而部署的資源具有必要的存取權限。  在這個工作中，您將前往使用 Microsoft Sentinel 執行個體所建立資源群組的存取控制 (IAM) 頁面，檢視可供使用的角色，並為自己 (MOD 管理員) 指派所需角色。在資源群組層級指派角色，可確保該角色套用至為支援 Microsoft Sentinel 而部署的所有資源。

1. 在 Microsoft Sentinel 頁面左上角，從 Microsoft Sentinel 的上方選取 「**所有服務**」。

2. 在篩選服務方塊中輸入「資源群組」，然後從提供的清單中選取 「**資源群組**」。

3. 在 「資源群組」 頁面中選取您使用 Microsoft Sentinel 建立的資源群組 **SC900-ResourceGroup**。

4. 在 SC900-ResourceGroup 頁面中，從左側導覽面板中選取**存取控制 (IAM)**。

5. 從存取控制頁面，請選取**檢視我的存取權**。  請注意，目前角色為安全性管理員。  透過選取視窗右上角的 **X** 關閉 MOD 管理員指派視窗。

6. 在存取控制頁面中，請選取 **+ 新增**，然後選取**新增角色指派**。

7. 新增角色指派視窗已開啟。  在選取角色欄位中選取下拉式箭頭以顯示可提供使用的角色。  對於此實驗，請選取**擁有者**。  備註：  作為最佳做法，您應該為角色指派最少的權限。  如需相關的參考資訊，請檢視 Microsoft Sentinel 中的權限：  https://docs.microsoft.com/zh-tw/azure/sentinel/roles

8. 從顯示的使用者清單中，請選取 **MOD 管理員**。

9. 請選取頁面底部的**儲存**。

10. 在存取控制頁面中，請選取**檢視我的存取權**以確認已新增角色，然後透過選取視窗右上角的 **X** 關閉視窗。

11. 透過從頁面左上角選取**所有服務**，其上方顯示為資源群組，退回至 Azure 的所有服務頁面。

#### 工作 3：  在此工作中，您將逐步說明將 Microsoft Sentinel 連線至資料來源，以開始收集資料的流程。注意：顯示連接器的連線狀態可能需要一些時間 (約 30 分鐘，實際時間取決於租用戶)。

1. 在 「所有服務」 頁面的 「篩選服務」 方塊中輸入 **Microsoft Sentinel**，然後從結果清單中選取 「**Microsoft Sentinel**」。 

2. 在 Microsoft Sentinel 頁面上選取您使用 Microsoft Sentinel 執行個體建立的工作區 **SC900-LogAnalytics-workspace**。

3. 使用 Microsoft Sentinel 的第一步是要能收集資料。在左側導覽面板中，從設定底下所列的項目中選取**資料連接器**。

4. 從資料連接器頁面，向下捲動主要視窗以檢視可用連接器的擴充清單。在資料連接器頁面的搜尋方塊中，輸入 **Azure**，然後從清單中選取 **Azure Active Directory**。

5. Azure Active Directory 連接器視窗已開啟。  請選取 **Open Connector 頁面**。

6. 在 Azure Active Directory 連接器頁面中，請檢閱說明並記下相關內容，其中包括活頁簿、查詢和分析規則範本。  

7. 主要視窗中的指示索引標籤會提供 Microsoft Sentinel 與 Azure Active Directory 整合的先決條件。   在設定底下選取 「**登入記錄**」，然後選取 「套用變更」 (可選擇多個連接器)。

8. 在下一步索引標籤中，請記下建議的活頁簿清單。   在建議的活頁簿下，請選取 **Azure 登入記錄** (可以選取其他活頁簿)。

9. 從活頁簿頁面並選取範本索引標籤 (已畫底線)，請選取 **Azure 登入記錄**。 

10. 從以開啟的 Azure AD 登入記錄視窗中，檢閱說明然後選取**檢視範本**。  透過選取螢幕右上角的 **X** 退出範本。  從頁面底部選取**儲存**，然後選取**確定**將活頁簿儲存至預設位置。

11. 在 「活頁簿」 頁面的左上角，選取 「活頁簿」 上方的 「**Microsoft Sentinel**」。您會隨即返回 Microsoft Sentinel 的 「資料連接器」 頁面。

12. 資料連接器頁面的頂部應該會顯示 1 個連接器已連線，以反映您現在已連線至 Azure Active Directory。

13. 從左側導覽面板，請選取**活頁簿**。

14. 從活頁簿頁面中，請選取搜尋方塊上方的**我的活頁簿**索引標籤。  您剛剛儲存的活頁簿已列出，並且可供您檢視和監視資料。

15. 請保持此頁面開啟，您將在下個工作中使用它。

#### 工作 4：  在此工作中，您將逐步了解使用內建分析規則範本建立規則以在發生可疑事件時取得通知的流程。

1. 從左側導覽面板，請選取**分析**。

2. 分析頁面將顯示活動規則 (預設情況下啟用進階多階段攻擊偵測)，並提供對規則範本的存取。  請選取**規則範本**索引標籤。  請注意可用範本的清單以及篩選清單的不同方法。  只要使用 Microsoft Sentinel 工作區中的內建分析警示，就能在出現任何可疑活動時收到通知。

3. 在搜尋列中輸入 **Azure 入口網站**。  請選取**嘗試登入 Azure 入口網站失敗**。  

4. 從開啟的視窗中，閱讀說明並檢閱與範本相關的資訊。  請選取頁面底部的**建立規則**。

5. 從分析規則精靈中，檢閱資訊，然後選取**下一步：設定規則邏輯 >**。

6. 設定規則邏輯頁面為定義新分析規則邏輯的位置。範本已經提供一些邏輯和預先定義的設定。  滾動頁面以查看可用設定。  保留預設值。請選取**下一步：事件設定 (預覽)>**。

7. 透過 「事件設定」，您可以將 Microsoft Sentinel 警示分組，將其彙整為應查看的事件。您可以設定此分析規則觸發的警報是否應該產生事件。  保留預設值設定，並選取**下一步：自動回應 >**。

8. 在自動回應索引標籤中，請注意如何新增劇本以進行自動回應。  同樣，您可以建立事件自動化規則。  在事件自動化下，請選取 **+ 新增**新的。  建立新自動化規則的視窗已開啟。  您在此頁面上建立的任何自動化規則都會由您正在使用的分析規則觸發。請注意，您可以為該規則新增條件和設定動作。   請選取**取消**以退出視窗。

9. 請選取**下一步：檢閱 >** 以檢閱與規則關聯並基於所選範本的所有詳細資料。此時，您可以透過選取建立以**建立**規則，或透過選取頁面右上角的 **X** 退出而不建立規則。

10. 請保持此頁面開啟，您將在下個工作中使用它。

#### 工作 5：  在上一個工作中，您已建立分析規則，以提醒可疑活動。  該精靈中內嵌基於特定規則自動回應事件的選項。  但是您也可以透過直接前往自動化設定選項來建立自動化規則。

1. 從左側導覽面板，請選取**自動化**。  

2. 請選取 **+ 建立**。從下拉式備註中選取如何新增新劇本或新增新規則。  請選取**新增新規則**。  

3. 建立新自動化規則的視窗已開啟。  請注意，您可以為規則新增條件和設定動作。  唯一的區別是第一個條件為關聯要套用此自動化規則的分析規則。  在上一個工作中，此選項顯示為灰階而無法使用，因為當時您正在為特定規則設定自動化功能。  請選取**取消**以退出建立新的自動化規則視窗。

4. 請保持此頁面開啟，您將在下個工作中使用它。


#### 工作 6：  刪除 Microsoft Sentinel 資源群組。  Microsoft Sentinel 會根據 Microsoft Sentinel 中實際用於分析作業的資料量來收取費用。儘管此實驗擷取的資料量很少，但建議您在探索完 Microsoft Sentinel 的功能後，刪除 Microsoft Sentinel 資源群組。

1. 在 Microsoft Sentinel 頁面左上角，從 Microsoft Sentinel 的上方選取 「**所有服務**」。

2. 在篩選服務方塊中輸入「資源群組」，然後從提供的清單中選取 「**資源群組**」。

3. 在 「資源群組」 頁面中選取您使用 Microsoft Sentinel 建立的資源群組 **SC900-ResourceGroup**。

4. 從頁面最上方的中間位置選取 「**刪除資源群組**」。  檢閱警告。  輸入資源群組名稱 **SC900-ResourceGroup**，然後從頁面底部選取**刪除**。  刪除資源群組需要幾分鐘的時間。

5. 驗證資源群組已刪除後，請關閉瀏覽器頁面。 


#### 回顧

在本實驗中，您已逐步說明 Microsoft Sentinel 執行個體的建立流程。  您也已設定權限，確保能順利存取與 Microsoft Sentinel 執行個體相關聯的資源。  建立 Microsoft Sentinel 執行個體後，您逐步講解將 Microsoft Sentinel 連線至資料來源的步驟，並使用內建的分析規則，取得任何可疑內容的通知，最後還探索了自動化功能。最後您刪除與所建立 Microsoft Sentinel 執行個體相關聯的資源群組，為此實驗畫下句號。
