---
title: Narzędzie rejestracji modelu ServiceModel (ServiceModelReg.exe)
ms.date: 03/30/2017
ms.assetid: 396ec5ae-e34f-4c64-a164-fcf50e86b6ac
ms.openlocfilehash: a6f65ccc6caa0a7e496e7de8c83259ab48903753
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183109"
---
# <a name="servicemodel-registration-tool-servicemodelregexe"></a><span data-ttu-id="fdcfc-102">Narzędzie rejestracji modelu ServiceModel (ServiceModelReg.exe)</span><span class="sxs-lookup"><span data-stu-id="fdcfc-102">ServiceModel Registration Tool (ServiceModelReg.exe)</span></span>
<span data-ttu-id="fdcfc-103">To narzędzie wiersza polecenia umożliwia zarządzanie rejestracją składników WCF i WF na jednym komputerze.</span><span class="sxs-lookup"><span data-stu-id="fdcfc-103">This command-line tool provides the ability to manage the registration of WCF and WF components on a single machine.</span></span> <span data-ttu-id="fdcfc-104">W normalnych warunkach nie należy używać tego narzędzia, ponieważ składniki WCF i WF są konfigurowane po zainstalowaniu.</span><span class="sxs-lookup"><span data-stu-id="fdcfc-104">Under normal circumstances you should not need to use this tool as WCF and WF components are configured when installed.</span></span> <span data-ttu-id="fdcfc-105">Ale jeśli występują problemy z aktywacją usługi, możesz spróbować zarejestrować składniki za pomocą tego narzędzia.</span><span class="sxs-lookup"><span data-stu-id="fdcfc-105">But if you are experiencing problems with service activation, you can try to register the components using this tool.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fdcfc-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="fdcfc-106">Syntax</span></span>  
  
```console  
ServiceModelReg.exe[(-ia|-ua|-r)|((-i|-u) -c:<command>)] [-v|-q] [-nologo] [-?]  
```  
  
## <a name="remarks"></a><span data-ttu-id="fdcfc-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fdcfc-107">Remarks</span></span>  
 <span data-ttu-id="fdcfc-108">Narzędzie można znaleźć w następującej lokalizacji:</span><span class="sxs-lookup"><span data-stu-id="fdcfc-108">The tool can be found in the following location:</span></span>  
  
 <span data-ttu-id="fdcfc-109">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="fdcfc-109">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation</span></span>\  
  
> [!NOTE]
> <span data-ttu-id="fdcfc-110">Po uruchomieniu narzędzia rejestracji ServiceModel w systemie Windows Vista okno dialogowe **Funkcje systemu Windows** może nie odzwierciedlać włączenia opcji **Aktywacja HTTP programu Windows Communication Foundation** w obszarze Microsoft **.NET Framework 3.0.**</span><span class="sxs-lookup"><span data-stu-id="fdcfc-110">When the ServiceModel Registration Tool is run on Windows Vista, the **Windows Features** dialog may not reflect that the **Windows Communication Foundation HTTP Activation** option under **Microsoft .NET Framework 3.0** is turned on.</span></span> <span data-ttu-id="fdcfc-111">Dostęp do okna dialogowego **Funkcje systemu Windows** można uzyskać, klikając przycisk **Start**, a następnie kliknij przycisk **Uruchom,** a następnie wpisując **polecenie Opcjonalne elementy .**</span><span class="sxs-lookup"><span data-stu-id="fdcfc-111">The **Windows Features** dialog can be accessed by clicking **Start**, then click **Run** and then typing **OptionalFeatures**.</span></span>  
  
 <span data-ttu-id="fdcfc-112">W poniższych tabelach opisano opcje, których można używać z programem ServiceModelReg.exe.</span><span class="sxs-lookup"><span data-stu-id="fdcfc-112">The following tables describe the options that can be used with ServiceModelReg.exe.</span></span>  
  
|<span data-ttu-id="fdcfc-113">Opcja</span><span class="sxs-lookup"><span data-stu-id="fdcfc-113">Option</span></span>|<span data-ttu-id="fdcfc-114">Opis</span><span class="sxs-lookup"><span data-stu-id="fdcfc-114">Description</span></span>|  
|------------|-----------------|  
|`-ia`|<span data-ttu-id="fdcfc-115">Instaluje wszystkie składniki WCF i WF.</span><span class="sxs-lookup"><span data-stu-id="fdcfc-115">Installs all WCF and WF components.</span></span>|  
|`-ua`|<span data-ttu-id="fdcfc-116">Odinstalowuje wszystkie składniki WCF i WF.</span><span class="sxs-lookup"><span data-stu-id="fdcfc-116">Uninstalls all WCF and WF components.</span></span>|  
|`-r`|<span data-ttu-id="fdcfc-117">Naprawia wszystkie komponenty WCF i WF.</span><span class="sxs-lookup"><span data-stu-id="fdcfc-117">Repairs all WCF and WF components.</span></span>|  
|`-i`|<span data-ttu-id="fdcfc-118">Instaluje składniki WCF i WF określone za pomocą –c.</span><span class="sxs-lookup"><span data-stu-id="fdcfc-118">Installs WCF and WF components specified with –c.</span></span>|  
|`-u`|<span data-ttu-id="fdcfc-119">Odinstalowuje składniki WCF i WF określone za pomocą –c.</span><span class="sxs-lookup"><span data-stu-id="fdcfc-119">Uninstalls WCF and WF components specified with –c.</span></span>|  
|`-c`|<span data-ttu-id="fdcfc-120">Instaluje lub odinstalowuje składnik:</span><span class="sxs-lookup"><span data-stu-id="fdcfc-120">Installs or uninstalls a component:</span></span><br /><br /> <span data-ttu-id="fdcfc-121">- httpnamespace - REZERWACJA OBSZARU NAZW HTTP</span><span class="sxs-lookup"><span data-stu-id="fdcfc-121">-   httpnamespace – HTTP Namespace Reservation</span></span><br /><span data-ttu-id="fdcfc-122">- tcpportsharing – usługa udostępniania portów TCP</span><span class="sxs-lookup"><span data-stu-id="fdcfc-122">-   tcpportsharing – TCP port sharing service</span></span><br /><span data-ttu-id="fdcfc-123">- tcpactivation – usługa aktywacji TCP (nieobsługiwała w profilu klienta .NET 4)</span><span class="sxs-lookup"><span data-stu-id="fdcfc-123">-   tcpactivation – TCP activation service (unsupported on .NET 4 Client Profile)</span></span><br /><span data-ttu-id="fdcfc-124">- namedpipeactivation - Nazwana usługa aktywacji potoku (nieobsługiwała w profilu klienta .NET 4</span><span class="sxs-lookup"><span data-stu-id="fdcfc-124">-   namedpipeactivation – Named pipe activation service (unsupported on .NET 4 Client Profile</span></span><br /><span data-ttu-id="fdcfc-125">- msmqactivation – usługa aktywacji USŁUGI MSMQ (nieobsługiwany w profilu klienta .NET 4</span><span class="sxs-lookup"><span data-stu-id="fdcfc-125">-   msmqactivation – MSMQ activation service (unsupported on .NET 4 Client Profile</span></span><br /><span data-ttu-id="fdcfc-126">- etw - manifesty śledzenia zdarzeń ETW (Windows Vista lub nowsze)</span><span class="sxs-lookup"><span data-stu-id="fdcfc-126">-   etw – ETW event tracing manifests (Windows Vista or later)</span></span>|  
|`-q`|<span data-ttu-id="fdcfc-127">Tryb cichy (tylko rejestrowanie błędów wyświetlania)</span><span class="sxs-lookup"><span data-stu-id="fdcfc-127">Quiet mode (only display error logging)</span></span>|  
|`-v`|<span data-ttu-id="fdcfc-128">Tryb informacji pełnej.</span><span class="sxs-lookup"><span data-stu-id="fdcfc-128">Verbose mode.</span></span>|  
|`-nologo`|<span data-ttu-id="fdcfc-129">Pomija przesłanie praw autorskich i banerów.</span><span class="sxs-lookup"><span data-stu-id="fdcfc-129">Suppresses the copyright and banner message.</span></span>|  
|`-?`|<span data-ttu-id="fdcfc-130">Wyświetla tekst pomocy</span><span class="sxs-lookup"><span data-stu-id="fdcfc-130">Displays help text</span></span>|  
  
## <a name="fixing-the-fileloadexception-error"></a><span data-ttu-id="fdcfc-131">Naprawianie błędu FileLoadException</span><span class="sxs-lookup"><span data-stu-id="fdcfc-131">Fixing the FileLoadException Error</span></span>  
 <span data-ttu-id="fdcfc-132">Jeśli zainstalowano poprzednie wersje WCF na komputerze, `FileLoadFoundException` może pojawić się błąd po uruchomieniu servicemodelreg narzędzie do zarejestrowania nowej instalacji.</span><span class="sxs-lookup"><span data-stu-id="fdcfc-132">If you installed previous versions of WCF on your machine, you may get a `FileLoadFoundException` error when you run the ServiceModelReg tool to register a new installation.</span></span> <span data-ttu-id="fdcfc-133">Może się tak zdarzyć, nawet jeśli ręcznie usunięto pliki z poprzedniej instalacji, ale ustawienia machine.config pozostały nienaruszone.</span><span class="sxs-lookup"><span data-stu-id="fdcfc-133">This can happen even if you have manually removed files from the previous install, but left the machine.config settings intact.</span></span>  
  
 <span data-ttu-id="fdcfc-134">Komunikat o błędzie jest podobny do następującego.</span><span class="sxs-lookup"><span data-stu-id="fdcfc-134">The error message is similar to the following.</span></span>  
  
```console  
Error: System.IO.FileLoadException: Could not load file or assembly 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies. The located assembly's manifest definition does not match the assembly reference. (Exception from HRESULT: 0x80131040)  
File name: 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'  
```  
  
 <span data-ttu-id="fdcfc-135">Z komunikatu o błędzie należy zauważyć, że zestaw System.ServiceModel w wersji 2.0.0.0 został zainstalowany przez wczesną wersję programu Customer Technology Preview (CTP).</span><span class="sxs-lookup"><span data-stu-id="fdcfc-135">You should note from the error message that the System.ServiceModel Version 2.0.0.0 assembly was installed by an early Customer Technology Preview (CTP) release.</span></span> <span data-ttu-id="fdcfc-136">Bieżąca wersja zestawu System.ServiceModel zwolniony jest 3.0.0.0 zamiast.</span><span class="sxs-lookup"><span data-stu-id="fdcfc-136">The current version of the System.ServiceModel assembly released is 3.0.0.0 instead.</span></span> <span data-ttu-id="fdcfc-137">W związku z tym ten problem występuje, gdy chcesz zainstalować oficjalne wydanie WCF na komputerze, na którym zainstalowano wczesną wersję CTP WCF, ale nie całkowicie odinstalowano.</span><span class="sxs-lookup"><span data-stu-id="fdcfc-137">Therefore, this issue is encountered when you want to install the official WCF release on a machine where an early CTP release of WCF was installed, but not completely uninstalled.</span></span>  
  
 <span data-ttu-id="fdcfc-138">Program ServiceModelReg.exe nie może wyczyścić wcześniejszych wpisów wersji ani rejestrować wpisów nowej wersji.</span><span class="sxs-lookup"><span data-stu-id="fdcfc-138">ServiceModelReg.exe cannot clean up prior version entries, nor can it register the new version's entries.</span></span> <span data-ttu-id="fdcfc-139">Jedynym obejściem jest ręczna edycja pliku machine.config. Możesz zlokalizować ten plik w następującej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="fdcfc-139">The only workaround is to manually edit machine.config. You can locate this file at the following location.</span></span>  
  
```console  
%windir%\Microsoft.NET\Framework\v2.0.50727\config\machine.config
```  
  
 <span data-ttu-id="fdcfc-140">Jeśli korzystasz z WCF na komputerze 64-bitowym, należy również edytować ten sam plik w tej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="fdcfc-140">If you are running WCF on a 64-bit machine, you should also edit the same file at this location.</span></span>  
  
```console  
%windir%\Microsoft.NET\Framework64\v2.0.50727\config\machine.config
```  
  
 <span data-ttu-id="fdcfc-141">Znajdź wszystkie węzły XML w tym pliku, które odwołują się do "System.ServiceModel, Version=2.0.0.0", usuń je i wszystkie węzły podrzędne.</span><span class="sxs-lookup"><span data-stu-id="fdcfc-141">Locate any XML nodes in this file that refer to "System.ServiceModel, Version=2.0.0.0", delete them and any child nodes.</span></span> <span data-ttu-id="fdcfc-142">Zapisz plik i ponownie uruchom program ServiceModelReg.exe rozwiązuje ten problem.</span><span class="sxs-lookup"><span data-stu-id="fdcfc-142">Save the file and re-run ServiceModelReg.exe resolves this problem.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="fdcfc-143">Przykłady</span><span class="sxs-lookup"><span data-stu-id="fdcfc-143">Examples</span></span>  
 <span data-ttu-id="fdcfc-144">Poniższe przykłady pokazują, jak korzystać z najczęstszych opcji narzędzia ServiceModelReg.exe.</span><span class="sxs-lookup"><span data-stu-id="fdcfc-144">The following examples show how to use the most common options of the ServiceModelReg.exe tool.</span></span>  
  
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
