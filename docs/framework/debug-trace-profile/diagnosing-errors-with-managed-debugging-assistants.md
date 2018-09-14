---
title: Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania
ms.date: 08/14/2018
f1_keywords:
- EHMDA
helpviewer_keywords:
- run-time error debugging
- managed code, run-time debugging
- resource debugging
- registry, MDAs
- common language runtime, debugging
- MDAs (managed debugging assistants)
- configuration files [.NET Framework], debugging runtime events
- messages, managed debugging assistants
- application configuration files, managed debugging assistants
- debugging [.NET Framework], managed debugging assistants
- environment variables, MDAs
- access violation debugging [.NET Framework]
- diagnostics, managed debugging assistants
- unmanaged code, run-time debugging
- default debug output stream
- memory, debugging
- app.config files, managed debugging assistants
- managed debugging assistants (MDAs)
- debugging [.NET Framework], run-time errors
- trapping events
- runtime, error debugging
- disabling MDAs
- output, managed debugging assistants
- errors [.NET Framework], managed debugging assistants
ms.assetid: 76994ee6-9fa9-4059-b813-26578d24427c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b745fa6a78ab2a7ab0b3a94c9921883d3c56c1b7
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45588515"
---
# <a name="diagnose-errors-with-managed-debugging-assistants"></a><span data-ttu-id="7e70b-102">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="7e70b-102">Diagnose Errors with Managed Debugging Assistants</span></span>

<span data-ttu-id="7e70b-103">Zarządzanie debugowaniem asystentów (mda) jest debugowany pomocy, które działają w połączeniu z środowisko uruchomieniowe języka wspólnego (CLR) zawiera informacje na temat stanu środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="7e70b-103">Managed debugging assistants (MDAs) are debugging aids that work in conjunction with the common language runtime (CLR) to provide information on runtime state.</span></span> <span data-ttu-id="7e70b-104">Asystenci Generowanie komunikaty o zdarzeniach środowiska uruchomieniowego, które w przeciwnym razie nie komunikat pułapki.</span><span class="sxs-lookup"><span data-stu-id="7e70b-104">The assistants generate informational messages about runtime events that you cannot otherwise trap.</span></span> <span data-ttu-id="7e70b-105">Mda umożliwia oddzieleniu błędów twardych znajdowanie aplikacji, które występują podczas przenoszenia między kodem zarządzanym i niezarządzanym.</span><span class="sxs-lookup"><span data-stu-id="7e70b-105">You can use MDAs to isolate hard-to-find application bugs that occur when transitioning between managed and unmanaged code.</span></span>

<span data-ttu-id="7e70b-106">Możesz [włączać lub wyłączać](#enable-and-disable-mdas) wszystkich mda przez dodanie klucza w rejestrze Windows lub przez ustawienie zmiennej środowiskowej.</span><span class="sxs-lookup"><span data-stu-id="7e70b-106">You can [enable or disable](#enable-and-disable-mdas) all MDAs by adding a key to the Windows registry or by setting an environment variable.</span></span> <span data-ttu-id="7e70b-107">Można włączyć określonego mda przy użyciu ustawień konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7e70b-107">You can enable specific MDAs by using application configuration settings.</span></span> <span data-ttu-id="7e70b-108">Dodatkowe ustawienia konfiguracji dla niektórych poszczególnych mda można ustawić w pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7e70b-108">You can set additional configuration settings for some individual MDAs in the application's configuration file.</span></span> <span data-ttu-id="7e70b-109">Ponieważ te pliki konfiguracyjne są w sytuacji, gdy jest ładowany przez środowisko uruchomieniowe, należy włączyć MDA przed uruchomieniem aplikacji zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="7e70b-109">Because these configuration files are parsed when the runtime is loaded, you must enable the MDA before the managed application starts.</span></span> <span data-ttu-id="7e70b-110">Nie możesz włączyć dla aplikacji, które zostały już uruchomione.</span><span class="sxs-lookup"><span data-stu-id="7e70b-110">You cannot enable it for applications that have already started.</span></span>

<span data-ttu-id="7e70b-111">W poniższej tabeli wymieniono mda, które są dostarczane za pomocą programu .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="7e70b-111">The following table lists the MDAs that ship with the .NET Framework:</span></span>

|||
|-|-|
|[<span data-ttu-id="7e70b-112">asynchronousThreadAbort</span><span class="sxs-lookup"><span data-stu-id="7e70b-112">asynchronousThreadAbort</span></span>](../../../docs/framework/debug-trace-profile/asynchronousthreadabort-mda.md)|[<span data-ttu-id="7e70b-113">bindingFailure</span><span class="sxs-lookup"><span data-stu-id="7e70b-113">bindingFailure</span></span>](../../../docs/framework/debug-trace-profile/bindingfailure-mda.md)|
|[<span data-ttu-id="7e70b-114">callbackOnCollectedDelegate</span><span class="sxs-lookup"><span data-stu-id="7e70b-114">callbackOnCollectedDelegate</span></span>](../../../docs/framework/debug-trace-profile/callbackoncollecteddelegate-mda.md)|[<span data-ttu-id="7e70b-115">contextSwitchDeadlock</span><span class="sxs-lookup"><span data-stu-id="7e70b-115">contextSwitchDeadlock</span></span>](../../../docs/framework/debug-trace-profile/contextswitchdeadlock-mda.md)|
|[<span data-ttu-id="7e70b-116">dangerousThreadingAPI</span><span class="sxs-lookup"><span data-stu-id="7e70b-116">dangerousThreadingAPI</span></span>](../../../docs/framework/debug-trace-profile/dangerousthreadingapi-mda.md)|[<span data-ttu-id="7e70b-117">dateTimeInvalidLocalFormat</span><span class="sxs-lookup"><span data-stu-id="7e70b-117">dateTimeInvalidLocalFormat</span></span>](../../../docs/framework/debug-trace-profile/datetimeinvalidlocalformat-mda.md)|
|[<span data-ttu-id="7e70b-118">dirtyCastAndCallOnInterface</span><span class="sxs-lookup"><span data-stu-id="7e70b-118">dirtyCastAndCallOnInterface</span></span>](../../../docs/framework/debug-trace-profile/dirtycastandcalloninterface-mda.md)|[<span data-ttu-id="7e70b-119">disconnectedContext</span><span class="sxs-lookup"><span data-stu-id="7e70b-119">disconnectedContext</span></span>](../../../docs/framework/debug-trace-profile/disconnectedcontext-mda.md)|
|[<span data-ttu-id="7e70b-120">dllMainReturnsFalse</span><span class="sxs-lookup"><span data-stu-id="7e70b-120">dllMainReturnsFalse</span></span>](../../../docs/framework/debug-trace-profile/dllmainreturnsfalse-mda.md)|[<span data-ttu-id="7e70b-121">exceptionSwallowedOnCallFromCom</span><span class="sxs-lookup"><span data-stu-id="7e70b-121">exceptionSwallowedOnCallFromCom</span></span>](../../../docs/framework/debug-trace-profile/exceptionswallowedoncallfromcom-mda.md)|
|[<span data-ttu-id="7e70b-122">failedQI</span><span class="sxs-lookup"><span data-stu-id="7e70b-122">failedQI</span></span>](../../../docs/framework/debug-trace-profile/failedqi-mda.md)|[<span data-ttu-id="7e70b-123">fatalExecutionEngineError</span><span class="sxs-lookup"><span data-stu-id="7e70b-123">fatalExecutionEngineError</span></span>](../../../docs/framework/debug-trace-profile/fatalexecutionengineerror-mda.md)|
|[<span data-ttu-id="7e70b-124">gcManagedToUnmanaged</span><span class="sxs-lookup"><span data-stu-id="7e70b-124">gcManagedToUnmanaged</span></span>](../../../docs/framework/debug-trace-profile/gcmanagedtounmanaged-mda.md)|[<span data-ttu-id="7e70b-125">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="7e70b-125">gcUnmanagedToManaged</span></span>](../../../docs/framework/debug-trace-profile/gcunmanagedtomanaged-mda.md)|
|[<span data-ttu-id="7e70b-126">illegalPrepareConstrainedRegion</span><span class="sxs-lookup"><span data-stu-id="7e70b-126">illegalPrepareConstrainedRegion</span></span>](../../../docs/framework/debug-trace-profile/illegalprepareconstrainedregion-mda.md)|[<span data-ttu-id="7e70b-127">invalidApartmentStateChange</span><span class="sxs-lookup"><span data-stu-id="7e70b-127">invalidApartmentStateChange</span></span>](../../../docs/framework/debug-trace-profile/invalidapartmentstatechange-mda.md)|
|[<span data-ttu-id="7e70b-128">invalidCERCall</span><span class="sxs-lookup"><span data-stu-id="7e70b-128">invalidCERCall</span></span>](../../../docs/framework/debug-trace-profile/invalidcercall-mda.md)|[<span data-ttu-id="7e70b-129">invalidFunctionPointerInDelegate</span><span class="sxs-lookup"><span data-stu-id="7e70b-129">invalidFunctionPointerInDelegate</span></span>](../../../docs/framework/debug-trace-profile/invalidfunctionpointerindelegate-mda.md)|
|[<span data-ttu-id="7e70b-130">invalidGCHandleCookie</span><span class="sxs-lookup"><span data-stu-id="7e70b-130">invalidGCHandleCookie</span></span>](../../../docs/framework/debug-trace-profile/invalidgchandlecookie-mda.md)|[<span data-ttu-id="7e70b-131">invalidIUnknown</span><span class="sxs-lookup"><span data-stu-id="7e70b-131">invalidIUnknown</span></span>](../../../docs/framework/debug-trace-profile/invalidiunknown-mda.md)|
|[<span data-ttu-id="7e70b-132">invalidMemberDeclaration</span><span class="sxs-lookup"><span data-stu-id="7e70b-132">invalidMemberDeclaration</span></span>](../../../docs/framework/debug-trace-profile/invalidmemberdeclaration-mda.md)|[<span data-ttu-id="7e70b-133">invalidOverlappedToPinvoke</span><span class="sxs-lookup"><span data-stu-id="7e70b-133">invalidOverlappedToPinvoke</span></span>](../../../docs/framework/debug-trace-profile/invalidoverlappedtopinvoke-mda.md)|
|[<span data-ttu-id="7e70b-134">invalidVariant</span><span class="sxs-lookup"><span data-stu-id="7e70b-134">invalidVariant</span></span>](../../../docs/framework/debug-trace-profile/invalidvariant-mda.md)|[<span data-ttu-id="7e70b-135">jitCompilationStart</span><span class="sxs-lookup"><span data-stu-id="7e70b-135">jitCompilationStart</span></span>](../../../docs/framework/debug-trace-profile/jitcompilationstart-mda.md)|
|[<span data-ttu-id="7e70b-136">loaderLock</span><span class="sxs-lookup"><span data-stu-id="7e70b-136">loaderLock</span></span>](../../../docs/framework/debug-trace-profile/loaderlock-mda.md)|[<span data-ttu-id="7e70b-137">loadFromContext</span><span class="sxs-lookup"><span data-stu-id="7e70b-137">loadFromContext</span></span>](../../../docs/framework/debug-trace-profile/loadfromcontext-mda.md)|
|[<span data-ttu-id="7e70b-138">marshalCleanupError</span><span class="sxs-lookup"><span data-stu-id="7e70b-138">marshalCleanupError</span></span>](../../../docs/framework/debug-trace-profile/marshalcleanuperror-mda.md)|[<span data-ttu-id="7e70b-139">marshaling</span><span class="sxs-lookup"><span data-stu-id="7e70b-139">marshaling</span></span>](../../../docs/framework/debug-trace-profile/marshaling-mda.md)|
|[<span data-ttu-id="7e70b-140">memberInfoCacheCreation</span><span class="sxs-lookup"><span data-stu-id="7e70b-140">memberInfoCacheCreation</span></span>](../../../docs/framework/debug-trace-profile/memberinfocachecreation-mda.md)|[<span data-ttu-id="7e70b-141">moduloObjectHashcode</span><span class="sxs-lookup"><span data-stu-id="7e70b-141">moduloObjectHashcode</span></span>](../../../docs/framework/debug-trace-profile/moduloobjecthashcode-mda.md)|
|[<span data-ttu-id="7e70b-142">nonComVisibleBaseClass</span><span class="sxs-lookup"><span data-stu-id="7e70b-142">nonComVisibleBaseClass</span></span>](../../../docs/framework/debug-trace-profile/noncomvisiblebaseclass-mda.md)|[<span data-ttu-id="7e70b-143">notMarshalable</span><span class="sxs-lookup"><span data-stu-id="7e70b-143">notMarshalable</span></span>](../../../docs/framework/debug-trace-profile/notmarshalable-mda.md)|
|[<span data-ttu-id="7e70b-144">openGenericCERCall</span><span class="sxs-lookup"><span data-stu-id="7e70b-144">openGenericCERCall</span></span>](../../../docs/framework/debug-trace-profile/opengenericcercall-mda.md)|[<span data-ttu-id="7e70b-145">overlappedFreeError</span><span class="sxs-lookup"><span data-stu-id="7e70b-145">overlappedFreeError</span></span>](../../../docs/framework/debug-trace-profile/overlappedfreeerror-mda.md)|
|[<span data-ttu-id="7e70b-146">pInvokeLog</span><span class="sxs-lookup"><span data-stu-id="7e70b-146">pInvokeLog</span></span>](../../../docs/framework/debug-trace-profile/pinvokelog-mda.md)|[<span data-ttu-id="7e70b-147">pInvokeStackImbalance</span><span class="sxs-lookup"><span data-stu-id="7e70b-147">pInvokeStackImbalance</span></span>](../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md)|
|[<span data-ttu-id="7e70b-148">raceOnRCWCleanup</span><span class="sxs-lookup"><span data-stu-id="7e70b-148">raceOnRCWCleanup</span></span>](../../../docs/framework/debug-trace-profile/raceonrcwcleanup-mda.md)|[<span data-ttu-id="7e70b-149">reentrancy</span><span class="sxs-lookup"><span data-stu-id="7e70b-149">reentrancy</span></span>](../../../docs/framework/debug-trace-profile/reentrancy-mda.md)|
|[<span data-ttu-id="7e70b-150">releaseHandleFailed</span><span class="sxs-lookup"><span data-stu-id="7e70b-150">releaseHandleFailed</span></span>](../../../docs/framework/debug-trace-profile/releasehandlefailed-mda.md)|[<span data-ttu-id="7e70b-151">reportAvOnComRelease</span><span class="sxs-lookup"><span data-stu-id="7e70b-151">reportAvOnComRelease</span></span>](../../../docs/framework/debug-trace-profile/reportavoncomrelease-mda.md)|
|[<span data-ttu-id="7e70b-152">streamWriterBufferedDataLost</span><span class="sxs-lookup"><span data-stu-id="7e70b-152">streamWriterBufferedDataLost</span></span>](../../../docs/framework/debug-trace-profile/streamwriterbuffereddatalost-mda.md)|[<span data-ttu-id="7e70b-153">virtualCERCall</span><span class="sxs-lookup"><span data-stu-id="7e70b-153">virtualCERCall</span></span>](../../../docs/framework/debug-trace-profile/virtualcercall-mda.md)|

<span data-ttu-id="7e70b-154">Domyślnie program .NET Framework aktywuje podzbiór mda dla wszystkich zarządzanych debugerów.</span><span class="sxs-lookup"><span data-stu-id="7e70b-154">By default, the .NET Framework activates a subset of MDAs for all managed debuggers.</span></span> <span data-ttu-id="7e70b-155">Możesz wyświetlić domyślnie w programie Visual Studio, wybierając **Windows** > **ustawienia wyjątków** na **debugowania** menu, a następnie rozwijając **Asystentów zarządzanego debugowania** listy.</span><span class="sxs-lookup"><span data-stu-id="7e70b-155">You can view the default set in Visual Studio by choosing **Windows** > **Exception Settings** on the **Debug** menu, and then expanding the **Managed Debugging Assistants** list.</span></span>

![Okno ustawień wyjątków w programie Visual Studio](media/diagnosing-errors-with-managed-debugging-assistants/exception-settings-mdas.png)

## <a name="enable-and-disable-mdas"></a><span data-ttu-id="7e70b-157">Włączanie i wyłączanie mda</span><span class="sxs-lookup"><span data-stu-id="7e70b-157">Enable and Disable MDAs</span></span>

<span data-ttu-id="7e70b-158">Można włączyć i wyłączyć mda przy użyciu klucza rejestru, zmienna środowiskowa i ustawienia konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7e70b-158">You can enable and disable MDAs by using a registry key, an environment variable, and application configuration settings.</span></span> <span data-ttu-id="7e70b-159">Należy włączyć klucz rejestru lub zmienną środowiskową Aby użyć ustawienia konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7e70b-159">You must enable either the registry key or the environment variable to use the application configuration settings.</span></span>

> [!TIP]
> <span data-ttu-id="7e70b-160">Zamiast wyłączanie mda, można zapobiec programu Visual Studio wyświetlanie okna dialogowego MDA zawsze wtedy, gdy zostanie odebrana wiadomość z powiadomieniem MDA.</span><span class="sxs-lookup"><span data-stu-id="7e70b-160">Instead of disabling MDAs, you can prevent Visual Studio from displaying the MDA dialog box whenever an MDA notification is received.</span></span> <span data-ttu-id="7e70b-161">Aby to zrobić, wybierz **Windows** > **ustawienia wyjątków** na **debugowania** menu, rozwiń węzeł **zarządzane debugowanie asystentów**listy, a następnie zaznacz lub wyczyść **Przerwij gdy zgłoszony** pole wyboru dla poszczególnych MDA.</span><span class="sxs-lookup"><span data-stu-id="7e70b-161">To do that, choose **Windows** > **Exception Settings** on the **Debug** menu, expand the **Managed Debugging Assistants** list, and then select or clear the **Break When Thrown** check box for the individual MDA.</span></span>

### <a name="registry-key"></a><span data-ttu-id="7e70b-162">Klucz rejestru</span><span class="sxs-lookup"><span data-stu-id="7e70b-162">Registry Key</span></span>

<span data-ttu-id="7e70b-163">Aby włączyć mda, Dodaj **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework\MDA** podklucz (typu REG_SZ, wartość 1) w rejestrze systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="7e70b-163">To enable MDAs, add the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\MDA** subkey (type REG_SZ, value 1) in the Windows registry.</span></span> <span data-ttu-id="7e70b-164">Skopiuj poniższy przykład do pliku tekstowego o nazwie *MDAEnable.reg*. Otwórz Edytor rejestru (RegEdit.exe), Windows i z **pliku** menu wybierz opcję **importu**.</span><span class="sxs-lookup"><span data-stu-id="7e70b-164">Copy the following example into a text file named *MDAEnable.reg*. Open the Windows Registry Editor (RegEdit.exe), and from the **File** menu choose **Import**.</span></span> <span data-ttu-id="7e70b-165">Wybierz *MDAEnable.reg* plik, aby umożliwić mda na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="7e70b-165">Select the *MDAEnable.reg* file to enable MDAs on that computer.</span></span> <span data-ttu-id="7e70b-166">Ustawienie go na wartość ciągu **1** (nie wartość DWORD **1**) umożliwia odczyt ustawień MDA *ApplicationName.suffix*. plik mda.config.</span><span class="sxs-lookup"><span data-stu-id="7e70b-166">Setting the subkey to string value of **1** (not DWORD value of **1**) enables the reading of MDA settings from the *ApplicationName.suffix*.mda.config file.</span></span> <span data-ttu-id="7e70b-167">Na przykład plik konfiguracji MDA Notatnik będzie nosić notepad.exe.mda.config.</span><span class="sxs-lookup"><span data-stu-id="7e70b-167">For example, the MDA configuration file for Notepad would be named notepad.exe.mda.config.</span></span>

```text
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework]
"MDA"="1"
```

<span data-ttu-id="7e70b-168">Jeśli komputer działa aplikacja 32-bitowa w 64-bitowym systemie operacyjnym, klucz MDA powinna być ustawiona podobnie do poniższych:</span><span class="sxs-lookup"><span data-stu-id="7e70b-168">If the computer is running a 32-bit application on a 64-bit operating system, then the MDA key should be set like the following:</span></span>

```text
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework]
"MDA"="1"
```

<span data-ttu-id="7e70b-169">Zobacz [ustawień konfiguracji specyficznych dla aplikacji](#application-specific-configuration-settings) Aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="7e70b-169">See [Application-Specific Configuration Settings](#application-specific-configuration-settings) for more information.</span></span> <span data-ttu-id="7e70b-170">Ustawienie rejestru może być zastąpiona przez zmienną środowiskową COMPLUS_MDA.</span><span class="sxs-lookup"><span data-stu-id="7e70b-170">The registry setting can be overridden by the COMPLUS_MDA environment variable.</span></span> <span data-ttu-id="7e70b-171">Zobacz [zmienna środowiskowa](#environment-variable) Aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="7e70b-171">See [Environment Variable](#environment-variable) for more information.</span></span>

<span data-ttu-id="7e70b-172">Aby wyłączyć mda, równa podklucz MDA **0** (zero) za pomocą Edytora rejestru Windows.</span><span class="sxs-lookup"><span data-stu-id="7e70b-172">To disable MDAs, set the MDA subkey to **0** (zero) using the Windows Registry Editor.</span></span>

<span data-ttu-id="7e70b-173">Domyślnie niektóre mda są włączone podczas uruchamiania aplikacji, która jest dołączona do debugera, nawet bez dodanie klucza rejestru.</span><span class="sxs-lookup"><span data-stu-id="7e70b-173">By default, some MDAs are enabled when you run an application that is attached to a debugger, even without adding the registry key.</span></span> <span data-ttu-id="7e70b-174">Można wyłączyć tych osób, uruchamiając *MDADisable.reg* plików zgodnie z wcześniejszym opisem w tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="7e70b-174">You can disable these assistants by running the *MDADisable.reg* file as described earlier in this section.</span></span>

### <a name="environment-variable"></a><span data-ttu-id="7e70b-175">Zmienna środowiskowa</span><span class="sxs-lookup"><span data-stu-id="7e70b-175">Environment Variable</span></span>

<span data-ttu-id="7e70b-176">MDA aktywacji może także kontrolowane przez zmienną środowiskową COMPLUS_MDA, która zastępuje klucz rejestru.</span><span class="sxs-lookup"><span data-stu-id="7e70b-176">MDA activation can also controlled by the environment variable COMPLUS_MDA, which overrides the registry key.</span></span> <span data-ttu-id="7e70b-177">Ciąg COMPLUS_MDA jest bez uwzględniania wielkości liter, rozdzielaną średnikami listę nazw MDA lub inne ciągi kontroli.</span><span class="sxs-lookup"><span data-stu-id="7e70b-177">The COMPLUS_MDA string is a case-insensitive, semicolon-delimited list of MDA names or other special control strings.</span></span> <span data-ttu-id="7e70b-178">Uruchamianie w debugerze zarządzanych lub niezarządzanych zapewnia zestaw mda domyślnie.</span><span class="sxs-lookup"><span data-stu-id="7e70b-178">Starting under a managed or unmanaged debugger enables a set of MDAs by default.</span></span> <span data-ttu-id="7e70b-179">Odbywa się przez niejawnie poprzedzenie jej rozdzieloną średnikami listę mda włączona domyślnie w ramach debugery wartość środowiska zmiennej lub klucza rejestru.</span><span class="sxs-lookup"><span data-stu-id="7e70b-179">This is done by implicitly prepending the semicolon-delimited list of MDAs enabled by default under debuggers to the value of the environment variable or registry key.</span></span> <span data-ttu-id="7e70b-180">Ciągi kontroli specjalne są następujące:</span><span class="sxs-lookup"><span data-stu-id="7e70b-180">The special control strings are the following:</span></span>

- <span data-ttu-id="7e70b-181">`0` -Dezaktywuje wszystkich mda.</span><span class="sxs-lookup"><span data-stu-id="7e70b-181">`0` - Deactivates all MDAs.</span></span>

- <span data-ttu-id="7e70b-182">`1` -Odczytuje ustawienia MDA z *ApplicationName*. mda.config.</span><span class="sxs-lookup"><span data-stu-id="7e70b-182">`1` - Reads MDA settings from *ApplicationName*.mda.config.</span></span>

- <span data-ttu-id="7e70b-183">`managedDebugger` -Jawnie aktywuje wszystkich mda, niejawnie są aktywowane podczas uruchamiania zarządzanego pliku wykonywalnego w debugerze.</span><span class="sxs-lookup"><span data-stu-id="7e70b-183">`managedDebugger` - Explicitly activates all MDAs that are implicitly activated when a managed executable is started under a debugger.</span></span>

- <span data-ttu-id="7e70b-184">`unmanagedDebugger` -Jawnie aktywuje wszystkich mda, niejawnie są aktywowane podczas uruchamiania pliku wykonywalnego niezarządzanych w debugerze.</span><span class="sxs-lookup"><span data-stu-id="7e70b-184">`unmanagedDebugger` - Explicitly activates all MDAs that are implicitly activated when an unmanaged executable is started under a debugger.</span></span>

<span data-ttu-id="7e70b-185">W przypadku ustawienia powodujące konflikt ostatnio używanych ustawień Zastąp poprzednie ustawienia:</span><span class="sxs-lookup"><span data-stu-id="7e70b-185">If there are conflicting settings, the most recent settings override previous settings:</span></span>

- <span data-ttu-id="7e70b-186">`COMPLUS_MDA=0` Wyłącza wszystkie mda, łącznie z tymi włączana domyślnie w debugerze.</span><span class="sxs-lookup"><span data-stu-id="7e70b-186">`COMPLUS_MDA=0` disables all MDAs, including those implicitly enabled under a debugger.</span></span>

- <span data-ttu-id="7e70b-187">`COMPLUS_MDA=gcUnmanagedToManaged` Włącza `gcUnmanagedToManaged` oprócz wszelkich mda, które są domyślnie włączone w debugerze.</span><span class="sxs-lookup"><span data-stu-id="7e70b-187">`COMPLUS_MDA=gcUnmanagedToManaged` enables `gcUnmanagedToManaged` in addition to any MDAs that are implicitly enabled under a debugger.</span></span>

- <span data-ttu-id="7e70b-188">`COMPLUS_MDA=0;gcUnmanagedToManaged` Włącza `gcUnmanagedToManaged` , ale wyłącza mda, które w przeciwnym razie można włączyć niejawnie w debugerze.</span><span class="sxs-lookup"><span data-stu-id="7e70b-188">`COMPLUS_MDA=0;gcUnmanagedToManaged` enables `gcUnmanagedToManaged` but disables MDAs that would otherwise be implicitly enabled under a debugger.</span></span>

### <a name="application-specific-configuration-settings"></a><span data-ttu-id="7e70b-189">Ustawienia konfiguracji specyficzne dla aplikacji</span><span class="sxs-lookup"><span data-stu-id="7e70b-189">Application-Specific Configuration Settings</span></span>

<span data-ttu-id="7e70b-190">Można włączyć, wyłączyć i skonfigurować niektóre asystentów osobno w pliku konfiguracyjnym MDA dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7e70b-190">You can enable, disable, and configure some assistants individually in the MDA configuration file for the application.</span></span> <span data-ttu-id="7e70b-191">Aby włączyć korzystanie z pliku konfiguracji aplikacji do konfigurowania mda, można ustawić klucz rejestru MDA lub zmiennej środowiskowej COMPLUS_MDA.</span><span class="sxs-lookup"><span data-stu-id="7e70b-191">To enable the use of an application configuration file for configuring MDAs, either the MDA registry key or the COMPLUS_MDA environment variable must be set.</span></span> <span data-ttu-id="7e70b-192">Plik konfiguracyjny aplikacji zwykle znajduje się w tym samym katalogu co plik wykonywalny (.exe) aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7e70b-192">The application configuration file is typically located in the same directory as the application's executable (.exe) file.</span></span> <span data-ttu-id="7e70b-193">Nazwa pliku ma postać *ApplicationName*. mda.config, na przykład notepad.exe.mda.config. Asystenci, które są włączone w pliku konfiguracji aplikacji mogą mieć atrybutów lub elementów zaprojektowane specjalnie w celu sterowania zachowaniem tej Asystenta ustawień.</span><span class="sxs-lookup"><span data-stu-id="7e70b-193">The file name takes the form *ApplicationName*.mda.config; for example, notepad.exe.mda.config. Assistants that are enabled in the application configuration file may have attributes or elements specifically designed to control that assistant's behavior.</span></span>

<span data-ttu-id="7e70b-194">Poniższy przykład pokazuje, jak włączyć i skonfigurować [marshaling](../../../docs/framework/debug-trace-profile/marshaling-mda.md):</span><span class="sxs-lookup"><span data-stu-id="7e70b-194">The following example shows how to enable and configure the [marshaling](../../../docs/framework/debug-trace-profile/marshaling-mda.md):</span></span>

```xml
<mdaConfig>
  <assistants>
    <marshaling>
      <methodFilter>
        <match name="*"/>
      </methodFilter>
      <fieldFilter>
        <match name="*"/>
      </fieldFilter>
    </marshaling>
  </assistants>
</mdaConfig>
```

<span data-ttu-id="7e70b-195">`Marshaling` MDA emituje informacje o typ zarządzany, który jest są przekazywane do typu niezarządzanego, dla każdego przejścia zarządzane do niezarządzanego w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7e70b-195">The `Marshaling` MDA emits information about the managed type that is being marshaled to an unmanaged type for each managed-to-unmanaged transition in the application.</span></span> <span data-ttu-id="7e70b-196">`Marshaling` MDA można również filtrować nazwy metod i pól struktury dostarczane w **methodFilter** i **fieldFilter** elementy podrzędne, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="7e70b-196">The `Marshaling` MDA can also filter the names of the method and structure fields supplied in the **methodFilter** and **fieldFilter** child elements, respectively.</span></span>

<span data-ttu-id="7e70b-197">Poniższy przykład pokazuje, jak włączyć wielu mda przy użyciu ustawień domyślnych:</span><span class="sxs-lookup"><span data-stu-id="7e70b-197">The following example shows how to enable multiple MDAs by using their default settings:</span></span>

```xml
<mdaConfig>
  <assistants>
    <illegalPrepareConstrainedRegion />
    <invalidCERCall />
    <openGenericCERCall />
    <virtualCERCall />
  </assistants>
</mdaConfig>
```

> [!IMPORTANT]
> <span data-ttu-id="7e70b-198">Po określeniu więcej niż jeden Asystenta ustawień w pliku konfiguracji należy wyświetlić je w kolejności alfabetycznej.</span><span class="sxs-lookup"><span data-stu-id="7e70b-198">When you specify more than one assistant in a configuration file, you must list them in alphabetical order.</span></span> <span data-ttu-id="7e70b-199">Na przykład, jeśli chcesz włączyć obie opcje `virtualCERCall` i `invalidCERCall` mda, należy dodać `<invalidCERCall />` wpis przed `<virtualCERCall />` wpisu.</span><span class="sxs-lookup"><span data-stu-id="7e70b-199">For example, if you want to enable both the `virtualCERCall` and the `invalidCERCall` MDAs, you must add the `<invalidCERCall />` entry before the `<virtualCERCall />` entry.</span></span> <span data-ttu-id="7e70b-200">Jeśli wpisy nie są w kolejności alfabetycznej, zostanie wyświetlony komunikat wyjątku pliku nieobsługiwany nieprawidłowej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="7e70b-200">If the entries are not in alphabetical order, an unhandled invalid configuration file exception message is displayed.</span></span>

## <a name="mda-exceptions"></a><span data-ttu-id="7e70b-201">Wyjątki MDA</span><span class="sxs-lookup"><span data-stu-id="7e70b-201">MDA exceptions</span></span>

<span data-ttu-id="7e70b-202">Po włączeniu MDA jest aktywna nawet po kodzie nie może być wykonane w debugerze.</span><span class="sxs-lookup"><span data-stu-id="7e70b-202">When an MDA is enabled, it's active even when your code is not executing under a debugger.</span></span> <span data-ttu-id="7e70b-203">Jeśli zdarzenie MDA jest wywoływane, gdy nie jest debugera, komunikatów o zdarzeniach są prezentowane w oknie dialogowym nieobsługiwany wyjątek, chociaż nie jest to nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="7e70b-203">If an MDA event is raised when a debugger is not present, the event message is presented in an unhandled exception dialog box, although it is not an unhandled exception.</span></span> <span data-ttu-id="7e70b-204">Aby uniknąć okno dialogowe, należy usunąć ustawienia włączania MDA, gdy kod nie jest wykonywany w środowisku debugowania.</span><span class="sxs-lookup"><span data-stu-id="7e70b-204">To avoid the dialog box, remove the MDA-enabling settings when your code is not executing in a debugging environment.</span></span>

<span data-ttu-id="7e70b-205">Podczas wykonywania kodu w programie Visual Studio zintegrowane środowisko programistyczne (IDE), można uniknąć, okno dialogowe wyjątku, który pojawia się dla określonego zdarzenia MDA.</span><span class="sxs-lookup"><span data-stu-id="7e70b-205">When your code executes in the Visual Studio integrated development environment (IDE), you can avoid the exception dialog box that appears for specific MDA events.</span></span> <span data-ttu-id="7e70b-206">Aby to zrobić, na **debugowania** menu, wybierz **Windows** > **ustawienia wyjątków**.</span><span class="sxs-lookup"><span data-stu-id="7e70b-206">To do that, on the **Debug** menu, choose **Windows** > **Exception Settings**.</span></span> <span data-ttu-id="7e70b-207">W **ustawienia wyjątków** okna, rozwiń węzeł **asystentów zarządzanego debugowania** listy, a następnie wyczyść **Przerwij gdy zgłoszony** pole wyboru dla poszczególnych MDA.</span><span class="sxs-lookup"><span data-stu-id="7e70b-207">In the **Exception Settings** window, expand the **Managed Debugging Assistants** list, and then clear the **Break When Thrown** check box for the individual MDA.</span></span> <span data-ttu-id="7e70b-208">Można również użyć tego okna dialogowego do *Włącz* wyświetlanie okien dialogowych wyjątek MDA.</span><span class="sxs-lookup"><span data-stu-id="7e70b-208">You can also use this dialog box to *enable* the display of MDA exception dialog boxes.</span></span>

## <a name="mda-output"></a><span data-ttu-id="7e70b-209">Dane wyjściowe MDA</span><span class="sxs-lookup"><span data-stu-id="7e70b-209">MDA Output</span></span>

<span data-ttu-id="7e70b-210">MDA rezultat jest podobny do poniższego przykładu, który pokazuje dane wyjściowe z `PInvokeStackImbalance` MDA:</span><span class="sxs-lookup"><span data-stu-id="7e70b-210">MDA output is similar to the following example, which shows the output from the `PInvokeStackImbalance` MDA:</span></span>

<span data-ttu-id="7e70b-211">**Wywołanie funkcji PInvoke "MDATest! MDATest.Program::StdCall "ma niezrównoważone stosu. Jest to prawdopodobnie, ponieważ zarządzanego podpisu PInvoke jest niezgodna z niezarządzanego podpisu docelowego. Sprawdź, czy Konwencja wywoływania i parametry podpisu funkcji PInvoke odpowiadają niezarządzanego podpisu docelowego.**</span><span class="sxs-lookup"><span data-stu-id="7e70b-211">**A call to PInvoke function 'MDATest!MDATest.Program::StdCall' has unbalanced the stack. This is likely because the managed PInvoke signature does not match the unmanaged target signature. Check that the calling convention and parameters of the PInvoke signature match the target unmanaged signature.**</span></span>

## <a name="see-also"></a><span data-ttu-id="7e70b-212">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7e70b-212">See also</span></span>

- [<span data-ttu-id="7e70b-213">Debugowanie, śledzenie i profilowanie</span><span class="sxs-lookup"><span data-stu-id="7e70b-213">Debugging, Tracing, and Profiling</span></span>](../../../docs/framework/debug-trace-profile/index.md)
