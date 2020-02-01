---
title: Narzędzie rejestracji usług przepływu pracy (WFServicesReg.exe)
ms.date: 03/30/2017
ms.assetid: 9e92c87b-99c5-4e8d-9d53-7944cc2b47d3
ms.openlocfilehash: 5e7d39062a8ad016eebf949daa625a5ba7848328
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2020
ms.locfileid: "76921228"
---
# <a name="workflow-service-registration-tool-wfservicesregexe"></a><span data-ttu-id="ef035-102">Narzędzie rejestracji usług przepływu pracy (WFServicesReg.exe)</span><span class="sxs-lookup"><span data-stu-id="ef035-102">WorkFlow Service Registration Tool (WFServicesReg.exe)</span></span>
<span data-ttu-id="ef035-103">Narzędzie rejestracji usług przepływu pracy (WFServicesReg. exe) to autonomiczne narzędzie, które służy do dodawania, usuwania lub naprawiania elementów konfiguracji dla usług Windows Workflow Foundation (WF).</span><span class="sxs-lookup"><span data-stu-id="ef035-103">Workflow Services Registration tool (WFServicesReg.exe) is a stand-alone tool that can be used to add, remove, or repair the configuration elements for Windows Workflow Foundation (WF) services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef035-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ef035-104">Syntax</span></span>  
  
```console  
WFServicesReg.exe [-c | -r | -v | -m | -i]  
```  
  
## <a name="remarks"></a><span data-ttu-id="ef035-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ef035-105">Remarks</span></span>  
 <span data-ttu-id="ef035-106">Narzędzie to można znaleźć w lokalizacji instalacji .NET Framework 3,5, w tym%windir%\Microsoft.NET\Framework\v3.5 lub w%windir%\Microsoft.NET\Framework64\v3.5 na maszynach z 64-bitowym.</span><span class="sxs-lookup"><span data-stu-id="ef035-106">The tool can be found at the .NET Framework 3.5 installation location, specifically, %windir%\Microsoft.NET\Framework\v3.5, or at %windir%\Microsoft.NET\Framework64\v3.5 in 64-bit machines.</span></span>  
  
 <span data-ttu-id="ef035-107">W poniższych tabelach opisano opcje, które mogą być używane z narzędziem rejestracji usług przepływu pracy (WFServicesReg. exe).</span><span class="sxs-lookup"><span data-stu-id="ef035-107">The following tables describe the options that can be used with the Workflow Services Registration tool (WFServicesReg.exe).</span></span>  
  
|<span data-ttu-id="ef035-108">Opcja</span><span class="sxs-lookup"><span data-stu-id="ef035-108">Option</span></span>|<span data-ttu-id="ef035-109">Opis</span><span class="sxs-lookup"><span data-stu-id="ef035-109">Description</span></span>|  
|------------|-----------------|  
|`/c`|<span data-ttu-id="ef035-110">Konfiguruje usługi przepływu pracy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="ef035-110">Configures Windows Workflow Services.</span></span> <span data-ttu-id="ef035-111">Używany w scenariuszach instalacji i naprawy.</span><span class="sxs-lookup"><span data-stu-id="ef035-111">Used in install and repair scenarios.</span></span>|  
|`/r`|<span data-ttu-id="ef035-112">Usuwa konfigurację usług Windows Workflow Services.</span><span class="sxs-lookup"><span data-stu-id="ef035-112">Removes Windows Workflow Services Configuration.</span></span>|  
|`/v`|<span data-ttu-id="ef035-113">Drukuj pełne informacje (dla konfiguracji lub usuwania).</span><span class="sxs-lookup"><span data-stu-id="ef035-113">Print verbose information (for either configuration or removal).</span></span>|  
|`/m`|<span data-ttu-id="ef035-114">Włącza Format rejestrowania MSI.</span><span class="sxs-lookup"><span data-stu-id="ef035-114">Enables MSI logging format.</span></span>|  
|`/i`|<span data-ttu-id="ef035-115">Minimalizuje okno, gdy aplikacja jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="ef035-115">Minimizes the window when the application runs.</span></span>|  
  
## <a name="registration"></a><span data-ttu-id="ef035-116">Rejestracja</span><span class="sxs-lookup"><span data-stu-id="ef035-116">Registration</span></span>  
 <span data-ttu-id="ef035-117">Narzędzie sprawdza plik Web. config i rejestruje następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="ef035-117">The tool inspects the Web.config file and registers the following:</span></span>  
  
- <span data-ttu-id="ef035-118">Zestawy odwołań .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="ef035-118">.NET Framework 3.5 reference assemblies.</span></span>  
  
- <span data-ttu-id="ef035-119">Dostawca kompilacji dla plików xoml.</span><span class="sxs-lookup"><span data-stu-id="ef035-119">A build provider for .xoml files.</span></span>  
  
- <span data-ttu-id="ef035-120">Obsługa protokołu HTTP dla plików xoml i. rules.</span><span class="sxs-lookup"><span data-stu-id="ef035-120">HTTP handlers for .xoml and .rules files.</span></span>  
  
 <span data-ttu-id="ef035-121">Narzędzie sprawdza plik Machine. config i rejestruje następujące rozszerzenia:</span><span class="sxs-lookup"><span data-stu-id="ef035-121">The tool inspects the Machine.config file and registers the following extensions:</span></span>  
  
- <span data-ttu-id="ef035-122">behaviorExtensions</span><span class="sxs-lookup"><span data-stu-id="ef035-122">behaviorExtensions</span></span>  
  
- <span data-ttu-id="ef035-123">bindingElementExtensions</span><span class="sxs-lookup"><span data-stu-id="ef035-123">bindingElementExtensions</span></span>  
  
- <span data-ttu-id="ef035-124">bindingExtensions</span><span class="sxs-lookup"><span data-stu-id="ef035-124">bindingExtensions</span></span>  
  
 <span data-ttu-id="ef035-125">Narzędzie rejestruje także następujących importerów metadanych klienta:</span><span class="sxs-lookup"><span data-stu-id="ef035-125">The tool also registers the following client metadata importers:</span></span>  
  
- <span data-ttu-id="ef035-126">policyImporters</span><span class="sxs-lookup"><span data-stu-id="ef035-126">policyImporters</span></span>  
  
- <span data-ttu-id="ef035-127">wsdlImporters</span><span class="sxs-lookup"><span data-stu-id="ef035-127">wsdlImporters</span></span>  
  
 <span data-ttu-id="ef035-128">Narzędzie rejestruje również właściwości xoml i. rules oraz programy obsługi w metabazie usług IIS.</span><span class="sxs-lookup"><span data-stu-id="ef035-128">The tool also registers .xoml and .rules scriptmaps and handlers in the IIS metabase.</span></span>  
  
 <span data-ttu-id="ef035-129">Na komputerach z systemem Windows Server 2003 i Windows XP (IIS 5,1 i IIS 6,0) jest rejestrowany jeden zestaw właściwości xoml i. rules.</span><span class="sxs-lookup"><span data-stu-id="ef035-129">On Windows Server 2003 and Windows XP machines (IIS 5.1 and IIS 6.0), one set of .xoml and .rules scriptmaps are registered.</span></span>  
  
 <span data-ttu-id="ef035-130">Na komputerach 64-bitowych narzędzie rejestruje w trybie WOW mapowania skryptów, jeśli przełącznik `Enable32BitAppOnWin64` jest włączony, lub natywnie 64-bitowe mapowania skryptów, jeśli przełącznik `Enable32BitAppOnWin64` jest wyłączony.</span><span class="sxs-lookup"><span data-stu-id="ef035-130">On 64-bit machines, the tool registers WOW mode scriptmaps if the `Enable32BitAppOnWin64` switch is enabled, or native 64-bit scriptmaps if the `Enable32BitAppOnWin64` switch is disabled.</span></span>  
  
 <span data-ttu-id="ef035-131">Na maszynach z systemem Windows Vista i Windows Server 2008 (IIS 7,0 lub nowszym) są rejestrowane dwa zestawy programów xoml i.</span><span class="sxs-lookup"><span data-stu-id="ef035-131">On Windows Vista and Windows Server 2008 (IIS 7.0 and above) machines, two sets of .xoml and .rules handlers are registered: one for Integrated mode and one for Classic mode.</span></span>  
  
 <span data-ttu-id="ef035-132">Na komputerach 64-bitowych są zarejestrowane trzy zestawy programów obsługi (bez względu na stan przełącznika `Enable32BitAppOnWin64`): jeden dla trybu zintegrowanego, jeden dla klasycznego trybu WOW i jeden dla natywnego 64-bitowego trybu klasycznego.</span><span class="sxs-lookup"><span data-stu-id="ef035-132">On 64-bit machines, three sets of handlers are registered (regardless of the state of the `Enable32BitAppOnWin64` switch): one for Integrated mode, one for WOW Classic mode and one for native 64-bit Classic mode.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ef035-133">W przeciwieństwie do ServiceModelreg. exe, WFServicesReg. exe nie zezwala na dodawanie, usuwanie ani naprawianie skryptów lub programów obsługi dla określonej witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="ef035-133">Unlike ServiceModelreg.exe, WFServicesReg.exe does not allow adding, removing, or repairing scriptmaps or handlers for a particular Web site.</span></span> <span data-ttu-id="ef035-134">Aby obejść ten problem, zobacz sekcję "Naprawa skryptów".</span><span class="sxs-lookup"><span data-stu-id="ef035-134">For a workaround to this issue, see the "Repairing the Scriptmaps" section.</span></span>  
  
## <a name="usage-scenarios"></a><span data-ttu-id="ef035-135">Scenariusze użycia</span><span class="sxs-lookup"><span data-stu-id="ef035-135">Usage Scenarios</span></span>  
  
### <a name="installing-iis-after-net-framework-35-is-installed"></a><span data-ttu-id="ef035-136">Instalowanie usług IIS po zainstalowaniu .NET Framework 3,5</span><span class="sxs-lookup"><span data-stu-id="ef035-136">Installing IIS after .NET Framework 3.5 is installed</span></span>  
 <span data-ttu-id="ef035-137">Na komputerze z systemem Windows Server 2003 program .NET Framework 3,5 jest instalowany przed instalacją usług IIS.</span><span class="sxs-lookup"><span data-stu-id="ef035-137">On a Windows Server 2003 machine, .NET Framework 3.5 is installed prior to IIS installation.</span></span> <span data-ttu-id="ef035-138">Ze względu na niedostępność metabazy usług IIS instalacja programu .NET Framework 3,5 kończy się niepowodzeniem bez instalowania. xoml i. rules.</span><span class="sxs-lookup"><span data-stu-id="ef035-138">Due to the unavailability of the IIS metabase, installation of .NET Framework 3.5 succeeds without installing .xoml and .rules scriptmaps.</span></span>  
  
 <span data-ttu-id="ef035-139">Po zainstalowaniu usług IIS można użyć narzędzia WFServicesReg. exe z przełącznikiem `/c`, aby zainstalować te konkretne mapy skryptów.</span><span class="sxs-lookup"><span data-stu-id="ef035-139">After IIS is installed, you can use the WFServicesReg.exe tool with the `/c` switch to install these specific scriptmaps.</span></span>  
  
### <a name="repairing-the-scriptmaps"></a><span data-ttu-id="ef035-140">Naprawianie skryptów</span><span class="sxs-lookup"><span data-stu-id="ef035-140">Repairing the Scriptmaps</span></span>  
  
#### <a name="scriptmap-deleted-under-web-sites-node"></a><span data-ttu-id="ef035-141">Właściwości scriptmap usunięte w węźle witryny sieci Web</span><span class="sxs-lookup"><span data-stu-id="ef035-141">Scriptmap deleted under Web Sites node</span></span>  
 <span data-ttu-id="ef035-142">Na komputerze z systemem Windows Server 2003, xoml lub. reguły są przypadkowo usuwane z węzła witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="ef035-142">On a Windows Server 2003 machine, .xoml or .rules is accidentally deleted from the Web Sites node.</span></span> <span data-ttu-id="ef035-143">Można to naprawić, uruchamiając narzędzie WFServicesReg. exe z przełącznikiem `/c`.</span><span class="sxs-lookup"><span data-stu-id="ef035-143">This can be repaired by running the WFServicesReg.exe tool with the `/c` switch.</span></span>  
  
#### <a name="scriptmap-deleted-under-a-particular-web-site"></a><span data-ttu-id="ef035-144">Właściwości scriptmap usunięte w określonej witrynie sieci Web</span><span class="sxs-lookup"><span data-stu-id="ef035-144">Scriptmap deleted under a particular Web site</span></span>  
 <span data-ttu-id="ef035-145">Na komputerze z systemem Windows Server 2003, xoml lub. reguły są przypadkowo usuwane z określonej witryny sieci Web (na przykład domyślnej witryny sieci Web), a nie z węzła witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="ef035-145">On a Windows Server 2003 machine, .xoml or .rules is accidentally deleted from a particular Web site (for example, the Default Web Site) rather than from the Web Sites node.</span></span>  
  
 <span data-ttu-id="ef035-146">Aby naprawić usunięte programy obsługi dla określonej witryny sieci Web, należy uruchomić polecenie "WFServicesReg. exe/r", aby usunąć programy obsługi ze wszystkich witryn sieci Web, a następnie uruchomić polecenie "WFServicesReg. exe/c" w celu utworzenia odpowiednich programów obsługi dla wszystkich witryn sieci Web.</span><span class="sxs-lookup"><span data-stu-id="ef035-146">To repair deleted handlers for a particular Web site, you should run "WFServicesReg.exe /r" to remove handlers from all Web sites, then run "WFServicesReg.exe /c" to create the appropriate handlers for all Web sites.</span></span>  
  
### <a name="configuring-handlers-after-switching-iis-mode"></a><span data-ttu-id="ef035-147">Konfigurowanie programów obsługi po przełączeniu trybu usług IIS</span><span class="sxs-lookup"><span data-stu-id="ef035-147">Configuring handlers after switching IIS mode</span></span>  
 <span data-ttu-id="ef035-148">Gdy usługi IIS są w trybie konfiguracji udostępnionej i zainstalowano .NET Framework 3,5, metabaza usług IIS jest konfigurowana w lokalizacji udostępnionej.</span><span class="sxs-lookup"><span data-stu-id="ef035-148">When IIS is in shared configuration mode and .NET Framework 3.5 is installed, the IIS metabase is configured under a shared location.</span></span> <span data-ttu-id="ef035-149">W przypadku przełączenia usług IIS do trybu konfiguracji nieudostępnionej, lokalna metabaza nie będzie zawierać wymaganych programów obsługi.</span><span class="sxs-lookup"><span data-stu-id="ef035-149">If you switch IIS to non-shared configuration mode, the local metabase will not contain the required handlers.</span></span> <span data-ttu-id="ef035-150">Aby prawidłowo skonfigurować lokalną metabazę, możesz zaimportować udostępnioną metabazę do lokalnego lub uruchomić polecenie "WFServicesReg. exe/c", które konfiguruje lokalną metabazę.</span><span class="sxs-lookup"><span data-stu-id="ef035-150">To configure the local metabase properly, you can either import the shared metabase to local, or run "WFServicesReg.exe /c", which configures the local metabase.</span></span>
