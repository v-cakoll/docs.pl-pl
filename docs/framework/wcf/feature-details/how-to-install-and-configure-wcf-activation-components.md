---
title: "Instrukcje: Instalowanie i konfigurowanie składników aktywacji programu WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: HTTP activation [WCF]
ms.assetid: 33a7054a-73ec-464d-83e5-b203aeded658
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ee57276efda7edcc464c300e2f1d100b6a7c9109
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-install-and-configure-wcf-activation-components"></a><span data-ttu-id="1cb0b-102">Instrukcje: Instalowanie i konfigurowanie składników aktywacji programu WCF</span><span class="sxs-lookup"><span data-stu-id="1cb0b-102">How to: Install and Configure WCF Activation Components</span></span>
<span data-ttu-id="1cb0b-103">W tym temacie opisano kroki wymagane do skonfigurowania Windows Process Activation Service (znanej także jako Usługa WAS) na [!INCLUDE[wv](../../../../includes/wv-md.md)] hosta [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] protokoły sieciowe usług, które nie komunikują się za pośrednictwem protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="1cb0b-103">This topic describes the steps required to set up Windows Process Activation Service (also known as WAS) on [!INCLUDE[wv](../../../../includes/wv-md.md)] to host [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] services that do not communicate over HTTP network protocols.</span></span> <span data-ttu-id="1cb0b-104">W poniższych sekcjach opisano czynności dla tej konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="1cb0b-104">The following sections outline the steps for this configuration:</span></span>  
  
-   <span data-ttu-id="1cb0b-105">Zainstaluj (lub potwierdź instalacji) [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] składników aktywacji.</span><span class="sxs-lookup"><span data-stu-id="1cb0b-105">Install (or confirm the installation of) the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] activation components.</span></span>  
  
-   <span data-ttu-id="1cb0b-106">Skonfiguruj WAS do obsługi protokołu innego niż HTTP.</span><span class="sxs-lookup"><span data-stu-id="1cb0b-106">Configure WAS to support a non-HTTP protocol.</span></span> <span data-ttu-id="1cb0b-107">Poniższa procedura umożliwia skonfigurowanie [!INCLUDE[wv](../../../../includes/wv-md.md)] aktywacji TCP.</span><span class="sxs-lookup"><span data-stu-id="1cb0b-107">The following procedure configures [!INCLUDE[wv](../../../../includes/wv-md.md)] for TCP activation.</span></span>  
  
 <span data-ttu-id="1cb0b-108">Po zainstalowaniu i skonfigurowaniu WAS, zobacz [porady: hostowanie usługi WCF w WAS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md) dla procedury tworzenia [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi udostępniającej punktu końcowego protokołu HTTP, który wykorzystuje WAS.</span><span class="sxs-lookup"><span data-stu-id="1cb0b-108">After installing and configuring WAS, see [How to: Host a WCF Service in WAS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md) for the procedures to create a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service that exposes an non-HTTP endpoint that employs WAS.</span></span>  
  
### <a name="to-install-the-wcf-non-http-activation-components"></a><span data-ttu-id="1cb0b-109">Aby zainstalować składniki Aktywacja bez HTTP programu WCF</span><span class="sxs-lookup"><span data-stu-id="1cb0b-109">To install the WCF non-HTTP activation components</span></span>  
  
1.  <span data-ttu-id="1cb0b-110">Kliknij przycisk **Start** przycisk, a następnie kliknij przycisk **Panelu sterowania**.</span><span class="sxs-lookup"><span data-stu-id="1cb0b-110">Click the **Start** button, and then click **Control Panel**.</span></span>  
  
2.  <span data-ttu-id="1cb0b-111">Kliknij przycisk **programy**, a następnie kliknij przycisk **programy i funkcje**.</span><span class="sxs-lookup"><span data-stu-id="1cb0b-111">Click **Programs**, and then click **Programs and Features**.</span></span>  
  
3.  <span data-ttu-id="1cb0b-112">Na **zadania** menu, kliknij przycisk **Włącz lub wyłącz funkcje systemu Windows**.</span><span class="sxs-lookup"><span data-stu-id="1cb0b-112">On the **Tasks** menu, click **Turn Windows features on or off**.</span></span>  
  
4.  <span data-ttu-id="1cb0b-113">Znajdź [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] węzła, wybierz, a następnie rozwiń węzeł.</span><span class="sxs-lookup"><span data-stu-id="1cb0b-113">Find the [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] node, select and then expand it.</span></span>  
  
5.  <span data-ttu-id="1cb0b-114">Wybierz **składników aktywacji programu WCF bez Http** i Zapisz ustawienia.</span><span class="sxs-lookup"><span data-stu-id="1cb0b-114">Select the **WCF Non-Http Activation Components** box and save the setting.</span></span>  
  
### <a name="to-configure-the-was-to-support-tcp-activation"></a><span data-ttu-id="1cb0b-115">Aby skonfigurować usługi WAS do obsługi aktywacji TCP</span><span class="sxs-lookup"><span data-stu-id="1cb0b-115">To configure the WAS to support TCP activation</span></span>  
  
1.  <span data-ttu-id="1cb0b-116">Aby zapewnić obsługę aktywacji net.tcp, domyślnej witryny sieci Web musi zostać powiązana do portów net.tcp.</span><span class="sxs-lookup"><span data-stu-id="1cb0b-116">To support net.tcp activation, the default Web site must first be bound to a net.tcp port.</span></span> <span data-ttu-id="1cb0b-117">Można to zrobić za pomocą Appcmd.exe, który jest instalowany z [!INCLUDE[iisver](../../../../includes/iisver-md.md)] narzędzi zarządzania.</span><span class="sxs-lookup"><span data-stu-id="1cb0b-117">You can do this by using Appcmd.exe, which is installed with the [!INCLUDE[iisver](../../../../includes/iisver-md.md)] management toolset.</span></span> <span data-ttu-id="1cb0b-118">W oknie wiersza polecenia uprawnień administratora uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="1cb0b-118">In an administrator-level Command Prompt window, run the following command.</span></span>  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="1cb0b-119">To polecenie jest pojedynczy wiersz tekstu.</span><span class="sxs-lookup"><span data-stu-id="1cb0b-119">This command is a single line of text.</span></span> <span data-ttu-id="1cb0b-120">To polecenie dodaje powiązania witryny net.tcp, do domyślnej witryny sieci Web nasłuchiwanie na porcie TCP 808 z żadną nazwą hosta.</span><span class="sxs-lookup"><span data-stu-id="1cb0b-120">This command adds a net.tcp site binding to the default Web site listening on TCP port 808 with any host name.</span></span>  
  
2.  <span data-ttu-id="1cb0b-121">Mimo że wszystkie aplikacje w obrębie lokacji korzystają wspólnej powiązanie net.tcp, każdej aplikacji można włączyć obsługę net.tcp pojedynczo.</span><span class="sxs-lookup"><span data-stu-id="1cb0b-121">Although all applications within a site share a common net.tcp binding, each application can enable net.tcp support individually.</span></span> <span data-ttu-id="1cb0b-122">Aby włączyć net.tcp dla aplikacji, uruchom następujące polecenie z wiersza polecenia z uprawnieniami administratora na poziomie.</span><span class="sxs-lookup"><span data-stu-id="1cb0b-122">To enable net.tcp for the application, run the following command from an administrator-level command prompt.</span></span>  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set app   
    "Default Web Site/<WCF Application>" /enabledProtocols:http,net.tcp  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="1cb0b-123">To polecenie jest pojedynczy wiersz tekstu.</span><span class="sxs-lookup"><span data-stu-id="1cb0b-123">This command is a single line of text.</span></span> <span data-ttu-id="1cb0b-124">To polecenie włącza /\<*aplikacja WCF*> aplikacji, aby uzyskać dostęp za pomocą obu http://localhost*/\<aplikacja WCF >* i net.tcp:// localhost /*\<aplikacja WCF >*.</span><span class="sxs-lookup"><span data-stu-id="1cb0b-124">This command enables the /\<*WCF Application*> application to be accessed using both http://localhost*/\<WCF Application>* and net.tcp://localhost/*\<WCF Application>*.</span></span>  
  
     <span data-ttu-id="1cb0b-125">Usuń powiązanie witryny net.tcp, dodane dla tego przykładu.</span><span class="sxs-lookup"><span data-stu-id="1cb0b-125">Remove the net.tcp site binding you added for this sample.</span></span>  
  
     <span data-ttu-id="1cb0b-126">Dla wygody następujące dwa kroki są implementowane w pliku wsadowym o nazwie RemoveNetTcpSiteBinding.cmd znajduje się w katalogu próbki.</span><span class="sxs-lookup"><span data-stu-id="1cb0b-126">As a convenience, the following two steps are implemented in a batch file called RemoveNetTcpSiteBinding.cmd located in the sample directory.</span></span>  
  
    1.  <span data-ttu-id="1cb0b-127">Usuń net.tcp z listy włączonych protokołów, uruchamiając następujące polecenie w oknie wiersza polecenia poziomie administratora.</span><span class="sxs-lookup"><span data-stu-id="1cb0b-127">Remove net.tcp from the list of enabled protocols by running the following command in an administrator-level Command Prompt window.</span></span>  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set app   
        "Default Web Site/servicemodelsamples<WCF Application>" " /enabledProtocols:http  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="1cb0b-128">To polecenie jest pojedynczy wiersz tekstu.</span><span class="sxs-lookup"><span data-stu-id="1cb0b-128">This command is a single line of text.</span></span>  
  
    2.  <span data-ttu-id="1cb0b-129">Usuń powiązanie witryny net.tcp, uruchamiając następujące polecenie w oknie wiersza polecenia z podwyższonym poziomem uprawnień:</span><span class="sxs-lookup"><span data-stu-id="1cb0b-129">Remove the net.tcp site binding by running the following command in an elevated Command Prompt window:</span></span>  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"   
        --bindings.[protocol='net.tcp',bindingInformation='808:*']  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="1cb0b-130">To polecenie jest pojedynczy wiersz tekstu.</span><span class="sxs-lookup"><span data-stu-id="1cb0b-130">This command is a single line of text.</span></span>  
  
### <a name="to-remove-nettcp-from-the-list-of-enabled-protocols"></a><span data-ttu-id="1cb0b-131">Aby usunąć z listy włączonych protokołów net.tcp</span><span class="sxs-lookup"><span data-stu-id="1cb0b-131">To remove net.tcp from the list of enabled protocols</span></span>  
  
1.  <span data-ttu-id="1cb0b-132">Aby usunąć net.tcp z listy włączonych protokołów, uruchom następujące polecenie w oknie wiersza polecenia poziomie administratora.</span><span class="sxs-lookup"><span data-stu-id="1cb0b-132">To remove net.tcp from the list of enabled protocols, run the following command in an administrator-level Command Prompt window.</span></span>  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples<WCF Application>" " /enabledProtocols:http  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="1cb0b-133">To polecenie jest pojedynczy wiersz tekstu.</span><span class="sxs-lookup"><span data-stu-id="1cb0b-133">This command is a single line of text.</span></span>  
  
### <a name="to-remove-the-nettcp-site-binding"></a><span data-ttu-id="1cb0b-134">Aby usunąć powiązanie witryny usługi net.tcp</span><span class="sxs-lookup"><span data-stu-id="1cb0b-134">To remove the net.tcp site binding</span></span>  
  
1.  <span data-ttu-id="1cb0b-135">Aby usunąć lokację net.tcp powiązanie uruchom następujące polecenie w oknie wiersza polecenia poziomie administratora.</span><span class="sxs-lookup"><span data-stu-id="1cb0b-135">To remove the net.tcp site binding run the following command in an administrator-level Command Prompt window.</span></span>  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"   
    -bindings.[protocol='net.tcp',bindingInformation='808:*']  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="1cb0b-136">To polecenie jest pojedynczy wiersz tekstu.</span><span class="sxs-lookup"><span data-stu-id="1cb0b-136">This command is a single line of text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cb0b-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1cb0b-137">See Also</span></span>  
 [<span data-ttu-id="1cb0b-138">Aktywacja TCP</span><span class="sxs-lookup"><span data-stu-id="1cb0b-138">TCP Activation</span></span>](../../../../docs/framework/wcf/samples/tcp-activation.md)  
 [<span data-ttu-id="1cb0b-139">Aktywacja usługi MSMQ</span><span class="sxs-lookup"><span data-stu-id="1cb0b-139">MSMQ Activation</span></span>](../../../../docs/framework/wcf/samples/msmq-activation.md)  
 [<span data-ttu-id="1cb0b-140">Aktywowanie elementu Namedpipe</span><span class="sxs-lookup"><span data-stu-id="1cb0b-140">NamedPipe Activation</span></span>](../../../../docs/framework/wcf/samples/namedpipe-activation.md)  
 [<span data-ttu-id="1cb0b-141">Windows Server AppFabric funkcje hostingu</span><span class="sxs-lookup"><span data-stu-id="1cb0b-141">Windows Server App Fabric Hosting Features</span></span>](http://go.microsoft.com/fwlink/?LinkId=201276)
