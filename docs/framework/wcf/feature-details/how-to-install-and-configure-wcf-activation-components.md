---
title: 'Instrukcje: Instalowanie i konfigurowanie składników aktywacji programu WCF'
description: Dowiedz się, jak skonfigurować usługę aktywacji procesów systemu Windows (WAS) w systemie Windows Vista do hostowania usług WCF, które nie komunikują się za pośrednictwem protokołu HTTP.
ms.date: 03/30/2017
helpviewer_keywords:
- HTTP activation [WCF]
ms.assetid: 33a7054a-73ec-464d-83e5-b203aeded658
ms.openlocfilehash: 84a0dcc4fed28ebd7a536bdabfcdc389be6072d8
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246886"
---
# <a name="how-to-install-and-configure-wcf-activation-components"></a><span data-ttu-id="7c7d6-103">Instrukcje: Instalowanie i konfigurowanie składników aktywacji programu WCF</span><span class="sxs-lookup"><span data-stu-id="7c7d6-103">How to: Install and Configure WCF Activation Components</span></span>

<span data-ttu-id="7c7d6-104">W tym temacie opisano kroki wymagane do skonfigurowania usługi aktywacji procesów systemu Windows (znanej także jako) w systemie Windows Vista do hostowania usług Windows Communication Foundation (WCF), które nie komunikują się za pośrednictwem protokołów sieciowych protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="7c7d6-104">This topic describes the steps required to set up Windows Process Activation Service (also known as WAS) on Windows Vista to host Windows Communication Foundation (WCF) services that do not communicate over HTTP network protocols.</span></span> <span data-ttu-id="7c7d6-105">W poniższych sekcjach opisano kroki tej konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="7c7d6-105">The following sections outline the steps for this configuration:</span></span>

- <span data-ttu-id="7c7d6-106">Zainstaluj program (lub Potwierdź instalację) składników aktywacji WCF.</span><span class="sxs-lookup"><span data-stu-id="7c7d6-106">Install (or confirm the installation of) the WCF activation components.</span></span>

- <span data-ttu-id="7c7d6-107">Skonfigurowano obsługę protokołu innego niż HTTP.</span><span class="sxs-lookup"><span data-stu-id="7c7d6-107">Configure WAS to support a non-HTTP protocol.</span></span> <span data-ttu-id="7c7d6-108">Poniższa procedura umożliwia skonfigurowanie aktywacji systemu Windows Vista do protokołu TCP.</span><span class="sxs-lookup"><span data-stu-id="7c7d6-108">The following procedure configures Windows Vista for TCP activation.</span></span>

<span data-ttu-id="7c7d6-109">Po zainstalowaniu i skonfigurowaniu programu zapoznaj się z tematem [jak: Hostowanie usługi WCF w usłudze was](how-to-host-a-wcf-service-in-was.md) , aby poznać procedury tworzenia usługi WCF, która uwidacznia punkt końcowy inny niż http.</span><span class="sxs-lookup"><span data-stu-id="7c7d6-109">After installing and configuring WAS, see [How to: Host a WCF Service in WAS](how-to-host-a-wcf-service-in-was.md) for the procedures to create a WCF service that exposes an non-HTTP endpoint that employs WAS.</span></span>

## <a name="to-install-the-wcf-non-http-activation-components"></a><span data-ttu-id="7c7d6-110">Aby zainstalować składniki aktywacji programu WCF inne niż HTTP</span><span class="sxs-lookup"><span data-stu-id="7c7d6-110">To install the WCF non-HTTP activation components</span></span>

1. <span data-ttu-id="7c7d6-111">Kliknij przycisk **Start** , a następnie kliknij pozycję **Panel sterowania**.</span><span class="sxs-lookup"><span data-stu-id="7c7d6-111">Click the **Start** button, and then click **Control Panel**.</span></span>

2. <span data-ttu-id="7c7d6-112">Kliknij pozycję **programy**, a następnie kliknij pozycję **programy i funkcje**.</span><span class="sxs-lookup"><span data-stu-id="7c7d6-112">Click **Programs**, and then click **Programs and Features**.</span></span>

3. <span data-ttu-id="7c7d6-113">W menu **zadania** kliknij pozycję **Włącz lub wyłącz funkcje systemu Windows**.</span><span class="sxs-lookup"><span data-stu-id="7c7d6-113">On the **Tasks** menu, click **Turn Windows features on or off**.</span></span>

4. <span data-ttu-id="7c7d6-114">Znajdź węzeł WinFX, wybierz go, a następnie rozwiń.</span><span class="sxs-lookup"><span data-stu-id="7c7d6-114">Find the WinFX node, select and then expand it.</span></span>

5. <span data-ttu-id="7c7d6-115">Zaznacz pole **Składniki aktywacji programu WCF inne niż http** i Zapisz ustawienie.</span><span class="sxs-lookup"><span data-stu-id="7c7d6-115">Select the **WCF Non-Http Activation Components** box and save the setting.</span></span>

## <a name="to-configure-the-was-to-support-tcp-activation"></a><span data-ttu-id="7c7d6-116">Aby skonfigurować obsługę aktywacji przy użyciu protokołu TCP</span><span class="sxs-lookup"><span data-stu-id="7c7d6-116">To configure the WAS to support TCP activation</span></span>

1. <span data-ttu-id="7c7d6-117">Aby można było obsługiwać aktywację net. TCP, domyślną witryną sieci Web należy najpierw powiązać z portem net. TCP.</span><span class="sxs-lookup"><span data-stu-id="7c7d6-117">To support net.tcp activation, the default Web site must first be bound to a net.tcp port.</span></span> <span data-ttu-id="7c7d6-118">Można to zrobić za pomocą Appcmd.exe, który jest instalowany przy użyciu zestawu narzędzi do zarządzania usługami IIS 7,0.</span><span class="sxs-lookup"><span data-stu-id="7c7d6-118">You can do this by using Appcmd.exe, which is installed with the IIS 7.0 management toolset.</span></span> <span data-ttu-id="7c7d6-119">W oknie wiersza polecenia na poziomie administratora uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="7c7d6-119">In an administrator-level Command Prompt window, run the following command.</span></span>

    ```console
    %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']
    ```

    > [!NOTE]
    > <span data-ttu-id="7c7d6-120">To polecenie jest pojedynczym wierszem tekstu.</span><span class="sxs-lookup"><span data-stu-id="7c7d6-120">This command is a single line of text.</span></span> <span data-ttu-id="7c7d6-121">To polecenie dodaje powiązanie witryny net. TCP do domyślnej witryny sieci Web nasłuchiwanie na porcie TCP 808 z dowolną nazwą hosta.</span><span class="sxs-lookup"><span data-stu-id="7c7d6-121">This command adds a net.tcp site binding to the default Web site listening on TCP port 808 with any host name.</span></span>

2. <span data-ttu-id="7c7d6-122">Mimo że wszystkie aplikacje w lokacji współdzielą wspólne powiązanie net. TCP, każda aplikacja może włączać pojedynczą obsługę protokołu net. TCP.</span><span class="sxs-lookup"><span data-stu-id="7c7d6-122">Although all applications within a site share a common net.tcp binding, each application can enable net.tcp support individually.</span></span> <span data-ttu-id="7c7d6-123">Aby włączyć usługę net. TCP dla aplikacji, uruchom następujące polecenie w wierszu polecenia na poziomie administratora.</span><span class="sxs-lookup"><span data-stu-id="7c7d6-123">To enable net.tcp for the application, run the following command from an administrator-level command prompt.</span></span>

    ```console
    %windir%\system32\inetsrv\appcmd.exe set app
    "Default Web Site/<WCF Application>" /enabledProtocols:http,net.tcp
    ```

    > [!NOTE]
    > <span data-ttu-id="7c7d6-124">To polecenie jest pojedynczym wierszem tekstu.</span><span class="sxs-lookup"><span data-stu-id="7c7d6-124">This command is a single line of text.</span></span> <span data-ttu-id="7c7d6-125">To polecenie umożliwia \<*WCF Application*> dostęp do/aplikacji przy użyciu obu `http://localhost/<WCF Application>` i `net.tcp://localhost/<WCF Application>` .</span><span class="sxs-lookup"><span data-stu-id="7c7d6-125">This command enables the /\<*WCF Application*> application to be accessed using both `http://localhost/<WCF Application>` and `net.tcp://localhost/<WCF Application>`.</span></span>

     <span data-ttu-id="7c7d6-126">Usuń powiązanie witryny net. TCP dodane do tego przykładu.</span><span class="sxs-lookup"><span data-stu-id="7c7d6-126">Remove the net.tcp site binding you added for this sample.</span></span>

     <span data-ttu-id="7c7d6-127">Jako wygoda, następujące dwa kroki są zaimplementowane w pliku wsadowym o nazwie RemoveNetTcpSiteBinding. cmd znajdującym się w przykładowym katalogu.</span><span class="sxs-lookup"><span data-stu-id="7c7d6-127">As a convenience, the following two steps are implemented in a batch file called RemoveNetTcpSiteBinding.cmd located in the sample directory.</span></span>

    1. <span data-ttu-id="7c7d6-128">Usuń usługę net. TCP z listy włączonych protokołów, uruchamiając następujące polecenie w oknie wiersza polecenia administratora.</span><span class="sxs-lookup"><span data-stu-id="7c7d6-128">Remove net.tcp from the list of enabled protocols by running the following command in an administrator-level Command Prompt window.</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app
        "Default Web Site/servicemodelsamples<WCF Application>" " /enabledProtocols:http
        ```

        > [!NOTE]
        > <span data-ttu-id="7c7d6-129">To polecenie jest pojedynczym wierszem tekstu.</span><span class="sxs-lookup"><span data-stu-id="7c7d6-129">This command is a single line of text.</span></span>

    2. <span data-ttu-id="7c7d6-130">Usuń powiązanie witryny net. TCP, uruchamiając następujące polecenie w oknie wiersza polecenia z podwyższonym poziomem uprawnień:</span><span class="sxs-lookup"><span data-stu-id="7c7d6-130">Remove the net.tcp site binding by running the following command in an elevated Command Prompt window:</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
        --bindings.[protocol='net.tcp',bindingInformation='808:*']
        ```

        > [!NOTE]
        > <span data-ttu-id="7c7d6-131">To polecenie jest pojedynczym wierszem tekstu.</span><span class="sxs-lookup"><span data-stu-id="7c7d6-131">This command is a single line of text.</span></span>

## <a name="to-remove-nettcp-from-the-list-of-enabled-protocols"></a><span data-ttu-id="7c7d6-132">Aby usunąć usługę net. TCP z listy włączonych protokołów</span><span class="sxs-lookup"><span data-stu-id="7c7d6-132">To remove net.tcp from the list of enabled protocols</span></span>

1. <span data-ttu-id="7c7d6-133">Aby usunąć usługę net. TCP z listy włączonych protokołów, uruchom następujące polecenie w oknie wiersza polecenia na poziomie administratora.</span><span class="sxs-lookup"><span data-stu-id="7c7d6-133">To remove net.tcp from the list of enabled protocols, run the following command in an administrator-level Command Prompt window.</span></span>

    ```console
    %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples<WCF Application>" " /enabledProtocols:http
    ```

    > [!NOTE]
    > <span data-ttu-id="7c7d6-134">To polecenie jest pojedynczym wierszem tekstu.</span><span class="sxs-lookup"><span data-stu-id="7c7d6-134">This command is a single line of text.</span></span>

## <a name="to-remove-the-nettcp-site-binding"></a><span data-ttu-id="7c7d6-135">Aby usunąć powiązanie witryny net. TCP</span><span class="sxs-lookup"><span data-stu-id="7c7d6-135">To remove the net.tcp site binding</span></span>

1. <span data-ttu-id="7c7d6-136">Aby usunąć powiązanie witryny net. TCP, uruchom następujące polecenie w oknie wiersza polecenia na poziomie administratora.</span><span class="sxs-lookup"><span data-stu-id="7c7d6-136">To remove the net.tcp site binding run the following command in an administrator-level Command Prompt window.</span></span>

    ```console
    %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
    -bindings.[protocol='net.tcp',bindingInformation='808:*']
    ```

    > [!NOTE]
    > <span data-ttu-id="7c7d6-137">To polecenie jest pojedynczym wierszem tekstu.</span><span class="sxs-lookup"><span data-stu-id="7c7d6-137">This command is a single line of text.</span></span>

## <a name="see-also"></a><span data-ttu-id="7c7d6-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7c7d6-138">See also</span></span>

- [<span data-ttu-id="7c7d6-139">Aktywacja TCP</span><span class="sxs-lookup"><span data-stu-id="7c7d6-139">TCP Activation</span></span>](../samples/tcp-activation.md)
- [<span data-ttu-id="7c7d6-140">Aktywacja usługi MSMQ</span><span class="sxs-lookup"><span data-stu-id="7c7d6-140">MSMQ Activation</span></span>](../samples/msmq-activation.md)
- [<span data-ttu-id="7c7d6-141">Aktywowanie elementu NamedPipe</span><span class="sxs-lookup"><span data-stu-id="7c7d6-141">NamedPipe Activation</span></span>](../samples/namedpipe-activation.md)
- <span data-ttu-id="7c7d6-142">[Funkcje hostingu sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="7c7d6-142">[Windows Server App Fabric Hosting Features](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
