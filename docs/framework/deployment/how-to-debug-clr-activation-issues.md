---
title: Jak debugować problemy dotyczące aktywacji środowiska CLR
ms.date: 03/30/2017
helpviewer_keywords:
- CLR activation, debugging issues
ms.assetid: 4fe17546-d56e-4344-a930-6d8e4a545914
ms.openlocfilehash: 602ee3c88237a902d48339836fbe25f636ae9705
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716507"
---
# <a name="how-to-debug-clr-activation-issues"></a><span data-ttu-id="5d446-102">Jak debugować problemy dotyczące aktywacji środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="5d446-102">How to debug CLR activation issues</span></span>

<span data-ttu-id="5d446-103">Jeśli wystąpią problemy z rozpoczęciem pracy aplikacji z poprawną wersją środowiska uruchomieniowego języka wspólnego (CLR), można wyświetlać i debugować dzienniki aktywacji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="5d446-103">If you encounter problems in getting your application to run with the correct version of the common language runtime (CLR), you can view and debug CLR activation logs.</span></span> <span data-ttu-id="5d446-104">Te dzienniki mogą być bardzo przydatne podczas określania głównej przyczyny problemu z aktywacją, gdy aplikacja ładuje inną wersję środowiska CLR niż oczekiwano lub nie ładuje środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="5d446-104">These logs can be very useful in determining the root cause of an activation issue, when your application either loads a different CLR version than expected or doesn't load the CLR at all.</span></span> <span data-ttu-id="5d446-105">[Błędy inicjowania .NET Framework: Zarządzanie środowiskiem użytkownika](initialization-errors-managing-the-user-experience.md) omawia środowisko, w którym nie znaleziono środowiska CLR dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5d446-105">The [.NET Framework Initialization Errors: Managing the User Experience](initialization-errors-managing-the-user-experience.md) discusses the experience when no CLR is found for an application.</span></span>

<span data-ttu-id="5d446-106">Rejestrowanie aktywacji środowiska CLR można włączyć na poziomie systemu przy użyciu klucza rejestru HKEY_LOCAL_MACHINE lub zmiennej środowiskowej system.</span><span class="sxs-lookup"><span data-stu-id="5d446-106">CLR activation logging can be enabled system-wide by using an HKEY_LOCAL_MACHINE registry key or a system environment variable.</span></span> <span data-ttu-id="5d446-107">Dziennik zostanie wygenerowany do momentu usunięcia wpisu rejestru lub zmiennej środowiskowej.</span><span class="sxs-lookup"><span data-stu-id="5d446-107">The log will be generated until the registry entry or the environment variable is removed.</span></span> <span data-ttu-id="5d446-108">Alternatywnie można użyć zmiennej środowiskowej użytkownika lub procesu lokalnego, aby włączyć rejestrowanie z innym zakresem i czasem trwania.</span><span class="sxs-lookup"><span data-stu-id="5d446-108">Alternatively, you can use a user or process-local environment variable to enable logging with a different scope and duration.</span></span>

<span data-ttu-id="5d446-109">Dzienników aktywacji środowiska CLR nie należy mylić z [dziennikami powiązań zestawów](../tools/fuslogvw-exe-assembly-binding-log-viewer.md), które są całkowicie inne.</span><span class="sxs-lookup"><span data-stu-id="5d446-109">CLR activation logs shouldn't be confused with [assembly binding logs](../tools/fuslogvw-exe-assembly-binding-log-viewer.md), which are entirely different.</span></span>

## <a name="to-enable-clr-activation-logging"></a><span data-ttu-id="5d446-110">Aby włączyć rejestrowanie aktywacji środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="5d446-110">To enable CLR activation logging</span></span>

### <a name="using-the-registry"></a><span data-ttu-id="5d446-111">Korzystanie z rejestru</span><span class="sxs-lookup"><span data-stu-id="5d446-111">Using the registry</span></span>

1. <span data-ttu-id="5d446-112">W Edytorze rejestru przejdź do HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\\. NETFramework (na komputerze 32-bitowym) lub\\HKEY_LOCAL_MACHINE \SOFTWARE\Wow6432Node\Microsoft. Folder NETFramework (na komputerze 64-bitowym).</span><span class="sxs-lookup"><span data-stu-id="5d446-112">In the Registry Editor, navigate to HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework (on a 32-bit computer) or HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework folder (on a 64-bit computer).</span></span>

2. <span data-ttu-id="5d446-113">Dodaj wartość ciągu o nazwie `CLRLoadLogDir`i ustaw ją na pełną ścieżkę do istniejącego katalogu, w którym chcesz przechowywać dzienniki aktywacji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="5d446-113">Add a string value named `CLRLoadLogDir`, and set it to the full path of an existing directory where you'd like to store CLR activation logs.</span></span>

<span data-ttu-id="5d446-114">Rejestrowanie aktywacji pozostaje włączone do momentu usunięcia wartości ciągu.</span><span class="sxs-lookup"><span data-stu-id="5d446-114">Activation logging remains enabled until you remove the string value.</span></span>

### <a name="using-an-environment-variable"></a><span data-ttu-id="5d446-115">Użycie zmiennej środowiskowej</span><span class="sxs-lookup"><span data-stu-id="5d446-115">Using an environment variable</span></span>

- <span data-ttu-id="5d446-116">Ustaw zmienną środowiskową `COMPLUS_CLRLoadLogDir` na ciąg, który reprezentuje pełną ścieżkę do istniejącego katalogu, w którym chcesz przechowywać dzienniki aktywacji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="5d446-116">Set the `COMPLUS_CLRLoadLogDir` environment variable to a string that represents the full path of an existing directory where you'd like to store CLR activation logs.</span></span>

    <span data-ttu-id="5d446-117">Sposób ustawiania zmiennej środowiskowej określa jej zakres:</span><span class="sxs-lookup"><span data-stu-id="5d446-117">How you set the environment variable determines its scope:</span></span>

  - <span data-ttu-id="5d446-118">Jeśli ustawisz ją na poziomie systemu, rejestrowanie aktywacji jest włączone dla wszystkich aplikacji .NET Framework na tym komputerze do momentu usunięcia zmiennej środowiskowej.</span><span class="sxs-lookup"><span data-stu-id="5d446-118">If you set it at the system level, activation logging is enabled for all .NET Framework applications on that computer until the environment variable is removed.</span></span>

  - <span data-ttu-id="5d446-119">Jeśli ustawisz ją na poziomie użytkownika, rejestrowanie aktywacji jest włączone tylko dla bieżącego konta użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5d446-119">If you set it at the user level, activation logging is enabled only for the current user account.</span></span> <span data-ttu-id="5d446-120">Rejestrowanie jest kontynuowane do momentu usunięcia zmiennej środowiskowej.</span><span class="sxs-lookup"><span data-stu-id="5d446-120">Logging continues until the environment variable is removed.</span></span>

  - <span data-ttu-id="5d446-121">Jeśli ustawisz ją z poziomu procesu przed załadowaniem środowiska CLR, rejestrowanie aktywacji zostanie włączone do momentu zakończenia procesu.</span><span class="sxs-lookup"><span data-stu-id="5d446-121">If you set it from within the process before loading the CLR, activation logging is enabled until the process terminates.</span></span>

  - <span data-ttu-id="5d446-122">Jeśli ustawisz go w wierszu polecenia przed uruchomieniem aplikacji, rejestrowanie aktywacji jest włączone dla każdej aplikacji, która jest uruchamiana z tego wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="5d446-122">If you set it at a command prompt before you run an application, activation logging is enabled for any application that is run from that command prompt.</span></span>

    <span data-ttu-id="5d446-123">Aby na przykład przechowywać dzienniki aktywacji w katalogu c:\clrloadlogs z zakresem poziomu procesu, Otwórz okno wiersza polecenia i wpisz następujące polecenie, aby uruchomić aplikację:</span><span class="sxs-lookup"><span data-stu-id="5d446-123">For example, to store activation logs in the c:\clrloadlogs directory with process-level scope, open a Command Prompt window and type the following before you run the application:</span></span>

    ```console
    set COMPLUS_CLRLoadLogDir=c:\clrloadlogs
    ```

## <a name="example"></a><span data-ttu-id="5d446-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="5d446-124">Example</span></span>

<span data-ttu-id="5d446-125">Dzienniki aktywacji środowiska CLR zapewniają dużą ilość danych dotyczących aktywacji środowiska CLR i używania interfejsów API hostingu środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="5d446-125">CLR activation logs provide a large amount of data about CLR activation and the use of the CLR hosting APIs.</span></span> <span data-ttu-id="5d446-126">Większość tych danych jest używana wewnętrznie przez firmę Microsoft, ale niektóre dane mogą być również przydatne dla deweloperów, zgodnie z opisem w tym artykule.</span><span class="sxs-lookup"><span data-stu-id="5d446-126">Most of this data is used internally by Microsoft, but some of the data can also be useful to developers, as described in this article.</span></span>

<span data-ttu-id="5d446-127">Dziennik odzwierciedla kolejność wywoływania interfejsów API hostingu środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="5d446-127">The log reflects the order in which the CLR hosting APIs were called.</span></span> <span data-ttu-id="5d446-128">Zawiera również przydatne dane dotyczące zestawu zainstalowanych środowisk uruchomieniowych na komputerze.</span><span class="sxs-lookup"><span data-stu-id="5d446-128">It also includes useful data about the set of installed runtimes detected on the computer.</span></span> <span data-ttu-id="5d446-129">Format dziennika aktywacji środowiska CLR nie jest udokumentowany, ale może służyć do ułatwienia deweloperom, którzy muszą rozwiązać problemy związane z aktywacją środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="5d446-129">The CLR activation log format is not itself documented, but can be used to aid developers who need to resolve CLR activation issues.</span></span>

> [!NOTE]
> <span data-ttu-id="5d446-130">Nie można otworzyć dziennika aktywacji do momentu zakończenia procesu, który używa środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="5d446-130">You cannot open an activation log until the process that uses the CLR has terminated.</span></span>

> [!NOTE]
> <span data-ttu-id="5d446-131">Dzienniki aktywacji środowiska CLR nie są zlokalizowane; są one zawsze generowane w języku angielskim.</span><span class="sxs-lookup"><span data-stu-id="5d446-131">CLR activation logs are not localized; they are always generated in the English language.</span></span>

<span data-ttu-id="5d446-132">W poniższym przykładzie dziennika aktywacji najbardziej przydatne informacje są wyróżnione i opisane po dzienniku.</span><span class="sxs-lookup"><span data-stu-id="5d446-132">In the following example of an activation log, the most useful information is highlighted and described after the log.</span></span>

```output
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

- <span data-ttu-id="5d446-133">**Dziennik ładowania środowiska CLR** zawiera ścieżkę do pliku wykonywalnego, który uruchomił proces, który załadował kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="5d446-133">**CLR Loading log** provides the path to the executable that started the process that loaded managed code.</span></span> <span data-ttu-id="5d446-134">Należy pamiętać, że może to być Host macierzysty.</span><span class="sxs-lookup"><span data-stu-id="5d446-134">Note that this could be a native host.</span></span>

    ```output
    532,205950.367,CLR Loading log for C:\Tests\myapp.exe
    ```

- <span data-ttu-id="5d446-135">**Zainstalowane środowisko uruchomieniowe** to zestaw wersji środowiska CLR zainstalowanych na komputerze, który jest kandydatem do żądania aktywacji.</span><span class="sxs-lookup"><span data-stu-id="5d446-135">**Installed Runtime** is the set of CLR versions installed on the computer that are candidates for the activation request.</span></span>

    ```output
    532,205950.382,Installed Runtime: v4.0.30319. VERSION_ARCHITECTURE: 0
    ```

- <span data-ttu-id="5d446-136">**wersja wbudowana** to wersja środowiska CLR, która została użyta do skompilowania pliku binarnego, który został dostarczony do metody, takiej jak [ICLRMetaHostPolicy:: GetRequestedRuntime —](../unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md).</span><span class="sxs-lookup"><span data-stu-id="5d446-136">**built with version** is the version of the CLR that was used to build the binary that was provided to a method such as [ICLRMetaHostPolicy::GetRequestedRuntime](../unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md).</span></span>

    ```output
    532,205950.382,C:\Tests\myapp.exe was built with version: v2.0.50727
    ```

- <span data-ttu-id="5d446-137">**Instalacja funkcji na żądanie** dotyczy .NET Framework 3,5 w systemie Windows 8.</span><span class="sxs-lookup"><span data-stu-id="5d446-137">**feature-on-demand installation** refers to enabling the .NET Framework 3.5 on Windows 8.</span></span> <span data-ttu-id="5d446-138">Zobacz [Błędy inicjowania .NET Framework: Zarządzanie czynnościami użytkownika,](initialization-errors-managing-the-user-experience.md) Aby uzyskać więcej informacji na temat tego scenariusza.</span><span class="sxs-lookup"><span data-stu-id="5d446-138">See [.NET Framework Initialization Errors: Managing the User Experience](initialization-errors-managing-the-user-experience.md) for more information about this scenario.</span></span>

    ```output
    532,205950.398,Launching feature-on-demand installation. CmdLine: C:\Windows\system32\fondue.exe /enable-feature:NetFx3
    ```

## <a name="see-also"></a><span data-ttu-id="5d446-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5d446-139">See also</span></span>

- [<span data-ttu-id="5d446-140">Wdrażanie</span><span class="sxs-lookup"><span data-stu-id="5d446-140">Deployment</span></span>](index.md)
- [<span data-ttu-id="5d446-141">Instrukcje: Konfigurowanie aplikacji do obsługi .NET Framework 4 lub nowszej wersji</span><span class="sxs-lookup"><span data-stu-id="5d446-141">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
