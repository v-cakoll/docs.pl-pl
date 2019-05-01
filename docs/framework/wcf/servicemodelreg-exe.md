---
title: Narzędzie rejestracji modelu ServiceModel (ServiceModelReg.exe)
ms.date: 03/30/2017
ms.assetid: 396ec5ae-e34f-4c64-a164-fcf50e86b6ac
ms.openlocfilehash: 5fab1a356cd035ed006bfe90d713e179907e0137
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051796"
---
# <a name="servicemodel-registration-tool-servicemodelregexe"></a><span data-ttu-id="cb274-102">Narzędzie rejestracji modelu ServiceModel (ServiceModelReg.exe)</span><span class="sxs-lookup"><span data-stu-id="cb274-102">ServiceModel Registration Tool (ServiceModelReg.exe)</span></span>
<span data-ttu-id="cb274-103">To narzędzie wiersza polecenia umożliwia zarządzanie rejestracją programu WCF i WF składników na jednym komputerze.</span><span class="sxs-lookup"><span data-stu-id="cb274-103">This command-line tool provides the ability to manage the registration of WCF and WF components on a single machine.</span></span> <span data-ttu-id="cb274-104">W normalnych warunkach nie należy do tego narzędzia można używać jako usługi WCF i WF składniki są konfigurowane podczas instalacji.</span><span class="sxs-lookup"><span data-stu-id="cb274-104">Under normal circumstances you should not need to use this tool as WCF and WF components are configured when installed.</span></span> <span data-ttu-id="cb274-105">Ale jeśli występują problemy z aktywacji usługi, możesz spróbować by zarejestrować komponenty za pomocą tego narzędzia.</span><span class="sxs-lookup"><span data-stu-id="cb274-105">But if you are experiencing problems with service activation, you can try to register the components using this tool.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb274-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="cb274-106">Syntax</span></span>  
  
```  
ServiceModelReg.exe[(-ia|-ua|-r)|((-i|-u) -c:<command>)] [-v|-q] [-nologo] [-?]  
```  
  
## <a name="remarks"></a><span data-ttu-id="cb274-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cb274-107">Remarks</span></span>  
 <span data-ttu-id="cb274-108">Narzędzie można znaleźć w następującej lokalizacji:</span><span class="sxs-lookup"><span data-stu-id="cb274-108">The tool can be found in the following location:</span></span>  
  
 <span data-ttu-id="cb274-109">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation\\</span><span class="sxs-lookup"><span data-stu-id="cb274-109">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation\\</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cb274-110">Po uruchomieniu narzędzie rejestracji modelu ServiceModel [!INCLUDE[wv](../../../includes/wv-md.md)], **funkcji Windows** oknie dialogowym mogą nie odzwierciedlać, **Aktywacja HTTP programu Windows Communication Foundation** opcję w obszarze **Microsoft .NET Framework 3.0** jest włączona.</span><span class="sxs-lookup"><span data-stu-id="cb274-110">When the ServiceModel Registration Tool is run on [!INCLUDE[wv](../../../includes/wv-md.md)], the **Windows Features** dialog may not reflect that the **Windows Communication Foundation HTTP Activation** option under **Microsoft .NET Framework 3.0** is turned on.</span></span> <span data-ttu-id="cb274-111">**Funkcji Windows** okno dialogowe jest możliwy, klikając **Start**, następnie kliknij przycisk **Uruchom** , a następnie wpisując **OptionalFeatures**.</span><span class="sxs-lookup"><span data-stu-id="cb274-111">The **Windows Features** dialog can be accessed by clicking **Start**, then click **Run** and then typing **OptionalFeatures**.</span></span>  
  
 <span data-ttu-id="cb274-112">W poniższych tabelach opisano opcje, które mogą być używane z ServiceModelReg.exe.</span><span class="sxs-lookup"><span data-stu-id="cb274-112">The following tables describe the options that can be used with ServiceModelReg.exe.</span></span>  
  
|<span data-ttu-id="cb274-113">Opcja</span><span class="sxs-lookup"><span data-stu-id="cb274-113">Option</span></span>|<span data-ttu-id="cb274-114">Opis</span><span class="sxs-lookup"><span data-stu-id="cb274-114">Description</span></span>|  
|------------|-----------------|  
|`-ia`|<span data-ttu-id="cb274-115">Instaluje wszystkie składniki programu WCF i WF.</span><span class="sxs-lookup"><span data-stu-id="cb274-115">Installs all WCF and WF components.</span></span>|  
|`-ua`|<span data-ttu-id="cb274-116">Odinstalowuje wszystkie składniki programu WCF i WF.</span><span class="sxs-lookup"><span data-stu-id="cb274-116">Uninstalls all WCF and WF components.</span></span>|  
|`-r`|<span data-ttu-id="cb274-117">Naprawia wszystkie składniki programu WCF i WF.</span><span class="sxs-lookup"><span data-stu-id="cb274-117">Repairs all WCF and WF components.</span></span>|  
|`-i`|<span data-ttu-id="cb274-118">Instaluje składniki usługi WCF i WF określony za pomocą – c.</span><span class="sxs-lookup"><span data-stu-id="cb274-118">Installs WCF and WF components specified with –c.</span></span>|  
|`-u`|<span data-ttu-id="cb274-119">Odinstalowuje program WCF i WF składniki określony za pomocą – c.</span><span class="sxs-lookup"><span data-stu-id="cb274-119">Uninstalls WCF and WF components specified with –c.</span></span>|  
|`-c`|<span data-ttu-id="cb274-120">Instaluje lub odinstalowuje składnik:</span><span class="sxs-lookup"><span data-stu-id="cb274-120">Installs or uninstalls a component:</span></span><br /><br /> <span data-ttu-id="cb274-121">-httpnamespace — rezerwacji Namespace HTTP</span><span class="sxs-lookup"><span data-stu-id="cb274-121">-   httpnamespace – HTTP Namespace Reservation</span></span><br /><span data-ttu-id="cb274-122">współużytkowania portów - tcpportsharing — TCP</span><span class="sxs-lookup"><span data-stu-id="cb274-122">-   tcpportsharing – TCP port sharing service</span></span><br /><span data-ttu-id="cb274-123">Usługa aktywacji - tcpactivation — TCP (nieobsługiwane w .NET 4 Client Profile)</span><span class="sxs-lookup"><span data-stu-id="cb274-123">-   tcpactivation – TCP activation service (unsupported on .NET 4 Client Profile)</span></span><br /><span data-ttu-id="cb274-124">usługi - namedpipeactivation — Aktywacja potoku nazwanego (nieobsługiwane w .NET 4 Client Profile</span><span class="sxs-lookup"><span data-stu-id="cb274-124">-   namedpipeactivation – Named pipe activation service (unsupported on .NET 4 Client Profile</span></span><br /><span data-ttu-id="cb274-125">Usługa aktywacji - msmqactivation — MSMQ (nieobsługiwane w .NET 4 Client Profile</span><span class="sxs-lookup"><span data-stu-id="cb274-125">-   msmqactivation – MSMQ activation service (unsupported on .NET 4 Client Profile</span></span><br /><span data-ttu-id="cb274-126">manifestów śledzenie zdarzeń — etw — zdarzeń systemu Windows (Windows Vista lub nowszy)</span><span class="sxs-lookup"><span data-stu-id="cb274-126">-   etw – ETW event tracing manifests (Windows Vista or later)</span></span>|  
|`-q`|<span data-ttu-id="cb274-127">Tryb cichy (tylko rejestrowanie błędów display)</span><span class="sxs-lookup"><span data-stu-id="cb274-127">Quiet mode (only display error logging)</span></span>|  
|`-v`|<span data-ttu-id="cb274-128">Tryb informacji pełnej.</span><span class="sxs-lookup"><span data-stu-id="cb274-128">Verbose mode.</span></span>|  
|`-nologo`|<span data-ttu-id="cb274-129">Pomija komunikat o prawach autorskich i baneru.</span><span class="sxs-lookup"><span data-stu-id="cb274-129">Suppresses the copyright and banner message.</span></span>|  
|`-?`|<span data-ttu-id="cb274-130">Wyświetla tekst pomocy</span><span class="sxs-lookup"><span data-stu-id="cb274-130">Displays help text</span></span>|  
  
## <a name="fixing-the-fileloadexception-error"></a><span data-ttu-id="cb274-131">Naprawianie błędów fileloadexception —</span><span class="sxs-lookup"><span data-stu-id="cb274-131">Fixing the FileLoadException Error</span></span>  
 <span data-ttu-id="cb274-132">Jeśli w poprzednich wersjach programu WCF jest zainstalowany na komputerze, może wystąpić `FileLoadFoundException` błąd podczas uruchamiania narzędzia ServiceModelReg do zarejestrowania nowej instalacji.</span><span class="sxs-lookup"><span data-stu-id="cb274-132">If you installed previous versions of WCF on your machine, you may get a `FileLoadFoundException` error when you run the ServiceModelReg tool to register a new installation.</span></span> <span data-ttu-id="cb274-133">Można to zrobić, nawet jeśli zajmujesz się ręcznie usunąć pliki z poprzedniej instalacji, ale ustawienia w pliku machine.config pozostają niezmienione.</span><span class="sxs-lookup"><span data-stu-id="cb274-133">This can happen even if you have manually removed files from the previous install, but left the machine.config settings intact.</span></span>  
  
 <span data-ttu-id="cb274-134">Komunikat o błędzie jest podobny do następującego.</span><span class="sxs-lookup"><span data-stu-id="cb274-134">The error message is similar to the following.</span></span>  
  
```  
Error: System.IO.FileLoadException: Could not load file or assembly 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies. The located assembly's manifest definition does not match the assembly reference. (Exception from HRESULT: 0x80131040)  
File name: 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'  
```  
  
 <span data-ttu-id="cb274-135">Należy zauważyć, z komunikatu o błędzie zainstalowanie zestawu System.ServiceModel wersji 2.0.0.0 lub nowszej, to wczesna wersja Customer Technology Preview (CTP).</span><span class="sxs-lookup"><span data-stu-id="cb274-135">You should note from the error message that the System.ServiceModel Version 2.0.0.0 assembly was installed by an early Customer Technology Preview (CTP) release.</span></span> <span data-ttu-id="cb274-136">Bieżąca wersja zestawu System.ServiceModel wydania jest 3.0.0.0 zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="cb274-136">The current version of the System.ServiceModel assembly released is 3.0.0.0 instead.</span></span> <span data-ttu-id="cb274-137">W związku z tym ten problem występuje, jeśli chcesz zainstalować oficjalnego wydania usługi WCF na komputerze, gdzie to wczesna wersja CTP programu WCF została zainstalowana, ale nie jest całkowicie odinstalowany.</span><span class="sxs-lookup"><span data-stu-id="cb274-137">Therefore, this issue is encountered when you want to install the official WCF release on a machine where an early CTP release of WCF was installed, but not completely uninstalled.</span></span>  
  
 <span data-ttu-id="cb274-138">ServiceModelReg.exe nie można wyczyścić wpisów z poprzedniej wersji, nie można zarejestrować nową wersję wpisów.</span><span class="sxs-lookup"><span data-stu-id="cb274-138">ServiceModelReg.exe cannot clean up prior version entries, nor can it register the new version's entries.</span></span> <span data-ttu-id="cb274-139">Jedynym obejściem jest ręczna Edycja pliku machine.config. Można zlokalizować ten plik w następującej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="cb274-139">The only workaround is to manually edit machine.config. You can locate this file at the following location.</span></span>  
  
```  
%windir%\Microsoft.NET\Framework\v2.0.50727\config\machine.config   
```  
  
 <span data-ttu-id="cb274-140">Jeśli używasz programu WCF na komputerze 64-bitowym, możesz również edytować tego samego pliku, w tym miejscu.</span><span class="sxs-lookup"><span data-stu-id="cb274-140">If you are running WCF on a 64-bit machine, you should also edit the same file at this location.</span></span>  
  
```  
%windir%\Microsoft.NET\Framework64\v2.0.50727\config\machine.config   
```  
  
 <span data-ttu-id="cb274-141">Znajdź żadnym węzłem XML w tym pliku, który odwołuje się do "System.ServiceModel, Version = 2.0.0.0", usuń je i wszystkie węzły podrzędne.</span><span class="sxs-lookup"><span data-stu-id="cb274-141">Locate any XML nodes in this file that refer to "System.ServiceModel, Version=2.0.0.0", delete them and any child nodes.</span></span> <span data-ttu-id="cb274-142">Zapisz plik i ponownie uruchom ServiceModelReg.exe rozwiązuje ten problem.</span><span class="sxs-lookup"><span data-stu-id="cb274-142">Save the file and re-run ServiceModelReg.exe resolves this problem.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="cb274-143">Przykłady</span><span class="sxs-lookup"><span data-stu-id="cb274-143">Examples</span></span>  
 <span data-ttu-id="cb274-144">Poniższe przykłady pokazują, jak korzystać z najbardziej typowych opcji narzędzia ServiceModelReg.exe.</span><span class="sxs-lookup"><span data-stu-id="cb274-144">The following examples show how to use the most common options of the ServiceModelReg.exe tool.</span></span>  
  
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
