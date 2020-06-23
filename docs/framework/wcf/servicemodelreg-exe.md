---
title: Narzędzie rejestracji modelu ServiceModel (ServiceModelReg.exe)
description: Za pomocą tego narzędzia wiersza polecenia można zarządzać rejestracją składników WCF i WF na jednym komputerze w przypadku wystąpienia problemów z aktywacją usługi.
ms.date: 03/30/2017
ms.assetid: 396ec5ae-e34f-4c64-a164-fcf50e86b6ac
ms.openlocfilehash: 347b1b8071abe7d8eb7e16ffd879c1fdb9825bc7
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245898"
---
# <a name="servicemodel-registration-tool-servicemodelregexe"></a><span data-ttu-id="d22d8-103">Narzędzie rejestracji modelu ServiceModel (ServiceModelReg.exe)</span><span class="sxs-lookup"><span data-stu-id="d22d8-103">ServiceModel Registration Tool (ServiceModelReg.exe)</span></span>
<span data-ttu-id="d22d8-104">To narzędzie wiersza polecenia zapewnia możliwość zarządzania rejestracją składników WCF i WF na jednym komputerze.</span><span class="sxs-lookup"><span data-stu-id="d22d8-104">This command-line tool provides the ability to manage the registration of WCF and WF components on a single machine.</span></span> <span data-ttu-id="d22d8-105">W normalnych okolicznościach nie należy używać tego narzędzia, ponieważ składniki WCF i WF są skonfigurowane podczas instalacji.</span><span class="sxs-lookup"><span data-stu-id="d22d8-105">Under normal circumstances you should not need to use this tool as WCF and WF components are configured when installed.</span></span> <span data-ttu-id="d22d8-106">Jeśli jednak występują problemy z aktywacją usługi, możesz spróbować zarejestrować składniki przy użyciu tego narzędzia.</span><span class="sxs-lookup"><span data-stu-id="d22d8-106">But if you are experiencing problems with service activation, you can try to register the components using this tool.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d22d8-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="d22d8-107">Syntax</span></span>  
  
```console  
ServiceModelReg.exe[(-ia|-ua|-r)|((-i|-u) -c:<command>)] [-v|-q] [-nologo] [-?]  
```  
  
## <a name="remarks"></a><span data-ttu-id="d22d8-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d22d8-108">Remarks</span></span>  
 <span data-ttu-id="d22d8-109">Narzędzie można znaleźć w następującej lokalizacji:</span><span class="sxs-lookup"><span data-stu-id="d22d8-109">The tool can be found in the following location:</span></span>  
  
 <span data-ttu-id="d22d8-110">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation </span><span class="sxs-lookup"><span data-stu-id="d22d8-110">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation</span></span>\  
  
> [!NOTE]
> <span data-ttu-id="d22d8-111">Po uruchomieniu narzędzia rejestracji ServiceModel w systemie Windows Vista okno dialogowe **funkcji systemu Windows** może nie odzwierciedlać, że opcja **Windows Communication Foundation aktywacji HTTP** w obszarze **Microsoft .NET Framework 3,0** jest włączona.</span><span class="sxs-lookup"><span data-stu-id="d22d8-111">When the ServiceModel Registration Tool is run on Windows Vista, the **Windows Features** dialog may not reflect that the **Windows Communication Foundation HTTP Activation** option under **Microsoft .NET Framework 3.0** is turned on.</span></span> <span data-ttu-id="d22d8-112">Do okna dialogowego **funkcje systemu Windows** można uzyskać dostęp przez kliknięcie przycisku **Start**, a następnie kliknij pozycję **Uruchom** , a następnie wpisz **OptionalFeatures**.</span><span class="sxs-lookup"><span data-stu-id="d22d8-112">The **Windows Features** dialog can be accessed by clicking **Start**, then click **Run** and then typing **OptionalFeatures**.</span></span>  
  
 <span data-ttu-id="d22d8-113">W poniższych tabelach opisano opcje, które mogą być używane z ServiceModelReg.exe.</span><span class="sxs-lookup"><span data-stu-id="d22d8-113">The following tables describe the options that can be used with ServiceModelReg.exe.</span></span>  
  
|<span data-ttu-id="d22d8-114">Opcja</span><span class="sxs-lookup"><span data-stu-id="d22d8-114">Option</span></span>|<span data-ttu-id="d22d8-115">Opis</span><span class="sxs-lookup"><span data-stu-id="d22d8-115">Description</span></span>|  
|------------|-----------------|  
|`-ia`|<span data-ttu-id="d22d8-116">Instaluje wszystkie składniki WCF i WF.</span><span class="sxs-lookup"><span data-stu-id="d22d8-116">Installs all WCF and WF components.</span></span>|  
|`-ua`|<span data-ttu-id="d22d8-117">Odinstalowuje wszystkie składniki WCF i WF.</span><span class="sxs-lookup"><span data-stu-id="d22d8-117">Uninstalls all WCF and WF components.</span></span>|  
|`-r`|<span data-ttu-id="d22d8-118">Naprawia wszystkie składniki WCF i WF.</span><span class="sxs-lookup"><span data-stu-id="d22d8-118">Repairs all WCF and WF components.</span></span>|  
|`-i`|<span data-ttu-id="d22d8-119">Instaluje składniki WCF i WF określone za pomocą parametru-c.</span><span class="sxs-lookup"><span data-stu-id="d22d8-119">Installs WCF and WF components specified with –c.</span></span>|  
|`-u`|<span data-ttu-id="d22d8-120">Odinstalowuje składniki WCF i WF określone za pomocą parametru-c.</span><span class="sxs-lookup"><span data-stu-id="d22d8-120">Uninstalls WCF and WF components specified with –c.</span></span>|  
|`-c`|<span data-ttu-id="d22d8-121">Instaluje lub Odinstalowuje składnik:</span><span class="sxs-lookup"><span data-stu-id="d22d8-121">Installs or uninstalls a component:</span></span><br /><br /> <span data-ttu-id="d22d8-122">-httpnamespace — rezerwacja przestrzeni nazw protokołu HTTP</span><span class="sxs-lookup"><span data-stu-id="d22d8-122">-   httpnamespace – HTTP Namespace Reservation</span></span><br /><span data-ttu-id="d22d8-123">-tcpportsharing — usługa udostępniania portów TCP</span><span class="sxs-lookup"><span data-stu-id="d22d8-123">-   tcpportsharing – TCP port sharing service</span></span><br /><span data-ttu-id="d22d8-124">-tcpactivation — usługa aktywacji TCP (nieobsługiwana w profilu klienta .NET 4)</span><span class="sxs-lookup"><span data-stu-id="d22d8-124">-   tcpactivation – TCP activation service (unsupported on .NET 4 Client Profile)</span></span><br /><span data-ttu-id="d22d8-125">-namedpipeactivation — usługa aktywacji potoków nazwanych (nieobsługiwana w profilu klienta .NET 4</span><span class="sxs-lookup"><span data-stu-id="d22d8-125">-   namedpipeactivation – Named pipe activation service (unsupported on .NET 4 Client Profile</span></span><br /><span data-ttu-id="d22d8-126">-Usługa MsmqActivation — usługa aktywacji usługi MSMQ (nieobsługiwana w profilu klienta .NET 4</span><span class="sxs-lookup"><span data-stu-id="d22d8-126">-   msmqactivation – MSMQ activation service (unsupported on .NET 4 Client Profile</span></span><br /><span data-ttu-id="d22d8-127">-ETW — manifesty śledzenia zdarzeń ETW (system Windows Vista lub nowszy)</span><span class="sxs-lookup"><span data-stu-id="d22d8-127">-   etw – ETW event tracing manifests (Windows Vista or later)</span></span>|  
|`-q`|<span data-ttu-id="d22d8-128">Tryb cichy (wyświetla tylko rejestrowanie błędów)</span><span class="sxs-lookup"><span data-stu-id="d22d8-128">Quiet mode (only display error logging)</span></span>|  
|`-v`|<span data-ttu-id="d22d8-129">Tryb informacji pełnej.</span><span class="sxs-lookup"><span data-stu-id="d22d8-129">Verbose mode.</span></span>|  
|`-nologo`|<span data-ttu-id="d22d8-130">Pomija informacje o prawach autorskich i baneru.</span><span class="sxs-lookup"><span data-stu-id="d22d8-130">Suppresses the copyright and banner message.</span></span>|  
|`-?`|<span data-ttu-id="d22d8-131">Wyświetla tekst pomocy</span><span class="sxs-lookup"><span data-stu-id="d22d8-131">Displays help text</span></span>|  
  
## <a name="fixing-the-fileloadexception-error"></a><span data-ttu-id="d22d8-132">Naprawianie błędu FileLoadException</span><span class="sxs-lookup"><span data-stu-id="d22d8-132">Fixing the FileLoadException Error</span></span>  
 <span data-ttu-id="d22d8-133">Jeśli na komputerze zainstalowano poprzednie wersje programu WCF, podczas `FileLoadFoundException` uruchamiania narzędzia ServiceModelReg w celu zarejestrowania nowej instalacji może wystąpić błąd.</span><span class="sxs-lookup"><span data-stu-id="d22d8-133">If you installed previous versions of WCF on your machine, you may get a `FileLoadFoundException` error when you run the ServiceModelReg tool to register a new installation.</span></span> <span data-ttu-id="d22d8-134">Może się tak zdarzyć nawet w przypadku ręcznego usuwania plików z poprzedniej instalacji, ale pozostawione ustawienia machine.config pozostają nienaruszone.</span><span class="sxs-lookup"><span data-stu-id="d22d8-134">This can happen even if you have manually removed files from the previous install, but left the machine.config settings intact.</span></span>  
  
 <span data-ttu-id="d22d8-135">Komunikat o błędzie jest podobny do poniższego.</span><span class="sxs-lookup"><span data-stu-id="d22d8-135">The error message is similar to the following.</span></span>  
  
```console  
Error: System.IO.FileLoadException: Could not load file or assembly 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies. The located assembly's manifest definition does not match the assembly reference. (Exception from HRESULT: 0x80131040)  
File name: 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'  
```  
  
 <span data-ttu-id="d22d8-136">Należy zwrócić uwagę na komunikat o błędzie informujący o tym, że zestaw 2.0.0.0 w wersji System. ServiceModel został zainstalowany przez wczesną wersję zapoznawczą klienta (CTP).</span><span class="sxs-lookup"><span data-stu-id="d22d8-136">You should note from the error message that the System.ServiceModel Version 2.0.0.0 assembly was installed by an early Customer Technology Preview (CTP) release.</span></span> <span data-ttu-id="d22d8-137">Bieżąca wersja zestawu System. ServiceModel wydano 3.0.0.0.</span><span class="sxs-lookup"><span data-stu-id="d22d8-137">The current version of the System.ServiceModel assembly released is 3.0.0.0 instead.</span></span> <span data-ttu-id="d22d8-138">W związku z tym ten problem występuje, gdy chcesz zainstalować oficjalną wersję programu WCF na komputerze, na którym zainstalowano wczesną wersję CTP programu WCF, ale nie została ona całkowicie odinstalowana.</span><span class="sxs-lookup"><span data-stu-id="d22d8-138">Therefore, this issue is encountered when you want to install the official WCF release on a machine where an early CTP release of WCF was installed, but not completely uninstalled.</span></span>  
  
 <span data-ttu-id="d22d8-139">ServiceModelReg.exe nie może oczyścić wcześniejszych wpisów wersji ani zarejestrować wpisów nowej wersji.</span><span class="sxs-lookup"><span data-stu-id="d22d8-139">ServiceModelReg.exe cannot clean up prior version entries, nor can it register the new version's entries.</span></span> <span data-ttu-id="d22d8-140">Jedyną obejściem jest ręczne edytowanie machine.config. Ten plik można zlokalizować w następującej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="d22d8-140">The only workaround is to manually edit machine.config. You can locate this file at the following location.</span></span>  
  
```console  
%windir%\Microsoft.NET\Framework\v2.0.50727\config\machine.config
```  
  
 <span data-ttu-id="d22d8-141">Jeśli używasz programu WCF na komputerze 64-bitowym, należy również edytować ten sam plik w tej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="d22d8-141">If you are running WCF on a 64-bit machine, you should also edit the same file at this location.</span></span>  
  
```console  
%windir%\Microsoft.NET\Framework64\v2.0.50727\config\machine.config
```  
  
 <span data-ttu-id="d22d8-142">Zlokalizuj wszystkie węzły XML w tym pliku, które odwołują się do "System. ServiceModel, Version = 2.0.0.0", usuń je i wszystkie węzły podrzędne.</span><span class="sxs-lookup"><span data-stu-id="d22d8-142">Locate any XML nodes in this file that refer to "System.ServiceModel, Version=2.0.0.0", delete them and any child nodes.</span></span> <span data-ttu-id="d22d8-143">Zapisz plik i ponownie uruchom ServiceModelReg.exe rozwiązuje ten problem.</span><span class="sxs-lookup"><span data-stu-id="d22d8-143">Save the file and re-run ServiceModelReg.exe resolves this problem.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="d22d8-144">Przykłady</span><span class="sxs-lookup"><span data-stu-id="d22d8-144">Examples</span></span>  
 <span data-ttu-id="d22d8-145">W poniższych przykładach pokazano, jak używać najbardziej typowych opcji narzędzia ServiceModelReg.exe.</span><span class="sxs-lookup"><span data-stu-id="d22d8-145">The following examples show how to use the most common options of the ServiceModelReg.exe tool.</span></span>  
  
```console  
ServiceModelReg.exe -ia  
  Installs all components  
ServiceModelReg.exe -i -c:httpnamespace -c:etw  
  Installs HTTP namespace reservation and ETW manifests  
ServiceModelReg.exe -u -c:etw  
  Uninstalls ETW manifests  
ServiceModelReg.exe -r  
  Repairs an extended install  
```
