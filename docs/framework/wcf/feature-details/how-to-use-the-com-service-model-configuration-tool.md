---
title: 'Instrukcje: Używanie narzędzia konfiguracji modelu usług COM+'
ms.date: 03/30/2017
helpviewer_keywords:
- COM+ [WCF], using service model configuration tool
ms.assetid: 7e68cd8d-5fda-4641-b92f-290db874376e
ms.openlocfilehash: 528e46a47daa6df865308592eb41658369a74b6e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54736250"
---
# <a name="how-to-use-the-com-service-model-configuration-tool"></a><span data-ttu-id="539fc-102">Instrukcje: Używanie narzędzia konfiguracji modelu usług COM+</span><span class="sxs-lookup"><span data-stu-id="539fc-102">How to: Use the COM+ Service Model Configuration Tool</span></span>
<span data-ttu-id="539fc-103">Po wybraniu odpowiedni tryb hostingu skonfiguruj interfejsy aplikacji, które będą dostępne jako usługi sieci Web za pomocą narzędzia wiersza polecenia w konfiguracji modelu usług COM + (ComSvcConfig.exe).</span><span class="sxs-lookup"><span data-stu-id="539fc-103">Once you have selected an appropriate hosting mode, use the COM+ Service Model Configuration command-line tool (ComSvcConfig.exe) to configure the application interfaces that will be exposed as Web services.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="539fc-104">Musi być administratorem na komputerze, aby wykonać dowolne z następujących czynności.</span><span class="sxs-lookup"><span data-stu-id="539fc-104">You must be an administrator on the machine to perform any of the following tasks.</span></span>  
  
 <span data-ttu-id="539fc-105">Korzystając z ComSvcConfig.exe na komputerze z Windows 7 można skonfigurować usługę sieci web, aby korzystać z najnowszej wersji modelu usługi (obecnie 4.5), wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="539fc-105">When using ComSvcConfig.exe on a Windows 7 machine to configure a web service to use the latest service model version (currently v4.5), perform the following steps:</span></span>  
  
1.  <span data-ttu-id="539fc-106">Ustaw klucz rejestru `[HKEY_LOCAL_COMPUTER\SOFTWARE\Microsoft\.NETFramework]\OnlyUseLatestCLR` wartość DWORD 0x00000001</span><span class="sxs-lookup"><span data-stu-id="539fc-106">Set the registry key  `[HKEY_LOCAL_COMPUTER\SOFTWARE\Microsoft\.NETFramework]\OnlyUseLatestCLR` to a DWORD value of 0x00000001</span></span>  
  
2.  <span data-ttu-id="539fc-107">Uruchom comsvcconfig.exe</span><span class="sxs-lookup"><span data-stu-id="539fc-107">Run comsvcconfig.exe</span></span>  
  
3.  <span data-ttu-id="539fc-108">Przywróć klucz rejestru, dodanej w kroku 1 do oryginalnej wartości lub usuń go, jeśli nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="539fc-108">Revert the registry key added in step 1 back to its original value, or delete it if did not exist.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="539fc-109">Ważne jest przywrócenie tego klucza rejestru.</span><span class="sxs-lookup"><span data-stu-id="539fc-109">Reverting this registry key is important.</span></span> <span data-ttu-id="539fc-110">Jest to klucz zgodności.</span><span class="sxs-lookup"><span data-stu-id="539fc-110">This is a compatibility key.</span></span> <span data-ttu-id="539fc-111">Przywracanie nie ta zmiana może spowodować problemy z innymi aplikacjami .NET na maszynie).</span><span class="sxs-lookup"><span data-stu-id="539fc-111">Not reverting this change may cause issues with other .NET applications running on the machine).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="539fc-112">Korzystając z ComSvcConfig.exe/install na komputerze Windows 8 okno dialogowe jest wyświetlony "aplikacji na komputerze wymaga następującej funkcji Windows: .NET Framework 3.5 (obejmuje .NET 2.0 i .NET 3.0" Jeśli nie zainstalowano programu .NET Framework 3.5.</span><span class="sxs-lookup"><span data-stu-id="539fc-112">When using ComSvcConfig.exe  /install on a Windows 8 machine a dialog is displayed stating "An app on your PC needs the following Windows feature: .NET Framework 3.5 (includes .NET 2.0 and .NET 3.0" if .NET Framework 3.5 is not installed.</span></span> <span data-ttu-id="539fc-113">Można zignorować to okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="539fc-113">This dialog may be ignored.</span></span> <span data-ttu-id="539fc-114">Alternatywnie możesz sed OnlyUseLatestCLR klucza rejestru w celu wartość DWORD 0x00000001</span><span class="sxs-lookup"><span data-stu-id="539fc-114">Alternatively you can sed the OnlyUseLatestCLR registry key to a DWORD value of 0x00000001</span></span>  
  
### <a name="to-add-an-interface-to-the-set-of-interfaces-that-are-to-be-exposed-as-web-services-using-the-com-hosting-mode"></a><span data-ttu-id="539fc-115">Aby dodać interfejs do zestawu interfejsów, które mają być widoczne jako usług sieci Web, przy użyciu trybu obsługi modelu COM +</span><span class="sxs-lookup"><span data-stu-id="539fc-115">To add an interface to the set of interfaces that are to be exposed as Web services, using the COM+ hosting mode</span></span>  
  
-   <span data-ttu-id="539fc-116">Uruchamianie przy użyciu ComSvcConfig `/install` i `/hosting:complus` opcji, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="539fc-116">Run ComSvcConfig using the `/install` and `/hosting:complus` options, as shown in the following example.</span></span>  
  
    ```  
    ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus /verbose  
    ```  
  
     <span data-ttu-id="539fc-117">Polecenie dodaje `IFinances` interfejsu `ItemOrders.IFinancial` składnika (z OnlineStore aplikacji COM +) do zestawu interfejsów, które będą dostępne jako usługi sieci Web.</span><span class="sxs-lookup"><span data-stu-id="539fc-117">The command adds the `IFinances` interface of the `ItemOrders.IFinancial` component (from the OnlineStore COM+ application) to the set of interfaces that will be exposed as Web services.</span></span> <span data-ttu-id="539fc-118">Usługa korzysta z modelu COM + hosting tryb i w związku z tym wymaga składnika Aktywacja jawne aplikacji.</span><span class="sxs-lookup"><span data-stu-id="539fc-118">The service uses the COM+ hosting mode and therefore requires explicit application activation.</span></span>  
  
     <span data-ttu-id="539fc-119">Chociaż wieloznacznego gwiazdki (\*) mogą być używane dla składnika i interfejsu, Unikaj korzystania z niego, ponieważ może uwidaczniać tylko wybrane funkcjonalność w postaci usługi sieci Web.</span><span class="sxs-lookup"><span data-stu-id="539fc-119">While the wildcard asterisk (\*) character can be used for the component and the interface, avoid using it because you might want to expose only selected functionality as a Web service.</span></span> <span data-ttu-id="539fc-120">Uruchom z przyszłych wersji tego składnika, z zastosowaniem symbolu wieloznacznego przypadkowo może narazić interfejsów, które nie mogły być obecna, gdy określono składni konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="539fc-120">If run with a future version of this component, using the wildcard may unintentionally expose interfaces that may not have been present when the configuration syntax was determined.</span></span>  
  
     <span data-ttu-id="539fc-121">/ Verbose — opcja powoduje, że narzędzie, aby wyświetlić ostrzeżenia, oprócz wszelkie błędy.</span><span class="sxs-lookup"><span data-stu-id="539fc-121">The /verbose option instructs the tool to display warnings in addition to any errors.</span></span>  
  
     <span data-ttu-id="539fc-122">Kontrakt usługi narażonych będzie zawierać wszystkie metody z `IFinances` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="539fc-122">The contract for the exposed service will contain all of the methods from the `IFinances` interface.</span></span>  
  
### <a name="to-add-only-specific-methods-from-an-interface-to-the-set-of-interfaces-that-are-to-be-exposed-as-web-services-using-the-com-hosting-mode"></a><span data-ttu-id="539fc-123">Aby dodać tylko konkretnych metod z interfejsu do zestawu interfejsów, które mają być widoczne jako usług sieci Web, przy użyciu trybu obsługi modelu COM +</span><span class="sxs-lookup"><span data-stu-id="539fc-123">To add only specific methods from an interface to the set of interfaces that are to be exposed as Web services, using the COM+ hosting mode</span></span>  
  
-   <span data-ttu-id="539fc-124">Uruchamianie przy użyciu ComSvcConfig `/install` i `/hosting:complus` opcje nazewnictwa jawnych metod wymaganych, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="539fc-124">Run ComSvcConfig using the `/install` and `/hosting:complus` options with explicit naming of the required methods, as shown in the following example.</span></span>  
  
    ```  
    ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances.{Credit,Debit} /hosting:complus /verbose  
    ```  
  
     <span data-ttu-id="539fc-125">Polecenie dodaje tylko `Credit` i `Debit` metody z `IFinances` interfejs jako operacji kontraktu usługi narażone.</span><span class="sxs-lookup"><span data-stu-id="539fc-125">The command adds only the `Credit` and `Debit` methods from the `IFinances` interface as operations to the exposed service contract.</span></span> <span data-ttu-id="539fc-126">Wszystkie inne metody w interfejsie zostanie pominięta kontrakt i nie będzie można wywołać za pomocą klientów usługi sieci Web.</span><span class="sxs-lookup"><span data-stu-id="539fc-126">All other methods on the interface will be omitted from the contract and will not be callable from Web service clients.</span></span>  
  
### <a name="to-add-an-interface-to-the-set-of-interfaces-that-are-to-be-exposed-as-web-services-using-the-web-hosting-mode"></a><span data-ttu-id="539fc-127">Aby dodać interfejs do zestawu interfejsów, które mają być widoczne jako usług sieci Web, przy użyciu trybu hostingu w sieci Web</span><span class="sxs-lookup"><span data-stu-id="539fc-127">To add an interface to the set of interfaces that are to be exposed as Web services, using the Web hosting mode</span></span>  
  
-   <span data-ttu-id="539fc-128">Uruchamianie przy użyciu ComSvcConfig `/install` opcji i `/hosting:was` opcji, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="539fc-128">Run ComSvcConfig using the `/install` option and the `/hosting:was` option, as shown in the following example.</span></span>  
  
    ```  
    ComSvcConfig.exe /install /application:OnlineWarehouse /contract:ItemInventory.Warehouse,IStockLevels /hosting:was /webDirectory:root/OnlineWarehouse /mex /verbose  
    ```  
  
     <span data-ttu-id="539fc-129">Polecenie dodaje `IStockLevels` interfejsu na `ItemInventory.Warehouse` składnik (z OnlineWarehouse aplikacji COM +), aby zestaw interfejsów, które będą dostępne jako usługi sieci Web.</span><span class="sxs-lookup"><span data-stu-id="539fc-129">The command adds the `IStockLevels` interface on the `ItemInventory.Warehouse` component (from the OnlineWarehouse COM+ application) to the set of interfaces that will be exposed as Web services.</span></span> <span data-ttu-id="539fc-130">Usługa jest hostowana w katalogu wirtualnym OnlineWarehouse usług IIS, a nie w modelu COM + w sieci Web i dlatego automatycznie aktywowano aplikację zgodnie z wymaganiami.</span><span class="sxs-lookup"><span data-stu-id="539fc-130">The service is Web hosted in the OnlineWarehouse virtual directory of IIS rather than in COM+, and thus the application is automatically activated as required.</span></span>  
  
     <span data-ttu-id="539fc-131">Do korzystania z konfiguracji w trakcie hostowanych w sieci Web, aplikacji COM +, musi być skonfigurowany do uruchamiania jako aplikacji biblioteki, a nie aplikacji serwera przy użyciu konsoli administracyjnej usługi składowe.</span><span class="sxs-lookup"><span data-stu-id="539fc-131">To use the Web-hosted in-process configuration, the COM+ application must be configured to run as a Library application rather than a Server application using the Component Services administration console.</span></span> <span data-ttu-id="539fc-132">Aplikacje, skonfigurowany jako serwer aplikacji używanie standardowego trybu hostowanej w sieci Web bez ponoszenia przeskoku procesu przetwarzania każdego żądania.</span><span class="sxs-lookup"><span data-stu-id="539fc-132">Applications configured as Server applications use the standard Web-hosted mode and incur a process hop to process each request.</span></span>  
  
     <span data-ttu-id="539fc-133">`/mex` Opcja dodaje dodatkowe metadane programu Exchange (MEX) usługi punktu końcowego, który używa tego samego transportu jako punkt końcowy usługi aplikacji do obsługi klientów, które mają zostać pobrane definicję kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="539fc-133">The `/mex` option adds an additional Metadata Exchange (MEX) service endpoint that uses the same transport as the application's service endpoint to support clients that want to retrieve a contract definition from the service.</span></span>  
  
### <a name="to-remove-a-web-service-for-a-specified-interface"></a><span data-ttu-id="539fc-134">Aby usunąć usługę sieci Web dla określonego interfejsu</span><span class="sxs-lookup"><span data-stu-id="539fc-134">To remove a Web service for a specified interface</span></span>  
  
-   <span data-ttu-id="539fc-135">Uruchamianie przy użyciu ComSvcConfig `/uninstall` opcji, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="539fc-135">Run ComSvcConfig using the `/uninstall` option, as shown in the following example.</span></span>  
  
    ```  
    ComSvcConfig.exe /uninstall /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus  
    ```  
  
     <span data-ttu-id="539fc-136">Polecenie usuwa `IFinances` interfejsu na `ItemOrders.Financial` składnika (z OnlineStore aplikacji COM +).</span><span class="sxs-lookup"><span data-stu-id="539fc-136">The command removes the `IFinances` interface on the `ItemOrders.Financial` component (from the OnlineStore COM+ application).</span></span>  
  
### <a name="to-list-currently-exposed-interfaces"></a><span data-ttu-id="539fc-137">Aby wyświetlić listę aktualnie interfejsów</span><span class="sxs-lookup"><span data-stu-id="539fc-137">To list currently exposed interfaces</span></span>  
  
-   <span data-ttu-id="539fc-138">Uruchamianie przy użyciu ComSvcConfig `/list` opcji, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="539fc-138">Run ComSvcConfig using the `/list` option, as shown in the following example.</span></span>  
  
    ```  
    ComSvcConfig.exe /list  
    ```  
  
     <span data-ttu-id="539fc-139">Polecenie wyświetla listę aktualnie interfejsów, oraz odpowiedni adres i powiązanie uzyskać szczegółowe informacje, ograniczone do komputera lokalnego.</span><span class="sxs-lookup"><span data-stu-id="539fc-139">The command lists the currently exposed interfaces, along with the corresponding address and binding details, scoped to the local machine.</span></span>  
  
### <a name="to-list-specific-currently-exposed-interfaces"></a><span data-ttu-id="539fc-140">Aby wyświetlić listę określonych aktualnie widoczne interfejsów</span><span class="sxs-lookup"><span data-stu-id="539fc-140">To list specific currently exposed interfaces</span></span>  
  
-   <span data-ttu-id="539fc-141">Uruchamianie przy użyciu ComSvcConfig `/list` opcji, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="539fc-141">Run ComSvcConfig using the `/list` option, as shown in the following example.</span></span>  
  
    ```  
    ComSvcConfig.exe /list /application:OnlineStore /hosting:complus  
    ```  
  
     <span data-ttu-id="539fc-142">Listy poleceń aktualnie widoczne COM + — obsługiwane interfejsy, wraz z odpowiednim adresem i szczegóły powiązania aplikacji OnlineStore COM +, na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="539fc-142">The command lists currently exposed COM+-hosted interfaces, along with the corresponding address and binding details, for the OnlineStore COM+ application on the local machine.</span></span>  
  
### <a name="to-display-help-on-the-options-that-can-be-used-with-the-utility"></a><span data-ttu-id="539fc-143">Aby wyświetlić Pomoc na temat opcji, które mogą służyć za pomocą narzędzia</span><span class="sxs-lookup"><span data-stu-id="539fc-143">To display help on the options that can be used with the utility</span></span>  
  
-   <span data-ttu-id="539fc-144">Uruchamianie przy użyciu ComSvcConfig /?</span><span class="sxs-lookup"><span data-stu-id="539fc-144">Run ComSvcConfig using the /?</span></span> <span data-ttu-id="539fc-145">opcja, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="539fc-145">option, as shown in the following example.</span></span>  
  
    ```  
    ComSvcConfig.exe /?  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="539fc-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="539fc-146">See also</span></span>
- [<span data-ttu-id="539fc-147">Przegląd integrowania z aplikacjami COM+</span><span class="sxs-lookup"><span data-stu-id="539fc-147">Integrating with COM+ Applications Overview</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications-overview.md)
