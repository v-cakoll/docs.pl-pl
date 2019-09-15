---
title: 'Instrukcje: instalowanie i konfigurowanie składników aktywacji programu WCF'
ms.date: 03/30/2017
helpviewer_keywords:
- HTTP activation [WCF]
ms.assetid: 33a7054a-73ec-464d-83e5-b203aeded658
ms.openlocfilehash: 70eab39e4bb24dfd1cdd6abc5216e50126ef1f4c
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972179"
---
# <a name="how-to-install-and-configure-wcf-activation-components"></a><span data-ttu-id="afadc-102">Instrukcje: instalowanie i konfigurowanie składników aktywacji programu WCF</span><span class="sxs-lookup"><span data-stu-id="afadc-102">How to: Install and Configure WCF Activation Components</span></span>

<span data-ttu-id="afadc-103">W tym temacie opisano kroki wymagane do skonfigurowania usługi aktywacji procesów systemu Windows (znanej także jako) na [!INCLUDE[wv](../../../../includes/wv-md.md)] potrzeby usług hosta Windows Communication Foundation (WCF), które nie komunikują się za pośrednictwem protokołów sieciowych protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="afadc-103">This topic describes the steps required to set up Windows Process Activation Service (also known as WAS) on [!INCLUDE[wv](../../../../includes/wv-md.md)] to host Windows Communication Foundation (WCF) services that do not communicate over HTTP network protocols.</span></span> <span data-ttu-id="afadc-104">W poniższych sekcjach opisano kroki tej konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="afadc-104">The following sections outline the steps for this configuration:</span></span>

- <span data-ttu-id="afadc-105">Zainstaluj program (lub Potwierdź instalację) składników aktywacji WCF.</span><span class="sxs-lookup"><span data-stu-id="afadc-105">Install (or confirm the installation of) the WCF activation components.</span></span>

- <span data-ttu-id="afadc-106">Skonfigurowano obsługę protokołu innego niż HTTP.</span><span class="sxs-lookup"><span data-stu-id="afadc-106">Configure WAS to support a non-HTTP protocol.</span></span> <span data-ttu-id="afadc-107">Poniższa procedura służy [!INCLUDE[wv](../../../../includes/wv-md.md)] do konfigurowania aktywacji przy użyciu protokołu TCP.</span><span class="sxs-lookup"><span data-stu-id="afadc-107">The following procedure configures [!INCLUDE[wv](../../../../includes/wv-md.md)] for TCP activation.</span></span>

<span data-ttu-id="afadc-108">Po zainstalowaniu i skonfigurowaniu programu zapoznaj [się z tematem How to: Hostowanie usługi WCF w programie](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md) dotyczyło procedur tworzenia usługi WCF, która uwidacznia punkt końcowy inny niż http.</span><span class="sxs-lookup"><span data-stu-id="afadc-108">After installing and configuring WAS, see [How to: Host a WCF Service in WAS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md) for the procedures to create a WCF service that exposes an non-HTTP endpoint that employs WAS.</span></span>

## <a name="to-install-the-wcf-non-http-activation-components"></a><span data-ttu-id="afadc-109">Aby zainstalować składniki aktywacji programu WCF inne niż HTTP</span><span class="sxs-lookup"><span data-stu-id="afadc-109">To install the WCF non-HTTP activation components</span></span>

1. <span data-ttu-id="afadc-110">Kliknij przycisk **Start** , a następnie kliknij pozycję **Panel sterowania**.</span><span class="sxs-lookup"><span data-stu-id="afadc-110">Click the **Start** button, and then click **Control Panel**.</span></span>

2. <span data-ttu-id="afadc-111">Kliknij pozycję **programy**, a następnie kliknij pozycję **programy i funkcje**.</span><span class="sxs-lookup"><span data-stu-id="afadc-111">Click **Programs**, and then click **Programs and Features**.</span></span>

3. <span data-ttu-id="afadc-112">W menu **zadania** kliknij pozycję **Włącz lub wyłącz funkcje systemu Windows**.</span><span class="sxs-lookup"><span data-stu-id="afadc-112">On the **Tasks** menu, click **Turn Windows features on or off**.</span></span>

4. <span data-ttu-id="afadc-113">Znajdź węzeł WinFX, wybierz go, a następnie rozwiń.</span><span class="sxs-lookup"><span data-stu-id="afadc-113">Find the WinFX node, select and then expand it.</span></span>

5. <span data-ttu-id="afadc-114">Zaznacz pole **Składniki aktywacji programu WCF inne niż http** i Zapisz ustawienie.</span><span class="sxs-lookup"><span data-stu-id="afadc-114">Select the **WCF Non-Http Activation Components** box and save the setting.</span></span>

## <a name="to-configure-the-was-to-support-tcp-activation"></a><span data-ttu-id="afadc-115">Aby skonfigurować obsługę aktywacji przy użyciu protokołu TCP</span><span class="sxs-lookup"><span data-stu-id="afadc-115">To configure the WAS to support TCP activation</span></span>

1. <span data-ttu-id="afadc-116">Aby można było obsługiwać aktywację net. TCP, domyślną witryną sieci Web należy najpierw powiązać z portem net. TCP.</span><span class="sxs-lookup"><span data-stu-id="afadc-116">To support net.tcp activation, the default Web site must first be bound to a net.tcp port.</span></span> <span data-ttu-id="afadc-117">Można to zrobić za pomocą programu Appcmd. exe, który jest instalowany za pomocą zestawu narzędzi do zarządzania usługami IIS 7,0.</span><span class="sxs-lookup"><span data-stu-id="afadc-117">You can do this by using Appcmd.exe, which is installed with the IIS 7.0 management toolset.</span></span> <span data-ttu-id="afadc-118">W oknie wiersza polecenia na poziomie administratora uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="afadc-118">In an administrator-level Command Prompt window, run the following command.</span></span>

    ```console
    %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']
    ```

    > [!NOTE]
    > <span data-ttu-id="afadc-119">To polecenie jest pojedynczym wierszem tekstu.</span><span class="sxs-lookup"><span data-stu-id="afadc-119">This command is a single line of text.</span></span> <span data-ttu-id="afadc-120">To polecenie dodaje powiązanie witryny net. TCP do domyślnej witryny sieci Web nasłuchiwanie na porcie TCP 808 z dowolną nazwą hosta.</span><span class="sxs-lookup"><span data-stu-id="afadc-120">This command adds a net.tcp site binding to the default Web site listening on TCP port 808 with any host name.</span></span>

2. <span data-ttu-id="afadc-121">Mimo że wszystkie aplikacje w lokacji współdzielą wspólne powiązanie net. TCP, każda aplikacja może włączać pojedynczą obsługę protokołu net. TCP.</span><span class="sxs-lookup"><span data-stu-id="afadc-121">Although all applications within a site share a common net.tcp binding, each application can enable net.tcp support individually.</span></span> <span data-ttu-id="afadc-122">Aby włączyć usługę net. TCP dla aplikacji, uruchom następujące polecenie w wierszu polecenia na poziomie administratora.</span><span class="sxs-lookup"><span data-stu-id="afadc-122">To enable net.tcp for the application, run the following command from an administrator-level command prompt.</span></span>

    ```console
    %windir%\system32\inetsrv\appcmd.exe set app
    "Default Web Site/<WCF Application>" /enabledProtocols:http,net.tcp
    ```

    > [!NOTE]
    > <span data-ttu-id="afadc-123">To polecenie jest pojedynczym wierszem tekstu.</span><span class="sxs-lookup"><span data-stu-id="afadc-123">This command is a single line of text.</span></span> <span data-ttu-id="afadc-124">To polecenie umożliwia dostęp do\<aplikacji/>*aplikacji programu WCF*przy użyciu `http://localhost/<WCF Application>` programów i. `net.tcp://localhost/<WCF Application>`</span><span class="sxs-lookup"><span data-stu-id="afadc-124">This command enables the /\<*WCF Application*> application to be accessed using both `http://localhost/<WCF Application>` and `net.tcp://localhost/<WCF Application>`.</span></span>

     <span data-ttu-id="afadc-125">Usuń powiązanie witryny net. TCP dodane do tego przykładu.</span><span class="sxs-lookup"><span data-stu-id="afadc-125">Remove the net.tcp site binding you added for this sample.</span></span>

     <span data-ttu-id="afadc-126">Jako wygoda, następujące dwa kroki są zaimplementowane w pliku wsadowym o nazwie RemoveNetTcpSiteBinding. cmd znajdującym się w przykładowym katalogu.</span><span class="sxs-lookup"><span data-stu-id="afadc-126">As a convenience, the following two steps are implemented in a batch file called RemoveNetTcpSiteBinding.cmd located in the sample directory.</span></span>

    1. <span data-ttu-id="afadc-127">Usuń usługę net. TCP z listy włączonych protokołów, uruchamiając następujące polecenie w oknie wiersza polecenia administratora.</span><span class="sxs-lookup"><span data-stu-id="afadc-127">Remove net.tcp from the list of enabled protocols by running the following command in an administrator-level Command Prompt window.</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app
        "Default Web Site/servicemodelsamples<WCF Application>" " /enabledProtocols:http
        ```

        > [!NOTE]
        > <span data-ttu-id="afadc-128">To polecenie jest pojedynczym wierszem tekstu.</span><span class="sxs-lookup"><span data-stu-id="afadc-128">This command is a single line of text.</span></span>

    2. <span data-ttu-id="afadc-129">Usuń powiązanie witryny net. TCP, uruchamiając następujące polecenie w oknie wiersza polecenia z podwyższonym poziomem uprawnień:</span><span class="sxs-lookup"><span data-stu-id="afadc-129">Remove the net.tcp site binding by running the following command in an elevated Command Prompt window:</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
        --bindings.[protocol='net.tcp',bindingInformation='808:*']
        ```

        > [!NOTE]
        > <span data-ttu-id="afadc-130">To polecenie jest pojedynczym wierszem tekstu.</span><span class="sxs-lookup"><span data-stu-id="afadc-130">This command is a single line of text.</span></span>

## <a name="to-remove-nettcp-from-the-list-of-enabled-protocols"></a><span data-ttu-id="afadc-131">Aby usunąć usługę net. TCP z listy włączonych protokołów</span><span class="sxs-lookup"><span data-stu-id="afadc-131">To remove net.tcp from the list of enabled protocols</span></span>

1. <span data-ttu-id="afadc-132">Aby usunąć usługę net. TCP z listy włączonych protokołów, uruchom następujące polecenie w oknie wiersza polecenia na poziomie administratora.</span><span class="sxs-lookup"><span data-stu-id="afadc-132">To remove net.tcp from the list of enabled protocols, run the following command in an administrator-level Command Prompt window.</span></span>

    ```console
    %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples<WCF Application>" " /enabledProtocols:http
    ```

    > [!NOTE]
    > <span data-ttu-id="afadc-133">To polecenie jest pojedynczym wierszem tekstu.</span><span class="sxs-lookup"><span data-stu-id="afadc-133">This command is a single line of text.</span></span>

## <a name="to-remove-the-nettcp-site-binding"></a><span data-ttu-id="afadc-134">Aby usunąć powiązanie witryny net. TCP</span><span class="sxs-lookup"><span data-stu-id="afadc-134">To remove the net.tcp site binding</span></span>

1. <span data-ttu-id="afadc-135">Aby usunąć powiązanie witryny net. TCP, uruchom następujące polecenie w oknie wiersza polecenia na poziomie administratora.</span><span class="sxs-lookup"><span data-stu-id="afadc-135">To remove the net.tcp site binding run the following command in an administrator-level Command Prompt window.</span></span>

    ```console
    %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
    -bindings.[protocol='net.tcp',bindingInformation='808:*']
    ```

    > [!NOTE]
    > <span data-ttu-id="afadc-136">To polecenie jest pojedynczym wierszem tekstu.</span><span class="sxs-lookup"><span data-stu-id="afadc-136">This command is a single line of text.</span></span>

## <a name="see-also"></a><span data-ttu-id="afadc-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="afadc-137">See also</span></span>

- [<span data-ttu-id="afadc-138">Aktywacja TCP</span><span class="sxs-lookup"><span data-stu-id="afadc-138">TCP Activation</span></span>](../../../../docs/framework/wcf/samples/tcp-activation.md)
- [<span data-ttu-id="afadc-139">Aktywacja usługi MSMQ</span><span class="sxs-lookup"><span data-stu-id="afadc-139">MSMQ Activation</span></span>](../../../../docs/framework/wcf/samples/msmq-activation.md)
- [<span data-ttu-id="afadc-140">Aktywowanie elementu NamedPipe</span><span class="sxs-lookup"><span data-stu-id="afadc-140">NamedPipe Activation</span></span>](../../../../docs/framework/wcf/samples/namedpipe-activation.md)
- [<span data-ttu-id="afadc-141">Funkcje hostingu sieci szkieletowej aplikacji systemu Windows Server</span><span class="sxs-lookup"><span data-stu-id="afadc-141">Windows Server App Fabric Hosting Features</span></span>](https://go.microsoft.com/fwlink/?LinkId=201276)
