---
title: 'Porady: debugowanie problemów aktywacji środowiska CLR'
ms.date: 03/30/2017
helpviewer_keywords:
- CLR activation, debugging issues
ms.assetid: 4fe17546-d56e-4344-a930-6d8e4a545914
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 89724e9a322f2f28dbe5d18ae697acbdd0a32d8e
ms.sourcegitcommit: 5fd80619c760fa8c25d33a6f5661247cb65da465
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2018
ms.locfileid: "50744473"
---
# <a name="how-to-debug-clr-activation-issues"></a><span data-ttu-id="b419e-102">Porady: debugowanie problemów aktywacji środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="b419e-102">How to: Debug CLR Activation Issues</span></span>
<span data-ttu-id="b419e-103">Jeśli wystąpią problemy podczas uzyskiwania aplikację do uruchamiania w odpowiedniej wersji środowiska uruchomieniowego języka wspólnego (CLR), można wyświetlać i debugowania dzienniki aktywacji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="b419e-103">If you encounter problems in getting your application to run with the correct version of the common language runtime (CLR), you can view and debug CLR activation logs.</span></span> <span data-ttu-id="b419e-104">Te dzienniki może być bardzo przydatne podczas ustalania głównej przyczyny problemu aktywacji, kiedy aplikacja różnych wersji środowiska CLR ładuje, niż oczekiwano lub w ogóle nie jest ładowana środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="b419e-104">These logs can be very useful in determining the root cause of an activation issue, when your application either loads a different CLR version than expected or doesn't load the CLR at all.</span></span> <span data-ttu-id="b419e-105">[Błędy inicjowania programu .NET Framework: Zarządzanie środowiska użytkownika](../../../docs/framework/deployment/initialization-errors-managing-the-user-experience.md) tym artykule omówiono środowisko CLR nie został znaleziony dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b419e-105">The [.NET Framework Initialization Errors: Managing the User Experience](../../../docs/framework/deployment/initialization-errors-managing-the-user-experience.md) discusses the experience when no CLR is found for an application.</span></span>  
  
 <span data-ttu-id="b419e-106">Rejestrowanie aktywacji środowiska CLR może być włączone całego systemu za pomocą klucza rejestru HKEY_LOCAL_MACHINE lub zmienną środowiskową systemu.</span><span class="sxs-lookup"><span data-stu-id="b419e-106">CLR activation logging can be enabled system-wide by using an HKEY_LOCAL_MACHINE registry key or a system environment variable.</span></span> <span data-ttu-id="b419e-107">Dziennik zostanie wygenerowany, aż do wpisu rejestru lub zmiennej środowiskowej zostanie usunięty.</span><span class="sxs-lookup"><span data-stu-id="b419e-107">The log will be generated until the registry entry or the environment variable is removed.</span></span> <span data-ttu-id="b419e-108">Alternatywnie można użyć użytkownika lub zmiennej środowiskowej proces lokalny Aby włączyć rejestrowanie za pomocą innego zakresu i czasu trwania.</span><span class="sxs-lookup"><span data-stu-id="b419e-108">Alternatively, you can use a user or process-local environment variable to enable logging with a different scope and duration.</span></span>  
  
 <span data-ttu-id="b419e-109">Dzienniki aktywacji środowiska CLR, nie należy mylić z [dzienniki powiązań zestawów](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md), które są zupełnie innego.</span><span class="sxs-lookup"><span data-stu-id="b419e-109">CLR activation logs shouldn't be confused with [assembly binding logs](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md), which are entirely different.</span></span>  
  
## <a name="to-enable-clr-activation-logging"></a><span data-ttu-id="b419e-110">Aby włączyć rejestrowanie aktywacji środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="b419e-110">To enable CLR activation logging</span></span>  
  
#### <a name="using-the-registry"></a><span data-ttu-id="b419e-111">Za pomocą rejestru</span><span class="sxs-lookup"><span data-stu-id="b419e-111">Using the registry</span></span>  
  
1.  <span data-ttu-id="b419e-112">W Edytorze rejestru przejdź do HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework (na komputerze 32-bitowa) lub HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\. Folder NETFramework (na komputerze 64-bitowych).</span><span class="sxs-lookup"><span data-stu-id="b419e-112">In the Registry Editor, navigate to HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework (on a 32-bit computer) or HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework folder (on a 64-bit computer).</span></span>  
  
2.  <span data-ttu-id="b419e-113">Dodaj wartość ciągu o nazwie `CLRLoadLogDir`i ustaw ją na pełną ścieżkę istniejącego katalogu, w którym chcesz przechowywać dzienniki aktywacji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="b419e-113">Add a string value named `CLRLoadLogDir`, and set it to the full path of an existing directory where you'd like to store CLR activation logs.</span></span>  
  
 <span data-ttu-id="b419e-114">Aktywacja rejestrowania pozostanie włączona, dopóki nie usuniesz wartość ciągu.</span><span class="sxs-lookup"><span data-stu-id="b419e-114">Activation logging remains enabled until you remove the string value.</span></span>  
  
#### <a name="using-an-environment-variable"></a><span data-ttu-id="b419e-115">Za pomocą zmiennej środowiskowej</span><span class="sxs-lookup"><span data-stu-id="b419e-115">Using an environment variable</span></span>  
  
-   <span data-ttu-id="b419e-116">Ustaw `COMPLUS_CLRLoadLogDir` zmienną środowiskową na ciąg, który reprezentuje pełną ścieżkę istniejącego katalogu, w którym chcesz przechowywać dzienniki aktywacji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="b419e-116">Set the `COMPLUS_CLRLoadLogDir` environment variable to a string that represents the full path of an existing directory where you'd like to store CLR activation logs.</span></span>  
  
     <span data-ttu-id="b419e-117">Zakres Określa, jak ustawić zmienną środowiskową:</span><span class="sxs-lookup"><span data-stu-id="b419e-117">How you set the environment variable determines its scope:</span></span>  
  
    -   <span data-ttu-id="b419e-118">Jeśli zostanie ustawiona na poziomie systemu, aktywacji rejestrowanie jest włączone dla wszystkich aplikacji .NET Framework na tym komputerze, do momentu usunięcia zmiennej środowiskowej.</span><span class="sxs-lookup"><span data-stu-id="b419e-118">If you set it at the system level, activation logging is enabled for all .NET Framework applications on that computer until the environment variable is removed.</span></span>  
  
    -   <span data-ttu-id="b419e-119">Jeśli zostanie ustawiona na poziomie użytkownika, aktywacji rejestrowanie jest włączone tylko dla bieżącego konta użytkownika.</span><span class="sxs-lookup"><span data-stu-id="b419e-119">If you set it at the user level, activation logging is enabled only for the current user account.</span></span> <span data-ttu-id="b419e-120">Rejestrowanie jest kontynuowany do momentu usunięcia zmiennej środowiskowej.</span><span class="sxs-lookup"><span data-stu-id="b419e-120">Logging continues until the environment variable is removed.</span></span>  
  
    -   <span data-ttu-id="b419e-121">Jeśli ustawisz go w ramach procesu przed załadowaniem środowiska CLR, aktywacji rejestrowanie jest włączone, aż do zakończenia procesu.</span><span class="sxs-lookup"><span data-stu-id="b419e-121">If you set it from within the process before loading the CLR, activation logging is enabled until the process terminates.</span></span>  
  
    -   <span data-ttu-id="b419e-122">Jeśli zostanie ustawiona w wierszu polecenia przed uruchomieniem aplikacji, rejestrowanie aktywacji jest włączone dla każdej aplikacji, uruchamianą w tym wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="b419e-122">If you set it at a command prompt before you run an application, activation logging is enabled for any application that is run from that command prompt.</span></span>  
  
     <span data-ttu-id="b419e-123">Na przykład do przechowywania dzienników aktywacji w katalogu c:\clrloadlogs zakresie na poziomie procesu, Otwórz okno wiersza polecenia i wpisz następujące polecenie przed uruchomieniem aplikacji:</span><span class="sxs-lookup"><span data-stu-id="b419e-123">For example, to store activation logs in the c:\clrloadlogs directory with process-level scope, open a Command Prompt window and type the following before you run the application:</span></span>  
  
    ```  
    set COMPLUS_CLRLoadLogDir=c:\clrloadlogs  
    ```  
  
## <a name="example"></a><span data-ttu-id="b419e-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="b419e-124">Example</span></span>  
 <span data-ttu-id="b419e-125">Dzienniki aktywacji środowiska CLR zapewniają dużą ilość danych o aktywacji środowiska CLR i używania środowiska CLR hostowania interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="b419e-125">CLR activation logs provide a large amount of data about CLR activation and the use of the CLR hosting APIs.</span></span> <span data-ttu-id="b419e-126">Większość z tych danych jest używana wewnętrznie przez firmę Microsoft, ale niektóre dane również może być przydatny dla deweloperów, zgodnie z opisem w tym artykule.</span><span class="sxs-lookup"><span data-stu-id="b419e-126">Most of this data is used internally by Microsoft, but some of the data can also be useful to developers, as described in this article.</span></span>  
  
 <span data-ttu-id="b419e-127">Dziennik odzwierciedla kolejność, w której CLR hostowania interfejsów API zostały wywołane.</span><span class="sxs-lookup"><span data-stu-id="b419e-127">The log reflects the order in which the CLR hosting APIs were called.</span></span> <span data-ttu-id="b419e-128">Zawiera on również użyteczne dane na temat zestawu zainstalowanego środowiska uruchomieniowe wykryty na komputerze.</span><span class="sxs-lookup"><span data-stu-id="b419e-128">It also includes useful data about the set of installed runtimes detected on the computer.</span></span> <span data-ttu-id="b419e-129">Format dziennika aktywacji środowiska CLR nie jest sam udokumentowane, ale może służyć do pomóc deweloperom, którzy muszą zostać rozwiązane problemów aktywacji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="b419e-129">The CLR activation log format is not itself documented, but can be used to aid developers who need to resolve CLR activation issues.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b419e-130">Nie można otworzyć dziennika aktywacji, dopóki nie zakończył procesu, który używa środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="b419e-130">You cannot open an activation log until the process that uses the CLR has terminated.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b419e-131">Dzienniki aktywacji środowiska CLR nie są lokalizowane; są one zawsze generowane w języku angielskim.</span><span class="sxs-lookup"><span data-stu-id="b419e-131">CLR activation logs are not localized; they are always generated in the English language.</span></span>  
  
 <span data-ttu-id="b419e-132">W poniższym przykładzie w dzienniku aktywacji najbardziej użyteczne informacje jest wyróżniona i opisem po dziennika.</span><span class="sxs-lookup"><span data-stu-id="b419e-132">In the following example of an activation log, the most useful information is highlighted and described after the log.</span></span>  
  
```  
532,205950.367,CLR Loading log for C:\Tests\myapp.exe   
532,205950.367,Log started at 4:26:12 PM on 10/6/2011   
532,205950.367,-----------------------------------   
532,205950.382,FunctionCall: _CorExeMain   
532,205950.382,FunctionCall: ClrCreateInstance, Clsid: {2EBCD49A-1B47-4A61-B13A-4A03701E594B}, Iid: {E2190695-77B2-492E-8E14-C4B3A7FDD593}   
532,205950.382,MethodCall: ICLRMetaHostPolicy::GetRequestedRuntime. Version: (null), Metahost Policy Flags: 0x168, Binary: (null), Iid: {BD39D1D2-BA2F-486A-89B0-B4B0CB466891}   
532,205950.382,Installed Runtime: v4.0.30319. VERSION_ARCHITECTURE: 0   
532,205950.382,Input values for ComputeVersionString follow this line   
532,205950.382,-----------------------------------   
532,205950.382,Default Application Name: C:\Tests\myapp.exe   
532,205950.382,IsLegacyBind is: 0   
532,205950.382,IsCapped is 0   
532,205950.382,SkuCheckFlags are 0   
532,205950.382,ShouldEmulateExeLaunch is 0   
532,205950.382,LegacyBindRequired is 0   
532,205950.382,-----------------------------------   
532,205950.382,Parsing config file: C:\Tests\myapp.exe   
532,205950.382,UseLegacyV2RuntimeActivationPolicy is set to 0   
532,205950.382,LegacyFunctionCall: GetFileVersion. Filename: C:\Tests\myapp.exe   
532,205950.382,LegacyFunctionCall: GetFileVersion. Filename: C:\Tests\myapp.exe   
532,205950.382,C:\Tests\myapp.exe was built with version: v2.0.50727   
532,205950.382,ERROR: Version v2.0.50727 is not present on the machine.   
532,205950.398,SEM_FAILCRITICALERRORS is set to 0   
532,205950.398,Launching feature-on-demand installation. CmdLine: C:\Windows\system32\fondue.exe /enable-feature:NetFx3   
532,205950.398,FunctionCall: RealDllMain. Reason: 0   
532,205950.398,FunctionCall: OnShimDllMainCalled. Reason: 0  
```  
  
-   <span data-ttu-id="b419e-133">**Dziennik ładowania CLR** zapewnia ścieżkę do pliku wykonywalnego, który uruchomił proces, który załadowany kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="b419e-133">**CLR Loading log** provides the path to the executable that started the process that loaded managed code.</span></span> <span data-ttu-id="b419e-134">Należy pamiętać, że może to być natywne hosta.</span><span class="sxs-lookup"><span data-stu-id="b419e-134">Note that this could be a native host.</span></span>  
  
    ```  
    532,205950.367,CLR Loading log for C:\Tests\myapp.exe  
    ```  
  
-   <span data-ttu-id="b419e-135">**Zainstalowane środowisko uruchomieniowe** to zestaw wersji środowiska CLR zainstalowany na komputerze, które nadają się do żądania aktywacji.</span><span class="sxs-lookup"><span data-stu-id="b419e-135">**Installed Runtime** is the set of CLR versions installed on the computer that are candidates for the activation request.</span></span>  
  
    ```  
    532,205950.382,Installed Runtime: v4.0.30319. VERSION_ARCHITECTURE: 0  
    ```  
  
-   <span data-ttu-id="b419e-136">**utworzonych za pomocą wersji** stanowi wersję środowiska CLR, który został użyty do tworzenia pliku binarnego, który został dostarczony do metody, takie jak [iclrmetahostpolicy::getrequestedruntime —](../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md).</span><span class="sxs-lookup"><span data-stu-id="b419e-136">**built with version** is the version of the CLR that was used to build the binary that was provided to a method such as [ICLRMetaHostPolicy::GetRequestedRuntime](../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md).</span></span>  
  
    ```  
    532,205950.382,C:\Tests\myapp.exe was built with version: v2.0.50727  
    ```  
  
-   <span data-ttu-id="b419e-137">**instalacji funkcji na żądanie** odwołuje się do włączania programu .NET Framework 3.5 w systemie Windows 8.</span><span class="sxs-lookup"><span data-stu-id="b419e-137">**feature-on-demand installation** refers to enabling the .NET Framework 3.5 on Windows 8.</span></span> <span data-ttu-id="b419e-138">Zobacz [błędy inicjowania programu .NET Framework: Zarządzanie wrażeniami użytkownika](../../../docs/framework/deployment/initialization-errors-managing-the-user-experience.md) Aby uzyskać więcej informacji na temat tego scenariusza.</span><span class="sxs-lookup"><span data-stu-id="b419e-138">See [.NET Framework Initialization Errors: Managing the User Experience](../../../docs/framework/deployment/initialization-errors-managing-the-user-experience.md) for more information about this scenario.</span></span>  
  
    ```  
    532,205950.398,Launching feature-on-demand installation. CmdLine: C:\Windows\system32\fondue.exe /enable-feature:NetFx3  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="b419e-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b419e-139">See Also</span></span>  
- [<span data-ttu-id="b419e-140">Wdrażanie</span><span class="sxs-lookup"><span data-stu-id="b419e-140">Deployment</span></span>](../../../docs/framework/deployment/index.md)  
- [<span data-ttu-id="b419e-141">Instrukcje: Konfiguracja aplikacji do obsługi w programie .NET Framework 4 lub 4.5</span><span class="sxs-lookup"><span data-stu-id="b419e-141">How to: Configure an App to Support .NET Framework 4 or 4.5</span></span>](../../../docs/framework/migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
