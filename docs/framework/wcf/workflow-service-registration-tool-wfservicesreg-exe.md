---
title: "Narzędzie rejestracji usług przepływu pracy (WFServicesReg.exe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9e92c87b-99c5-4e8d-9d53-7944cc2b47d3
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: adf5939013e7411dde2b313a030e788b365c40ea
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="workflow-service-registration-tool-wfservicesregexe"></a><span data-ttu-id="5a0ef-102">Narzędzie rejestracji usług przepływu pracy (WFServicesReg.exe)</span><span class="sxs-lookup"><span data-stu-id="5a0ef-102">WorkFlow Service Registration Tool (WFServicesReg.exe)</span></span>
<span data-ttu-id="5a0ef-103">Narzędzie rejestracji usług przepływu pracy (WFServicesReg.exe) jest autonomicznym narzędziem, które można dodać, usunąć lub napraw elementy konfiguracji dla usług Windows Workflow Foundation (WF).</span><span class="sxs-lookup"><span data-stu-id="5a0ef-103">Workflow Services Registration tool (WFServicesReg.exe) is a stand-alone tool that can be used to add, remove, or repair the configuration elements for Windows Workflow Foundation (WF) services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a0ef-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5a0ef-104">Syntax</span></span>  
  
```  
WFServicesReg.exe [-c | -r | -v | -m | -i]  
```  
  
## <a name="remarks"></a><span data-ttu-id="5a0ef-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5a0ef-105">Remarks</span></span>  
 <span data-ttu-id="5a0ef-106">Narzędzie znajduje się w temacie [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] lokalizacja instalacji, w szczególności % windir%\Microsoft.NET\Framework\v3.5 lub %windir%\Microsoft.NET\Framework64\v3.5 w 64-bitowych maszyn.</span><span class="sxs-lookup"><span data-stu-id="5a0ef-106">The tool can be found at the [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] installation location, specifically, %windir%\Microsoft.NET\Framework\v3.5, or at %windir%\Microsoft.NET\Framework64\v3.5 in 64-bit machines.</span></span>  
  
 <span data-ttu-id="5a0ef-107">W poniższych tabelach opisano opcje, które mogą być używane z narzędzie rejestracji usług przepływu pracy (WFServicesReg.exe).</span><span class="sxs-lookup"><span data-stu-id="5a0ef-107">The following tables describe the options that can be used with the Workflow Services Registration tool (WFServicesReg.exe).</span></span>  
  
|<span data-ttu-id="5a0ef-108">Opcja</span><span class="sxs-lookup"><span data-stu-id="5a0ef-108">Option</span></span>|<span data-ttu-id="5a0ef-109">Opis</span><span class="sxs-lookup"><span data-stu-id="5a0ef-109">Description</span></span>|  
|------------|-----------------|  
|`/c`|<span data-ttu-id="5a0ef-110">Konfiguruje usługi przepływu pracy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="5a0ef-110">Configures Windows Workflow Services.</span></span> <span data-ttu-id="5a0ef-111">Używane w instalacji i naprawy scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="5a0ef-111">Used in install and repair scenarios.</span></span>|  
|`/r`|<span data-ttu-id="5a0ef-112">Usuwa konfiguracji usługi przepływu pracy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="5a0ef-112">Removes Windows Workflow Services Configuration.</span></span>|  
|`/v`|<span data-ttu-id="5a0ef-113">Pełne informacje dotyczące drukowania (dla konfiguracji lub usuwania).</span><span class="sxs-lookup"><span data-stu-id="5a0ef-113">Print verbose information (for either configuration or removal).</span></span>|  
|`/m`|<span data-ttu-id="5a0ef-114">Włącza format rejestrowania MSI.</span><span class="sxs-lookup"><span data-stu-id="5a0ef-114">Enables MSI logging format.</span></span>|  
|`/i`|<span data-ttu-id="5a0ef-115">Minimalizuje okno po uruchomieniu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5a0ef-115">Minimizes the window when the application runs.</span></span>|  
  
## <a name="registration"></a><span data-ttu-id="5a0ef-116">Rejestracja</span><span class="sxs-lookup"><span data-stu-id="5a0ef-116">Registration</span></span>  
 <span data-ttu-id="5a0ef-117">Narzędzie bada pliku Web.config i rejestruje następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="5a0ef-117">The tool inspects the Web.config file and registers the following:</span></span>  
  
-   [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)]<span data-ttu-id="5a0ef-118">zestawy odwołań.</span><span class="sxs-lookup"><span data-stu-id="5a0ef-118"> reference assemblies.</span></span>  
  
-   <span data-ttu-id="5a0ef-119">Dostawcę kompilacji dla plików xoml.</span><span class="sxs-lookup"><span data-stu-id="5a0ef-119">A build provider for .xoml files.</span></span>  
  
-   <span data-ttu-id="5a0ef-120">Programy obsługi HTTP pliki xoml i rules.</span><span class="sxs-lookup"><span data-stu-id="5a0ef-120">HTTP handlers for .xoml and .rules files.</span></span>  
  
 <span data-ttu-id="5a0ef-121">Narzędzie bada pliku Machine.config i rejestruje następujące rozszerzenia:</span><span class="sxs-lookup"><span data-stu-id="5a0ef-121">The tool inspects the Machine.config file and registers the following extensions:</span></span>  
  
-   <span data-ttu-id="5a0ef-122">behaviorExtensions</span><span class="sxs-lookup"><span data-stu-id="5a0ef-122">behaviorExtensions</span></span>  
  
-   <span data-ttu-id="5a0ef-123">bindingElementExtensions</span><span class="sxs-lookup"><span data-stu-id="5a0ef-123">bindingElementExtensions</span></span>  
  
-   <span data-ttu-id="5a0ef-124">bindingExtensions</span><span class="sxs-lookup"><span data-stu-id="5a0ef-124">bindingExtensions</span></span>  
  
 <span data-ttu-id="5a0ef-125">Narzędzie rejestruje także następujące importerów metadane klienta:</span><span class="sxs-lookup"><span data-stu-id="5a0ef-125">The tool also registers the following client metadata importers:</span></span>  
  
-   <span data-ttu-id="5a0ef-126">policyImporters</span><span class="sxs-lookup"><span data-stu-id="5a0ef-126">policyImporters</span></span>  
  
-   <span data-ttu-id="5a0ef-127">wsdlImporters</span><span class="sxs-lookup"><span data-stu-id="5a0ef-127">wsdlImporters</span></span>  
  
 <span data-ttu-id="5a0ef-128">Narzędzie rejestruje także xoml i Rules mapy skryptów i obsługi w metabazie usług IIS.</span><span class="sxs-lookup"><span data-stu-id="5a0ef-128">The tool also registers .xoml and .rules scriptmaps and handlers in the IIS metabase.</span></span>  
  
 <span data-ttu-id="5a0ef-129">Na [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] i [!INCLUDE[wxp](../../../includes/wxp-md.md)] maszyny (usługi IIS 5.1 i [!INCLUDE[iis601](../../../includes/iis601-md.md)]), jeden zestaw xoml i Rules mapy skryptów są zarejestrowane.</span><span class="sxs-lookup"><span data-stu-id="5a0ef-129">On [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] and [!INCLUDE[wxp](../../../includes/wxp-md.md)] machines (IIS 5.1 and [!INCLUDE[iis601](../../../includes/iis601-md.md)]), one set of .xoml and .rules scriptmaps are registered.</span></span>  
  
 <span data-ttu-id="5a0ef-130">Na komputerach 64-bitowych, narzędzie rejestruje mapy skryptów trybie WOW, jeśli `Enable32BitAppOnWin64` przełącznik jest włączone lub natywnych 64-bitowych mapy skryptów, jeśli `Enable32BitAppOnWin64` przełącznik jest wyłączony.</span><span class="sxs-lookup"><span data-stu-id="5a0ef-130">On 64-bit machines, the tool registers WOW mode scriptmaps if the `Enable32BitAppOnWin64` switch is enabled, or native 64-bit scriptmaps if the `Enable32BitAppOnWin64` switch is disabled.</span></span>  
  
 <span data-ttu-id="5a0ef-131">Na [!INCLUDE[wv](../../../includes/wv-md.md)] i Windows Server 2008 (usługi IIS 7.0 lub nowszym) maszyny, dwa zestawy xoml i Rules są zarejestrowane: jeden dla trybu zintegrowanego i jeden dla trybu klasycznego.</span><span class="sxs-lookup"><span data-stu-id="5a0ef-131">On [!INCLUDE[wv](../../../includes/wv-md.md)] and Windows Server 2008 (IIS 7.0 and above) machines, two sets of .xoml and .rules handlers are registered: one for Integrated mode and one for Classic mode.</span></span>  
  
 <span data-ttu-id="5a0ef-132">Na komputerach 64-bitowych, są rejestrowane trzy zestawy programów obsługi (niezależnie od stanu `Enable32BitAppOnWin64` przełącznika): jeden dla działania w trybie zintegrowanym, w trybie WOW klasycznym i jeden do trybu macierzystego Classic 64-bitowych.</span><span class="sxs-lookup"><span data-stu-id="5a0ef-132">On 64-bit machines, three sets of handlers are registered (regardless of the state of the `Enable32BitAppOnWin64` switch): one for Integrated mode, one for WOW Classic mode and one for native 64-bit Classic mode.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5a0ef-133">W odróżnieniu od ServiceModelreg.exe WFServicesReg.exe nie zezwala na dodawanie, usuwanie lub naprawianie mapy skryptów lub programy obsługi dla określonej witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="5a0ef-133">Unlike ServiceModelreg.exe, WFServicesReg.exe does not allow adding, removing, or repairing scriptmaps or handlers for a particular Web site.</span></span> <span data-ttu-id="5a0ef-134">Obejścia tego problemu zobacz sekcję "Naprawianie mapy skryptów".</span><span class="sxs-lookup"><span data-stu-id="5a0ef-134">For a workaround to this issue, see the "Repairing the Scriptmaps" section.</span></span>  
  
## <a name="usage-scenarios"></a><span data-ttu-id="5a0ef-135">Scenariusze użycia</span><span class="sxs-lookup"><span data-stu-id="5a0ef-135">Usage Scenarios</span></span>  
  
### <a name="installing-iis-after-net-framework-35-is-installed"></a><span data-ttu-id="5a0ef-136">Instalowanie programu IIS po zainstalowaniu programu .NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="5a0ef-136">Installing IIS after .NET Framework 3.5 is installed</span></span>  
 <span data-ttu-id="5a0ef-137">Na [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] maszyny, [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] jest zainstalowany przed instalacją usług IIS.</span><span class="sxs-lookup"><span data-stu-id="5a0ef-137">On a [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] machine, [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] is installed prior to IIS installation.</span></span> <span data-ttu-id="5a0ef-138">Z powodu niedostępności metabazy usług IIS, instalacja [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] zakończy się pomyślnie bez instalowania xoml i Rules mapy skryptów.</span><span class="sxs-lookup"><span data-stu-id="5a0ef-138">Due to the unavailability of the IIS metabase, installation of [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] succeeds without installing .xoml and .rules scriptmaps.</span></span>  
  
 <span data-ttu-id="5a0ef-139">Po zainstalowaniu usług IIS, można użyć narzędzia WFServicesReg.exe z `/c` przełącznik, aby zainstalować te określone mapy skryptów.</span><span class="sxs-lookup"><span data-stu-id="5a0ef-139">After IIS is installed, you can use the WFServicesReg.exe tool with the `/c` switch to install these specific scriptmaps.</span></span>  
  
### <a name="repairing-the-scriptmaps"></a><span data-ttu-id="5a0ef-140">Naprawianie mapowania skryptów</span><span class="sxs-lookup"><span data-stu-id="5a0ef-140">Repairing the Scriptmaps</span></span>  
  
#### <a name="scriptmap-deleted-under-web-sites-node"></a><span data-ttu-id="5a0ef-141">Usunięte w węźle witryn sieci Web właściwościach scriptmap</span><span class="sxs-lookup"><span data-stu-id="5a0ef-141">Scriptmap deleted under Web Sites node</span></span>  
 <span data-ttu-id="5a0ef-142">Na [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] maszyny, xoml lub Rules zostaną przypadkowo usunięte z węzła witryn sieci Web.</span><span class="sxs-lookup"><span data-stu-id="5a0ef-142">On a [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] machine, .xoml or .rules is accidentally deleted from the Web Sites node.</span></span> <span data-ttu-id="5a0ef-143">Można to naprawić, uruchamiając narzędzie WFServicesReg.exe z `/c` przełącznika.</span><span class="sxs-lookup"><span data-stu-id="5a0ef-143">This can be repaired by running the WFServicesReg.exe tool with the `/c` switch.</span></span>  
  
#### <a name="scriptmap-deleted-under-a-particular-web-site"></a><span data-ttu-id="5a0ef-144">Usunięte w obszarze określonej witryny sieci Web właściwościach scriptmap</span><span class="sxs-lookup"><span data-stu-id="5a0ef-144">Scriptmap deleted under a particular Web site</span></span>  
 <span data-ttu-id="5a0ef-145">Na [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] maszyny, xoml lub Rules zostaną przypadkowo usunięte z określonej witryny sieci Web (na przykład domyślna witryna sieci Web), a nie z węzła witryn sieci Web.</span><span class="sxs-lookup"><span data-stu-id="5a0ef-145">On a [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] machine, .xoml or .rules is accidentally deleted from a particular Web site (for example, the Default Web Site) rather than from the Web Sites node.</span></span>  
  
 <span data-ttu-id="5a0ef-146">Aby naprawić usunięto programy obsługi dla określonej witryny sieci Web, należy uruchomić "WFServicesReg.exe r" Aby usunąć obsługi z wszystkich witryn sieci Web, a następnie uruchomić "WFServicesReg.exe c" Aby utworzyć odpowiednie programy obsługi dla wszystkich witryn sieci Web.</span><span class="sxs-lookup"><span data-stu-id="5a0ef-146">To repair deleted handlers for a particular Web site, you should run "WFServicesReg.exe /r" to remove handlers from all Web sites, then run "WFServicesReg.exe /c" to create the appropriate handlers for all Web sites.</span></span>  
  
### <a name="configuring-handlers-after-switching-iis-mode"></a><span data-ttu-id="5a0ef-147">Konfigurowanie obsługi po przełączeniu w tryb usług IIS</span><span class="sxs-lookup"><span data-stu-id="5a0ef-147">Configuring handlers after switching IIS mode</span></span>  
 <span data-ttu-id="5a0ef-148">Gdy usługi IIS działają w trybie konfiguracji udostępnionej i [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] jest zainstalowany, metabazy usług IIS jest skonfigurowany w lokalizacji udostępnionej.</span><span class="sxs-lookup"><span data-stu-id="5a0ef-148">When IIS is in shared configuration mode and [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] is installed, the IIS metabase is configured under a shared location.</span></span> <span data-ttu-id="5a0ef-149">Jeśli usługi IIS nastąpi przełączenie do trybu konfiguracji nieudostępnione, metabazy lokalnej nie będzie zawierać wymagane programy obsługi.</span><span class="sxs-lookup"><span data-stu-id="5a0ef-149">If you switch IIS to non-shared configuration mode, the local metabase will not contain the required handlers.</span></span> <span data-ttu-id="5a0ef-150">Aby poprawnie skonfigurować lokalne metabazy, możesz zaimportować udostępnionego metabazy do lokalnego lub wykonywania "WFServicesReg.exe /c", który konfiguruje metabazy lokalnej.</span><span class="sxs-lookup"><span data-stu-id="5a0ef-150">To configure the local metabase properly, you can either import the shared metabase to local, or run "WFServicesReg.exe /c", which configures the local metabase.</span></span>
