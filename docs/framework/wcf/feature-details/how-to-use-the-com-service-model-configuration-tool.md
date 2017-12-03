---
title: "Instrukcje: Używanie narzędzia konfiguracji modelu usług COM+"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: COM+ [WCF], using service model configuration tool
ms.assetid: 7e68cd8d-5fda-4641-b92f-290db874376e
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5ac7410f919ceef50827b9c98adf3ad6312122ec
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-use-the-com-service-model-configuration-tool"></a><span data-ttu-id="c4087-102">Instrukcje: Używanie narzędzia konfiguracji modelu usług COM+</span><span class="sxs-lookup"><span data-stu-id="c4087-102">How to: Use the COM+ Service Model Configuration Tool</span></span>
<span data-ttu-id="c4087-103">Po wybraniu odpowiednich trybu hostingu umożliwia skonfigurowanie interfejsów aplikacji, które mają być widoczne jako usługi sieci Web narzędzie wiersza polecenia konfiguracji modelu usług COM + (ComSvcConfig.exe).</span><span class="sxs-lookup"><span data-stu-id="c4087-103">Once you have selected an appropriate hosting mode, use the COM+ Service Model Configuration command-line tool (ComSvcConfig.exe) to configure the application interfaces that will be exposed as Web services.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c4087-104">Musi być administratorowi wykonaj jedną z następujących zadań na komputerze.</span><span class="sxs-lookup"><span data-stu-id="c4087-104">You must be an administrator on the machine to perform any of the following tasks.</span></span>  
  
 <span data-ttu-id="c4087-105">Za pomocą ComSvcConfig.exe na komputerze z systemem Windows 7 Konfiguruj usługę sieci web, aby używać najnowszej wersji modelu usług (obecnie 4.5), wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="c4087-105">When using ComSvcConfig.exe on a Windows 7 machine to configure a web service to use the latest service model version (currently v4.5), perform the following steps:</span></span>  
  
1.  <span data-ttu-id="c4087-106">Ustaw klucz rejestru `[HKEY_LOCAL_COMPUTER\SOFTWARE\Microsoft\.NETFramework]\OnlyUseLatestCLR` na wartość DWORD 0x00000001</span><span class="sxs-lookup"><span data-stu-id="c4087-106">Set the registry key  `[HKEY_LOCAL_COMPUTER\SOFTWARE\Microsoft\.NETFramework]\OnlyUseLatestCLR` to a DWORD value of 0x00000001</span></span>  
  
2.  <span data-ttu-id="c4087-107">Uruchom comsvcconfig.exe</span><span class="sxs-lookup"><span data-stu-id="c4087-107">Run comsvcconfig.exe</span></span>  
  
3.  <span data-ttu-id="c4087-108">Przywróć klucz rejestru dodanej w kroku 1 do oryginalnej wartości lub usuń go, jeśli nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="c4087-108">Revert the registry key added in step 1 back to its original value, or delete it if did not exist.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c4087-109">Ważne jest przywrócenie tego klucza rejestru.</span><span class="sxs-lookup"><span data-stu-id="c4087-109">Reverting this registry key is important.</span></span> <span data-ttu-id="c4087-110">Jest to klucz zgodności.</span><span class="sxs-lookup"><span data-stu-id="c4087-110">This is a compatibility key.</span></span> <span data-ttu-id="c4087-111">Przywracanie nie ta zmiana może spowodować problemy z innych aplikacji .NET uruchomionych na komputerze).</span><span class="sxs-lookup"><span data-stu-id="c4087-111">Not reverting this change may cause issues with other .NET applications running on the machine).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="c4087-112">Podczas używania ComSvcConfig.exe/install na komputerze z systemem Windows 8 okno dialogowe jest wyświetlane, podając "aplikacji na komputerze wymaga następujących funkcji systemu Windows: .NET Framework 3.5 (obejmuje .NET 2.0 i .NET 3.0" Jeśli nie jest zainstalowany program .NET Framework 3.5.</span><span class="sxs-lookup"><span data-stu-id="c4087-112">When using ComSvcConfig.exe  /install on a Windows 8 machine a dialog is displayed stating "An app on your PC needs the following Windows feature: .NET Framework 3.5 (includes .NET 2.0 and .NET 3.0" if .NET Framework 3.5 is not installed.</span></span> <span data-ttu-id="c4087-113">Można zignorować to okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="c4087-113">This dialog may be ignored.</span></span> <span data-ttu-id="c4087-114">Alternatywnie możesz mniejszyć OnlyUseLatestCLR klucza rejestru na wartość DWORD 0x00000001</span><span class="sxs-lookup"><span data-stu-id="c4087-114">Alternatively you can sed the OnlyUseLatestCLR registry key to a DWORD value of 0x00000001</span></span>  
  
### <a name="to-add-an-interface-to-the-set-of-interfaces-that-are-to-be-exposed-as-web-services-using-the-com-hosting-mode"></a><span data-ttu-id="c4087-115">Aby dodać interfejs do zestawu interfejsów, które mają być udostępniany jako usługi sieci Web, przy użyciu trybu hostingu modelu COM +</span><span class="sxs-lookup"><span data-stu-id="c4087-115">To add an interface to the set of interfaces that are to be exposed as Web services, using the COM+ hosting mode</span></span>  
  
-   <span data-ttu-id="c4087-116">Uruchom przy użyciu ComSvcConfig `/install` i `/hosting:complus` opcje, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="c4087-116">Run ComSvcConfig using the `/install` and `/hosting:complus` options, as shown in the following example.</span></span>  
  
    ```  
    ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus /verbose  
    ```  
  
     <span data-ttu-id="c4087-117">Polecenie dodaje `IFinances` interfejsu `ItemOrders.IFinancial` składnik (z OnlineStore aplikacji COM +), aby zestaw interfejsów, które mają być widoczne jako usługi sieci Web.</span><span class="sxs-lookup"><span data-stu-id="c4087-117">The command adds the `IFinances` interface of the `ItemOrders.IFinancial` component (from the OnlineStore COM+ application) to the set of interfaces that will be exposed as Web services.</span></span> <span data-ttu-id="c4087-118">Usługa korzysta z trybu obsługi modelu COM + i dlatego wymaga aktywację jawnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c4087-118">The service uses the COM+ hosting mode and therefore requires explicit application activation.</span></span>  
  
     <span data-ttu-id="c4087-119">Gdy znaku wieloznacznego gwiazdki (*) może służyć do działania składnika i interfejsie, unikać używania go, ponieważ można udostępniać tylko wybrane funkcje jako usługę sieci Web.</span><span class="sxs-lookup"><span data-stu-id="c4087-119">While the wildcard asterisk (*) character can be used for the component and the interface, avoid using it because you might want to expose only selected functionality as a Web service.</span></span> <span data-ttu-id="c4087-120">Jeśli są uruchomione przy przyszłych wersjach tego składnika, przy użyciu symbolu wieloznacznego przypadkowo może narazić interfejsów, które mogły nie być wyświetlany, jeśli określono składni konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="c4087-120">If run with a future version of this component, using the wildcard may unintentionally expose interfaces that may not have been present when the configuration syntax was determined.</span></span>  
  
     <span data-ttu-id="c4087-121">/ Verbose — opcja powoduje, że narzędzie do wyświetlania ostrzeżeń oprócz wszelkie błędy.</span><span class="sxs-lookup"><span data-stu-id="c4087-121">The /verbose option instructs the tool to display warnings in addition to any errors.</span></span>  
  
     <span data-ttu-id="c4087-122">Kontrakt usługi narażonych będzie zawierać wszystkie metody z `IFinances` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="c4087-122">The contract for the exposed service will contain all of the methods from the `IFinances` interface.</span></span>  
  
### <a name="to-add-only-specific-methods-from-an-interface-to-the-set-of-interfaces-that-are-to-be-exposed-as-web-services-using-the-com-hosting-mode"></a><span data-ttu-id="c4087-123">Aby dodać tylko konkretnych metod z interfejsem do zestawu interfejsów, które mają być udostępniany jako usługi sieci Web, przy użyciu trybu hostingu modelu COM +</span><span class="sxs-lookup"><span data-stu-id="c4087-123">To add only specific methods from an interface to the set of interfaces that are to be exposed as Web services, using the COM+ hosting mode</span></span>  
  
-   <span data-ttu-id="c4087-124">Uruchom przy użyciu ComSvcConfig `/install` i `/hosting:complus` opcje za pomocą nazw jawnych metod wymaganych, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="c4087-124">Run ComSvcConfig using the `/install` and `/hosting:complus` options with explicit naming of the required methods, as shown in the following example.</span></span>  
  
    ```  
    ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances.{Credit,Debit} /hosting:complus /verbose  
    ```  
  
     <span data-ttu-id="c4087-125">Polecenie dodaje tylko `Credit` i `Debit` metody `IFinances` interfejsu jako operacje narażonych serwisowej.</span><span class="sxs-lookup"><span data-stu-id="c4087-125">The command adds only the `Credit` and `Debit` methods from the `IFinances` interface as operations to the exposed service contract.</span></span> <span data-ttu-id="c4087-126">Wszystkie inne metody w interfejsie zostanie pominięta kontrakt i nie będzie można wywołać z klientami usługi sieci Web.</span><span class="sxs-lookup"><span data-stu-id="c4087-126">All other methods on the interface will be omitted from the contract and will not be callable from Web service clients.</span></span>  
  
### <a name="to-add-an-interface-to-the-set-of-interfaces-that-are-to-be-exposed-as-web-services-using-the-web-hosting-mode"></a><span data-ttu-id="c4087-127">Aby dodać interfejs do zestawu interfejsów, które mają być udostępniany jako usługi sieci Web, przy użyciu trybu hostingu sieci Web</span><span class="sxs-lookup"><span data-stu-id="c4087-127">To add an interface to the set of interfaces that are to be exposed as Web services, using the Web hosting mode</span></span>  
  
-   <span data-ttu-id="c4087-128">Uruchom przy użyciu ComSvcConfig `/install` opcji i `/hosting:was` opcji, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="c4087-128">Run ComSvcConfig using the `/install` option and the `/hosting:was` option, as shown in the following example.</span></span>  
  
    ```  
    ComSvcConfig.exe /install /application:OnlineWarehouse /contract:ItemInventory.Warehouse,IStockLevels /hosting:was /webDirectory:root/OnlineWarehouse /mex /verbose  
    ```  
  
     <span data-ttu-id="c4087-129">Polecenie dodaje `IStockLevels` interfejs w `ItemInventory.Warehouse` składnik (z OnlineWarehouse aplikacji COM +), aby zestaw interfejsów, które mają być widoczne jako usługi sieci Web.</span><span class="sxs-lookup"><span data-stu-id="c4087-129">The command adds the `IStockLevels` interface on the `ItemInventory.Warehouse` component (from the OnlineWarehouse COM+ application) to the set of interfaces that will be exposed as Web services.</span></span> <span data-ttu-id="c4087-130">Usługa jest hostowana w OnlineWarehouse katalog wirtualny usług IIS, a nie w modelu COM + w sieci Web i w związku z tym aplikacja jest aktywowana automatycznie zgodnie z wymaganiami.</span><span class="sxs-lookup"><span data-stu-id="c4087-130">The service is Web hosted in the OnlineWarehouse virtual directory of IIS rather than in COM+, and thus the application is automatically activated as required.</span></span>  
  
     <span data-ttu-id="c4087-131">Do korzystania z sieci Web hostowanych w procesie konfiguracji, aplikacja COM + musi być skonfigurowana do uruchamiania jako aplikacja biblioteki, a nie aplikacji serwera za pomocą konsoli administracyjnej usług składowych.</span><span class="sxs-lookup"><span data-stu-id="c4087-131">To use the Web-hosted in-process configuration, the COM+ application must be configured to run as a Library application rather than a Server application using the Component Services administration console.</span></span> <span data-ttu-id="c4087-132">Aplikacje skonfigurowane jako aplikacji serwerowych Tryb standardowy hostowanych w sieci Web i pociągnąć za sobą przeskoku procesu przetwarzania każdego żądania.</span><span class="sxs-lookup"><span data-stu-id="c4087-132">Applications configured as Server applications use the standard Web-hosted mode and incur a process hop to process each request.</span></span>  
  
     <span data-ttu-id="c4087-133">`/mex` Opcja dodaje dodatkowe punktu końcowego usługi wymiany metadanych (MEX), który używa tego samego transportu jako punkt końcowy usługi aplikacji do obsługi klientów, które ma zostać pobrane definicję kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="c4087-133">The `/mex` option adds an additional Metadata Exchange (MEX) service endpoint that uses the same transport as the application's service endpoint to support clients that want to retrieve a contract definition from the service.</span></span>  
  
### <a name="to-remove-a-web-service-for-a-specified-interface"></a><span data-ttu-id="c4087-134">Aby usunąć usługi sieci Web dla określonego interfejsu</span><span class="sxs-lookup"><span data-stu-id="c4087-134">To remove a Web service for a specified interface</span></span>  
  
-   <span data-ttu-id="c4087-135">Uruchom przy użyciu ComSvcConfig `/uninstall` opcji, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="c4087-135">Run ComSvcConfig using the `/uninstall` option, as shown in the following example.</span></span>  
  
    ```  
    ComSvcConfig.exe /uninstall /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus  
    ```  
  
     <span data-ttu-id="c4087-136">Usuwa polecenie `IFinances` interfejs w `ItemOrders.Financial` części (z OnlineStore aplikacji COM +).</span><span class="sxs-lookup"><span data-stu-id="c4087-136">The command removes the `IFinances` interface on the `ItemOrders.Financial` component (from the OnlineStore COM+ application).</span></span>  
  
### <a name="to-list-currently-exposed-interfaces"></a><span data-ttu-id="c4087-137">Aby wyświetlić listę aktualnie interfejsów</span><span class="sxs-lookup"><span data-stu-id="c4087-137">To list currently exposed interfaces</span></span>  
  
-   <span data-ttu-id="c4087-138">Uruchom przy użyciu ComSvcConfig `/list` opcji, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="c4087-138">Run ComSvcConfig using the `/list` option, as shown in the following example.</span></span>  
  
    ```  
    ComSvcConfig.exe /list  
    ```  
  
     <span data-ttu-id="c4087-139">Polecenie wyświetla listę aktualnie interfejsów, oraz odpowiedni adres i powiązanie uzyskać szczegółowe informacje, zakres na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="c4087-139">The command lists the currently exposed interfaces, along with the corresponding address and binding details, scoped to the local machine.</span></span>  
  
### <a name="to-list-specific-currently-exposed-interfaces"></a><span data-ttu-id="c4087-140">Aby wyświetlić listę aktualnie określonego widoczne interfejsów</span><span class="sxs-lookup"><span data-stu-id="c4087-140">To list specific currently exposed interfaces</span></span>  
  
-   <span data-ttu-id="c4087-141">Uruchom przy użyciu ComSvcConfig `/list` opcji, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="c4087-141">Run ComSvcConfig using the `/list` option, as shown in the following example.</span></span>  
  
    ```  
    ComSvcConfig.exe /list /application:OnlineStore /hosting:complus  
    ```  
  
     <span data-ttu-id="c4087-142">List poleceń aktualnie widoczne COM +-hostowanej interfejsów, oraz odpowiedni adres i powiązanie uzyskać szczegółowe informacje, na podstawie OnlineStore COM + na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="c4087-142">The command lists currently exposed COM+-hosted interfaces, along with the corresponding address and binding details, for the OnlineStore COM+ application on the local machine.</span></span>  
  
### <a name="to-display-help-on-the-options-that-can-be-used-with-the-utility"></a><span data-ttu-id="c4087-143">Aby wyświetlić Pomoc na temat opcji, które mogą służyć za pomocą narzędzia</span><span class="sxs-lookup"><span data-stu-id="c4087-143">To display help on the options that can be used with the utility</span></span>  
  
-   <span data-ttu-id="c4087-144">Uruchom przy użyciu ComSvcConfig /?</span><span class="sxs-lookup"><span data-stu-id="c4087-144">Run ComSvcConfig using the /?</span></span> <span data-ttu-id="c4087-145">opcja, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="c4087-145">option, as shown in the following example.</span></span>  
  
    ```  
    ComSvcConfig.exe /?  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="c4087-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c4087-146">See Also</span></span>  
 [<span data-ttu-id="c4087-147">Przegląd integrowania z modelu COM + aplikacjami</span><span class="sxs-lookup"><span data-stu-id="c4087-147">Integrating with COM+ Applications Overview</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications-overview.md)
