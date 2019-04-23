---
title: 'Instrukcje: instalowanie i konfigurowanie składników aktywacji programu WCF'
ms.date: 03/30/2017
helpviewer_keywords:
- HTTP activation [WCF]
ms.assetid: 33a7054a-73ec-464d-83e5-b203aeded658
ms.openlocfilehash: 2677c57c825675c884d057827e065f05d7c8bf30
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59327987"
---
# <a name="how-to-install-and-configure-wcf-activation-components"></a><span data-ttu-id="87621-102">Instrukcje: instalowanie i konfigurowanie składników aktywacji programu WCF</span><span class="sxs-lookup"><span data-stu-id="87621-102">How to: Install and Configure WCF Activation Components</span></span>
<span data-ttu-id="87621-103">W tym temacie opisano kroki wymagane do skonfigurowania usługi aktywacji procesów systemu Windows (znany także jako WAS) na [!INCLUDE[wv](../../../../includes/wv-md.md)] do hostowania usług Windows Communication Foundation (WCF) protokołów sieciowych usług, które nie komunikują się za pośrednictwem protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="87621-103">This topic describes the steps required to set up Windows Process Activation Service (also known as WAS) on [!INCLUDE[wv](../../../../includes/wv-md.md)] to host Windows Communication Foundation (WCF) services that do not communicate over HTTP network protocols.</span></span> <span data-ttu-id="87621-104">W poniższych sekcjach opisano w krokach dla tej konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="87621-104">The following sections outline the steps for this configuration:</span></span>  
  
-   <span data-ttu-id="87621-105">Zainstalować (lub Potwierdź instalację) składników aktywacji programu WCF.</span><span class="sxs-lookup"><span data-stu-id="87621-105">Install (or confirm the installation of) the WCF activation components.</span></span>  
  
-   <span data-ttu-id="87621-106">Skonfiguruj WAS do obsługi protokołu innego niż HTTP.</span><span class="sxs-lookup"><span data-stu-id="87621-106">Configure WAS to support a non-HTTP protocol.</span></span> <span data-ttu-id="87621-107">Poniższa procedura umożliwia skonfigurowanie [!INCLUDE[wv](../../../../includes/wv-md.md)] aktywacji TCP.</span><span class="sxs-lookup"><span data-stu-id="87621-107">The following procedure configures [!INCLUDE[wv](../../../../includes/wv-md.md)] for TCP activation.</span></span>  
  
 <span data-ttu-id="87621-108">Gdy instalowanie i konfigurowanie usługi WAS, zobaczysz [jak: Hostowanie usługi WCF w WAS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md) procedury utworzyć usługę WCF, która uwidacznia punkt końcowy protokołu HTTP, który wykorzystuje WAS.</span><span class="sxs-lookup"><span data-stu-id="87621-108">After installing and configuring WAS, see [How to: Host a WCF Service in WAS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md) for the procedures to create a WCF service that exposes an non-HTTP endpoint that employs WAS.</span></span>  
  
### <a name="to-install-the-wcf-non-http-activation-components"></a><span data-ttu-id="87621-109">Aby zainstalować składniki Aktywacja bez HTTP programu WCF</span><span class="sxs-lookup"><span data-stu-id="87621-109">To install the WCF non-HTTP activation components</span></span>  
  
1. <span data-ttu-id="87621-110">Kliknij przycisk **Start** przycisk, a następnie kliknij przycisk **Panelu sterowania**.</span><span class="sxs-lookup"><span data-stu-id="87621-110">Click the **Start** button, and then click **Control Panel**.</span></span>  
  
2. <span data-ttu-id="87621-111">Kliknij przycisk **programy**, a następnie kliknij przycisk **programy i funkcje**.</span><span class="sxs-lookup"><span data-stu-id="87621-111">Click **Programs**, and then click **Programs and Features**.</span></span>  
  
3. <span data-ttu-id="87621-112">Na **zadania** menu, kliknij przycisk **Windows Włącz lub wyłącz funkcje**.</span><span class="sxs-lookup"><span data-stu-id="87621-112">On the **Tasks** menu, click **Turn Windows features on or off**.</span></span>  
  
4. <span data-ttu-id="87621-113">Znajdź [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] węzła, wybierz, a następnie rozwiń węzeł.</span><span class="sxs-lookup"><span data-stu-id="87621-113">Find the [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] node, select and then expand it.</span></span>  
  
5. <span data-ttu-id="87621-114">Wybierz **składników Aktywacja bez Http programu WCF** pole, a następnie Zapisz ustawienia.</span><span class="sxs-lookup"><span data-stu-id="87621-114">Select the **WCF Non-Http Activation Components** box and save the setting.</span></span>  
  
### <a name="to-configure-the-was-to-support-tcp-activation"></a><span data-ttu-id="87621-115">Aby skonfigurować WAS do obsługi Aktywacja TCP</span><span class="sxs-lookup"><span data-stu-id="87621-115">To configure the WAS to support TCP activation</span></span>  
  
1. <span data-ttu-id="87621-116">Aby zapewnić obsługę aktywacji net.tcp, domyślna witryna sieci Web musi zostać powiązana portów net.tcp.</span><span class="sxs-lookup"><span data-stu-id="87621-116">To support net.tcp activation, the default Web site must first be bound to a net.tcp port.</span></span> <span data-ttu-id="87621-117">Można to zrobić za pomocą Appcmd.exe, który został zainstalowany przy użyciu [!INCLUDE[iisver](../../../../includes/iisver-md.md)] zestaw narzędzi do zarządzania.</span><span class="sxs-lookup"><span data-stu-id="87621-117">You can do this by using Appcmd.exe, which is installed with the [!INCLUDE[iisver](../../../../includes/iisver-md.md)] management toolset.</span></span> <span data-ttu-id="87621-118">W oknie wiersza polecenia uprawnień administratora uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="87621-118">In an administrator-level Command Prompt window, run the following command.</span></span>  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="87621-119">To polecenie jest pojedynczy wiersz tekstu.</span><span class="sxs-lookup"><span data-stu-id="87621-119">This command is a single line of text.</span></span> <span data-ttu-id="87621-120">To polecenie dodaje powiązanie witryny net.tcp, do domyślnej witryny sieci Web nasłuchiwanie na porcie TCP 808 z nazwą hosta.</span><span class="sxs-lookup"><span data-stu-id="87621-120">This command adds a net.tcp site binding to the default Web site listening on TCP port 808 with any host name.</span></span>  
  
2. <span data-ttu-id="87621-121">Mimo że wszystkie aplikacje w ramach lokacji mają wspólne powiązanie net.tcp, każdej aplikacji można włączyć obsługę net.tcp indywidualnie.</span><span class="sxs-lookup"><span data-stu-id="87621-121">Although all applications within a site share a common net.tcp binding, each application can enable net.tcp support individually.</span></span> <span data-ttu-id="87621-122">Aby włączyć net.tcp dla aplikacji, uruchom następujące polecenie z wiersza polecenia z uprawnieniami administratora na poziomie.</span><span class="sxs-lookup"><span data-stu-id="87621-122">To enable net.tcp for the application, run the following command from an administrator-level command prompt.</span></span>  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set app   
    "Default Web Site/<WCF Application>" /enabledProtocols:http,net.tcp  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="87621-123">To polecenie jest pojedynczy wiersz tekstu.</span><span class="sxs-lookup"><span data-stu-id="87621-123">This command is a single line of text.</span></span> <span data-ttu-id="87621-124">To polecenie włącza /\<*aplikacji WCF*> aplikacji można uzyskać za pomocą zarówno `http://localhost/<WCF Application>` i `net.tcp://localhost/<WCF Application>`.</span><span class="sxs-lookup"><span data-stu-id="87621-124">This command enables the /\<*WCF Application*> application to be accessed using both `http://localhost/<WCF Application>` and `net.tcp://localhost/<WCF Application>`.</span></span>
  
     <span data-ttu-id="87621-125">Usuń powiązanie witryny net.tcp, dodane dla tego przykładu.</span><span class="sxs-lookup"><span data-stu-id="87621-125">Remove the net.tcp site binding you added for this sample.</span></span>  
  
     <span data-ttu-id="87621-126">Dla wygody następujące dwa kroki są implementowane w pliku wsadowym, o nazwie RemoveNetTcpSiteBinding.cmd znajduje się w katalogu próbki.</span><span class="sxs-lookup"><span data-stu-id="87621-126">As a convenience, the following two steps are implemented in a batch file called RemoveNetTcpSiteBinding.cmd located in the sample directory.</span></span>  
  
    1.  <span data-ttu-id="87621-127">Usuń net.tcp z listy włączone protokoły, uruchamiając następujące polecenie w oknie wiersza polecenia uprawnień administratora.</span><span class="sxs-lookup"><span data-stu-id="87621-127">Remove net.tcp from the list of enabled protocols by running the following command in an administrator-level Command Prompt window.</span></span>  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set app   
        "Default Web Site/servicemodelsamples<WCF Application>" " /enabledProtocols:http  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="87621-128">To polecenie jest pojedynczy wiersz tekstu.</span><span class="sxs-lookup"><span data-stu-id="87621-128">This command is a single line of text.</span></span>  
  
    2.  <span data-ttu-id="87621-129">Usuń powiązanie witryny net.tcp, uruchamiając następujące polecenie w oknie wiersza polecenia z podwyższonym poziomem uprawnień:</span><span class="sxs-lookup"><span data-stu-id="87621-129">Remove the net.tcp site binding by running the following command in an elevated Command Prompt window:</span></span>  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"   
        --bindings.[protocol='net.tcp',bindingInformation='808:*']  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="87621-130">To polecenie jest pojedynczy wiersz tekstu.</span><span class="sxs-lookup"><span data-stu-id="87621-130">This command is a single line of text.</span></span>  
  
### <a name="to-remove-nettcp-from-the-list-of-enabled-protocols"></a><span data-ttu-id="87621-131">Aby usunąć net.tcp, z listy włączone protokoły</span><span class="sxs-lookup"><span data-stu-id="87621-131">To remove net.tcp from the list of enabled protocols</span></span>  
  
1. <span data-ttu-id="87621-132">Aby usunąć net.tcp, z listy włączone protokoły, uruchom następujące polecenie w oknie wiersza polecenia uprawnień administratora.</span><span class="sxs-lookup"><span data-stu-id="87621-132">To remove net.tcp from the list of enabled protocols, run the following command in an administrator-level Command Prompt window.</span></span>  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples<WCF Application>" " /enabledProtocols:http  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="87621-133">To polecenie jest pojedynczy wiersz tekstu.</span><span class="sxs-lookup"><span data-stu-id="87621-133">This command is a single line of text.</span></span>  
  
### <a name="to-remove-the-nettcp-site-binding"></a><span data-ttu-id="87621-134">Aby usunąć powiązanie witryny net.tcp</span><span class="sxs-lookup"><span data-stu-id="87621-134">To remove the net.tcp site binding</span></span>  
  
1. <span data-ttu-id="87621-135">Aby usunąć lokację net.tcp powiązania uruchom następujące polecenie w oknie wiersza polecenia uprawnień administratora.</span><span class="sxs-lookup"><span data-stu-id="87621-135">To remove the net.tcp site binding run the following command in an administrator-level Command Prompt window.</span></span>  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"   
    -bindings.[protocol='net.tcp',bindingInformation='808:*']  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="87621-136">To polecenie jest pojedynczy wiersz tekstu.</span><span class="sxs-lookup"><span data-stu-id="87621-136">This command is a single line of text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87621-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="87621-137">See also</span></span>

- [<span data-ttu-id="87621-138">Aktywacja TCP</span><span class="sxs-lookup"><span data-stu-id="87621-138">TCP Activation</span></span>](../../../../docs/framework/wcf/samples/tcp-activation.md)
- [<span data-ttu-id="87621-139">Aktywacja usługi MSMQ</span><span class="sxs-lookup"><span data-stu-id="87621-139">MSMQ Activation</span></span>](../../../../docs/framework/wcf/samples/msmq-activation.md)
- [<span data-ttu-id="87621-140">Aktywowanie elementu NamedPipe</span><span class="sxs-lookup"><span data-stu-id="87621-140">NamedPipe Activation</span></span>](../../../../docs/framework/wcf/samples/namedpipe-activation.md)
- [<span data-ttu-id="87621-141">Windows Server AppFabric funkcje hostingu</span><span class="sxs-lookup"><span data-stu-id="87621-141">Windows Server App Fabric Hosting Features</span></span>](https://go.microsoft.com/fwlink/?LinkId=201276)
