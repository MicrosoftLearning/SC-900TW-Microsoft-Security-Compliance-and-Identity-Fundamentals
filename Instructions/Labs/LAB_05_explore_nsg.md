---
lab:
    title: '探索 Azure 網路安全性群組 (NSG)'
    module: '單元 3，第 1 課：描述 Microsoft 安全性解決方案的功能：描述 Azure 的基本安全功能。'
---


# 實驗：探索 Azure 網路安全性群組 (NSG)。

## 實驗案例
在本實驗中，您將探索 Azure 中的網路安全性群組的功能。  您將透過建立不需要任何網路安全性群組 (NSG) 的 VM 來進行。  在沒有任何篩選流量的 NSG 的情況下，VM 中所有連接埠皆披露於公共網際網路中。  然後，您將完成建立 NSG 並將 VM 的介面指派給 NSG 的流程。  設定完成後，您將使用預設的 NSG 規則以及您將建立的規則測試與 VM 的連線。
  

**預估時間**：15-20 分鐘

#### 工作 1：  在本工作中，您將建立 Windows 10 虛擬機器。    
1.	開啟 Microsoft Edge。  在網址列輸入 **portal.azure.com**。

1. 登入管理員認證。
    1. 在登入視窗中輸入 **admin@WWLxZZZZZZ.onmicrosoft.com** (其中 ZZZZZZ 是您的實驗託管提供者提供的唯一租用戶 ID)，然後選取**下一步**。

    1. 輸入應由您的實驗託管提供者提供的管理員密碼。請選取**登入**。
    1. 當提示保持登入狀態時，請選取**是**。
1. 在螢幕左上角的 Microsoft Azure 旁邊，請選取 [顯示入口網站功能表] 圖示 (三條水平線，又稱為漢堡圖示)，接著選取**所有服務**。  
1. 在主視窗的 [功能] 下方，請選取 [虛擬機器]。  如果未列出 [虛擬機器]，請在搜尋列中輸入，接著在搜尋結果選取。
1. 從頁面左上角，選取 **+ 建立**，然後選取 **+ 虛擬機器**。
1. 在基本索引標籤中，填寫以下資訊 (對於未列出的內容，保留預設設定)：
    1. 訂用帳戶：驗證預設設定為 Azure Pass – 贊助。

    1. 資源群組：  請選取**建立新群組**，然後在名稱欄位中輸入 **LabsSC900-RG**，然後選取**確定**。
    1. 虛擬機器名稱：  輸入 **SC900-WinVM**。
    1. 映像：  從下拉式清單中，請選取 **Windows 10 Pro，版本 20H2 – Gen 1**。
    1. 大小:  從下拉式清單中選取**查看所有尺寸**，然後選取 **B2s**，然後按下頁面底部的**選取**。
    1. 使用者名稱：  輸入 **AzureUser**。
    1. 密碼：  輸入 **SC900AzureLabs**。
    1. 公用輸入連接埠：  請選取**無**。
    1. 授權：  請選取**本人確認擁有符合條件具有多租用戶託管權限的 Windows 10 授權**，以便方塊中出現核取記號。
    1. 請選取**下一步：磁碟**。 
1. 您現在位於 VM 設定的 [磁碟] 索引標籤中。  將所有設定保留為預設值，然後選取**下一步：網路 >**。
1. 您現在位於 VM 設定的網路索引標籤中。  填寫以下資訊 (對於未列出的內容，保留預設設定)：
    1. NIC 網路安全性群組：  請選取**無**。

    1. 請選取**下一步：  管理 >**。
1. 您現在位於 VM 設定的 [管理] 索引標籤中。  將所有設定保留為預設值，然後選取**下一步：進階 >**。
1. 您現在位於 VM 設定的 [進階] 索引標籤中。  將所有設定保留為預設值，然後選取**下一步：標記 >**。
1. 您現在位於 VM 設定的 [標記] 索引標籤中。  將所有設定保留為預設值，然後選取**下一步：檢閱 + 建立 >**。
1. 檢閱 VM 的設定。  需注意以下幾點：此 VM 有公共 IP 位址，沒有 NIC 網路安全性群組。  從安全性角度來看，這會讓 VM 暴露在外。  我們將在後續任務中解決此問題。請選取 [建立]。  完成 VM 部署可能需要幾分鐘的時間。
1. 請注意網路介面的名稱為 **sc900-winvmXXX** (XXX 將特定於 VM 的網路介面)。
1. VM 部署完成後，請選取**前往資源**。
1. 您現在位於 SC900-WinVM 頁面。  請注意公共 IP 位址。 
1. 請選取頁面上方的**連線**，接著在下拉式功能表選取 **RDP**。
1. 驗證 IP 位址是否設定為公共 IP 位址，保留預設連接埠編號並選取**下載 DRP 檔案**。 
1. 開啟已下載的檔案並選取**連線**。 
1. 將提示您輸入認證。  請輸入 **AzureUser** 作為使用者名稱。  請輸入 **SC900AzureLabs** 作為密碼。 
1. 遠端桌面連線視窗開啟，顯示無法驗證遠端電腦的身分識別。  仍要繼續連線？  請選取**是**。
1. 您現在已連線至剛剛建立的 Windows VM。請依照提示完成 Windows 設定。儘管您透過 RDP 和常用的 RDP 連接埠連線至 VM，但此 VM 的所有連接埠都已開啟，並且沒有篩選流量內容。 
1. 透過選取顯示 IP 位址的頁面頂部中心的 **X**，關閉遠端桌面連線。  快顯示窗顯示您的遠端工作階段將會中斷連線。請選取**確定**。
1. 您現在將退回 Azure 入口網站中的 SC900-WinVM 頁面。  保持此瀏覽器索引標籤處於開啟狀態，以供下一個工作使用。

#### 工作 2：  建立網路安全性群組，將 VM 的網路介面指派給 NSG。

1. 在瀏覽器上開啟 [SC900-WinVM – Microsoft Azure] 索引標籤。

1. 在頁面左上角的 Microsoft Azure 旁，請選取 [顯示入口網站功能表] 圖示 (三條水平線，又稱為漢堡圖示)，接著選取**所有服務**。
1. 在 [所有服務] 旁邊的 [篩選服務] 方塊中，輸入**網路安全性群組**，然後從結果中選取**網路安全性群組** (請勿選取 [網路安全性群組傳統版])。
1. 從網路安全性群組頁面的頂部，選取 **+ 建立**。
1. 在建立網路安全性群組頁面的基本索引標籤上，指定下列設定：
    1. 訂用帳戶：  Azure Pass – 贊助

    1. 資源群組：  **LabsSC900**
    1. 名稱：  **NSG-SC900**
    1. 區域：  保留預設值 **(US) 美國東部**
    1. 請選取**檢閱 + 建立**然後選取**建立**。
1. 部署完成後，請選取**前往資源**。
1. 請注意 NSG 中的預設輸入和輸出規則。  雖然已建立 NSG，且有篩選流量的預設規則，但是沒有與 NSG 關聯的介面，所以 VM 仍易受攻擊，因為所有連接埠皆揭露於公共網際網路。
1. 從 NSG-SC900 頁面左側導覽窗格中的設定下，請選取**網路介面**。
1. 請選取 [搜尋] 方塊上方的 **+ 關聯**。
1. 在關聯網路介面頁面中，請選取 **sc900-winvmXXX** (XXX 將特定於 VM 的網路介面)。  當介面已進行關聯時，您將在螢幕右上角看到通知方塊。
1. 一旦介面與 NSG 關聯，它就會顯示在清單上。
1. VM 介面與網路安全性群組及預設 NSG 規則產生關聯後，任何試圖連線至 VM 的動作都會失敗。  
1. 請選取頁面左上角的**所有服務**，接著請選取 [功能] 下方的**虛擬機器**。
1. 從虛擬機器頁面中，請選取 **SC900-WinVM**。
1. 從 **SC900-WinVM** 頁面的頂部，請選取**連線**，然後選取 **RDP**。
1. 驗證 IP 位址是否設定為公共 IP 位址，保留預設連接埠編號並選取**下載 DRP 檔案**。
1. 開啟已下載的檔案並選取**連線**。
1. 在嘗試連線幾秒鐘後，您將看到連線失敗訊息，其表明遠端桌面無法連線至遠端電腦。  請選取**確定**。

#### 工作 3：在此工作中，您將會利用 RDP 在連接埠 3389 上建立允許輸入流量的 NSG 規則。  您將會接著使用 RDP 試圖連線至 VM 以測試該規則。 

1. 在瀏覽器上開啟 [SC900-WinVM – Microsoft Azure] 索引標籤。

1. 從左側導覽面板的設定下，選取**網路**。
1. 選取 [輸入連接埠規則] 索引標籤後，您將會看到預設的輸入規則。您無法移除預設規則，但可以建立優先順序更高的規則來覆寫。在頁面的右側，請選取**新增輸入連接埠規則**：
1. 在 [新增輸入安全性規則] 頁面上，指定下列設定：
    1. 來源：  **任何**

    1. 來源連接埠範圍： *
    1. 目的地：  **任何**
    1. 服務：  **RDP**
    1. 行動：  **允許**
    1. 優先順序：  **300**；請注意：編號較小的規則優先順序較高，應首先進行處理。
    1. 名稱：  **AllowRDP**
1. 請選取**新增**
1. 建置規則後，它將出現在輸入規則清單中。
1. 現在驗證是否可以使用 RDP 連線至 VM。  從左側導覽面板中選取**連線**。
1. 驗證 IP 位址是否設定為公共 IP 位址，保留預設連接埠編號並選取**下載 DRP 檔案**。
1. 開啟已下載的檔案並選取**連線**。
1. 將提示您輸入認證。  請輸入 **AzureUser** 作為使用者名稱。  請輸入 **SC900AzureLabs** 作為密碼。
1. 遠端桌面連線視窗開啟，顯示無法驗證遠端電腦的身分識別。  仍要繼續連線？  請選取**是**。
1. 您現在已連線至 VM。在這種情況下，您能夠連線至 VM，因為您建立的輸入流量規則允許透過 RDP 向 VM 傳送輸入流量。
1. 請保持 VM 開啟，您將在下個工作中使用它。

#### 工作 4：  預設的 NSG 輸出規則允許輸出網際網路流量，因此您將會驗證是否可連線至網際網路。  接著，您將會進行建立自訂輸出規則的流程，以封鎖傳出的網際網路流量與測試該規則。

1. 在 VM 上，請選取 **Edge** 以開啟瀏覽器。  
1. 在瀏覽器網址列輸入 **https://www.bing.com** 並確認您是否能連線至搜尋引擎。
1. 關閉 VM 上的瀏覽器，但是保持 VM 為開啟狀態，因為您將會在後續的步驟中使用。
1. 退回至 Azure 入口網站，在瀏覽器上開啟 [SC900-WinVM – Microsoft Azure] 索引標籤。
1. 從左側導覽面板的設定下，選取**網路**。
1. 請選取**輸出連接埠規則**索引標籤。  您將會看到預設輸出規則。  請注意預設規則「AllowInternetOutBound」。此規則允許所有輸出網際網路流量。您無法移除預設規則，但可以建立優先順序更高的規則來覆寫。在頁面的右側，請選取**新增輸出連接埠規則**。
1. 在 [新增輸出安全性規則] 頁面上，指定下列設定：
    1. 來源：  **任何**

    1. 來源連接埠範圍：  *
    1. 目的地：  **服務標籤**
    1. 目的地服務標籤：  **網際網路**
    1. 服務：  **自訂** (保留預設值)
    1. 目的地連接埠範圍：  * (請確保在目的地連接埠範圍欄位中輸入星號)
    1. 通訊協定: **任何**
    1. 行動：**拒絕**
    1. 優先順序：  **4000**
    1. 名稱：  **DenyInternet**
1. 請選取**新增**
1. 建置規則後，它將出現在輸入規則清單中。  雖然出現在清單上，仍需要數分鐘才能生效 (等待數分鐘，再繼續下一個步驟)。  
1. 退回您的 VM
1. 開啟 VM 中的 Edge 瀏覽器並輸入 **https://www.bing.com** 該頁面不應顯示。  請注意：如果您能夠連線至網際網路並驗證輸出規則的所有參數都已正確設定，則可能是因為該規則需要幾分鐘才會生效。  關閉瀏覽器，等待數幾分鐘後，然後重試。
1. 透過選取顯示 IP 位址的頁面頂部中心的 **X**，關閉遠端桌面連線。  快顯示窗顯示您的遠端工作階段將會中斷連線。請選取**確定**。
1. 在此工作中，您已成功在 NSG 中設定輸出規則，以封鎖輸出網際網路流量。

#### 工作 5：  重要：在此工作中，您將刪除資源群組及其包含的所有資源。   這對於避免額外收費非常重要。

1. 在瀏覽器上開啟 SC900-WinVM – Microsoft Azure 索引標籤。

1. 從頁面的左上角，請選取**所有服務**。
1. 在所有服務旁邊的篩選服務方塊中，輸入**資源群組**，然後從結果中選取**資源群組**。
1. 選取 **LabsSC900**。
1. 從 LabsSC900 頁面的頂部中心，請選取**刪除資源群組**。
1. 在開啟的視窗中，輸入資源群組名稱 **LabsSC900**，確認刪除資源群組及其所有資源，然後從頁面底部選取**刪除**。
1. 刪除所有資源和資源群組可能需要幾分鐘的時間。

#### 回顧

在此實驗中，您已進行設定附加與無附加網路安全性群組 (NSG) 的流程，並檢視預設 NSG 規則的影響。  您也已了解建立 NSG 規則的流程。
