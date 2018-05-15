---
title: 'Porady: debugowanie problemów aktywacji środowiska CLR'
ms.date: 03/30/2017
helpviewer_keywords:
- CLR activation, debugging issues
ms.assetid: 4fe17546-d56e-4344-a930-6d8e4a545914
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b78d917b95e06a14b74c812bf92107476ad17212
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-debug-clr-activation-issues"></a><span data-ttu-id="87bfb-102">Porady: debugowanie problemów aktywacji środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="87bfb-102">How to: Debug CLR Activation Issues</span></span>
<span data-ttu-id="87bfb-103">Jeśli wystąpią problemy podczas pobierania aplikacji do uruchamiania w odpowiedniej wersji środowisko uruchomieniowe języka wspólnego (CLR), można wyświetlać i debugowania dzienniki aktywacji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="87bfb-103">If you encounter problems in getting your application to run with the correct version of the common language runtime (CLR), you can view and debug CLR activation logs.</span></span> <span data-ttu-id="87bfb-104">Te dzienniki może być bardzo przydatne podczas określania głównej przyczyny problemu aktywacji, gdy aplikacji ładuje inną wersję środowiska CLR, niż oczekiwano lub w ogóle nie jest ładowana środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="87bfb-104">These logs can be very useful in determining the root cause of an activation issue, when your application either loads a different CLR version than expected or doesn't load the CLR at all.</span></span> <span data-ttu-id="87bfb-105">[Błędy inicjowania programu .NET Framework: Zarządzanie czynności użytkownika](../../../docs/framework/deployment/initialization-errors-managing-the-user-experience.md) tym artykule omówiono środowisko CLR nie został znaleziony dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="87bfb-105">The [.NET Framework Initialization Errors: Managing the User Experience](../../../docs/framework/deployment/initialization-errors-managing-the-user-experience.md) discusses the experience when no CLR is found for an application.</span></span>  
  
 <span data-ttu-id="87bfb-106">Rejestrowanie aktywacji środowiska CLR może być włączone całego systemu za pomocą klucza rejestru HKEY_LOCAL_MACHINE lub zmienną środowiskową systemu.</span><span class="sxs-lookup"><span data-stu-id="87bfb-106">CLR activation logging can be enabled system-wide by using an HKEY_LOCAL_MACHINE registry key or a system environment variable.</span></span> <span data-ttu-id="87bfb-107">Dziennik zostaną wygenerowane do wpisu rejestru lub zmiennej środowiskowej zostanie usunięta.</span><span class="sxs-lookup"><span data-stu-id="87bfb-107">The log will be generated until the registry entry or the environment variable is removed.</span></span> <span data-ttu-id="87bfb-108">Alternatywnie można użyć użytkownika lub zmiennej środowiskowej proces lokalny do włączania rejestrowania zdarzeń z różnych zakresu i czasu trwania.</span><span class="sxs-lookup"><span data-stu-id="87bfb-108">Alternatively, you can use a user or process-local environment variable to enable logging with a different scope and duration.</span></span>  
  
 <span data-ttu-id="87bfb-109">Dzienniki aktywacji środowiska CLR nie należy mylić z [dzienniki powiązań zestawów](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md), które są całkowicie innej.</span><span class="sxs-lookup"><span data-stu-id="87bfb-109">CLR activation logs shouldn't be confused with [assembly binding logs](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md), which are entirely different.</span></span>  
  
## <a name="to-enable-clr-activation-logging"></a><span data-ttu-id="87bfb-110">Aby włączyć rejestrowanie aktywacji środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="87bfb-110">To enable CLR activation logging</span></span>  
  
#### <a name="using-the-registry"></a><span data-ttu-id="87bfb-111">Za pomocą rejestru</span><span class="sxs-lookup"><span data-stu-id="87bfb-111">Using the registry</span></span>  
  
1.  <span data-ttu-id="87bfb-112">W Edytorze rejestru przejdź do HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework (na komputerze 32-bitowe) lub HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\. Folder NETFramework (na komputerze 64-bitowe).</span><span class="sxs-lookup"><span data-stu-id="87bfb-112">In the Registry Editor, navigate to HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework (on a 32-bit computer) or HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework folder (on a 64-bit computer).</span></span>  
  
2.  <span data-ttu-id="87bfb-113">Dodaj wartość ciągu o nazwie `CLRLoadLogDir`i ustaw ją na pełną ścieżkę istniejącego katalogu, w którym chcesz przechowywać dzienniki aktywacji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="87bfb-113">Add a string value named `CLRLoadLogDir`, and set it to the full path of an existing directory where you'd like to store CLR activation logs.</span></span>  
  
 <span data-ttu-id="87bfb-114">Aktywacja rejestrowania pozostaje włączona do momentu usunięcia wartości ciągu.</span><span class="sxs-lookup"><span data-stu-id="87bfb-114">Activation logging remains enabled until you remove the string value.</span></span>  
  
#### <a name="using-an-environment-variable"></a><span data-ttu-id="87bfb-115">Za pomocą zmiennej środowiskowej</span><span class="sxs-lookup"><span data-stu-id="87bfb-115">Using an environment variable</span></span>  
  
-   <span data-ttu-id="87bfb-116">Ustaw `COMPLUS_CLRLoadLogDir` zmiennej środowiskowej na ciąg, który reprezentuje pełną ścieżkę istniejącego katalogu, w którym chcesz przechowywać dzienniki aktywacji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="87bfb-116">Set the `COMPLUS_CLRLoadLogDir` environment variable to a string that represents the full path of an existing directory where you'd like to store CLR activation logs.</span></span>  
  
     <span data-ttu-id="87bfb-117">Jak ustawić zmienną środowiskową określa zakres:</span><span class="sxs-lookup"><span data-stu-id="87bfb-117">How you set the environment variable determines its scope:</span></span>  
  
    -   <span data-ttu-id="87bfb-118">Jeśli zostanie ustawiona na poziomie systemu, aktywacji rejestrowanie jest włączone dla wszystkich aplikacji .NET Framework na tym komputerze, aż do usunięcia zmiennej środowiskowej.</span><span class="sxs-lookup"><span data-stu-id="87bfb-118">If you set it at the system level, activation logging is enabled for all .NET Framework applications on that computer until the environment variable is removed.</span></span>  
  
    -   <span data-ttu-id="87bfb-119">Jeśli zostanie ustawiona na poziomie użytkownika, aktywacji rejestrowanie jest włączone tylko dla bieżącego konta użytkownika.</span><span class="sxs-lookup"><span data-stu-id="87bfb-119">If you set it at the user level, activation logging is enabled only for the current user account.</span></span> <span data-ttu-id="87bfb-120">Rejestrowanie będzie kontynuowane do czasu usunięcia zmiennej środowiskowej.</span><span class="sxs-lookup"><span data-stu-id="87bfb-120">Logging continues until the environment variable is removed.</span></span>  
  
    -   <span data-ttu-id="87bfb-121">Jeśli ustawisz go z procesu przed załadowaniem CLR, aktywacji rejestrowanie jest włączone, aż do zakończenia procesu.</span><span class="sxs-lookup"><span data-stu-id="87bfb-121">If you set it from within the process before loading the CLR, activation logging is enabled until the process terminates.</span></span>  
  
    -   <span data-ttu-id="87bfb-122">Jeśli zostanie ustawiona w wierszu polecenia przed uruchomieniem aplikacji, aktywacji rejestrowanie jest włączone dla dowolnej aplikacji, który jest uruchamiany z tego wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="87bfb-122">If you set it at a command prompt before you run an application, activation logging is enabled for any application that is run from that command prompt.</span></span>  
  
     <span data-ttu-id="87bfb-123">Na przykład aby aktywacji dzienniki są przechowywane w katalogu c:\clrloadlogs o zasięgu na poziomie procesu, Otwórz okno wiersza polecenia i wpisz następujące polecenie, aby uruchomić aplikację:</span><span class="sxs-lookup"><span data-stu-id="87bfb-123">For example, to store activation logs in the c:\clrloadlogs directory with process-level scope, open a Command Prompt window and type the following before you run the application:</span></span>  
  
    ```  
    set COMPLUS_CLRLoadLogDir=c:\clrloadlogs  
    ```  
  
## <a name="example"></a><span data-ttu-id="87bfb-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="87bfb-124">Example</span></span>  
 <span data-ttu-id="87bfb-125">Dzienniki aktywacji środowiska CLR zapewniają dużą ilość danych o aktywacji środowiska CLR i korzystanie z aparatu CLR hostingu interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="87bfb-125">CLR activation logs provide a large amount of data about CLR activation and the use of the CLR hosting APIs.</span></span> <span data-ttu-id="87bfb-126">Większość tych danych jest używana wewnętrznie przez firmę Microsoft, ale niektóre dane mogą być przydatne także deweloperom, zgodnie z opisem w tym artykule.</span><span class="sxs-lookup"><span data-stu-id="87bfb-126">Most of this data is used internally by Microsoft, but some of the data can also be useful to developers, as described in this article.</span></span>  
  
 <span data-ttu-id="87bfb-127">Dziennik odzwierciedla w kolejności CLR hostingu API wywołane.</span><span class="sxs-lookup"><span data-stu-id="87bfb-127">The log reflects the order in which the CLR hosting APIs were called.</span></span> <span data-ttu-id="87bfb-128">Obejmuje on też przydatne dane dotyczące zestawu zainstalowanych środowisk uruchomieniowych wykrył na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="87bfb-128">It also includes useful data about the set of installed runtimes detected on the computer.</span></span> <span data-ttu-id="87bfb-129">Format dziennika aktywacji środowiska CLR nie jest swoim udokumentowane, ale może służyć do pomocy deweloperów chcących rozwiązać problemy dotyczące aktywacji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="87bfb-129">The CLR activation log format is not itself documented, but can be used to aid developers who need to resolve CLR activation issues.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="87bfb-130">Nie można otworzyć dziennika aktywacji, dopóki proces, który używa środowiska CLR został zakończony.</span><span class="sxs-lookup"><span data-stu-id="87bfb-130">You cannot open an activation log until the process that uses the CLR has terminated.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="87bfb-131">Dzienniki aktywacji środowiska CLR nie są zlokalizowane; są one zawsze generowane w języku angielskim.</span><span class="sxs-lookup"><span data-stu-id="87bfb-131">CLR activation logs are not localized; they are always generated in the English language.</span></span>  
  
 <span data-ttu-id="87bfb-132">W poniższym przykładzie dziennika aktywacji najbardziej przydatne informacje jest wyróżniony i opisem po dziennika.</span><span class="sxs-lookup"><span data-stu-id="87bfb-132">In the following example of an activation log, the most useful information is highlighted and described after the log.</span></span>  
  
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
  
-   <span data-ttu-id="87bfb-133">**Dziennik ładowania środowiska CLR** Określa ścieżkę do pliku wykonywalnego, który uruchomił proces, który załadowano kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="87bfb-133">**CLR Loading log** provides the path to the executable that started the process that loaded managed code.</span></span> <span data-ttu-id="87bfb-134">Należy pamiętać, że może to być hostem natywnego.</span><span class="sxs-lookup"><span data-stu-id="87bfb-134">Note that this could be a native host.</span></span>  
  
    ```  
    532,205950.367,CLR Loading log for C:\Tests\myapp.exe  
    ```  
  
-   <span data-ttu-id="87bfb-135">**Zainstalowane środowisko uruchomieniowe** Zestaw CLR wersje zainstalowane na komputerze, przeznaczone dla żądania aktywacji.</span><span class="sxs-lookup"><span data-stu-id="87bfb-135">**Installed Runtime** is the set of CLR versions installed on the computer that are candidates for the activation request.</span></span>  
  
    ```  
    532,205950.382,Installed Runtime: v4.0.30319. VERSION_ARCHITECTURE: 0  
    ```  
  
-   <span data-ttu-id="87bfb-136">**skompilowany jako wersja** jest wersja środowiska CLR, który został użyty do budowania plik binarny, który został dostarczony do metody, takie jak [ICLRMetaHostPolicy::GetRequestedRuntime](../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md).</span><span class="sxs-lookup"><span data-stu-id="87bfb-136">**built with version** is the version of the CLR that was used to build the binary that was provided to a method such as [ICLRMetaHostPolicy::GetRequestedRuntime](../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md).</span></span>  
  
    ```  
    532,205950.382,C:\Tests\myapp.exe was built with version: v2.0.50727  
    ```  
  
-   <span data-ttu-id="87bfb-137">**Instalacja funkcji na żądanie** odwołuje się do włączania programu .NET Framework 3.5 w systemie Windows 8.</span><span class="sxs-lookup"><span data-stu-id="87bfb-137">**feature-on-demand installation** refers to enabling the .NET Framework 3.5 on Windows 8.</span></span> <span data-ttu-id="87bfb-138">Zobacz [błędy inicjowania programu .NET Framework: Zarządzanie wrażeniami użytkownika](../../../docs/framework/deployment/initialization-errors-managing-the-user-experience.md) Aby uzyskać więcej informacji na temat tego scenariusza.</span><span class="sxs-lookup"><span data-stu-id="87bfb-138">See [.NET Framework Initialization Errors: Managing the User Experience](../../../docs/framework/deployment/initialization-errors-managing-the-user-experience.md) for more information about this scenario.</span></span>  
  
    ```  
    532,205950.398,Launching feature-on-demand installation. CmdLine: C:\Windows\system32\fondue.exe /enable-feature:NetFx3  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="87bfb-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="87bfb-139">See Also</span></span>  
 [<span data-ttu-id="87bfb-140">Wdrażanie</span><span class="sxs-lookup"><span data-stu-id="87bfb-140">Deployment</span></span>](../../../docs/framework/deployment/index.md)  
 [<span data-ttu-id="87bfb-141">Instrukcje: Konfiguracja aplikacji do obsługi w programie .NET Framework 4 lub 4.5</span><span class="sxs-lookup"><span data-stu-id="87bfb-141">How to: Configure an App to Support .NET Framework 4 or 4.5</span></span>](../../../docs/framework/migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
