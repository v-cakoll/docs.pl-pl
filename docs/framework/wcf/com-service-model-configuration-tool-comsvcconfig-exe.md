---
title: Narzędzie konfiguracji modelu usług COM+ (ComSvcConfig.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, COM+ integration
- WCF, COM+ integration
ms.assetid: 7717c6c2-85fc-418b-a8ed-bad8e61cec5c
ms.openlocfilehash: 13368dfa7ca9d7981ac146b87e83f77077eaf537
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320735"
---
# <a name="com-service-model-configuration-tool-comsvcconfigexe"></a><span data-ttu-id="f387f-102">Narzędzie konfiguracji modelu usług COM+ (ComSvcConfig.exe)</span><span class="sxs-lookup"><span data-stu-id="f387f-102">COM+ Service Model Configuration Tool (ComSvcConfig.exe)</span></span>
<span data-ttu-id="f387f-103">Narzędzie wiersza polecenia konfiguracji modelu usług COM+ (ComSvcConfig. exe) umożliwia konfigurowanie interfejsów COM+, które mają być udostępniane jako usługi sieci Web.</span><span class="sxs-lookup"><span data-stu-id="f387f-103">The COM+ Service Model Configuration command-line tool (ComSvcConfig.exe) enables you to configure COM+ interfaces to be exposed as Web services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f387f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f387f-104">Syntax</span></span>  
  
```console  
ComSvcConfig.exe /install | /uninstall | /list [/application:<ApplicationID | ApplicationName>] [/contract:<ClassID | ProgID | *,InterfaceID | InterfaceName | *>] [/hosting:<complus | was>] [/webSite:<WebsiteName>] [/webDirectory:<WebDirectoryName>] [/mex] [/id] [/nologo] [/verbose] [/help] [/partial]  
```  
  
## <a name="remarks"></a><span data-ttu-id="f387f-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f387f-105">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f387f-106">Aby użyć programu ComSvcConfig. exe, musisz być administratorem na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="f387f-106">You must be an administrator on the local computer to use ComSvcConfig.exe.</span></span>  
  
 <span data-ttu-id="f387f-107">Narzędzie można znaleźć w następującej lokalizacji</span><span class="sxs-lookup"><span data-stu-id="f387f-107">The tool can be found in the following location</span></span>  
  
 <span data-ttu-id="f387f-108">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="f387f-108">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation</span></span>\  
  
 <span data-ttu-id="f387f-109">Aby uzyskać więcej informacji na temat programu ComSvcConfig. exe, zobacz [How to: use a com+ Service Model Configuration Tool](./feature-details/how-to-use-the-com-service-model-configuration-tool.md).</span><span class="sxs-lookup"><span data-stu-id="f387f-109">For more information about ComSvcConfig.exe, see [How to: Use the COM+ Service Model Configuration Tool](./feature-details/how-to-use-the-com-service-model-configuration-tool.md).</span></span>  
  
 <span data-ttu-id="f387f-110">W poniższej tabeli opisano tryby, które mogą być używane z ComSvcConfig. exe.</span><span class="sxs-lookup"><span data-stu-id="f387f-110">The following table describes the modes that can be used with ComSvcConfig.exe.</span></span>  
  
|<span data-ttu-id="f387f-111">Opcja</span><span class="sxs-lookup"><span data-stu-id="f387f-111">Option</span></span>|<span data-ttu-id="f387f-112">Opis</span><span class="sxs-lookup"><span data-stu-id="f387f-112">Description</span></span>|  
|------------|-----------------|  
|`install`|<span data-ttu-id="f387f-113">Instaluje konfigurację interfejsu COM+ dla integracji modelu usług.</span><span class="sxs-lookup"><span data-stu-id="f387f-113">Installs a configuration for a COM+ interface for Service Model integration.</span></span><br /><br /> <span data-ttu-id="f387f-114">Krótka `/i`formularza.</span><span class="sxs-lookup"><span data-stu-id="f387f-114">Short form `/i`.</span></span>|  
|`uninstall`|<span data-ttu-id="f387f-115">Odinstalowuje konfigurację interfejsu COM+ z integracji modelu usług.</span><span class="sxs-lookup"><span data-stu-id="f387f-115">Uninstalls a configuration for a COM+ interface from Service Model integration.</span></span><br /><br /> <span data-ttu-id="f387f-116">Krótka `/u`formularza.</span><span class="sxs-lookup"><span data-stu-id="f387f-116">Short form `/u`.</span></span>|  
|`list`|<span data-ttu-id="f387f-117">Wyświetla listę informacji dotyczących aplikacji i składników modelu COM+ z interfejsami skonfigurowanymi do integracji z modelem usług.</span><span class="sxs-lookup"><span data-stu-id="f387f-117">Lists information about COM+ applications and components that have interfaces that are configured for Service Model integration.</span></span><br /><br /> <span data-ttu-id="f387f-118">Krótka `/l`formularza.</span><span class="sxs-lookup"><span data-stu-id="f387f-118">Short form `/l`.</span></span>|  
  
 <span data-ttu-id="f387f-119">W poniższej tabeli opisano flagi, które mogą być używane z ComSvcConfig. exe.</span><span class="sxs-lookup"><span data-stu-id="f387f-119">The following table describes the flags that can be used with ComSvcConfig.exe.</span></span>  
  
|<span data-ttu-id="f387f-120">Opcja</span><span class="sxs-lookup"><span data-stu-id="f387f-120">Option</span></span>|<span data-ttu-id="f387f-121">Opis</span><span class="sxs-lookup"><span data-stu-id="f387f-121">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="f387f-122">`/application:` \< &#124; *ApplicationName*\></span><span class="sxs-lookup"><span data-stu-id="f387f-122">`/application:` \<*ApplicationID* &#124; *ApplicationName*\></span></span>|<span data-ttu-id="f387f-123">Określa aplikację COM+ do skonfigurowania.</span><span class="sxs-lookup"><span data-stu-id="f387f-123">Specifies the COM+ application to configure.</span></span><br /><br /> <span data-ttu-id="f387f-124">Krótka `/a`formularza.</span><span class="sxs-lookup"><span data-stu-id="f387f-124">Short form `/a`.</span></span>|  
|<span data-ttu-id="f387f-125">`/contract:` \< &#124; *ProgID* &#124; o identyfikatorze ClassID *\*InterfaceID* &#124; *InterfaceName* &#124; \*\></span><span class="sxs-lookup"><span data-stu-id="f387f-125">`/contract:` \<*ClassID*  &#124; *ProgID*  &#124; \*,*InterfaceID* &#124; *InterfaceName* &#124; \*\></span></span>|<span data-ttu-id="f387f-126">Określa składnik i interfejs modelu COM+, który zostanie skonfigurowany jako kontrakt dla usługi.</span><span class="sxs-lookup"><span data-stu-id="f387f-126">Specifies the COM+ component and interface that will be configured as the contract for the service.</span></span><br /><br /> <span data-ttu-id="f387f-127">Krótka `/c`formularza.</span><span class="sxs-lookup"><span data-stu-id="f387f-127">Short form `/c`.</span></span><br /><br /> <span data-ttu-id="f387f-128">Symbol wieloznaczny (\*) może być używany podczas określania nazw składników i interfejsów, dlatego zalecamy, aby nie używać go, ponieważ mogą ujawniać interfejsy, które nie zostały zamierzone.</span><span class="sxs-lookup"><span data-stu-id="f387f-128">While the wildcard character (\*) can be used when you specify the component and interface names, we recommend that you do not use it, because you might expose interfaces that you did not intend to.</span></span>|  
|<span data-ttu-id="f387f-129">`/hosting:` \<*complus*  &#124; *was*\></span><span class="sxs-lookup"><span data-stu-id="f387f-129">`/hosting:` \<*complus*  &#124; *was*\></span></span>|<span data-ttu-id="f387f-130">Określa, czy ma być używany tryb hostingu modelu COM+ czy tryb hostingu w sieci Web.</span><span class="sxs-lookup"><span data-stu-id="f387f-130">Specifies whether to use the COM+ hosting mode or the Web hosting mode.</span></span><br /><br /> <span data-ttu-id="f387f-131">Krótka `/h`formularza.</span><span class="sxs-lookup"><span data-stu-id="f387f-131">Short form `/h`.</span></span><br /><br /> <span data-ttu-id="f387f-132">Użycie trybu hostingu modelu COM+ wymaga jawnej aktywacji aplikacji modelu COM+.</span><span class="sxs-lookup"><span data-stu-id="f387f-132">Using the COM+ hosting mode requires explicit activation of the COM+ application.</span></span> <span data-ttu-id="f387f-133">Użycie trybu hostingu w sieci Web umożliwia automatyczne Aktywowanie aplikacji COM+ w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="f387f-133">Using the Web hosting mode allows the COM+ application to be automatically activated as required.</span></span> <span data-ttu-id="f387f-134">Jeśli aplikacja modelu COM+ jest aplikacją biblioteki, działa w procesie Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="f387f-134">If the COM+ application is a library application, it runs in the Internet Information Services (IIS) process.</span></span> <span data-ttu-id="f387f-135">Jeśli aplikacja COM+ jest aplikacją serwerową, działa w procesie dllhost. exe.</span><span class="sxs-lookup"><span data-stu-id="f387f-135">If the COM+ application is a server application, it runs in the Dllhost.exe process.</span></span>|  
|<span data-ttu-id="f387f-136">`/webSite:` \<*websitename*\></span><span class="sxs-lookup"><span data-stu-id="f387f-136">`/webSite:` \<*WebsiteName*\></span></span>|<span data-ttu-id="f387f-137">Określa witrynę sieci Web do hostowania, gdy jest używany tryb hostingu w sieci Web (patrz flaga `/hosting`).</span><span class="sxs-lookup"><span data-stu-id="f387f-137">Specifies the Web site for hosting when Web hosting mode is used (see the `/hosting` flag).</span></span><br /><br /> <span data-ttu-id="f387f-138">Krótka `/w`formularza.</span><span class="sxs-lookup"><span data-stu-id="f387f-138">Short form `/w`.</span></span><br /><br /> <span data-ttu-id="f387f-139">Jeśli żadna witryna sieci Web nie zostanie określona, zostanie użyta domyślna witryna sieci Web.</span><span class="sxs-lookup"><span data-stu-id="f387f-139">If no Web site is specified, the default Web site is used.</span></span>|  
|<span data-ttu-id="f387f-140">`/webDirectory:` \<*Webdirectoryname*\></span><span class="sxs-lookup"><span data-stu-id="f387f-140">`/webDirectory:` \<*WebDirectoryName*\></span></span>|<span data-ttu-id="f387f-141">Określa katalog wirtualny do hostowania, gdy jest używany hosting w sieci Web (patrz flaga `/hosting`).</span><span class="sxs-lookup"><span data-stu-id="f387f-141">Specifies the virtual directory for hosting when Web hosting is used (see the `/hosting` flag).</span></span><br /><br /> <span data-ttu-id="f387f-142">Krótka `/d`formularza.</span><span class="sxs-lookup"><span data-stu-id="f387f-142">Short form `/d`.</span></span>|  
|`/mex`|<span data-ttu-id="f387f-143">Dodaje punkt końcowy usługi wymiany metadanych (MEX) do domyślnej konfiguracji usługi w celu obsługi klientów, którzy chcą pobrać definicję kontraktu z usługi.</span><span class="sxs-lookup"><span data-stu-id="f387f-143">Adds a Metadata Exchange (MEX) service endpoint to the default service configuration to support clients that want to retrieve a contract definition from the service.</span></span><br /><br /> <span data-ttu-id="f387f-144">Krótka `/x`formularza.</span><span class="sxs-lookup"><span data-stu-id="f387f-144">Short form `/x`.</span></span>|  
|`/id`|<span data-ttu-id="f387f-145">Wyświetla informacje o aplikacji, składniku i interfejsie jako identyfikatory.</span><span class="sxs-lookup"><span data-stu-id="f387f-145">Displays the application, component, and interface information as IDs.</span></span><br /><br /> <span data-ttu-id="f387f-146">Krótka `/k`formularza.</span><span class="sxs-lookup"><span data-stu-id="f387f-146">Short form `/k`.</span></span>|  
|`/nologo`|<span data-ttu-id="f387f-147">Uniemożliwia programowi ComSvcConfig. exe wyświetlanie jego logo.</span><span class="sxs-lookup"><span data-stu-id="f387f-147">Prevents ComSvcConfig.exe from displaying its logo.</span></span><br /><br /> <span data-ttu-id="f387f-148">Krótka `/n`formularza.</span><span class="sxs-lookup"><span data-stu-id="f387f-148">Short form `/n`.</span></span>|  
|`/verbose`|<span data-ttu-id="f387f-149">Oprócz napotkanych błędów są wyprowadzane wszystkie ostrzeżenia lub tekst informacyjny.</span><span class="sxs-lookup"><span data-stu-id="f387f-149">Outputs all warnings or informational text in addition to any errors encountered.</span></span><br /><br /> <span data-ttu-id="f387f-150">Krótka `/v`formularza.</span><span class="sxs-lookup"><span data-stu-id="f387f-150">Short form `/v`.</span></span>|  
|`/help`|<span data-ttu-id="f387f-151">Wyświetla komunikat o użyciu.</span><span class="sxs-lookup"><span data-stu-id="f387f-151">Displays the usage message.</span></span><br /><br /> <span data-ttu-id="f387f-152">Krótka `/?`formularza.</span><span class="sxs-lookup"><span data-stu-id="f387f-152">Short form `/?`.</span></span>|  
|`/partial`|<span data-ttu-id="f387f-153">Generuje konfigurację usługi, gdy określony interfejs zawiera jeden lub więcej podpisów metod, które mogą być uwidocznione.</span><span class="sxs-lookup"><span data-stu-id="f387f-153">Generates a service configuration when the specified interface includes one or more method signatures that can be exposed.</span></span> <span data-ttu-id="f387f-154">W czasie inicjalizacji usługi zgodne metody są wyświetlane jako operacje w kontrakcie usługi, a niezgodne metody są ignorowane i nie są obecne w kontrakcie usługi.</span><span class="sxs-lookup"><span data-stu-id="f387f-154">At service initialization time, compatible methods appear as operations on the service contract, and non-compatible methods are ignored and absent from the service contract.</span></span><br /><br /> <span data-ttu-id="f387f-155">W przypadku braku tej flagi narzędzie nie generuje konfiguracji usługi, gdy określony interfejs zawiera co najmniej jedną niezgodną metodę.</span><span class="sxs-lookup"><span data-stu-id="f387f-155">If this flag is missing, the tool will not generate a service configuration when the specified interface includes one or more incompatible methods.</span></span>|  
  
## <a name="examples"></a><span data-ttu-id="f387f-156">Przykłady</span><span class="sxs-lookup"><span data-stu-id="f387f-156">Examples</span></span>  
  
### <a name="description"></a><span data-ttu-id="f387f-157">Opis</span><span class="sxs-lookup"><span data-stu-id="f387f-157">Description</span></span>  
 <span data-ttu-id="f387f-158">Poniższy przykład dodaje interfejs `IFinances` składnika `ItemOrders.IFinancial` (z aplikacji OnlineStore COM+) do zestawu interfejsów, które są udostępniane jako usługi sieci Web, przy użyciu trybu hostingu modelu COM+.</span><span class="sxs-lookup"><span data-stu-id="f387f-158">The following example adds the `IFinances` interface of the `ItemOrders.IFinancial` component (from the OnlineStore COM+ application) to the set of interfaces that are exposed as Web services, using the COM+ hosting mode.</span></span> <span data-ttu-id="f387f-159">Wszystkie ostrzeżenia będą dodatkowo wykrytymi błędami.</span><span class="sxs-lookup"><span data-stu-id="f387f-159">All warnings will be output in addition to any errors encountered.</span></span>  
  
### <a name="code"></a><span data-ttu-id="f387f-160">Kod</span><span class="sxs-lookup"><span data-stu-id="f387f-160">Code</span></span>  
  
```console  
ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus /verbose  
```  
  
### <a name="description"></a><span data-ttu-id="f387f-161">Opis</span><span class="sxs-lookup"><span data-stu-id="f387f-161">Description</span></span>  
 <span data-ttu-id="f387f-162">Poniższy przykład dodaje interfejs `IStockLevels` składnika `ItemInventory.Warehouse` (z aplikacji OnlineWarehouse COM+) do zestawu interfejsów, które są udostępniane jako usługi sieci Web, przy użyciu trybu hostingu w sieci Web.</span><span class="sxs-lookup"><span data-stu-id="f387f-162">The following example adds the `IStockLevels` interface of the `ItemInventory.Warehouse` component (from the OnlineWarehouse COM+ application) to the set of interfaces that are exposed as Web services, using the Web hosting mode.</span></span> <span data-ttu-id="f387f-163">Usługa sieci Web jest hostowana w sieci Web w katalogu wirtualnym OnlineWarehouse usług IIS.</span><span class="sxs-lookup"><span data-stu-id="f387f-163">The Web service is Web hosted in the OnlineWarehouse virtual directory of IIS.</span></span>  
  
### <a name="code"></a><span data-ttu-id="f387f-164">Kod</span><span class="sxs-lookup"><span data-stu-id="f387f-164">Code</span></span>  
  
```console  
ComSvcConfig.exe /install /application:OnlineWarehouse /contract:ItemInventory.Warehouse,IStockLevels /hosting:was /webDirectory:root/OnlineWarehouse  
```  
  
### <a name="description"></a><span data-ttu-id="f387f-165">Opis</span><span class="sxs-lookup"><span data-stu-id="f387f-165">Description</span></span>  
 <span data-ttu-id="f387f-166">Poniższy przykład usuwa interfejs `IFinances` składnika `ItemOrders.Financial` (z aplikacji OnlineStore COM+) z zestawu interfejsów, które są udostępniane jako usługi sieci Web.</span><span class="sxs-lookup"><span data-stu-id="f387f-166">The following example removes the `IFinances` interface of the `ItemOrders.Financial` component (from the OnlineStore COM+ application) from the set of interfaces that are exposed as Web services.</span></span>  
  
### <a name="code"></a><span data-ttu-id="f387f-167">Kod</span><span class="sxs-lookup"><span data-stu-id="f387f-167">Code</span></span>  
  
```console  
ComSvcConfig.exe /uninstall /application:OnlineStore /interface:ItemOrders.Financial,IFinances /hosting:complus  
```  
  
### <a name="description"></a><span data-ttu-id="f387f-168">Opis</span><span class="sxs-lookup"><span data-stu-id="f387f-168">Description</span></span>  
 <span data-ttu-id="f387f-169">W poniższym przykładzie przedstawiono aktualnie uwidocznione interfejsy obsługiwane przez model COM+ oraz odpowiednie adresy i szczegóły dotyczące powiązań dla aplikacji OnlineStore COM+ na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="f387f-169">The following example lists currently exposed COM+ hosted interfaces, along with the corresponding address and binding details, for the OnlineStore COM+ application on the local machine.</span></span>  
  
### <a name="code"></a><span data-ttu-id="f387f-170">Kod</span><span class="sxs-lookup"><span data-stu-id="f387f-170">Code</span></span>  
  
```console  
ComSvcConfig.exe /list /application:OnlineStore /hosting:complus  
```  
  
## <a name="see-also"></a><span data-ttu-id="f387f-171">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f387f-171">See also</span></span>

- [<span data-ttu-id="f387f-172">Instrukcje: używanie narzędzia konfiguracji modelu usług COM+</span><span class="sxs-lookup"><span data-stu-id="f387f-172">How to: Use the COM+ Service Model Configuration Tool</span></span>](./feature-details/how-to-use-the-com-service-model-configuration-tool.md)
