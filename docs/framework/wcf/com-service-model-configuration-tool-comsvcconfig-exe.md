---
title: Narzędzie konfiguracji modelu usług COM+ (ComSvcConfig.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, COM+ integration
- WCF, COM+ integration
ms.assetid: 7717c6c2-85fc-418b-a8ed-bad8e61cec5c
ms.openlocfilehash: 6d0967355e64640e0fd5c81f04a5bf4f33c7b3f7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61608843"
---
# <a name="com-service-model-configuration-tool-comsvcconfigexe"></a><span data-ttu-id="d211d-102">Narzędzie konfiguracji modelu usług COM+ (ComSvcConfig.exe)</span><span class="sxs-lookup"><span data-stu-id="d211d-102">COM+ Service Model Configuration Tool (ComSvcConfig.exe)</span></span>
<span data-ttu-id="d211d-103">Narzędzie wiersza polecenia w konfiguracji modelu usług COM + (ComSvcConfig.exe) umożliwia skonfigurowanie interfejsów modelu COM + być udostępniane jako usługi sieci Web.</span><span class="sxs-lookup"><span data-stu-id="d211d-103">The COM+ Service Model Configuration command-line tool (ComSvcConfig.exe) enables you to configure COM+ interfaces to be exposed as Web services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d211d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d211d-104">Syntax</span></span>  
  
```  
ComSvcConfig.exe /install | /uninstall | /list [/application:<ApplicationID | ApplicationName>] [/contract:<ClassID | ProgID | *,InterfaceID | InterfaceName | *>] [/hosting:<complus | was>] [/webSite:<WebsiteName>] [/webDirectory:<WebDirectoryName>] [/mex] [/id] [/nologo] [/verbose] [/help] [/partial]  
```  
  
## <a name="remarks"></a><span data-ttu-id="d211d-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d211d-105">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d211d-106">Musisz być administratorem na komputerze lokalnym do użycia ComSvcConfig.exe.</span><span class="sxs-lookup"><span data-stu-id="d211d-106">You must be an administrator on the local computer to use ComSvcConfig.exe.</span></span>  
  
 <span data-ttu-id="d211d-107">Narzędzie można znaleźć w następującej lokalizacji</span><span class="sxs-lookup"><span data-stu-id="d211d-107">The tool can be found in the following location</span></span>  
  
 <span data-ttu-id="d211d-108">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation\\</span><span class="sxs-lookup"><span data-stu-id="d211d-108">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation\\</span></span>  
  
 <span data-ttu-id="d211d-109">Aby uzyskać więcej informacji na temat ComSvcConfig.exe zobacz [jak: Używanie narzędzia konfiguracji modelu usług COM +](../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md).</span><span class="sxs-lookup"><span data-stu-id="d211d-109">For more information about ComSvcConfig.exe, see [How to: Use the COM+ Service Model Configuration Tool](../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md).</span></span>  
  
 <span data-ttu-id="d211d-110">W poniższej tabeli opisano tryby, które mogą być używane z ComSvcConfig.exe.</span><span class="sxs-lookup"><span data-stu-id="d211d-110">The following table describes the modes that can be used with ComSvcConfig.exe.</span></span>  
  
|<span data-ttu-id="d211d-111">Opcja</span><span class="sxs-lookup"><span data-stu-id="d211d-111">Option</span></span>|<span data-ttu-id="d211d-112">Opis</span><span class="sxs-lookup"><span data-stu-id="d211d-112">Description</span></span>|  
|------------|-----------------|  
|`install`|<span data-ttu-id="d211d-113">Instaluje konfiguracji interfejsu COM + Service Model integration.</span><span class="sxs-lookup"><span data-stu-id="d211d-113">Installs a configuration for a COM+ interface for Service Model integration.</span></span><br /><br /> <span data-ttu-id="d211d-114">Skrócona forma `/i`.</span><span class="sxs-lookup"><span data-stu-id="d211d-114">Short form `/i`.</span></span>|  
|`uninstall`|<span data-ttu-id="d211d-115">Odinstalowuje konfigurację interfejsu COM + z modelu usług integracji.</span><span class="sxs-lookup"><span data-stu-id="d211d-115">Uninstalls a configuration for a COM+ interface from Service Model integration.</span></span><br /><br /> <span data-ttu-id="d211d-116">Skrócona forma `/u`.</span><span class="sxs-lookup"><span data-stu-id="d211d-116">Short form `/u`.</span></span>|  
|`list`|<span data-ttu-id="d211d-117">Wyświetla informacje na temat składników mających interfejsy, które są skonfigurowane do integracji modelu usług i aplikacji COM +.</span><span class="sxs-lookup"><span data-stu-id="d211d-117">Lists information about COM+ applications and components that have interfaces that are configured for Service Model integration.</span></span><br /><br /> <span data-ttu-id="d211d-118">Skrócona forma `/l`.</span><span class="sxs-lookup"><span data-stu-id="d211d-118">Short form `/l`.</span></span>|  
  
 <span data-ttu-id="d211d-119">W poniższej tabeli opisano flagi, które mogą być używane z ComSvcConfig.exe.</span><span class="sxs-lookup"><span data-stu-id="d211d-119">The following table describes the flags that can be used with ComSvcConfig.exe.</span></span>  
  
|<span data-ttu-id="d211d-120">Opcja</span><span class="sxs-lookup"><span data-stu-id="d211d-120">Option</span></span>|<span data-ttu-id="d211d-121">Opis</span><span class="sxs-lookup"><span data-stu-id="d211d-121">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="d211d-122">`/application:` \<*ApplicationID* &#124; *ApplicationName*\></span><span class="sxs-lookup"><span data-stu-id="d211d-122">`/application:` \<*ApplicationID* &#124; *ApplicationName*\></span></span>|<span data-ttu-id="d211d-123">Określa aplikacji COM +, aby skonfigurować.</span><span class="sxs-lookup"><span data-stu-id="d211d-123">Specifies the COM+ application to configure.</span></span><br /><br /> <span data-ttu-id="d211d-124">Skrócona forma `/a`.</span><span class="sxs-lookup"><span data-stu-id="d211d-124">Short form `/a`.</span></span>|  
|<span data-ttu-id="d211d-125">`/contract:` \<*Identyfikator klasy* &#124; *ProgID* &#124; \*,*InterfaceID* &#124; *InterfaceName*    &#124; \*\></span><span class="sxs-lookup"><span data-stu-id="d211d-125">`/contract:` \<*ClassID*  &#124; *ProgID*  &#124; \*,*InterfaceID* &#124; *InterfaceName* &#124; \*\></span></span>|<span data-ttu-id="d211d-126">Określa składnik COM + i interfejs, który zostanie skonfigurowany jako kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="d211d-126">Specifies the COM+ component and interface that will be configured as the contract for the service.</span></span><br /><br /> <span data-ttu-id="d211d-127">Skrócona forma `/c`.</span><span class="sxs-lookup"><span data-stu-id="d211d-127">Short form `/c`.</span></span><br /><br /> <span data-ttu-id="d211d-128">Podczas gdy znak symbolu wieloznacznego (\*) mogą być używane podczas określenia nazwy składnika i interfejs zaleca się nie korzystać, ponieważ może uwidaczniać interfejsy, które nie ma do.</span><span class="sxs-lookup"><span data-stu-id="d211d-128">While the wildcard character (\*) can be used when you specify the component and interface names, we recommend that you do not use it, because you might expose interfaces that you did not intend to.</span></span>|  
|<span data-ttu-id="d211d-129">`/hosting:` \<*complus*  &#124; *was*\></span><span class="sxs-lookup"><span data-stu-id="d211d-129">`/hosting:` \<*complus*  &#124; *was*\></span></span>|<span data-ttu-id="d211d-130">Określa, czy używać modelu COM + hosting trybu lub trybie hostingu w sieci Web.</span><span class="sxs-lookup"><span data-stu-id="d211d-130">Specifies whether to use the COM+ hosting mode or the Web hosting mode.</span></span><br /><br /> <span data-ttu-id="d211d-131">Skrócona forma `/h`.</span><span class="sxs-lookup"><span data-stu-id="d211d-131">Short form `/h`.</span></span><br /><br /> <span data-ttu-id="d211d-132">Za pomocą modelu COM + hosting trybu wymaga jawnego aktywacji aplikacji COM +.</span><span class="sxs-lookup"><span data-stu-id="d211d-132">Using the COM+ hosting mode requires explicit activation of the COM+ application.</span></span> <span data-ttu-id="d211d-133">Korzystanie z sieci Web w trybie hostingu umożliwia aplikacji COM + automatycznie aktywowane jako wymagane.</span><span class="sxs-lookup"><span data-stu-id="d211d-133">Using the Web hosting mode allows the COM+ application to be automatically activated as required.</span></span> <span data-ttu-id="d211d-134">Jeśli aplikacja COM + jest aplikacja biblioteki, działa w procesie Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="d211d-134">If the COM+ application is a library application, it runs in the Internet Information Services (IIS) process.</span></span> <span data-ttu-id="d211d-135">Aplikacja modelu COM + w przypadku aplikacji serwera, jest uruchamiany w procesie Dllhost.exe.</span><span class="sxs-lookup"><span data-stu-id="d211d-135">If the COM+ application is a server application, it runs in the Dllhost.exe process.</span></span>|  
|<span data-ttu-id="d211d-136">`/webSite:` \<*WebsiteName*\></span><span class="sxs-lookup"><span data-stu-id="d211d-136">`/webSite:` \<*WebsiteName*\></span></span>|<span data-ttu-id="d211d-137">Określa witryny sieci Web do hostowania, gdy tryb hostingu w sieci Web jest używana (zobacz `/hosting` flagi).</span><span class="sxs-lookup"><span data-stu-id="d211d-137">Specifies the Web site for hosting when Web hosting mode is used (see the `/hosting` flag).</span></span><br /><br /> <span data-ttu-id="d211d-138">Skrócona forma `/w`.</span><span class="sxs-lookup"><span data-stu-id="d211d-138">Short form `/w`.</span></span><br /><br /> <span data-ttu-id="d211d-139">Jeśli ma witryny sieci Web jest określony, domyślna witryna sieci Web jest używana.</span><span class="sxs-lookup"><span data-stu-id="d211d-139">If no Web site is specified, the default Web site is used.</span></span>|  
|<span data-ttu-id="d211d-140">`/webDirectory:` \<*WebDirectoryName*\></span><span class="sxs-lookup"><span data-stu-id="d211d-140">`/webDirectory:` \<*WebDirectoryName*\></span></span>|<span data-ttu-id="d211d-141">Określa katalog wirtualny dla hostingu stosowania hosting sieci Web (zobacz `/hosting` flagi).</span><span class="sxs-lookup"><span data-stu-id="d211d-141">Specifies the virtual directory for hosting when Web hosting is used (see the `/hosting` flag).</span></span><br /><br /> <span data-ttu-id="d211d-142">Skrócona forma `/d`.</span><span class="sxs-lookup"><span data-stu-id="d211d-142">Short form `/d`.</span></span>|  
|`/mex`|<span data-ttu-id="d211d-143">W domyślnej konfiguracji Usługa do obsługi klientów, które mają zostać pobrane definicję kontraktu usługi, dodaje punkt końcowy usługi wymiany metadanych (MEX).</span><span class="sxs-lookup"><span data-stu-id="d211d-143">Adds a Metadata Exchange (MEX) service endpoint to the default service configuration to support clients that want to retrieve a contract definition from the service.</span></span><br /><br /> <span data-ttu-id="d211d-144">Skrócona forma `/x`.</span><span class="sxs-lookup"><span data-stu-id="d211d-144">Short form `/x`.</span></span>|  
|`/id`|<span data-ttu-id="d211d-145">Wyświetla aplikacji, składników i informacje o interfejsie jako identyfikatorów.</span><span class="sxs-lookup"><span data-stu-id="d211d-145">Displays the application, component, and interface information as IDs.</span></span><br /><br /> <span data-ttu-id="d211d-146">Skrócona forma `/k`.</span><span class="sxs-lookup"><span data-stu-id="d211d-146">Short form `/k`.</span></span>|  
|`/nologo`|<span data-ttu-id="d211d-147">ComSvcConfig.exe uniemożliwia wyświetlanie logo jej.</span><span class="sxs-lookup"><span data-stu-id="d211d-147">Prevents ComSvcConfig.exe from displaying its logo.</span></span><br /><br /> <span data-ttu-id="d211d-148">Skrócona forma `/n`.</span><span class="sxs-lookup"><span data-stu-id="d211d-148">Short form `/n`.</span></span>|  
|`/verbose`|<span data-ttu-id="d211d-149">Wyświetla wszystkie ostrzeżenia i tekst informacyjny, oprócz wszystkich wykrytych błędów.</span><span class="sxs-lookup"><span data-stu-id="d211d-149">Outputs all warnings or informational text in addition to any errors encountered.</span></span><br /><br /> <span data-ttu-id="d211d-150">Skrócona forma `/v`.</span><span class="sxs-lookup"><span data-stu-id="d211d-150">Short form `/v`.</span></span>|  
|`/help`|<span data-ttu-id="d211d-151">Wyświetla komunikat o sposobie użycia.</span><span class="sxs-lookup"><span data-stu-id="d211d-151">Displays the usage message.</span></span><br /><br /> <span data-ttu-id="d211d-152">Skrócona forma `/?`.</span><span class="sxs-lookup"><span data-stu-id="d211d-152">Short form `/?`.</span></span>|  
|`/partial`|<span data-ttu-id="d211d-153">Generuje konfiguracji usługi, gdy określony interfejs zawiera podpisy metod, które mogą być udostępniane.</span><span class="sxs-lookup"><span data-stu-id="d211d-153">Generates a service configuration when the specified interface includes one or more method signatures that can be exposed.</span></span> <span data-ttu-id="d211d-154">Podczas inicjowania usługi zgodne metody są wyświetlane jako operacje na kontrakt usługi i metod niezgodnych są ignorowane i znajduje się poza kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="d211d-154">At service initialization time, compatible methods appear as operations on the service contract, and non-compatible methods are ignored and absent from the service contract.</span></span><br /><br /> <span data-ttu-id="d211d-155">Jeśli brakuje tej flagi, narzędzie nie wygeneruje konfiguracji usługi, gdy określony interfejs zawiera jedną lub więcej metod niezgodnych.</span><span class="sxs-lookup"><span data-stu-id="d211d-155">If this flag is missing, the tool will not generate a service configuration when the specified interface includes one or more incompatible methods.</span></span>|  
  
## <a name="examples"></a><span data-ttu-id="d211d-156">Przykłady</span><span class="sxs-lookup"><span data-stu-id="d211d-156">Examples</span></span>  
  
### <a name="description"></a><span data-ttu-id="d211d-157">Opis</span><span class="sxs-lookup"><span data-stu-id="d211d-157">Description</span></span>  
 <span data-ttu-id="d211d-158">W poniższym przykładzie dodano `IFinances` interfejsu `ItemOrders.IFinancial` składnika (z OnlineStore aplikacji COM +) do zestawu interfejsów, które są dostępne jako usługi sieci Web, przy użyciu trybu macierzystego modelu COM +.</span><span class="sxs-lookup"><span data-stu-id="d211d-158">The following example adds the `IFinances` interface of the `ItemOrders.IFinancial` component (from the OnlineStore COM+ application) to the set of interfaces that are exposed as Web services, using the COM+ hosting mode.</span></span> <span data-ttu-id="d211d-159">Wszystkie ostrzeżenia będą dane wyjściowe, oprócz wszystkich wykrytych błędów.</span><span class="sxs-lookup"><span data-stu-id="d211d-159">All warnings will be output in addition to any errors encountered.</span></span>  
  
### <a name="code"></a><span data-ttu-id="d211d-160">Kod</span><span class="sxs-lookup"><span data-stu-id="d211d-160">Code</span></span>  
  
```  
ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus /verbose  
```  
  
### <a name="description"></a><span data-ttu-id="d211d-161">Opis</span><span class="sxs-lookup"><span data-stu-id="d211d-161">Description</span></span>  
 <span data-ttu-id="d211d-162">W poniższym przykładzie dodano `IStockLevels` interfejsu `ItemInventory.Warehouse` składnika (z OnlineWarehouse aplikacji COM +) do zestawu interfejsów, które są dostępne jako usługi sieci Web w trybie hostingu w sieci Web.</span><span class="sxs-lookup"><span data-stu-id="d211d-162">The following example adds the `IStockLevels` interface of the `ItemInventory.Warehouse` component (from the OnlineWarehouse COM+ application) to the set of interfaces that are exposed as Web services, using the Web hosting mode.</span></span> <span data-ttu-id="d211d-163">Usługa sieci Web jest sieci Web hostowanych w katalogu wirtualnym OnlineWarehouse usług IIS.</span><span class="sxs-lookup"><span data-stu-id="d211d-163">The Web service is Web hosted in the OnlineWarehouse virtual directory of IIS.</span></span>  
  
### <a name="code"></a><span data-ttu-id="d211d-164">Kod</span><span class="sxs-lookup"><span data-stu-id="d211d-164">Code</span></span>  
  
```  
ComSvcConfig.exe /install /application:OnlineWarehouse /contract:ItemInventory.Warehouse,IStockLevels /hosting:was /webDirectory:root/OnlineWarehouse  
```  
  
### <a name="description"></a><span data-ttu-id="d211d-165">Opis</span><span class="sxs-lookup"><span data-stu-id="d211d-165">Description</span></span>  
 <span data-ttu-id="d211d-166">Poniższy przykład usuwa `IFinances` interfejsu `ItemOrders.Financial` składnika (z OnlineStore aplikacji COM +) z zestawu interfejsów, które są dostępne jako usługi sieci Web.</span><span class="sxs-lookup"><span data-stu-id="d211d-166">The following example removes the `IFinances` interface of the `ItemOrders.Financial` component (from the OnlineStore COM+ application) from the set of interfaces that are exposed as Web services.</span></span>  
  
### <a name="code"></a><span data-ttu-id="d211d-167">Kod</span><span class="sxs-lookup"><span data-stu-id="d211d-167">Code</span></span>  
  
```  
ComSvcConfig.exe /uninstall /application:OnlineStore /interface:ItemOrders.Financial,IFinances /hosting:complus  
```  
  
### <a name="description"></a><span data-ttu-id="d211d-168">Opis</span><span class="sxs-lookup"><span data-stu-id="d211d-168">Description</span></span>  
 <span data-ttu-id="d211d-169">Na poniższych listach przykład aktualnie widoczne interfejsów modelu COM + hostowane, oraz odpowiedni adres i powiązanie uzyskać szczegółowe informacje, dla aplikacji OnlineStore COM +, na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="d211d-169">The following example lists currently exposed COM+ hosted interfaces, along with the corresponding address and binding details, for the OnlineStore COM+ application on the local machine.</span></span>  
  
### <a name="code"></a><span data-ttu-id="d211d-170">Kod</span><span class="sxs-lookup"><span data-stu-id="d211d-170">Code</span></span>  
  
```  
ComSvcConfig.exe /list /application:OnlineStore /hosting:complus  
```  
  
## <a name="see-also"></a><span data-ttu-id="d211d-171">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d211d-171">See also</span></span>

- [<span data-ttu-id="d211d-172">Instrukcje: Używanie narzędzia konfiguracji modelu usług COM +</span><span class="sxs-lookup"><span data-stu-id="d211d-172">How to: Use the COM+ Service Model Configuration Tool</span></span>](../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md)
