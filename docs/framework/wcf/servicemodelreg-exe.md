---
title: Narzędzie rejestracji modelu ServiceModel (ServiceModelReg.exe)
ms.date: 03/30/2017
ms.assetid: 396ec5ae-e34f-4c64-a164-fcf50e86b6ac
ms.openlocfilehash: 5fab1a356cd035ed006bfe90d713e179907e0137
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="servicemodel-registration-tool-servicemodelregexe"></a><span data-ttu-id="e8d9b-102">Narzędzie rejestracji modelu ServiceModel (ServiceModelReg.exe)</span><span class="sxs-lookup"><span data-stu-id="e8d9b-102">ServiceModel Registration Tool (ServiceModelReg.exe)</span></span>
<span data-ttu-id="e8d9b-103">To narzędzie wiersza polecenia umożliwia zarządzanie rejestracją składników WCF i WF na jednym komputerze.</span><span class="sxs-lookup"><span data-stu-id="e8d9b-103">This command-line tool provides the ability to manage the registration of WCF and WF components on a single machine.</span></span> <span data-ttu-id="e8d9b-104">W normalnych okolicznościach nie należy do tego narzędzia można użyć jako WCF i WF składniki są konfigurowane podczas instalacji.</span><span class="sxs-lookup"><span data-stu-id="e8d9b-104">Under normal circumstances you should not need to use this tool as WCF and WF components are configured when installed.</span></span> <span data-ttu-id="e8d9b-105">Ale jeśli masz problemy z aktywacją usługi, możesz zarejestrować składników za pomocą tego narzędzia.</span><span class="sxs-lookup"><span data-stu-id="e8d9b-105">But if you are experiencing problems with service activation, you can try to register the components using this tool.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8d9b-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="e8d9b-106">Syntax</span></span>  
  
```  
ServiceModelReg.exe[(-ia|-ua|-r)|((-i|-u) -c:<command>)] [-v|-q] [-nologo] [-?]  
```  
  
## <a name="remarks"></a><span data-ttu-id="e8d9b-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e8d9b-107">Remarks</span></span>  
 <span data-ttu-id="e8d9b-108">Narzędzie można znaleźć w następującej lokalizacji:</span><span class="sxs-lookup"><span data-stu-id="e8d9b-108">The tool can be found in the following location:</span></span>  
  
 <span data-ttu-id="e8d9b-109">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Foundation\ komunikacji</span><span class="sxs-lookup"><span data-stu-id="e8d9b-109">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation\\</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e8d9b-110">Po uruchomieniu narzędzia rejestracji modelu ServiceModel [!INCLUDE[wv](../../../includes/wv-md.md)], **funkcje systemu Windows** oknie dialogowym mogą nie uwzględniać który **Aktywacja HTTP programu Windows Communication Foundation** opcję w obszarze **Microsoft .NET Framework 3.0** jest włączona.</span><span class="sxs-lookup"><span data-stu-id="e8d9b-110">When the ServiceModel Registration Tool is run on [!INCLUDE[wv](../../../includes/wv-md.md)], the **Windows Features** dialog may not reflect that the **Windows Communication Foundation HTTP Activation** option under **Microsoft .NET Framework 3.0** is turned on.</span></span> <span data-ttu-id="e8d9b-111">**Funkcje systemu Windows** okna dialogowego można uzyskać, klikając **Start**, następnie kliknij przycisk **Uruchom** , a następnie wpisując **OptionalFeatures**.</span><span class="sxs-lookup"><span data-stu-id="e8d9b-111">The **Windows Features** dialog can be accessed by clicking **Start**, then click **Run** and then typing **OptionalFeatures**.</span></span>  
  
 <span data-ttu-id="e8d9b-112">W poniższych tabelach opisano opcje, które mogą być używane z ServiceModelReg.exe.</span><span class="sxs-lookup"><span data-stu-id="e8d9b-112">The following tables describe the options that can be used with ServiceModelReg.exe.</span></span>  
  
|<span data-ttu-id="e8d9b-113">Opcja</span><span class="sxs-lookup"><span data-stu-id="e8d9b-113">Option</span></span>|<span data-ttu-id="e8d9b-114">Opis</span><span class="sxs-lookup"><span data-stu-id="e8d9b-114">Description</span></span>|  
|------------|-----------------|  
|`-ia`|<span data-ttu-id="e8d9b-115">Instaluje wszystkie składniki usługi WCF i WF.</span><span class="sxs-lookup"><span data-stu-id="e8d9b-115">Installs all WCF and WF components.</span></span>|  
|`-ua`|<span data-ttu-id="e8d9b-116">Odinstalowuje wszystkie składniki usługi WCF i WF.</span><span class="sxs-lookup"><span data-stu-id="e8d9b-116">Uninstalls all WCF and WF components.</span></span>|  
|`-r`|<span data-ttu-id="e8d9b-117">Naprawia wszystkie składniki usługi WCF i WF.</span><span class="sxs-lookup"><span data-stu-id="e8d9b-117">Repairs all WCF and WF components.</span></span>|  
|`-i`|<span data-ttu-id="e8d9b-118">Instaluje składniki usługi WCF i WF określony za pomocą – c.</span><span class="sxs-lookup"><span data-stu-id="e8d9b-118">Installs WCF and WF components specified with –c.</span></span>|  
|`-u`|<span data-ttu-id="e8d9b-119">Odinstalowuje składniki usługi WCF i WF określony za pomocą – c.</span><span class="sxs-lookup"><span data-stu-id="e8d9b-119">Uninstalls WCF and WF components specified with –c.</span></span>|  
|`-c`|<span data-ttu-id="e8d9b-120">Instaluje lub odinstalowuje składnik:</span><span class="sxs-lookup"><span data-stu-id="e8d9b-120">Installs or uninstalls a component:</span></span><br /><br /> <span data-ttu-id="e8d9b-121">-httpnamespace — Rezerwacja Namespace protokołu HTTP</span><span class="sxs-lookup"><span data-stu-id="e8d9b-121">-   httpnamespace – HTTP Namespace Reservation</span></span><br /><span data-ttu-id="e8d9b-122">Usługa udostępniania portów - tcpportsharing — TCP</span><span class="sxs-lookup"><span data-stu-id="e8d9b-122">-   tcpportsharing – TCP port sharing service</span></span><br /><span data-ttu-id="e8d9b-123">Usługa aktywacji - tcpactivation — TCP (obsługiwane na .NET 4 Client Profile)</span><span class="sxs-lookup"><span data-stu-id="e8d9b-123">-   tcpactivation – TCP activation service (unsupported on .NET 4 Client Profile)</span></span><br /><span data-ttu-id="e8d9b-124">usługi - namedpipeactivation — nazwanego potoku aktywacji (obsługiwane na .NET 4 Client Profile</span><span class="sxs-lookup"><span data-stu-id="e8d9b-124">-   namedpipeactivation – Named pipe activation service (unsupported on .NET 4 Client Profile</span></span><br /><span data-ttu-id="e8d9b-125">Usługa aktywacji - msmqactivation — MSMQ (obsługiwane na .NET 4 Client Profile</span><span class="sxs-lookup"><span data-stu-id="e8d9b-125">-   msmqactivation – MSMQ activation service (unsupported on .NET 4 Client Profile</span></span><br /><span data-ttu-id="e8d9b-126">manifesty śledzenie zdarzeń — etw — ETW (system Windows Vista lub nowszy)</span><span class="sxs-lookup"><span data-stu-id="e8d9b-126">-   etw – ETW event tracing manifests (Windows Vista or later)</span></span>|  
|`-q`|<span data-ttu-id="e8d9b-127">Tryb cichy (tylko rejestrowania błędów wyświetlania)</span><span class="sxs-lookup"><span data-stu-id="e8d9b-127">Quiet mode (only display error logging)</span></span>|  
|`-v`|<span data-ttu-id="e8d9b-128">Tryb informacji pełnej.</span><span class="sxs-lookup"><span data-stu-id="e8d9b-128">Verbose mode.</span></span>|  
|`-nologo`|<span data-ttu-id="e8d9b-129">Pomija komunikat o prawach autorskich oraz transparent.</span><span class="sxs-lookup"><span data-stu-id="e8d9b-129">Suppresses the copyright and banner message.</span></span>|  
|`-?`|<span data-ttu-id="e8d9b-130">Wyświetla Pomoc</span><span class="sxs-lookup"><span data-stu-id="e8d9b-130">Displays help text</span></span>|  
  
## <a name="fixing-the-fileloadexception-error"></a><span data-ttu-id="e8d9b-131">Naprawienie błędu fileloadexception —</span><span class="sxs-lookup"><span data-stu-id="e8d9b-131">Fixing the FileLoadException Error</span></span>  
 <span data-ttu-id="e8d9b-132">Jeśli poprzednie wersje usług WCF jest zainstalowany na tym komputerze, mogą wystąpić `FileLoadFoundException` błąd podczas uruchamiania narzędzia ServiceModelReg można zarejestrować nowej instalacji.</span><span class="sxs-lookup"><span data-stu-id="e8d9b-132">If you installed previous versions of WCF on your machine, you may get a `FileLoadFoundException` error when you run the ServiceModelReg tool to register a new installation.</span></span> <span data-ttu-id="e8d9b-133">Może to nastąpić, nawet jeśli masz ręcznie usunąć pliki z poprzedniej instalacji, ale pozostanie bez zmian ustawień pliku machine.config.</span><span class="sxs-lookup"><span data-stu-id="e8d9b-133">This can happen even if you have manually removed files from the previous install, but left the machine.config settings intact.</span></span>  
  
 <span data-ttu-id="e8d9b-134">Komunikat o błędzie jest podobny do następującego.</span><span class="sxs-lookup"><span data-stu-id="e8d9b-134">The error message is similar to the following.</span></span>  
  
```  
Error: System.IO.FileLoadException: Could not load file or assembly 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies. The located assembly's manifest definition does not match the assembly reference. (Exception from HRESULT: 0x80131040)  
File name: 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'  
```  
  
 <span data-ttu-id="e8d9b-135">Należy zauważyć, komunikat o błędzie do zainstalowania zestawu System.ServiceModel wersji 2.0.0.0 przez wczesnego wydawania klienta Technology Preview (CTP).</span><span class="sxs-lookup"><span data-stu-id="e8d9b-135">You should note from the error message that the System.ServiceModel Version 2.0.0.0 assembly was installed by an early Customer Technology Preview (CTP) release.</span></span> <span data-ttu-id="e8d9b-136">Bieżąca wersja zestawu System.ServiceModel wydane jest 3.0.0.0 w zamian.</span><span class="sxs-lookup"><span data-stu-id="e8d9b-136">The current version of the System.ServiceModel assembly released is 3.0.0.0 instead.</span></span> <span data-ttu-id="e8d9b-137">Jeśli chcesz zainstalować oficjalnego wydania usługi WCF na komputerze, na którym wczesne wersji CTP programu WCF został zainstalowany, ale nie całkowicie odinstalowany w związku z tym napotkano ten problem.</span><span class="sxs-lookup"><span data-stu-id="e8d9b-137">Therefore, this issue is encountered when you want to install the official WCF release on a machine where an early CTP release of WCF was installed, but not completely uninstalled.</span></span>  
  
 <span data-ttu-id="e8d9b-138">ServiceModelReg.exe nie można wyczyścić wpisy wcześniejsze niż wersja, nie można zarejestrować nową wersję wpisów.</span><span class="sxs-lookup"><span data-stu-id="e8d9b-138">ServiceModelReg.exe cannot clean up prior version entries, nor can it register the new version's entries.</span></span> <span data-ttu-id="e8d9b-139">Tylko obejście jest ręcznie edytować pliku machine.config. Możesz znaleźć tego pliku w następującej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="e8d9b-139">The only workaround is to manually edit machine.config. You can locate this file at the following location.</span></span>  
  
```  
%windir%\Microsoft.NET\Framework\v2.0.50727\config\machine.config   
```  
  
 <span data-ttu-id="e8d9b-140">Jeśli używasz usługi WCF na komputerze 64-bitowych, należy również edytować tego samego pliku w tej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="e8d9b-140">If you are running WCF on a 64-bit machine, you should also edit the same file at this location.</span></span>  
  
```  
%windir%\Microsoft.NET\Framework64\v2.0.50727\config\machine.config   
```  
  
 <span data-ttu-id="e8d9b-141">Zlokalizuj żadnym węzłem XML w tym pliku, która odwołuje się do "System.ServiceModel, Version = 2.0.0.0", usuń je i węzły podrzędne.</span><span class="sxs-lookup"><span data-stu-id="e8d9b-141">Locate any XML nodes in this file that refer to "System.ServiceModel, Version=2.0.0.0", delete them and any child nodes.</span></span> <span data-ttu-id="e8d9b-142">Zapisz plik i ponownie uruchom ServiceModelReg.exe rozwiązuje ten problem.</span><span class="sxs-lookup"><span data-stu-id="e8d9b-142">Save the file and re-run ServiceModelReg.exe resolves this problem.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="e8d9b-143">Przykłady</span><span class="sxs-lookup"><span data-stu-id="e8d9b-143">Examples</span></span>  
 <span data-ttu-id="e8d9b-144">Następujące przykłady przedstawiają sposób użycia najczęściej używanych opcji narzędzia ServiceModelReg.exe.</span><span class="sxs-lookup"><span data-stu-id="e8d9b-144">The following examples show how to use the most common options of the ServiceModelReg.exe tool.</span></span>  
  
```  
ServiceModelReg.exe -ia  
  Installs all components  
ServiceModelReg.exe -i -c:httpnamespace -c:etw  
  Installs HTTP namespace reservation and ETW manifests  
ServiceModelReg.exe -u -c:etw  
  Uninstalls ETW manifests  
ServiceModelReg.exe -r  
  Repairs an extended install  
```
