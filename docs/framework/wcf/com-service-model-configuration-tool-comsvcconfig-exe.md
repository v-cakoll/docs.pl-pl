---
title: Narzędzie konfiguracji modelu usług COM+ (ComSvcConfig.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, COM+ integration
- WCF, COM+ integration
ms.assetid: 7717c6c2-85fc-418b-a8ed-bad8e61cec5c
ms.openlocfilehash: db4518a66c54574f498c4657e25a29676f0f720a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33462068"
---
# <a name="com-service-model-configuration-tool-comsvcconfigexe"></a><span data-ttu-id="28740-102">Narzędzie konfiguracji modelu usług COM+ (ComSvcConfig.exe)</span><span class="sxs-lookup"><span data-stu-id="28740-102">COM+ Service Model Configuration Tool (ComSvcConfig.exe)</span></span>
<span data-ttu-id="28740-103">Narzędzie wiersza polecenia konfiguracji modelu usług COM + (ComSvcConfig.exe) umożliwia skonfigurowanie interfejsów modelu COM + mają być uwidaczniane jako usługi sieci Web.</span><span class="sxs-lookup"><span data-stu-id="28740-103">The COM+ Service Model Configuration command-line tool (ComSvcConfig.exe) enables you to configure COM+ interfaces to be exposed as Web services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28740-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="28740-104">Syntax</span></span>  
  
```  
ComSvcConfig.exe /install | /uninstall | /list [/application:<ApplicationID | ApplicationName>] [/contract:<ClassID | ProgID | *,InterfaceID | InterfaceName | *>] [/hosting:<complus | was>] [/webSite:<WebsiteName>] [/webDirectory:<WebDirectoryName>] [/mex] [/id] [/nologo] [/verbose] [/help] [/partial]  
```  
  
## <a name="remarks"></a><span data-ttu-id="28740-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="28740-105">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="28740-106">Musi być administratorem na komputerze lokalnym do użycia ComSvcConfig.exe.</span><span class="sxs-lookup"><span data-stu-id="28740-106">You must be an administrator on the local computer to use ComSvcConfig.exe.</span></span>  
  
 <span data-ttu-id="28740-107">Narzędzie można znaleźć w następującej lokalizacji</span><span class="sxs-lookup"><span data-stu-id="28740-107">The tool can be found in the following location</span></span>  
  
 <span data-ttu-id="28740-108">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Foundation\ komunikacji</span><span class="sxs-lookup"><span data-stu-id="28740-108">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation\\</span></span>  
  
 <span data-ttu-id="28740-109">Aby uzyskać więcej informacji o ComSvcConfig.exe, zobacz [porady: Użyj modelu COM + narzędzia konfiguracji modelu usług](../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md).</span><span class="sxs-lookup"><span data-stu-id="28740-109">For more information about ComSvcConfig.exe, see [How to: Use the COM+ Service Model Configuration Tool](../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md).</span></span>  
  
 <span data-ttu-id="28740-110">W poniższej tabeli opisano tryby, które mogą być używane z ComSvcConfig.exe.</span><span class="sxs-lookup"><span data-stu-id="28740-110">The following table describes the modes that can be used with ComSvcConfig.exe.</span></span>  
  
|<span data-ttu-id="28740-111">Opcja</span><span class="sxs-lookup"><span data-stu-id="28740-111">Option</span></span>|<span data-ttu-id="28740-112">Opis</span><span class="sxs-lookup"><span data-stu-id="28740-112">Description</span></span>|  
|------------|-----------------|  
|`install`|<span data-ttu-id="28740-113">Instaluje konfiguracji interfejsu COM + integracji modelu usług.</span><span class="sxs-lookup"><span data-stu-id="28740-113">Installs a configuration for a COM+ interface for Service Model integration.</span></span><br /><br /> <span data-ttu-id="28740-114">Skrócona forma `/i`.</span><span class="sxs-lookup"><span data-stu-id="28740-114">Short form `/i`.</span></span>|  
|`uninstall`|<span data-ttu-id="28740-115">Odinstalowuje konfiguracji dla interfejsu COM + z integracji modelu usług.</span><span class="sxs-lookup"><span data-stu-id="28740-115">Uninstalls a configuration for a COM+ interface from Service Model integration.</span></span><br /><br /> <span data-ttu-id="28740-116">Skrócona forma `/u`.</span><span class="sxs-lookup"><span data-stu-id="28740-116">Short form `/u`.</span></span>|  
|`list`|<span data-ttu-id="28740-117">Wyświetla informacje o aplikacji COM + i składników, które interfejsy, które są skonfigurowane dla integracji modelu usług.</span><span class="sxs-lookup"><span data-stu-id="28740-117">Lists information about COM+ applications and components that have interfaces that are configured for Service Model integration.</span></span><br /><br /> <span data-ttu-id="28740-118">Skrócona forma `/l`.</span><span class="sxs-lookup"><span data-stu-id="28740-118">Short form `/l`.</span></span>|  
  
 <span data-ttu-id="28740-119">W poniższej tabeli opisano flagi, które mogą być używane z ComSvcConfig.exe.</span><span class="sxs-lookup"><span data-stu-id="28740-119">The following table describes the flags that can be used with ComSvcConfig.exe.</span></span>  
  
|<span data-ttu-id="28740-120">Opcja</span><span class="sxs-lookup"><span data-stu-id="28740-120">Option</span></span>|<span data-ttu-id="28740-121">Opis</span><span class="sxs-lookup"><span data-stu-id="28740-121">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="28740-122">`/application:` \<*Identyfikator aplikacji ApplicationID* &#124; *ApplicationName*\></span><span class="sxs-lookup"><span data-stu-id="28740-122">`/application:` \<*ApplicationID* &#124; *ApplicationName*\></span></span>|<span data-ttu-id="28740-123">Określa konfigurowania aplikacji COM +.</span><span class="sxs-lookup"><span data-stu-id="28740-123">Specifies the COM+ application to configure.</span></span><br /><br /> <span data-ttu-id="28740-124">Skrócona forma `/a`.</span><span class="sxs-lookup"><span data-stu-id="28740-124">Short form `/a`.</span></span>|  
|<span data-ttu-id="28740-125">`/contract:` \<*Identyfikator klasy* &#124; *ProgID* &#124; \*,*identyfikator interfejsu* &#124; *InterfaceName*    &#124; \*\></span><span class="sxs-lookup"><span data-stu-id="28740-125">`/contract:` \<*ClassID*  &#124; *ProgID*  &#124; \*,*InterfaceID* &#124; *InterfaceName* &#124; \*\></span></span>|<span data-ttu-id="28740-126">Określa interfejs, który zostanie skonfigurowany jako kontraktu usługi i składnik modelu COM +.</span><span class="sxs-lookup"><span data-stu-id="28740-126">Specifies the COM+ component and interface that will be configured as the contract for the service.</span></span><br /><br /> <span data-ttu-id="28740-127">Skrócona forma `/c`.</span><span class="sxs-lookup"><span data-stu-id="28740-127">Short form `/c`.</span></span><br /><br /> <span data-ttu-id="28740-128">Podczas symbol wieloznaczny (\*) można używać podczas określania nazwy składników i interfejsów, zalecamy, aby używać go, ponieważ może narazić interfejsów, które nie ma do.</span><span class="sxs-lookup"><span data-stu-id="28740-128">While the wildcard character (\*) can be used when you specify the component and interface names, we recommend that you do not use it, because you might expose interfaces that you did not intend to.</span></span>|  
|<span data-ttu-id="28740-129">`/hosting:` \<*ComPlus* &#124; *został* \></span><span class="sxs-lookup"><span data-stu-id="28740-129">`/hosting:` \<*complus*  &#124; *was*\></span></span>|<span data-ttu-id="28740-130">Określa, czy ma być używany tryb lub trybu hostingu sieci Web COM +.</span><span class="sxs-lookup"><span data-stu-id="28740-130">Specifies whether to use the COM+ hosting mode or the Web hosting mode.</span></span><br /><br /> <span data-ttu-id="28740-131">Skrócona forma `/h`.</span><span class="sxs-lookup"><span data-stu-id="28740-131">Short form `/h`.</span></span><br /><br /> <span data-ttu-id="28740-132">Za pomocą modelu COM + można zastosować trybu hostingu wymaga jawnego aktywacji aplikacji COM +.</span><span class="sxs-lookup"><span data-stu-id="28740-132">Using the COM+ hosting mode requires explicit activation of the COM+ application.</span></span> <span data-ttu-id="28740-133">Korzystanie z sieci Web trybu hostingu umożliwia aplikacji COM + automatycznie aktywowane jako wymagane.</span><span class="sxs-lookup"><span data-stu-id="28740-133">Using the Web hosting mode allows the COM+ application to be automatically activated as required.</span></span> <span data-ttu-id="28740-134">Aplikacja COM + w przypadku aplikacji biblioteki, jest uruchamiana w procesie Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="28740-134">If the COM+ application is a library application, it runs in the Internet Information Services (IIS) process.</span></span> <span data-ttu-id="28740-135">Aplikacja COM + w przypadku aplikacji serwera, jest uruchamiana w procesie Dllhost.exe.</span><span class="sxs-lookup"><span data-stu-id="28740-135">If the COM+ application is a server application, it runs in the Dllhost.exe process.</span></span>|  
|<span data-ttu-id="28740-136">`/webSite:` \<*Podaną*\></span><span class="sxs-lookup"><span data-stu-id="28740-136">`/webSite:` \<*WebsiteName*\></span></span>|<span data-ttu-id="28740-137">Określa witrynę sieci Web do obsługi, gdy trybu hostingu w sieci Web jest używana (zobacz `/hosting` flagi).</span><span class="sxs-lookup"><span data-stu-id="28740-137">Specifies the Web site for hosting when Web hosting mode is used (see the `/hosting` flag).</span></span><br /><br /> <span data-ttu-id="28740-138">Skrócona forma `/w`.</span><span class="sxs-lookup"><span data-stu-id="28740-138">Short form `/w`.</span></span><br /><br /> <span data-ttu-id="28740-139">Jeśli zostanie określona żadna witryna sieci Web, jest używana domyślna witryna sieci Web.</span><span class="sxs-lookup"><span data-stu-id="28740-139">If no Web site is specified, the default Web site is used.</span></span>|  
|<span data-ttu-id="28740-140">`/webDirectory:` \<*WebDirectoryName*\></span><span class="sxs-lookup"><span data-stu-id="28740-140">`/webDirectory:` \<*WebDirectoryName*\></span></span>|<span data-ttu-id="28740-141">Określa katalog wirtualny dla hostingu, gdy jest używana usługa hostingu sieci Web (zobacz `/hosting` flagi).</span><span class="sxs-lookup"><span data-stu-id="28740-141">Specifies the virtual directory for hosting when Web hosting is used (see the `/hosting` flag).</span></span><br /><br /> <span data-ttu-id="28740-142">Skrócona forma `/d`.</span><span class="sxs-lookup"><span data-stu-id="28740-142">Short form `/d`.</span></span>|  
|`/mex`|<span data-ttu-id="28740-143">Dodaje punkt końcowy usługi wymiany metadanych (MEX) w domyślnej konfiguracji usługi do obsługi klientów, które ma zostać pobrane z usługi definicję kontraktu.</span><span class="sxs-lookup"><span data-stu-id="28740-143">Adds a Metadata Exchange (MEX) service endpoint to the default service configuration to support clients that want to retrieve a contract definition from the service.</span></span><br /><br /> <span data-ttu-id="28740-144">Skrócona forma `/x`.</span><span class="sxs-lookup"><span data-stu-id="28740-144">Short form `/x`.</span></span>|  
|`/id`|<span data-ttu-id="28740-145">Wyświetla aplikacji, składników i informacje o interfejsie jako identyfikatorów.</span><span class="sxs-lookup"><span data-stu-id="28740-145">Displays the application, component, and interface information as IDs.</span></span><br /><br /> <span data-ttu-id="28740-146">Skrócona forma `/k`.</span><span class="sxs-lookup"><span data-stu-id="28740-146">Short form `/k`.</span></span>|  
|`/nologo`|<span data-ttu-id="28740-147">Uniemożliwia wyświetlanie logo jego ComSvcConfig.exe.</span><span class="sxs-lookup"><span data-stu-id="28740-147">Prevents ComSvcConfig.exe from displaying its logo.</span></span><br /><br /> <span data-ttu-id="28740-148">Skrócona forma `/n`.</span><span class="sxs-lookup"><span data-stu-id="28740-148">Short form `/n`.</span></span>|  
|`/verbose`|<span data-ttu-id="28740-149">Wyświetla wszystkie ostrzeżenia i tekst informacyjny oprócz wszystkich wykrytych błędów.</span><span class="sxs-lookup"><span data-stu-id="28740-149">Outputs all warnings or informational text in addition to any errors encountered.</span></span><br /><br /> <span data-ttu-id="28740-150">Skrócona forma `/v`.</span><span class="sxs-lookup"><span data-stu-id="28740-150">Short form `/v`.</span></span>|  
|`/help`|<span data-ttu-id="28740-151">Wyświetla komunikat o sposobie użycia.</span><span class="sxs-lookup"><span data-stu-id="28740-151">Displays the usage message.</span></span><br /><br /> <span data-ttu-id="28740-152">Skrócona forma `/?`.</span><span class="sxs-lookup"><span data-stu-id="28740-152">Short form `/?`.</span></span>|  
|`/partial`|<span data-ttu-id="28740-153">Generuje konfiguracji usługi, jeśli określony interfejs zawiera podpisy metod, które można uwidocznić.</span><span class="sxs-lookup"><span data-stu-id="28740-153">Generates a service configuration when the specified interface includes one or more method signatures that can be exposed.</span></span> <span data-ttu-id="28740-154">Podczas inicjowania usługi zgodne metody są wyświetlane jako operacje na kontrakt usługi i metody niezgodnymi są ignorowane i znajduje się poza kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="28740-154">At service initialization time, compatible methods appear as operations on the service contract, and non-compatible methods are ignored and absent from the service contract.</span></span><br /><br /> <span data-ttu-id="28740-155">W przypadku braku tej flagi narzędzie nie będą generowane konfiguracji usługi, jeśli określony interfejs zawiera co najmniej jedną metodę niezgodne.</span><span class="sxs-lookup"><span data-stu-id="28740-155">If this flag is missing, the tool will not generate a service configuration when the specified interface includes one or more incompatible methods.</span></span>|  
  
## <a name="examples"></a><span data-ttu-id="28740-156">Przykłady</span><span class="sxs-lookup"><span data-stu-id="28740-156">Examples</span></span>  
  
### <a name="description"></a><span data-ttu-id="28740-157">Opis</span><span class="sxs-lookup"><span data-stu-id="28740-157">Description</span></span>  
 <span data-ttu-id="28740-158">W poniższym przykładzie dodano `IFinances` interfejsu `ItemOrders.IFinancial` składnik (z OnlineStore aplikacji COM +), aby zestaw interfejsów, które są dostępne jako usługi sieci Web, przy użyciu trybu hostingu modelu COM +.</span><span class="sxs-lookup"><span data-stu-id="28740-158">The following example adds the `IFinances` interface of the `ItemOrders.IFinancial` component (from the OnlineStore COM+ application) to the set of interfaces that are exposed as Web services, using the COM+ hosting mode.</span></span> <span data-ttu-id="28740-159">Wszystkie ostrzeżenia będą dane wyjściowe, oprócz wszystkich wykrytych błędów.</span><span class="sxs-lookup"><span data-stu-id="28740-159">All warnings will be output in addition to any errors encountered.</span></span>  
  
### <a name="code"></a><span data-ttu-id="28740-160">Kod</span><span class="sxs-lookup"><span data-stu-id="28740-160">Code</span></span>  
  
```  
ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus /verbose  
```  
  
### <a name="description"></a><span data-ttu-id="28740-161">Opis</span><span class="sxs-lookup"><span data-stu-id="28740-161">Description</span></span>  
 <span data-ttu-id="28740-162">W poniższym przykładzie dodano `IStockLevels` interfejsu `ItemInventory.Warehouse` składnik (z OnlineWarehouse aplikacji COM +), aby zestaw interfejsów, które są dostępne jako usługi sieci Web, przy użyciu trybu hostingu.</span><span class="sxs-lookup"><span data-stu-id="28740-162">The following example adds the `IStockLevels` interface of the `ItemInventory.Warehouse` component (from the OnlineWarehouse COM+ application) to the set of interfaces that are exposed as Web services, using the Web hosting mode.</span></span> <span data-ttu-id="28740-163">Usługi sieci Web jest sieci Web hostowanych w OnlineWarehouse katalog wirtualny usług IIS.</span><span class="sxs-lookup"><span data-stu-id="28740-163">The Web service is Web hosted in the OnlineWarehouse virtual directory of IIS.</span></span>  
  
### <a name="code"></a><span data-ttu-id="28740-164">Kod</span><span class="sxs-lookup"><span data-stu-id="28740-164">Code</span></span>  
  
```  
ComSvcConfig.exe /install /application:OnlineWarehouse /contract:ItemInventory.Warehouse,IStockLevels /hosting:was /webDirectory:root/OnlineWarehouse  
```  
  
### <a name="description"></a><span data-ttu-id="28740-165">Opis</span><span class="sxs-lookup"><span data-stu-id="28740-165">Description</span></span>  
 <span data-ttu-id="28740-166">Poniższy przykład umożliwia usunięcie `IFinances` interfejsu `ItemOrders.Financial` składnik (z OnlineStore aplikacji COM +) z zestawu interfejsów, które są dostępne jako usługi sieci Web.</span><span class="sxs-lookup"><span data-stu-id="28740-166">The following example removes the `IFinances` interface of the `ItemOrders.Financial` component (from the OnlineStore COM+ application) from the set of interfaces that are exposed as Web services.</span></span>  
  
### <a name="code"></a><span data-ttu-id="28740-167">Kod</span><span class="sxs-lookup"><span data-stu-id="28740-167">Code</span></span>  
  
```  
ComSvcConfig.exe /uninstall /application:OnlineStore /interface:ItemOrders.Financial,IFinances /hosting:complus  
```  
  
### <a name="description"></a><span data-ttu-id="28740-168">Opis</span><span class="sxs-lookup"><span data-stu-id="28740-168">Description</span></span>  
 <span data-ttu-id="28740-169">Na poniższych listach przykład widoczne obecnie interfejsów modelu COM + hostowanych, oraz odpowiedni adres i powiązanie uzyskać szczegółowe informacje, na podstawie OnlineStore COM + na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="28740-169">The following example lists currently exposed COM+ hosted interfaces, along with the corresponding address and binding details, for the OnlineStore COM+ application on the local machine.</span></span>  
  
### <a name="code"></a><span data-ttu-id="28740-170">Kod</span><span class="sxs-lookup"><span data-stu-id="28740-170">Code</span></span>  
  
```  
ComSvcConfig.exe /list /application:OnlineStore /hosting:complus  
```  
  
## <a name="see-also"></a><span data-ttu-id="28740-171">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="28740-171">See Also</span></span>  
 [<span data-ttu-id="28740-172">Instrukcje: używanie narzędzia konfiguracji modelu usług COM+</span><span class="sxs-lookup"><span data-stu-id="28740-172">How to: Use the COM+ Service Model Configuration Tool</span></span>](../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md)
