---
title: Narzędzie rejestracji usług przepływu pracy (WFServicesReg.exe)
ms.date: 03/30/2017
ms.assetid: 9e92c87b-99c5-4e8d-9d53-7944cc2b47d3
ms.openlocfilehash: 0a9cd5039c085f82f5507c93ebe0855cc620825d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916822"
---
# <a name="workflow-service-registration-tool-wfservicesregexe"></a><span data-ttu-id="e2776-102">Narzędzie rejestracji usług przepływu pracy (WFServicesReg.exe)</span><span class="sxs-lookup"><span data-stu-id="e2776-102">WorkFlow Service Registration Tool (WFServicesReg.exe)</span></span>
<span data-ttu-id="e2776-103">Narzędzie rejestracji usług przepływu pracy (WFServicesReg. exe) to autonomiczne narzędzie, które służy do dodawania, usuwania lub naprawiania elementów konfiguracji dla usług Windows Workflow Foundation (WF).</span><span class="sxs-lookup"><span data-stu-id="e2776-103">Workflow Services Registration tool (WFServicesReg.exe) is a stand-alone tool that can be used to add, remove, or repair the configuration elements for Windows Workflow Foundation (WF) services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2776-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e2776-104">Syntax</span></span>  
  
```  
WFServicesReg.exe [-c | -r | -v | -m | -i]  
```  
  
## <a name="remarks"></a><span data-ttu-id="e2776-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e2776-105">Remarks</span></span>  
 <span data-ttu-id="e2776-106">Narzędzie to można znaleźć w lokalizacji instalacji [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] , w tym%windir%\Microsoft.Net\Framework\v3.5 lub w%windir%\Microsoft.NET\Framework64\v3.5 na maszynach 64-bitowych.</span><span class="sxs-lookup"><span data-stu-id="e2776-106">The tool can be found at the [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] installation location, specifically, %windir%\Microsoft.NET\Framework\v3.5, or at %windir%\Microsoft.NET\Framework64\v3.5 in 64-bit machines.</span></span>  
  
 <span data-ttu-id="e2776-107">W poniższych tabelach opisano opcje, które mogą być używane z narzędziem rejestracji usług przepływu pracy (WFServicesReg. exe).</span><span class="sxs-lookup"><span data-stu-id="e2776-107">The following tables describe the options that can be used with the Workflow Services Registration tool (WFServicesReg.exe).</span></span>  
  
|<span data-ttu-id="e2776-108">Opcja</span><span class="sxs-lookup"><span data-stu-id="e2776-108">Option</span></span>|<span data-ttu-id="e2776-109">Opis</span><span class="sxs-lookup"><span data-stu-id="e2776-109">Description</span></span>|  
|------------|-----------------|  
|`/c`|<span data-ttu-id="e2776-110">Konfiguruje usługi przepływu pracy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="e2776-110">Configures Windows Workflow Services.</span></span> <span data-ttu-id="e2776-111">Używany w scenariuszach instalacji i naprawy.</span><span class="sxs-lookup"><span data-stu-id="e2776-111">Used in install and repair scenarios.</span></span>|  
|`/r`|<span data-ttu-id="e2776-112">Usuwa konfigurację usług Windows Workflow Services.</span><span class="sxs-lookup"><span data-stu-id="e2776-112">Removes Windows Workflow Services Configuration.</span></span>|  
|`/v`|<span data-ttu-id="e2776-113">Drukuj pełne informacje (dla konfiguracji lub usuwania).</span><span class="sxs-lookup"><span data-stu-id="e2776-113">Print verbose information (for either configuration or removal).</span></span>|  
|`/m`|<span data-ttu-id="e2776-114">Włącza Format rejestrowania MSI.</span><span class="sxs-lookup"><span data-stu-id="e2776-114">Enables MSI logging format.</span></span>|  
|`/i`|<span data-ttu-id="e2776-115">Minimalizuje okno, gdy aplikacja jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="e2776-115">Minimizes the window when the application runs.</span></span>|  
  
## <a name="registration"></a><span data-ttu-id="e2776-116">Rejestracja</span><span class="sxs-lookup"><span data-stu-id="e2776-116">Registration</span></span>  
 <span data-ttu-id="e2776-117">Narzędzie sprawdza plik Web. config i rejestruje następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="e2776-117">The tool inspects the Web.config file and registers the following:</span></span>  
  
- [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)]<span data-ttu-id="e2776-118">zestawy odwołań.</span><span class="sxs-lookup"><span data-stu-id="e2776-118">reference assemblies.</span></span>  
  
- <span data-ttu-id="e2776-119">Dostawca kompilacji dla plików xoml.</span><span class="sxs-lookup"><span data-stu-id="e2776-119">A build provider for .xoml files.</span></span>  
  
- <span data-ttu-id="e2776-120">Obsługa protokołu HTTP dla plików xoml i. rules.</span><span class="sxs-lookup"><span data-stu-id="e2776-120">HTTP handlers for .xoml and .rules files.</span></span>  
  
 <span data-ttu-id="e2776-121">Narzędzie sprawdza plik Machine. config i rejestruje następujące rozszerzenia:</span><span class="sxs-lookup"><span data-stu-id="e2776-121">The tool inspects the Machine.config file and registers the following extensions:</span></span>  
  
- <span data-ttu-id="e2776-122">behaviorExtensions</span><span class="sxs-lookup"><span data-stu-id="e2776-122">behaviorExtensions</span></span>  
  
- <span data-ttu-id="e2776-123">bindingElementExtensions</span><span class="sxs-lookup"><span data-stu-id="e2776-123">bindingElementExtensions</span></span>  
  
- <span data-ttu-id="e2776-124">bindingExtensions</span><span class="sxs-lookup"><span data-stu-id="e2776-124">bindingExtensions</span></span>  
  
 <span data-ttu-id="e2776-125">Narzędzie rejestruje także następujących importerów metadanych klienta:</span><span class="sxs-lookup"><span data-stu-id="e2776-125">The tool also registers the following client metadata importers:</span></span>  
  
- <span data-ttu-id="e2776-126">policyImporters</span><span class="sxs-lookup"><span data-stu-id="e2776-126">policyImporters</span></span>  
  
- <span data-ttu-id="e2776-127">wsdlImporters</span><span class="sxs-lookup"><span data-stu-id="e2776-127">wsdlImporters</span></span>  
  
 <span data-ttu-id="e2776-128">Narzędzie rejestruje również właściwości xoml i. rules oraz programy obsługi w metabazie usług IIS.</span><span class="sxs-lookup"><span data-stu-id="e2776-128">The tool also registers .xoml and .rules scriptmaps and handlers in the IIS metabase.</span></span>  
  
 <span data-ttu-id="e2776-129">W [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] systemach [!INCLUDE[wxp](../../../includes/wxp-md.md)] i na maszynach (IIS 5,1 i IIS 6,0) jest rejestrowany jeden zestaw właściwości xoml i rules.</span><span class="sxs-lookup"><span data-stu-id="e2776-129">On [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] and [!INCLUDE[wxp](../../../includes/wxp-md.md)] machines (IIS 5.1 and IIS 6.0), one set of .xoml and .rules scriptmaps are registered.</span></span>  
  
 <span data-ttu-id="e2776-130">Na komputerach 64-bitowych narzędzie rejestruje w trybie WOW mapowania skryptów, jeśli `Enable32BitAppOnWin64` przełącznik jest włączony, lub natywnie 64-bitowej mapy skryptów `Enable32BitAppOnWin64` , jeśli przełącznik jest wyłączony.</span><span class="sxs-lookup"><span data-stu-id="e2776-130">On 64-bit machines, the tool registers WOW mode scriptmaps if the `Enable32BitAppOnWin64` switch is enabled, or native 64-bit scriptmaps if the `Enable32BitAppOnWin64` switch is disabled.</span></span>  
  
 <span data-ttu-id="e2776-131">Na [!INCLUDE[wv](../../../includes/wv-md.md)] maszynach i na komputerach z systemem Windows Server 2008 (IIS 7,0 lub nowszym) są rejestrowane dwa zestawy programów xoml i.</span><span class="sxs-lookup"><span data-stu-id="e2776-131">On [!INCLUDE[wv](../../../includes/wv-md.md)] and Windows Server 2008 (IIS 7.0 and above) machines, two sets of .xoml and .rules handlers are registered: one for Integrated mode and one for Classic mode.</span></span>  
  
 <span data-ttu-id="e2776-132">Na komputerach 64-bitowych są zarejestrowane trzy zestawy programów obsługi (bez względu na stan `Enable32BitAppOnWin64` przełącznika): jeden dla trybu zintegrowanego, jeden dla klasycznego trybu WOW i jeden dla natywnego 64-bitowego trybu klasycznego.</span><span class="sxs-lookup"><span data-stu-id="e2776-132">On 64-bit machines, three sets of handlers are registered (regardless of the state of the `Enable32BitAppOnWin64` switch): one for Integrated mode, one for WOW Classic mode and one for native 64-bit Classic mode.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e2776-133">W przeciwieństwie do ServiceModelreg. exe, WFServicesReg. exe nie zezwala na dodawanie, usuwanie ani naprawianie skryptów lub programów obsługi dla określonej witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="e2776-133">Unlike ServiceModelreg.exe, WFServicesReg.exe does not allow adding, removing, or repairing scriptmaps or handlers for a particular Web site.</span></span> <span data-ttu-id="e2776-134">Aby obejść ten problem, zobacz sekcję "Naprawa skryptów".</span><span class="sxs-lookup"><span data-stu-id="e2776-134">For a workaround to this issue, see the "Repairing the Scriptmaps" section.</span></span>  
  
## <a name="usage-scenarios"></a><span data-ttu-id="e2776-135">Scenariusze użycia</span><span class="sxs-lookup"><span data-stu-id="e2776-135">Usage Scenarios</span></span>  
  
### <a name="installing-iis-after-net-framework-35-is-installed"></a><span data-ttu-id="e2776-136">Instalowanie usług IIS po zainstalowaniu .NET Framework 3,5</span><span class="sxs-lookup"><span data-stu-id="e2776-136">Installing IIS after .NET Framework 3.5 is installed</span></span>  
 <span data-ttu-id="e2776-137">Na komputerze program [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] jest instalowany przed instalacją usług IIS. [!INCLUDE[ws2003](../../../includes/ws2003-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2776-137">On a [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] machine, [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] is installed prior to IIS installation.</span></span> <span data-ttu-id="e2776-138">Ze względu na niedostępność metabazy usług IIS instalacja [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] programu kończy się powodzeniem bez instalowania. xoml i. rules.</span><span class="sxs-lookup"><span data-stu-id="e2776-138">Due to the unavailability of the IIS metabase, installation of [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] succeeds without installing .xoml and .rules scriptmaps.</span></span>  
  
 <span data-ttu-id="e2776-139">Po zainstalowaniu usług IIS można użyć narzędzia WFServicesReg. exe z `/c` przełącznikiem, aby zainstalować te konkretne mapy skryptów.</span><span class="sxs-lookup"><span data-stu-id="e2776-139">After IIS is installed, you can use the WFServicesReg.exe tool with the `/c` switch to install these specific scriptmaps.</span></span>  
  
### <a name="repairing-the-scriptmaps"></a><span data-ttu-id="e2776-140">Naprawianie skryptów</span><span class="sxs-lookup"><span data-stu-id="e2776-140">Repairing the Scriptmaps</span></span>  
  
#### <a name="scriptmap-deleted-under-web-sites-node"></a><span data-ttu-id="e2776-141">Właściwości scriptmap usunięte w węźle witryny sieci Web</span><span class="sxs-lookup"><span data-stu-id="e2776-141">Scriptmap deleted under Web Sites node</span></span>  
 <span data-ttu-id="e2776-142">[!INCLUDE[ws2003](../../../includes/ws2003-md.md)] Na komputerze, xoml lub. reguły są przypadkowo usuwane z węzła witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="e2776-142">On a [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] machine, .xoml or .rules is accidentally deleted from the Web Sites node.</span></span> <span data-ttu-id="e2776-143">Można to naprawić, uruchamiając narzędzie WFServicesReg. exe z `/c` przełącznikiem.</span><span class="sxs-lookup"><span data-stu-id="e2776-143">This can be repaired by running the WFServicesReg.exe tool with the `/c` switch.</span></span>  
  
#### <a name="scriptmap-deleted-under-a-particular-web-site"></a><span data-ttu-id="e2776-144">Właściwości scriptmap usunięte w określonej witrynie sieci Web</span><span class="sxs-lookup"><span data-stu-id="e2776-144">Scriptmap deleted under a particular Web site</span></span>  
 <span data-ttu-id="e2776-145">[!INCLUDE[ws2003](../../../includes/ws2003-md.md)] Na komputerze, xoml lub. reguły są przypadkowo usuwane z określonej witryny sieci Web (na przykład domyślnej witryny sieci Web), a nie z węzła witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="e2776-145">On a [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] machine, .xoml or .rules is accidentally deleted from a particular Web site (for example, the Default Web Site) rather than from the Web Sites node.</span></span>  
  
 <span data-ttu-id="e2776-146">Aby naprawić usunięte programy obsługi dla określonej witryny sieci Web, należy uruchomić polecenie "WFServicesReg. exe/r", aby usunąć programy obsługi ze wszystkich witryn sieci Web, a następnie uruchomić polecenie "WFServicesReg. exe/c" w celu utworzenia odpowiednich programów obsługi dla wszystkich witryn sieci Web.</span><span class="sxs-lookup"><span data-stu-id="e2776-146">To repair deleted handlers for a particular Web site, you should run "WFServicesReg.exe /r" to remove handlers from all Web sites, then run "WFServicesReg.exe /c" to create the appropriate handlers for all Web sites.</span></span>  
  
### <a name="configuring-handlers-after-switching-iis-mode"></a><span data-ttu-id="e2776-147">Konfigurowanie programów obsługi po przełączeniu trybu usług IIS</span><span class="sxs-lookup"><span data-stu-id="e2776-147">Configuring handlers after switching IIS mode</span></span>  
 <span data-ttu-id="e2776-148">Gdy usługi IIS są w trybie konfiguracji udostępnionej i [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] są zainstalowane, metabaza usług IIS jest konfigurowana w lokalizacji udostępnionej.</span><span class="sxs-lookup"><span data-stu-id="e2776-148">When IIS is in shared configuration mode and [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] is installed, the IIS metabase is configured under a shared location.</span></span> <span data-ttu-id="e2776-149">W przypadku przełączenia usług IIS do trybu konfiguracji nieudostępnionej, lokalna metabaza nie będzie zawierać wymaganych programów obsługi.</span><span class="sxs-lookup"><span data-stu-id="e2776-149">If you switch IIS to non-shared configuration mode, the local metabase will not contain the required handlers.</span></span> <span data-ttu-id="e2776-150">Aby prawidłowo skonfigurować lokalną metabazę, możesz zaimportować udostępnioną metabazę do lokalnego lub uruchomić polecenie "WFServicesReg. exe/c", które konfiguruje lokalną metabazę.</span><span class="sxs-lookup"><span data-stu-id="e2776-150">To configure the local metabase properly, you can either import the shared metabase to local, or run "WFServicesReg.exe /c", which configures the local metabase.</span></span>
