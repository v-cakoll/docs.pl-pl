---
title: Narzędzie rejestracji usług przepływu pracy (WFServicesReg.exe)
ms.date: 03/30/2017
ms.assetid: 9e92c87b-99c5-4e8d-9d53-7944cc2b47d3
ms.openlocfilehash: bb0989fb8747a5065ce3d7332311cdefba95b80d
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73425290"
---
# <a name="workflow-service-registration-tool-wfservicesregexe"></a><span data-ttu-id="8b182-102">Narzędzie rejestracji usług przepływu pracy (WFServicesReg.exe)</span><span class="sxs-lookup"><span data-stu-id="8b182-102">WorkFlow Service Registration Tool (WFServicesReg.exe)</span></span>
<span data-ttu-id="8b182-103">Narzędzie rejestracji usług przepływu pracy (WFServicesReg. exe) to autonomiczne narzędzie, które służy do dodawania, usuwania lub naprawiania elementów konfiguracji dla usług Windows Workflow Foundation (WF).</span><span class="sxs-lookup"><span data-stu-id="8b182-103">Workflow Services Registration tool (WFServicesReg.exe) is a stand-alone tool that can be used to add, remove, or repair the configuration elements for Windows Workflow Foundation (WF) services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b182-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8b182-104">Syntax</span></span>  
  
```console  
WFServicesReg.exe [-c | -r | -v | -m | -i]  
```  
  
## <a name="remarks"></a><span data-ttu-id="8b182-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8b182-105">Remarks</span></span>  
 <span data-ttu-id="8b182-106">Narzędzie to można znaleźć w lokalizacji instalacji [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)], w%windir%\Microsoft.NET\Framework\v3.5 lub w%windir%\Microsoft.NET\Framework64\v3.5 na maszynach 64-bitowych.</span><span class="sxs-lookup"><span data-stu-id="8b182-106">The tool can be found at the [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] installation location, specifically, %windir%\Microsoft.NET\Framework\v3.5, or at %windir%\Microsoft.NET\Framework64\v3.5 in 64-bit machines.</span></span>  
  
 <span data-ttu-id="8b182-107">W poniższych tabelach opisano opcje, które mogą być używane z narzędziem rejestracji usług przepływu pracy (WFServicesReg. exe).</span><span class="sxs-lookup"><span data-stu-id="8b182-107">The following tables describe the options that can be used with the Workflow Services Registration tool (WFServicesReg.exe).</span></span>  
  
|<span data-ttu-id="8b182-108">Opcja</span><span class="sxs-lookup"><span data-stu-id="8b182-108">Option</span></span>|<span data-ttu-id="8b182-109">Opis</span><span class="sxs-lookup"><span data-stu-id="8b182-109">Description</span></span>|  
|------------|-----------------|  
|`/c`|<span data-ttu-id="8b182-110">Konfiguruje usługi przepływu pracy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="8b182-110">Configures Windows Workflow Services.</span></span> <span data-ttu-id="8b182-111">Używany w scenariuszach instalacji i naprawy.</span><span class="sxs-lookup"><span data-stu-id="8b182-111">Used in install and repair scenarios.</span></span>|  
|`/r`|<span data-ttu-id="8b182-112">Usuwa konfigurację usług Windows Workflow Services.</span><span class="sxs-lookup"><span data-stu-id="8b182-112">Removes Windows Workflow Services Configuration.</span></span>|  
|`/v`|<span data-ttu-id="8b182-113">Drukuj pełne informacje (dla konfiguracji lub usuwania).</span><span class="sxs-lookup"><span data-stu-id="8b182-113">Print verbose information (for either configuration or removal).</span></span>|  
|`/m`|<span data-ttu-id="8b182-114">Włącza Format rejestrowania MSI.</span><span class="sxs-lookup"><span data-stu-id="8b182-114">Enables MSI logging format.</span></span>|  
|`/i`|<span data-ttu-id="8b182-115">Minimalizuje okno, gdy aplikacja jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="8b182-115">Minimizes the window when the application runs.</span></span>|  
  
## <a name="registration"></a><span data-ttu-id="8b182-116">Rejestracja</span><span class="sxs-lookup"><span data-stu-id="8b182-116">Registration</span></span>  
 <span data-ttu-id="8b182-117">Narzędzie sprawdza plik Web. config i rejestruje następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="8b182-117">The tool inspects the Web.config file and registers the following:</span></span>  
  
- <span data-ttu-id="8b182-118">zestawy odwołań [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8b182-118">[!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] reference assemblies.</span></span>  
  
- <span data-ttu-id="8b182-119">Dostawca kompilacji dla plików xoml.</span><span class="sxs-lookup"><span data-stu-id="8b182-119">A build provider for .xoml files.</span></span>  
  
- <span data-ttu-id="8b182-120">Obsługa protokołu HTTP dla plików xoml i. rules.</span><span class="sxs-lookup"><span data-stu-id="8b182-120">HTTP handlers for .xoml and .rules files.</span></span>  
  
 <span data-ttu-id="8b182-121">Narzędzie sprawdza plik Machine. config i rejestruje następujące rozszerzenia:</span><span class="sxs-lookup"><span data-stu-id="8b182-121">The tool inspects the Machine.config file and registers the following extensions:</span></span>  
  
- <span data-ttu-id="8b182-122">behaviorExtensions</span><span class="sxs-lookup"><span data-stu-id="8b182-122">behaviorExtensions</span></span>  
  
- <span data-ttu-id="8b182-123">bindingElementExtensions</span><span class="sxs-lookup"><span data-stu-id="8b182-123">bindingElementExtensions</span></span>  
  
- <span data-ttu-id="8b182-124">bindingExtensions</span><span class="sxs-lookup"><span data-stu-id="8b182-124">bindingExtensions</span></span>  
  
 <span data-ttu-id="8b182-125">Narzędzie rejestruje także następujących importerów metadanych klienta:</span><span class="sxs-lookup"><span data-stu-id="8b182-125">The tool also registers the following client metadata importers:</span></span>  
  
- <span data-ttu-id="8b182-126">policyImporters</span><span class="sxs-lookup"><span data-stu-id="8b182-126">policyImporters</span></span>  
  
- <span data-ttu-id="8b182-127">wsdlImporters</span><span class="sxs-lookup"><span data-stu-id="8b182-127">wsdlImporters</span></span>  
  
 <span data-ttu-id="8b182-128">Narzędzie rejestruje również właściwości xoml i. rules oraz programy obsługi w metabazie usług IIS.</span><span class="sxs-lookup"><span data-stu-id="8b182-128">The tool also registers .xoml and .rules scriptmaps and handlers in the IIS metabase.</span></span>  
  
 <span data-ttu-id="8b182-129">Na maszynach [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] i [!INCLUDE[wxp](../../../includes/wxp-md.md)] (IIS 5,1 i IIS 6,0) jest rejestrowany jeden zestaw właściwości xoml i. rules.</span><span class="sxs-lookup"><span data-stu-id="8b182-129">On [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] and [!INCLUDE[wxp](../../../includes/wxp-md.md)] machines (IIS 5.1 and IIS 6.0), one set of .xoml and .rules scriptmaps are registered.</span></span>  
  
 <span data-ttu-id="8b182-130">Na komputerach 64-bitowych narzędzie rejestruje w trybie WOW mapowania skryptów, jeśli przełącznik `Enable32BitAppOnWin64` jest włączony, lub natywnie 64-bitowe mapowania skryptów, jeśli przełącznik `Enable32BitAppOnWin64` jest wyłączony.</span><span class="sxs-lookup"><span data-stu-id="8b182-130">On 64-bit machines, the tool registers WOW mode scriptmaps if the `Enable32BitAppOnWin64` switch is enabled, or native 64-bit scriptmaps if the `Enable32BitAppOnWin64` switch is disabled.</span></span>  
  
 <span data-ttu-id="8b182-131">Na maszynach [!INCLUDE[wv](../../../includes/wv-md.md)] i Windows Server 2008 (IIS 7,0 i nowsze) są rejestrowane dwa zestawy programów xoml i rules: jeden dla trybu zintegrowanego i jeden dla trybu klasycznego.</span><span class="sxs-lookup"><span data-stu-id="8b182-131">On [!INCLUDE[wv](../../../includes/wv-md.md)] and Windows Server 2008 (IIS 7.0 and above) machines, two sets of .xoml and .rules handlers are registered: one for Integrated mode and one for Classic mode.</span></span>  
  
 <span data-ttu-id="8b182-132">Na komputerach 64-bitowych są zarejestrowane trzy zestawy programów obsługi (bez względu na stan przełącznika `Enable32BitAppOnWin64`): jeden dla trybu zintegrowanego, jeden dla klasycznego trybu WOW i jeden dla natywnego 64-bitowego trybu klasycznego.</span><span class="sxs-lookup"><span data-stu-id="8b182-132">On 64-bit machines, three sets of handlers are registered (regardless of the state of the `Enable32BitAppOnWin64` switch): one for Integrated mode, one for WOW Classic mode and one for native 64-bit Classic mode.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8b182-133">W przeciwieństwie do ServiceModelreg. exe, WFServicesReg. exe nie zezwala na dodawanie, usuwanie ani naprawianie skryptów lub programów obsługi dla określonej witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="8b182-133">Unlike ServiceModelreg.exe, WFServicesReg.exe does not allow adding, removing, or repairing scriptmaps or handlers for a particular Web site.</span></span> <span data-ttu-id="8b182-134">Aby obejść ten problem, zobacz sekcję "Naprawa skryptów".</span><span class="sxs-lookup"><span data-stu-id="8b182-134">For a workaround to this issue, see the "Repairing the Scriptmaps" section.</span></span>  
  
## <a name="usage-scenarios"></a><span data-ttu-id="8b182-135">Scenariusze użycia</span><span class="sxs-lookup"><span data-stu-id="8b182-135">Usage Scenarios</span></span>  
  
### <a name="installing-iis-after-net-framework-35-is-installed"></a><span data-ttu-id="8b182-136">Instalowanie usług IIS po zainstalowaniu .NET Framework 3,5</span><span class="sxs-lookup"><span data-stu-id="8b182-136">Installing IIS after .NET Framework 3.5 is installed</span></span>  
 <span data-ttu-id="8b182-137">Na komputerze [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] jest instalowany przed instalacją usług IIS.</span><span class="sxs-lookup"><span data-stu-id="8b182-137">On a [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] machine, [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] is installed prior to IIS installation.</span></span> <span data-ttu-id="8b182-138">Ze względu na niedostępność metabazy usług IIS instalacja programu [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] zakończona pomyślnie bez instalowania. xoml i. rules.</span><span class="sxs-lookup"><span data-stu-id="8b182-138">Due to the unavailability of the IIS metabase, installation of [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] succeeds without installing .xoml and .rules scriptmaps.</span></span>  
  
 <span data-ttu-id="8b182-139">Po zainstalowaniu usług IIS można użyć narzędzia WFServicesReg. exe z przełącznikiem `/c`, aby zainstalować te konkretne mapy skryptów.</span><span class="sxs-lookup"><span data-stu-id="8b182-139">After IIS is installed, you can use the WFServicesReg.exe tool with the `/c` switch to install these specific scriptmaps.</span></span>  
  
### <a name="repairing-the-scriptmaps"></a><span data-ttu-id="8b182-140">Naprawianie skryptów</span><span class="sxs-lookup"><span data-stu-id="8b182-140">Repairing the Scriptmaps</span></span>  
  
#### <a name="scriptmap-deleted-under-web-sites-node"></a><span data-ttu-id="8b182-141">Właściwości scriptmap usunięte w węźle witryny sieci Web</span><span class="sxs-lookup"><span data-stu-id="8b182-141">Scriptmap deleted under Web Sites node</span></span>  
 <span data-ttu-id="8b182-142">Na maszynie [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], pliku xoml lub reguły są przypadkowo usuwane z węzła witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="8b182-142">On a [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] machine, .xoml or .rules is accidentally deleted from the Web Sites node.</span></span> <span data-ttu-id="8b182-143">Można to naprawić, uruchamiając narzędzie WFServicesReg. exe z przełącznikiem `/c`.</span><span class="sxs-lookup"><span data-stu-id="8b182-143">This can be repaired by running the WFServicesReg.exe tool with the `/c` switch.</span></span>  
  
#### <a name="scriptmap-deleted-under-a-particular-web-site"></a><span data-ttu-id="8b182-144">Właściwości scriptmap usunięte w określonej witrynie sieci Web</span><span class="sxs-lookup"><span data-stu-id="8b182-144">Scriptmap deleted under a particular Web site</span></span>  
 <span data-ttu-id="8b182-145">Na komputerze [!INCLUDE[ws2003](../../../includes/ws2003-md.md)],. xoml lub. reguły są przypadkowo usuwane z określonej witryny sieci Web (na przykład domyślnej witryny sieci Web), a nie z węzła witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="8b182-145">On a [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] machine, .xoml or .rules is accidentally deleted from a particular Web site (for example, the Default Web Site) rather than from the Web Sites node.</span></span>  
  
 <span data-ttu-id="8b182-146">Aby naprawić usunięte programy obsługi dla określonej witryny sieci Web, należy uruchomić polecenie "WFServicesReg. exe/r", aby usunąć programy obsługi ze wszystkich witryn sieci Web, a następnie uruchomić polecenie "WFServicesReg. exe/c" w celu utworzenia odpowiednich programów obsługi dla wszystkich witryn sieci Web.</span><span class="sxs-lookup"><span data-stu-id="8b182-146">To repair deleted handlers for a particular Web site, you should run "WFServicesReg.exe /r" to remove handlers from all Web sites, then run "WFServicesReg.exe /c" to create the appropriate handlers for all Web sites.</span></span>  
  
### <a name="configuring-handlers-after-switching-iis-mode"></a><span data-ttu-id="8b182-147">Konfigurowanie programów obsługi po przełączeniu trybu usług IIS</span><span class="sxs-lookup"><span data-stu-id="8b182-147">Configuring handlers after switching IIS mode</span></span>  
 <span data-ttu-id="8b182-148">Gdy usługi IIS są w trybie konfiguracji udostępnionej i zainstalowano [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)], metabaza usług IIS jest konfigurowana w lokalizacji udostępnionej.</span><span class="sxs-lookup"><span data-stu-id="8b182-148">When IIS is in shared configuration mode and [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] is installed, the IIS metabase is configured under a shared location.</span></span> <span data-ttu-id="8b182-149">W przypadku przełączenia usług IIS do trybu konfiguracji nieudostępnionej, lokalna metabaza nie będzie zawierać wymaganych programów obsługi.</span><span class="sxs-lookup"><span data-stu-id="8b182-149">If you switch IIS to non-shared configuration mode, the local metabase will not contain the required handlers.</span></span> <span data-ttu-id="8b182-150">Aby prawidłowo skonfigurować lokalną metabazę, możesz zaimportować udostępnioną metabazę do lokalnego lub uruchomić polecenie "WFServicesReg. exe/c", które konfiguruje lokalną metabazę.</span><span class="sxs-lookup"><span data-stu-id="8b182-150">To configure the local metabase properly, you can either import the shared metabase to local, or run "WFServicesReg.exe /c", which configures the local metabase.</span></span>
