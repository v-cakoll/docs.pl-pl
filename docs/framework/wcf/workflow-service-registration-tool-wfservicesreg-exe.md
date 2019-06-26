---
title: Narzędzie rejestracji usług przepływu pracy (WFServicesReg.exe)
ms.date: 03/30/2017
ms.assetid: 9e92c87b-99c5-4e8d-9d53-7944cc2b47d3
ms.openlocfilehash: 211af75c04dfe971228bc1710fbe1fc4d7aaee60
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2019
ms.locfileid: "67402483"
---
# <a name="workflow-service-registration-tool-wfservicesregexe"></a><span data-ttu-id="14e25-102">Narzędzie rejestracji usług przepływu pracy (WFServicesReg.exe)</span><span class="sxs-lookup"><span data-stu-id="14e25-102">WorkFlow Service Registration Tool (WFServicesReg.exe)</span></span>
<span data-ttu-id="14e25-103">Narzędzie rejestracji usług przepływu pracy (WFServicesReg.exe) jest autonomicznym narzędziem, które można dodać, usunąć lub naprawić elementy konfiguracji dla usług Windows Workflow Foundation (WF).</span><span class="sxs-lookup"><span data-stu-id="14e25-103">Workflow Services Registration tool (WFServicesReg.exe) is a stand-alone tool that can be used to add, remove, or repair the configuration elements for Windows Workflow Foundation (WF) services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14e25-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="14e25-104">Syntax</span></span>  
  
```  
WFServicesReg.exe [-c | -r | -v | -m | -i]  
```  
  
## <a name="remarks"></a><span data-ttu-id="14e25-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="14e25-105">Remarks</span></span>  
 <span data-ttu-id="14e25-106">Narzędzie znajduje się w temacie [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] lokalizację instalacji, w szczególności % windir%\Microsoft.NET\Framework\v3.5 lub %windir%\Microsoft.NET\Framework64\v3.5 w 64-bitowych maszyn.</span><span class="sxs-lookup"><span data-stu-id="14e25-106">The tool can be found at the [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] installation location, specifically, %windir%\Microsoft.NET\Framework\v3.5, or at %windir%\Microsoft.NET\Framework64\v3.5 in 64-bit machines.</span></span>  
  
 <span data-ttu-id="14e25-107">W poniższych tabelach opisano opcje, które mogą być używane z narzędzia rejestracji usług przepływu pracy (WFServicesReg.exe).</span><span class="sxs-lookup"><span data-stu-id="14e25-107">The following tables describe the options that can be used with the Workflow Services Registration tool (WFServicesReg.exe).</span></span>  
  
|<span data-ttu-id="14e25-108">Opcja</span><span class="sxs-lookup"><span data-stu-id="14e25-108">Option</span></span>|<span data-ttu-id="14e25-109">Opis</span><span class="sxs-lookup"><span data-stu-id="14e25-109">Description</span></span>|  
|------------|-----------------|  
|`/c`|<span data-ttu-id="14e25-110">Umożliwia skonfigurowanie usług przepływu pracy Windows.</span><span class="sxs-lookup"><span data-stu-id="14e25-110">Configures Windows Workflow Services.</span></span> <span data-ttu-id="14e25-111">Używane w instalacji i naprawiania scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="14e25-111">Used in install and repair scenarios.</span></span>|  
|`/r`|<span data-ttu-id="14e25-112">Usuwa konfigurację usługi przepływu pracy Windows.</span><span class="sxs-lookup"><span data-stu-id="14e25-112">Removes Windows Workflow Services Configuration.</span></span>|  
|`/v`|<span data-ttu-id="14e25-113">Pełne informacje dotyczące drukowania (dla konfiguracji lub usuwania).</span><span class="sxs-lookup"><span data-stu-id="14e25-113">Print verbose information (for either configuration or removal).</span></span>|  
|`/m`|<span data-ttu-id="14e25-114">Włącza format rejestrowania tożsamości usługi Zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="14e25-114">Enables MSI logging format.</span></span>|  
|`/i`|<span data-ttu-id="14e25-115">Minimalizuje okna, gdy aplikacja zostanie uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="14e25-115">Minimizes the window when the application runs.</span></span>|  
  
## <a name="registration"></a><span data-ttu-id="14e25-116">Rejestracja</span><span class="sxs-lookup"><span data-stu-id="14e25-116">Registration</span></span>  
 <span data-ttu-id="14e25-117">Narzędzie sprawdza plik Web.config i rejestruje następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="14e25-117">The tool inspects the Web.config file and registers the following:</span></span>  
  
- [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] <span data-ttu-id="14e25-118">zestawy referencyjne.</span><span class="sxs-lookup"><span data-stu-id="14e25-118">reference assemblies.</span></span>  
  
- <span data-ttu-id="14e25-119">Dostawca kompilacji pliki xoml.</span><span class="sxs-lookup"><span data-stu-id="14e25-119">A build provider for .xoml files.</span></span>  
  
- <span data-ttu-id="14e25-120">Aby uzyskać pliki xoml i Rules funkcje obsługi protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="14e25-120">HTTP handlers for .xoml and .rules files.</span></span>  
  
 <span data-ttu-id="14e25-121">Narzędzie sprawdza plik Machine.config i rejestruje następujące rozszerzenia:</span><span class="sxs-lookup"><span data-stu-id="14e25-121">The tool inspects the Machine.config file and registers the following extensions:</span></span>  
  
- <span data-ttu-id="14e25-122">behaviorExtensions</span><span class="sxs-lookup"><span data-stu-id="14e25-122">behaviorExtensions</span></span>  
  
- <span data-ttu-id="14e25-123">bindingElementExtensions</span><span class="sxs-lookup"><span data-stu-id="14e25-123">bindingElementExtensions</span></span>  
  
- <span data-ttu-id="14e25-124">bindingExtensions</span><span class="sxs-lookup"><span data-stu-id="14e25-124">bindingExtensions</span></span>  
  
 <span data-ttu-id="14e25-125">Narzędzie rejestruje także następujące importerów metadane klienta:</span><span class="sxs-lookup"><span data-stu-id="14e25-125">The tool also registers the following client metadata importers:</span></span>  
  
- <span data-ttu-id="14e25-126">policyImporters</span><span class="sxs-lookup"><span data-stu-id="14e25-126">policyImporters</span></span>  
  
- <span data-ttu-id="14e25-127">wsdlImporters</span><span class="sxs-lookup"><span data-stu-id="14e25-127">wsdlImporters</span></span>  
  
 <span data-ttu-id="14e25-128">Narzędzie rejestruje także xoml i Rules mapy skryptów i programów obsługi w metabazie IIS.</span><span class="sxs-lookup"><span data-stu-id="14e25-128">The tool also registers .xoml and .rules scriptmaps and handlers in the IIS metabase.</span></span>  
  
 <span data-ttu-id="14e25-129">Na [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] i [!INCLUDE[wxp](../../../includes/wxp-md.md)] maszyny (usługi IIS 5.1 i IIS 6.0), jeden zestaw xoml i Rules mapy skryptów są zarejestrowane.</span><span class="sxs-lookup"><span data-stu-id="14e25-129">On [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] and [!INCLUDE[wxp](../../../includes/wxp-md.md)] machines (IIS 5.1 and IIS 6.0), one set of .xoml and .rules scriptmaps are registered.</span></span>  
  
 <span data-ttu-id="14e25-130">Na komputerach 64-bitowe narzędzie rejestruje mapy skryptów trybie WOW, jeśli `Enable32BitAppOnWin64` przełącznik jest włączony lub natywnych 64-bitowych mapy skryptów, jeśli `Enable32BitAppOnWin64` przełącznik jest wyłączony.</span><span class="sxs-lookup"><span data-stu-id="14e25-130">On 64-bit machines, the tool registers WOW mode scriptmaps if the `Enable32BitAppOnWin64` switch is enabled, or native 64-bit scriptmaps if the `Enable32BitAppOnWin64` switch is disabled.</span></span>  
  
 <span data-ttu-id="14e25-131">Na [!INCLUDE[wv](../../../includes/wv-md.md)] i Windows Server 2008 (usługi IIS 7.0 i nowsze wersje) maszyny, dwa zestawy xoml i Rules obsługi są zarejestrowane: jeden dla trybu zintegrowanego i jeden dla trybu klasycznego.</span><span class="sxs-lookup"><span data-stu-id="14e25-131">On [!INCLUDE[wv](../../../includes/wv-md.md)] and Windows Server 2008 (IIS 7.0 and above) machines, two sets of .xoml and .rules handlers are registered: one for Integrated mode and one for Classic mode.</span></span>  
  
 <span data-ttu-id="14e25-132">Na komputerach 64-bitowych zarejestrowano trzy rodzaje obsługi (bez względu na stan `Enable32BitAppOnWin64` przełącznika): jeden dla działania w trybie zintegrowanym, w trybie WOW klasycznym i jeden dla trybu macierzystego Classic 64-bitowych.</span><span class="sxs-lookup"><span data-stu-id="14e25-132">On 64-bit machines, three sets of handlers are registered (regardless of the state of the `Enable32BitAppOnWin64` switch): one for Integrated mode, one for WOW Classic mode and one for native 64-bit Classic mode.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="14e25-133">W odróżnieniu od ServiceModelreg.exe WFServicesReg.exe nie zezwala na dodawanie, usuwanie lub naprawianie mapy skryptów lub programów obsługi dla określonej witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="14e25-133">Unlike ServiceModelreg.exe, WFServicesReg.exe does not allow adding, removing, or repairing scriptmaps or handlers for a particular Web site.</span></span> <span data-ttu-id="14e25-134">Obejście tego problemu znajduje się w sekcji "Naprawa mapy skryptów".</span><span class="sxs-lookup"><span data-stu-id="14e25-134">For a workaround to this issue, see the "Repairing the Scriptmaps" section.</span></span>  
  
## <a name="usage-scenarios"></a><span data-ttu-id="14e25-135">Scenariusze użycia</span><span class="sxs-lookup"><span data-stu-id="14e25-135">Usage Scenarios</span></span>  
  
### <a name="installing-iis-after-net-framework-35-is-installed"></a><span data-ttu-id="14e25-136">Instalowanie usług IIS po zainstalowaniu programu .NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="14e25-136">Installing IIS after .NET Framework 3.5 is installed</span></span>  
 <span data-ttu-id="14e25-137">Na [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] maszyny [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] jest zainstalowany przed instalacją usług IIS.</span><span class="sxs-lookup"><span data-stu-id="14e25-137">On a [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] machine, [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] is installed prior to IIS installation.</span></span> <span data-ttu-id="14e25-138">Z powodu niedostępności metabazy usług IIS, instalacja [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] zakończy się pomyślnie bez konieczności instalowania xoml i Rules mapy skryptów.</span><span class="sxs-lookup"><span data-stu-id="14e25-138">Due to the unavailability of the IIS metabase, installation of [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] succeeds without installing .xoml and .rules scriptmaps.</span></span>  
  
 <span data-ttu-id="14e25-139">Po zainstalowaniu usług IIS, można użyć narzędzia WFServicesReg.exe z `/c` przełącznik, aby zainstalować te określonego mapowania skryptów.</span><span class="sxs-lookup"><span data-stu-id="14e25-139">After IIS is installed, you can use the WFServicesReg.exe tool with the `/c` switch to install these specific scriptmaps.</span></span>  
  
### <a name="repairing-the-scriptmaps"></a><span data-ttu-id="14e25-140">Naprawianie mapowania skryptów</span><span class="sxs-lookup"><span data-stu-id="14e25-140">Repairing the Scriptmaps</span></span>  
  
#### <a name="scriptmap-deleted-under-web-sites-node"></a><span data-ttu-id="14e25-141">Mapowania skryptów usunięte w węźle witryn sieci Web</span><span class="sxs-lookup"><span data-stu-id="14e25-141">Scriptmap deleted under Web Sites node</span></span>  
 <span data-ttu-id="14e25-142">Na [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] maszyny, xoml lub Rules zostanie przypadkowo usunięta z węzeł witryn sieci Web.</span><span class="sxs-lookup"><span data-stu-id="14e25-142">On a [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] machine, .xoml or .rules is accidentally deleted from the Web Sites node.</span></span> <span data-ttu-id="14e25-143">Można to naprawić, uruchamiając narzędzie WFServicesReg.exe z `/c` przełącznika.</span><span class="sxs-lookup"><span data-stu-id="14e25-143">This can be repaired by running the WFServicesReg.exe tool with the `/c` switch.</span></span>  
  
#### <a name="scriptmap-deleted-under-a-particular-web-site"></a><span data-ttu-id="14e25-144">Mapowania skryptów usunięte w ramach określonej witryny sieci Web</span><span class="sxs-lookup"><span data-stu-id="14e25-144">Scriptmap deleted under a particular Web site</span></span>  
 <span data-ttu-id="14e25-145">Na [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] maszyny, xoml lub Rules zostaną przypadkowo usunięte z określonej witryny sieci Web (na przykład, domyślna witryna sieci Web), a nie z węzła witryn sieci Web.</span><span class="sxs-lookup"><span data-stu-id="14e25-145">On a [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] machine, .xoml or .rules is accidentally deleted from a particular Web site (for example, the Default Web Site) rather than from the Web Sites node.</span></span>  
  
 <span data-ttu-id="14e25-146">Aby naprawić usunięte programy obsługi dla określonej witryny sieci Web, należy uruchomić "WFServicesReg.exe/r" Aby usunąć obsługi z wszystkich witryn sieci Web, a następnie uruchom "WFServicesReg.exe c" można utworzyć odpowiednie programy obsługi dla wszystkich witryn sieci Web.</span><span class="sxs-lookup"><span data-stu-id="14e25-146">To repair deleted handlers for a particular Web site, you should run "WFServicesReg.exe /r" to remove handlers from all Web sites, then run "WFServicesReg.exe /c" to create the appropriate handlers for all Web sites.</span></span>  
  
### <a name="configuring-handlers-after-switching-iis-mode"></a><span data-ttu-id="14e25-147">Konfigurowanie obsługi po przełączeniu do trybu usług IIS</span><span class="sxs-lookup"><span data-stu-id="14e25-147">Configuring handlers after switching IIS mode</span></span>  
 <span data-ttu-id="14e25-148">Gdy program IIS jest w trybie konfiguracji udostępnionej i [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] jest zainstalowany, metabazy usług IIS jest skonfigurowane w lokalizacji udostępnionej.</span><span class="sxs-lookup"><span data-stu-id="14e25-148">When IIS is in shared configuration mode and [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] is installed, the IIS metabase is configured under a shared location.</span></span> <span data-ttu-id="14e25-149">Jeśli usługi IIS przełączyć się do trybu konfiguracji nieudostępnione, lokalnej metabazy nie będzie zawierać wymagane programy obsługi.</span><span class="sxs-lookup"><span data-stu-id="14e25-149">If you switch IIS to non-shared configuration mode, the local metabase will not contain the required handlers.</span></span> <span data-ttu-id="14e25-150">Aby poprawnie skonfigurować lokalne metabazy, możesz zaimportować udostępnionych metabazy do lokalnego lub wykonywania "WFServicesReg.exe /c", który konfiguruje metabazy lokalnej.</span><span class="sxs-lookup"><span data-stu-id="14e25-150">To configure the local metabase properly, you can either import the shared metabase to local, or run "WFServicesReg.exe /c", which configures the local metabase.</span></span>
