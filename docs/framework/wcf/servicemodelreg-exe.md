---
title: Narzędzie rejestracji modelu ServiceModel (ServiceModelReg.exe)
ms.date: 03/30/2017
ms.assetid: 396ec5ae-e34f-4c64-a164-fcf50e86b6ac
ms.openlocfilehash: 519f303507ed873266cc05a7556073887b66ba6f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923028"
---
# <a name="servicemodel-registration-tool-servicemodelregexe"></a><span data-ttu-id="e409f-102">Narzędzie rejestracji modelu ServiceModel (ServiceModelReg.exe)</span><span class="sxs-lookup"><span data-stu-id="e409f-102">ServiceModel Registration Tool (ServiceModelReg.exe)</span></span>
<span data-ttu-id="e409f-103">To narzędzie wiersza polecenia zapewnia możliwość zarządzania rejestracją składników WCF i WF na jednym komputerze.</span><span class="sxs-lookup"><span data-stu-id="e409f-103">This command-line tool provides the ability to manage the registration of WCF and WF components on a single machine.</span></span> <span data-ttu-id="e409f-104">W normalnych okolicznościach nie należy używać tego narzędzia, ponieważ składniki WCF i WF są skonfigurowane podczas instalacji.</span><span class="sxs-lookup"><span data-stu-id="e409f-104">Under normal circumstances you should not need to use this tool as WCF and WF components are configured when installed.</span></span> <span data-ttu-id="e409f-105">Jeśli jednak występują problemy z aktywacją usługi, możesz spróbować zarejestrować składniki przy użyciu tego narzędzia.</span><span class="sxs-lookup"><span data-stu-id="e409f-105">But if you are experiencing problems with service activation, you can try to register the components using this tool.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e409f-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="e409f-106">Syntax</span></span>  
  
```  
ServiceModelReg.exe[(-ia|-ua|-r)|((-i|-u) -c:<command>)] [-v|-q] [-nologo] [-?]  
```  
  
## <a name="remarks"></a><span data-ttu-id="e409f-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e409f-107">Remarks</span></span>  
 <span data-ttu-id="e409f-108">Narzędzie można znaleźć w następującej lokalizacji:</span><span class="sxs-lookup"><span data-stu-id="e409f-108">The tool can be found in the following location:</span></span>  
  
 <span data-ttu-id="e409f-109">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="e409f-109">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation</span></span>\  
  
> [!NOTE]
> <span data-ttu-id="e409f-110">Po uruchomieniu narzędzia rejestracji [!INCLUDE[wv](../../../includes/wv-md.md)]ServiceModel w systemie okno dialogowe **funkcji systemu Windows** może nie odzwierciedlać, że opcja **Windows Communication Foundation Aktywacja HTTP** w obszarze **Microsoft .NET Framework 3,0** jest włączona.</span><span class="sxs-lookup"><span data-stu-id="e409f-110">When the ServiceModel Registration Tool is run on [!INCLUDE[wv](../../../includes/wv-md.md)], the **Windows Features** dialog may not reflect that the **Windows Communication Foundation HTTP Activation** option under **Microsoft .NET Framework 3.0** is turned on.</span></span> <span data-ttu-id="e409f-111">Do okna dialogowego **funkcje systemu Windows** można uzyskać dostęp przez kliknięcie przycisku **Start**, a następnie kliknij pozycję **Uruchom** , a następnie wpisz **OptionalFeatures**.</span><span class="sxs-lookup"><span data-stu-id="e409f-111">The **Windows Features** dialog can be accessed by clicking **Start**, then click **Run** and then typing **OptionalFeatures**.</span></span>  
  
 <span data-ttu-id="e409f-112">W poniższych tabelach opisano opcje, których można użyć w programie ServiceModelReg. exe.</span><span class="sxs-lookup"><span data-stu-id="e409f-112">The following tables describe the options that can be used with ServiceModelReg.exe.</span></span>  
  
|<span data-ttu-id="e409f-113">Opcja</span><span class="sxs-lookup"><span data-stu-id="e409f-113">Option</span></span>|<span data-ttu-id="e409f-114">Opis</span><span class="sxs-lookup"><span data-stu-id="e409f-114">Description</span></span>|  
|------------|-----------------|  
|`-ia`|<span data-ttu-id="e409f-115">Instaluje wszystkie składniki WCF i WF.</span><span class="sxs-lookup"><span data-stu-id="e409f-115">Installs all WCF and WF components.</span></span>|  
|`-ua`|<span data-ttu-id="e409f-116">Odinstalowuje wszystkie składniki WCF i WF.</span><span class="sxs-lookup"><span data-stu-id="e409f-116">Uninstalls all WCF and WF components.</span></span>|  
|`-r`|<span data-ttu-id="e409f-117">Naprawia wszystkie składniki WCF i WF.</span><span class="sxs-lookup"><span data-stu-id="e409f-117">Repairs all WCF and WF components.</span></span>|  
|`-i`|<span data-ttu-id="e409f-118">Instaluje składniki WCF i WF określone za pomocą parametru-c.</span><span class="sxs-lookup"><span data-stu-id="e409f-118">Installs WCF and WF components specified with –c.</span></span>|  
|`-u`|<span data-ttu-id="e409f-119">Odinstalowuje składniki WCF i WF określone za pomocą parametru-c.</span><span class="sxs-lookup"><span data-stu-id="e409f-119">Uninstalls WCF and WF components specified with –c.</span></span>|  
|`-c`|<span data-ttu-id="e409f-120">Instaluje lub Odinstalowuje składnik:</span><span class="sxs-lookup"><span data-stu-id="e409f-120">Installs or uninstalls a component:</span></span><br /><br /> <span data-ttu-id="e409f-121">-httpnamespace — rezerwacja przestrzeni nazw protokołu HTTP</span><span class="sxs-lookup"><span data-stu-id="e409f-121">-   httpnamespace – HTTP Namespace Reservation</span></span><br /><span data-ttu-id="e409f-122">-tcpportsharing — usługa udostępniania portów TCP</span><span class="sxs-lookup"><span data-stu-id="e409f-122">-   tcpportsharing – TCP port sharing service</span></span><br /><span data-ttu-id="e409f-123">-tcpactivation — usługa aktywacji TCP (nieobsługiwana w profilu klienta .NET 4)</span><span class="sxs-lookup"><span data-stu-id="e409f-123">-   tcpactivation – TCP activation service (unsupported on .NET 4 Client Profile)</span></span><br /><span data-ttu-id="e409f-124">-namedpipeactivation — usługa aktywacji potoków nazwanych (nieobsługiwana w profilu klienta .NET 4</span><span class="sxs-lookup"><span data-stu-id="e409f-124">-   namedpipeactivation – Named pipe activation service (unsupported on .NET 4 Client Profile</span></span><br /><span data-ttu-id="e409f-125">-Usługa MsmqActivation — usługa aktywacji usługi MSMQ (nieobsługiwana w profilu klienta .NET 4</span><span class="sxs-lookup"><span data-stu-id="e409f-125">-   msmqactivation – MSMQ activation service (unsupported on .NET 4 Client Profile</span></span><br /><span data-ttu-id="e409f-126">-ETW — manifesty śledzenia zdarzeń ETW (system Windows Vista lub nowszy)</span><span class="sxs-lookup"><span data-stu-id="e409f-126">-   etw – ETW event tracing manifests (Windows Vista or later)</span></span>|  
|`-q`|<span data-ttu-id="e409f-127">Tryb cichy (wyświetla tylko rejestrowanie błędów)</span><span class="sxs-lookup"><span data-stu-id="e409f-127">Quiet mode (only display error logging)</span></span>|  
|`-v`|<span data-ttu-id="e409f-128">Tryb informacji pełnej.</span><span class="sxs-lookup"><span data-stu-id="e409f-128">Verbose mode.</span></span>|  
|`-nologo`|<span data-ttu-id="e409f-129">Pomija informacje o prawach autorskich i baneru.</span><span class="sxs-lookup"><span data-stu-id="e409f-129">Suppresses the copyright and banner message.</span></span>|  
|`-?`|<span data-ttu-id="e409f-130">Wyświetla tekst pomocy</span><span class="sxs-lookup"><span data-stu-id="e409f-130">Displays help text</span></span>|  
  
## <a name="fixing-the-fileloadexception-error"></a><span data-ttu-id="e409f-131">Naprawianie błędu FileLoadException</span><span class="sxs-lookup"><span data-stu-id="e409f-131">Fixing the FileLoadException Error</span></span>  
 <span data-ttu-id="e409f-132">Jeśli na komputerze zainstalowano poprzednie wersje programu WCF, podczas uruchamiania narzędzia ServiceModelReg `FileLoadFoundException` w celu zarejestrowania nowej instalacji może wystąpić błąd.</span><span class="sxs-lookup"><span data-stu-id="e409f-132">If you installed previous versions of WCF on your machine, you may get a `FileLoadFoundException` error when you run the ServiceModelReg tool to register a new installation.</span></span> <span data-ttu-id="e409f-133">Może się tak zdarzyć nawet w przypadku ręcznego usuwania plików z poprzedniej instalacji, ale pozostawionie ustawień Machine. config bez zmian.</span><span class="sxs-lookup"><span data-stu-id="e409f-133">This can happen even if you have manually removed files from the previous install, but left the machine.config settings intact.</span></span>  
  
 <span data-ttu-id="e409f-134">Komunikat o błędzie jest podobny do poniższego.</span><span class="sxs-lookup"><span data-stu-id="e409f-134">The error message is similar to the following.</span></span>  
  
```  
Error: System.IO.FileLoadException: Could not load file or assembly 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies. The located assembly's manifest definition does not match the assembly reference. (Exception from HRESULT: 0x80131040)  
File name: 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'  
```  
  
 <span data-ttu-id="e409f-135">Należy zwrócić uwagę na komunikat o błędzie informujący o tym, że zestaw 2.0.0.0 w wersji System. ServiceModel został zainstalowany przez wczesną wersję zapoznawczą klienta (CTP).</span><span class="sxs-lookup"><span data-stu-id="e409f-135">You should note from the error message that the System.ServiceModel Version 2.0.0.0 assembly was installed by an early Customer Technology Preview (CTP) release.</span></span> <span data-ttu-id="e409f-136">Bieżąca wersja zestawu System. ServiceModel wydano 3.0.0.0.</span><span class="sxs-lookup"><span data-stu-id="e409f-136">The current version of the System.ServiceModel assembly released is 3.0.0.0 instead.</span></span> <span data-ttu-id="e409f-137">W związku z tym ten problem występuje, gdy chcesz zainstalować oficjalną wersję programu WCF na komputerze, na którym zainstalowano wczesną wersję CTP programu WCF, ale nie została ona całkowicie odinstalowana.</span><span class="sxs-lookup"><span data-stu-id="e409f-137">Therefore, this issue is encountered when you want to install the official WCF release on a machine where an early CTP release of WCF was installed, but not completely uninstalled.</span></span>  
  
 <span data-ttu-id="e409f-138">ServiceModelReg. exe nie może oczyścić wcześniejszych wpisów wersji ani nie może zarejestrować wpisów nowej wersji.</span><span class="sxs-lookup"><span data-stu-id="e409f-138">ServiceModelReg.exe cannot clean up prior version entries, nor can it register the new version's entries.</span></span> <span data-ttu-id="e409f-139">Jedyną obejściem jest ręczne edytowanie pliku Machine. config. Ten plik można zlokalizować w następującej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="e409f-139">The only workaround is to manually edit machine.config. You can locate this file at the following location.</span></span>  
  
```  
%windir%\Microsoft.NET\Framework\v2.0.50727\config\machine.config   
```  
  
 <span data-ttu-id="e409f-140">Jeśli używasz programu WCF na komputerze 64-bitowym, należy również edytować ten sam plik w tej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="e409f-140">If you are running WCF on a 64-bit machine, you should also edit the same file at this location.</span></span>  
  
```  
%windir%\Microsoft.NET\Framework64\v2.0.50727\config\machine.config   
```  
  
 <span data-ttu-id="e409f-141">Zlokalizuj wszystkie węzły XML w tym pliku, które odwołują się do "System. ServiceModel, Version = 2.0.0.0", usuń je i wszystkie węzły podrzędne.</span><span class="sxs-lookup"><span data-stu-id="e409f-141">Locate any XML nodes in this file that refer to "System.ServiceModel, Version=2.0.0.0", delete them and any child nodes.</span></span> <span data-ttu-id="e409f-142">Zapisz plik i ponownie uruchom ServiceModelReg. exe rozwiązuje ten problem.</span><span class="sxs-lookup"><span data-stu-id="e409f-142">Save the file and re-run ServiceModelReg.exe resolves this problem.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="e409f-143">Przykłady</span><span class="sxs-lookup"><span data-stu-id="e409f-143">Examples</span></span>  
 <span data-ttu-id="e409f-144">W poniższych przykładach pokazano, jak używać najbardziej typowych opcji narzędzia ServiceModelReg. exe.</span><span class="sxs-lookup"><span data-stu-id="e409f-144">The following examples show how to use the most common options of the ServiceModelReg.exe tool.</span></span>  
  
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
