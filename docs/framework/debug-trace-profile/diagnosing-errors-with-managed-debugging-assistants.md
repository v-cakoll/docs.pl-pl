---
title: Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania
description: Diagnozowanie błędów w programie .NET przy użyciu asystentów zarządzanego debugowania. MDA to pomoce debugowania działające w połączeniu z środowiskiem CLR w celu zapewnienia informacji o stanie środowiska uruchomieniowego.
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
ms.openlocfilehash: ac6fdc09fb057cc55659ce076d37ab96fe2354d1
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2020
ms.locfileid: "85416099"
---
# <a name="diagnose-errors-with-managed-debugging-assistants"></a><span data-ttu-id="094d3-104">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="094d3-104">Diagnose Errors with Managed Debugging Assistants</span></span>

<span data-ttu-id="094d3-105">Zarządzane Asystenci debugowania (MDA) to pomoce debugowania, które działają w połączeniu ze środowiskiem uruchomieniowym języka wspólnego (CLR) w celu zapewnienia informacji o stanie środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="094d3-105">Managed debugging assistants (MDAs) are debugging aids that work in conjunction with the common language runtime (CLR) to provide information on runtime state.</span></span> <span data-ttu-id="094d3-106">Asystenci generują komunikaty informacyjne dotyczące zdarzeń środowiska uruchomieniowego, które nie mogą być pułapki w przeciwnym razie.</span><span class="sxs-lookup"><span data-stu-id="094d3-106">The assistants generate informational messages about runtime events that you cannot otherwise trap.</span></span> <span data-ttu-id="094d3-107">Możesz użyć MDA, aby wyizolować trudne do znalezienia usterki aplikacji występujące podczas przechodzenia między kodem zarządzanym i niezarządzanym.</span><span class="sxs-lookup"><span data-stu-id="094d3-107">You can use MDAs to isolate hard-to-find application bugs that occur when transitioning between managed and unmanaged code.</span></span>

<span data-ttu-id="094d3-108">Możesz [włączyć lub wyłączyć](#enable-and-disable-mdas) wszystkie MDA przez dodanie klucza do rejestru systemu Windows lub przez ustawienie zmiennej środowiskowej.</span><span class="sxs-lookup"><span data-stu-id="094d3-108">You can [enable or disable](#enable-and-disable-mdas) all MDAs by adding a key to the Windows registry or by setting an environment variable.</span></span> <span data-ttu-id="094d3-109">Konkretne MDA można włączyć za pomocą ustawień konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="094d3-109">You can enable specific MDAs by using application configuration settings.</span></span> <span data-ttu-id="094d3-110">Można ustawić dodatkowe ustawienia konfiguracji dla niektórych pojedynczych MDA w pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="094d3-110">You can set additional configuration settings for some individual MDAs in the application's configuration file.</span></span> <span data-ttu-id="094d3-111">Ponieważ te pliki konfiguracji są analizowane podczas ładowania środowiska uruchomieniowego, przed uruchomieniem aplikacji zarządzanej należy włączyć funkcję MDA.</span><span class="sxs-lookup"><span data-stu-id="094d3-111">Because these configuration files are parsed when the runtime is loaded, you must enable the MDA before the managed application starts.</span></span> <span data-ttu-id="094d3-112">Nie można go włączyć dla aplikacji, które zostały już uruchomione.</span><span class="sxs-lookup"><span data-stu-id="094d3-112">You cannot enable it for applications that have already started.</span></span>

<span data-ttu-id="094d3-113">Poniższa tabela zawiera listę MDA, które są dostarczane z .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="094d3-113">The following table lists the MDAs that ship with the .NET Framework:</span></span>

|||
|-|-|
|[<span data-ttu-id="094d3-114">asynchronousThreadAbort</span><span class="sxs-lookup"><span data-stu-id="094d3-114">asynchronousThreadAbort</span></span>](asynchronousthreadabort-mda.md)|[<span data-ttu-id="094d3-115">bindingFailure</span><span class="sxs-lookup"><span data-stu-id="094d3-115">bindingFailure</span></span>](bindingfailure-mda.md)|
|[<span data-ttu-id="094d3-116">callbackOnCollectedDelegate</span><span class="sxs-lookup"><span data-stu-id="094d3-116">callbackOnCollectedDelegate</span></span>](callbackoncollecteddelegate-mda.md)|[<span data-ttu-id="094d3-117">contextSwitchDeadlock</span><span class="sxs-lookup"><span data-stu-id="094d3-117">contextSwitchDeadlock</span></span>](contextswitchdeadlock-mda.md)|
|[<span data-ttu-id="094d3-118">dangerousThreadingAPI</span><span class="sxs-lookup"><span data-stu-id="094d3-118">dangerousThreadingAPI</span></span>](dangerousthreadingapi-mda.md)|[<span data-ttu-id="094d3-119">dateTimeInvalidLocalFormat</span><span class="sxs-lookup"><span data-stu-id="094d3-119">dateTimeInvalidLocalFormat</span></span>](datetimeinvalidlocalformat-mda.md)|
|[<span data-ttu-id="094d3-120">dirtyCastAndCallOnInterface</span><span class="sxs-lookup"><span data-stu-id="094d3-120">dirtyCastAndCallOnInterface</span></span>](dirtycastandcalloninterface-mda.md)|[<span data-ttu-id="094d3-121">disconnectedContext</span><span class="sxs-lookup"><span data-stu-id="094d3-121">disconnectedContext</span></span>](disconnectedcontext-mda.md)|
|[<span data-ttu-id="094d3-122">dllMainReturnsFalse</span><span class="sxs-lookup"><span data-stu-id="094d3-122">dllMainReturnsFalse</span></span>](dllmainreturnsfalse-mda.md)|[<span data-ttu-id="094d3-123">exceptionSwallowedOnCallFromCom</span><span class="sxs-lookup"><span data-stu-id="094d3-123">exceptionSwallowedOnCallFromCom</span></span>](exceptionswallowedoncallfromcom-mda.md)|
|[<span data-ttu-id="094d3-124">failedQI</span><span class="sxs-lookup"><span data-stu-id="094d3-124">failedQI</span></span>](failedqi-mda.md)|[<span data-ttu-id="094d3-125">fatalExecutionEngineError</span><span class="sxs-lookup"><span data-stu-id="094d3-125">fatalExecutionEngineError</span></span>](fatalexecutionengineerror-mda.md)|
|[<span data-ttu-id="094d3-126">gcManagedToUnmanaged</span><span class="sxs-lookup"><span data-stu-id="094d3-126">gcManagedToUnmanaged</span></span>](gcmanagedtounmanaged-mda.md)|[<span data-ttu-id="094d3-127">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="094d3-127">gcUnmanagedToManaged</span></span>](gcunmanagedtomanaged-mda.md)|
|[<span data-ttu-id="094d3-128">illegalPrepareConstrainedRegion</span><span class="sxs-lookup"><span data-stu-id="094d3-128">illegalPrepareConstrainedRegion</span></span>](illegalprepareconstrainedregion-mda.md)|[<span data-ttu-id="094d3-129">invalidApartmentStateChange</span><span class="sxs-lookup"><span data-stu-id="094d3-129">invalidApartmentStateChange</span></span>](invalidapartmentstatechange-mda.md)|
|[<span data-ttu-id="094d3-130">invalidCERCall</span><span class="sxs-lookup"><span data-stu-id="094d3-130">invalidCERCall</span></span>](invalidcercall-mda.md)|[<span data-ttu-id="094d3-131">invalidFunctionPointerInDelegate</span><span class="sxs-lookup"><span data-stu-id="094d3-131">invalidFunctionPointerInDelegate</span></span>](invalidfunctionpointerindelegate-mda.md)|
|[<span data-ttu-id="094d3-132">invalidGCHandleCookie</span><span class="sxs-lookup"><span data-stu-id="094d3-132">invalidGCHandleCookie</span></span>](invalidgchandlecookie-mda.md)|[<span data-ttu-id="094d3-133">invalidIUnknown</span><span class="sxs-lookup"><span data-stu-id="094d3-133">invalidIUnknown</span></span>](invalidiunknown-mda.md)|
|[<span data-ttu-id="094d3-134">invalidMemberDeclaration</span><span class="sxs-lookup"><span data-stu-id="094d3-134">invalidMemberDeclaration</span></span>](invalidmemberdeclaration-mda.md)|[<span data-ttu-id="094d3-135">invalidOverlappedToPinvoke</span><span class="sxs-lookup"><span data-stu-id="094d3-135">invalidOverlappedToPinvoke</span></span>](invalidoverlappedtopinvoke-mda.md)|
|[<span data-ttu-id="094d3-136">invalidVariant</span><span class="sxs-lookup"><span data-stu-id="094d3-136">invalidVariant</span></span>](invalidvariant-mda.md)|[<span data-ttu-id="094d3-137">jitCompilationStart</span><span class="sxs-lookup"><span data-stu-id="094d3-137">jitCompilationStart</span></span>](jitcompilationstart-mda.md)|
|[<span data-ttu-id="094d3-138">loaderLock</span><span class="sxs-lookup"><span data-stu-id="094d3-138">loaderLock</span></span>](loaderlock-mda.md)|[<span data-ttu-id="094d3-139">loadFromContext</span><span class="sxs-lookup"><span data-stu-id="094d3-139">loadFromContext</span></span>](loadfromcontext-mda.md)|
|[<span data-ttu-id="094d3-140">marshalCleanupError</span><span class="sxs-lookup"><span data-stu-id="094d3-140">marshalCleanupError</span></span>](marshalcleanuperror-mda.md)|[<span data-ttu-id="094d3-141">marshaling</span><span class="sxs-lookup"><span data-stu-id="094d3-141">marshaling</span></span>](marshaling-mda.md)|
|[<span data-ttu-id="094d3-142">memberInfoCacheCreation</span><span class="sxs-lookup"><span data-stu-id="094d3-142">memberInfoCacheCreation</span></span>](memberinfocachecreation-mda.md)|[<span data-ttu-id="094d3-143">moduloObjectHashcode</span><span class="sxs-lookup"><span data-stu-id="094d3-143">moduloObjectHashcode</span></span>](moduloobjecthashcode-mda.md)|
|[<span data-ttu-id="094d3-144">nonComVisibleBaseClass</span><span class="sxs-lookup"><span data-stu-id="094d3-144">nonComVisibleBaseClass</span></span>](noncomvisiblebaseclass-mda.md)|[<span data-ttu-id="094d3-145">notMarshalable</span><span class="sxs-lookup"><span data-stu-id="094d3-145">notMarshalable</span></span>](notmarshalable-mda.md)|
|[<span data-ttu-id="094d3-146">openGenericCERCall</span><span class="sxs-lookup"><span data-stu-id="094d3-146">openGenericCERCall</span></span>](opengenericcercall-mda.md)|[<span data-ttu-id="094d3-147">overlappedFreeError</span><span class="sxs-lookup"><span data-stu-id="094d3-147">overlappedFreeError</span></span>](overlappedfreeerror-mda.md)|
|[<span data-ttu-id="094d3-148">pInvokeLog</span><span class="sxs-lookup"><span data-stu-id="094d3-148">pInvokeLog</span></span>](pinvokelog-mda.md)|[<span data-ttu-id="094d3-149">pInvokeStackImbalance</span><span class="sxs-lookup"><span data-stu-id="094d3-149">pInvokeStackImbalance</span></span>](pinvokestackimbalance-mda.md)|
|[<span data-ttu-id="094d3-150">raceOnRCWCleanup</span><span class="sxs-lookup"><span data-stu-id="094d3-150">raceOnRCWCleanup</span></span>](raceonrcwcleanup-mda.md)|[<span data-ttu-id="094d3-151">współużytkowania wątkowości</span><span class="sxs-lookup"><span data-stu-id="094d3-151">reentrancy</span></span>](reentrancy-mda.md)|
|[<span data-ttu-id="094d3-152">releaseHandleFailed</span><span class="sxs-lookup"><span data-stu-id="094d3-152">releaseHandleFailed</span></span>](releasehandlefailed-mda.md)|[<span data-ttu-id="094d3-153">reportAvOnComRelease</span><span class="sxs-lookup"><span data-stu-id="094d3-153">reportAvOnComRelease</span></span>](reportavoncomrelease-mda.md)|
|[<span data-ttu-id="094d3-154">streamWriterBufferedDataLost</span><span class="sxs-lookup"><span data-stu-id="094d3-154">streamWriterBufferedDataLost</span></span>](streamwriterbuffereddatalost-mda.md)|[<span data-ttu-id="094d3-155">virtualCERCall</span><span class="sxs-lookup"><span data-stu-id="094d3-155">virtualCERCall</span></span>](virtualcercall-mda.md)|

<span data-ttu-id="094d3-156">Domyślnie .NET Framework aktywuje podzbiór MDA dla wszystkich zarządzanych debugerów.</span><span class="sxs-lookup"><span data-stu-id="094d3-156">By default, the .NET Framework activates a subset of MDAs for all managed debuggers.</span></span> <span data-ttu-id="094d3-157">Możesz wyświetlić domyślny zestaw w programie Visual Studio, wybierając pozycję **Windows**  >  **Ustawienia wyjątków** systemu Windows w menu **Debuguj** , a następnie rozwijając listę **asystentów debugowania zarządzanego** .</span><span class="sxs-lookup"><span data-stu-id="094d3-157">You can view the default set in Visual Studio by choosing **Windows** > **Exception Settings** on the **Debug** menu, and then expanding the **Managed Debugging Assistants** list.</span></span>

![Okno ustawień wyjątków w programie Visual Studio](./media/diagnosing-errors-with-managed-debugging-assistants/exception-settings-mdas.png)

## <a name="enable-and-disable-mdas"></a><span data-ttu-id="094d3-159">Włączanie i wyłączanie MDA</span><span class="sxs-lookup"><span data-stu-id="094d3-159">Enable and Disable MDAs</span></span>

<span data-ttu-id="094d3-160">MDA można włączać i wyłączać za pomocą klucza rejestru, zmiennej środowiskowej i ustawień konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="094d3-160">You can enable and disable MDAs by using a registry key, an environment variable, and application configuration settings.</span></span> <span data-ttu-id="094d3-161">Należy włączyć klucz rejestru lub zmienną środowiskową, aby użyć ustawień konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="094d3-161">You must enable either the registry key or the environment variable to use the application configuration settings.</span></span>

> [!TIP]
> <span data-ttu-id="094d3-162">Zamiast wyłączać MDA, można zapobiec wyświetlaniu przez program Visual Studio okna dialogowego MDA przy każdym odebraniu powiadomienia MDA.</span><span class="sxs-lookup"><span data-stu-id="094d3-162">Instead of disabling MDAs, you can prevent Visual Studio from displaying the MDA dialog box whenever an MDA notification is received.</span></span> <span data-ttu-id="094d3-163">W tym celu wybierz pozycję **Windows**  >  **Ustawienia wyjątków** systemu Windows w menu **debugowanie** , rozwiń listę **Asystenci debugowania zarządzanego** , a następnie zaznacz lub wyczyść pole wyboru **Przerwij, gdy zostanie zgłoszone dla pojedynczego przerzucania** .</span><span class="sxs-lookup"><span data-stu-id="094d3-163">To do that, choose **Windows** > **Exception Settings** on the **Debug** menu, expand the **Managed Debugging Assistants** list, and then select or clear the **Break When Thrown** check box for the individual MDA.</span></span>

### <a name="registry-key"></a><span data-ttu-id="094d3-164">Klucz rejestru</span><span class="sxs-lookup"><span data-stu-id="094d3-164">Registry Key</span></span>

<span data-ttu-id="094d3-165">Aby włączyć MDA, Dodaj **HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft \\ . Podklucz NETFramework\MDA** (typ REG_SZ, wartość 1) w rejestrze systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="094d3-165">To enable MDAs, add the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\MDA** subkey (type REG_SZ, value 1) in the Windows registry.</span></span> <span data-ttu-id="094d3-166">Skopiuj poniższy przykład do pliku tekstowego o nazwie *MDAEnable. reg*. Otwórz Edytor rejestru systemu Windows (RegEdit.exe), a następnie z menu **plik** wybierz pozycję **Importuj**.</span><span class="sxs-lookup"><span data-stu-id="094d3-166">Copy the following example into a text file named *MDAEnable.reg*. Open the Windows Registry Editor (RegEdit.exe), and from the **File** menu choose **Import**.</span></span> <span data-ttu-id="094d3-167">Wybierz plik *MDAEnable. reg* , aby włączyć MDA na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="094d3-167">Select the *MDAEnable.reg* file to enable MDAs on that computer.</span></span> <span data-ttu-id="094d3-168">Ustawienie podklucza do wartości ciągu **1** (nie wartość DWORD **1**) umożliwia odczytywanie ustawień MDA z pliku.mda.config *ApplicationName. sufiksu* .</span><span class="sxs-lookup"><span data-stu-id="094d3-168">Setting the subkey to string value of **1** (not DWORD value of **1**) enables the reading of MDA settings from the *ApplicationName.suffix*.mda.config file.</span></span> <span data-ttu-id="094d3-169">Na przykład plik konfiguracji MDA dla programu Notepad ma nazwę notepad.exe.mda.config.</span><span class="sxs-lookup"><span data-stu-id="094d3-169">For example, the MDA configuration file for Notepad would be named notepad.exe.mda.config.</span></span>

```text
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework]
"MDA"="1"
```

<span data-ttu-id="094d3-170">Jeśli na komputerze działa aplikacja 32-bitowa w 64-bitowym systemie operacyjnym, należy ustawić klucz MDA podobny do następującego:</span><span class="sxs-lookup"><span data-stu-id="094d3-170">If the computer is running a 32-bit application on a 64-bit operating system, then the MDA key should be set like the following:</span></span>

```text
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework]
"MDA"="1"
```

<span data-ttu-id="094d3-171">Aby uzyskać więcej informacji, zobacz [Ustawienia konfiguracji specyficzne dla aplikacji](#application-specific-configuration-settings) .</span><span class="sxs-lookup"><span data-stu-id="094d3-171">See [Application-Specific Configuration Settings](#application-specific-configuration-settings) for more information.</span></span> <span data-ttu-id="094d3-172">Ustawienie rejestru może być zastąpione przez zmienną środowiskową COMPLUS_MDA.</span><span class="sxs-lookup"><span data-stu-id="094d3-172">The registry setting can be overridden by the COMPLUS_MDA environment variable.</span></span> <span data-ttu-id="094d3-173">Aby uzyskać więcej informacji, zobacz [zmienna środowiskowa](#environment-variable) .</span><span class="sxs-lookup"><span data-stu-id="094d3-173">See [Environment Variable](#environment-variable) for more information.</span></span>

<span data-ttu-id="094d3-174">Aby wyłączyć MDA, ustaw podklucz MDA na **0** (zero) przy użyciu Edytora rejestru systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="094d3-174">To disable MDAs, set the MDA subkey to **0** (zero) using the Windows Registry Editor.</span></span>

<span data-ttu-id="094d3-175">Domyślnie niektóre MDA są włączane po uruchomieniu aplikacji dołączonej do debugera, nawet bez dodawania klucza rejestru.</span><span class="sxs-lookup"><span data-stu-id="094d3-175">By default, some MDAs are enabled when you run an application that is attached to a debugger, even without adding the registry key.</span></span> <span data-ttu-id="094d3-176">Te Asystenci można wyłączyć, uruchamiając plik *MDADisable. reg* zgodnie z wcześniejszym opisem w tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="094d3-176">You can disable these assistants by running the *MDADisable.reg* file as described earlier in this section.</span></span>

### <a name="environment-variable"></a><span data-ttu-id="094d3-177">Zmienna środowiskowa</span><span class="sxs-lookup"><span data-stu-id="094d3-177">Environment Variable</span></span>

<span data-ttu-id="094d3-178">Aktywację MDA można również kontrolować przy użyciu zmiennej środowiskowej COMPLUS_MDA, która zastępuje klucz rejestru.</span><span class="sxs-lookup"><span data-stu-id="094d3-178">MDA activation can also controlled by the environment variable COMPLUS_MDA, which overrides the registry key.</span></span> <span data-ttu-id="094d3-179">Ciąg COMPLUS_MDA to rozdzielana średnikami lista nazw MDA lub innych specjalnych ciągów sterujących.</span><span class="sxs-lookup"><span data-stu-id="094d3-179">The COMPLUS_MDA string is a case-insensitive, semicolon-delimited list of MDA names or other special control strings.</span></span> <span data-ttu-id="094d3-180">Uruchomienie w debugerze zarządzanym lub niezarządzanym domyślnie włącza zestaw MDA.</span><span class="sxs-lookup"><span data-stu-id="094d3-180">Starting under a managed or unmanaged debugger enables a set of MDAs by default.</span></span> <span data-ttu-id="094d3-181">Jest to realizowane przez niejawnie oczekującą listę rozdzielonych średnikami MDA włączonych domyślnie w obszarze debugery do wartości zmiennej środowiskowej lub klucza rejestru.</span><span class="sxs-lookup"><span data-stu-id="094d3-181">This is done by implicitly prepending the semicolon-delimited list of MDAs enabled by default under debuggers to the value of the environment variable or registry key.</span></span> <span data-ttu-id="094d3-182">Specjalne ciągi sterujące są następujące:</span><span class="sxs-lookup"><span data-stu-id="094d3-182">The special control strings are the following:</span></span>

- <span data-ttu-id="094d3-183">`0`— Dezaktywuje wszystkie MDA.</span><span class="sxs-lookup"><span data-stu-id="094d3-183">`0` - Deactivates all MDAs.</span></span>

- <span data-ttu-id="094d3-184">`1`-Odczytuje ustawienia MDA z *ApplicationName*.mda.config.</span><span class="sxs-lookup"><span data-stu-id="094d3-184">`1` - Reads MDA settings from *ApplicationName*.mda.config.</span></span>

- <span data-ttu-id="094d3-185">`managedDebugger`— Jawnie aktywuje wszystkie MDA, które są niejawnie aktywowane, gdy zarządzany plik wykonywalny jest uruchamiany w debugerze.</span><span class="sxs-lookup"><span data-stu-id="094d3-185">`managedDebugger` - Explicitly activates all MDAs that are implicitly activated when a managed executable is started under a debugger.</span></span>

- <span data-ttu-id="094d3-186">`unmanagedDebugger`— Jawnie aktywuje wszystkie MDA, które są niejawnie aktywowane, gdy niezarządzany plik wykonywalny jest uruchamiany w debugerze.</span><span class="sxs-lookup"><span data-stu-id="094d3-186">`unmanagedDebugger` - Explicitly activates all MDAs that are implicitly activated when an unmanaged executable is started under a debugger.</span></span>

<span data-ttu-id="094d3-187">Jeśli istnieją jakieś ustawienia powodujące konflikt, ostatnie ustawienia zastępują poprzednie ustawienia:</span><span class="sxs-lookup"><span data-stu-id="094d3-187">If there are conflicting settings, the most recent settings override previous settings:</span></span>

- <span data-ttu-id="094d3-188">`COMPLUS_MDA=0`wyłącza wszystkie MDA, włącznie z niejawnie włączonymi w debugerze.</span><span class="sxs-lookup"><span data-stu-id="094d3-188">`COMPLUS_MDA=0` disables all MDAs, including those implicitly enabled under a debugger.</span></span>

- <span data-ttu-id="094d3-189">`COMPLUS_MDA=gcUnmanagedToManaged`Włącza `gcUnmanagedToManaged` dodatek do wszystkich MDA, które są niejawnie włączone w debugerze.</span><span class="sxs-lookup"><span data-stu-id="094d3-189">`COMPLUS_MDA=gcUnmanagedToManaged` enables `gcUnmanagedToManaged` in addition to any MDAs that are implicitly enabled under a debugger.</span></span>

- <span data-ttu-id="094d3-190">`COMPLUS_MDA=0;gcUnmanagedToManaged`Włącza `gcUnmanagedToManaged` , ale wyłącza MDA, które w przeciwnym razie byłyby niejawnie włączone w debugerze.</span><span class="sxs-lookup"><span data-stu-id="094d3-190">`COMPLUS_MDA=0;gcUnmanagedToManaged` enables `gcUnmanagedToManaged` but disables MDAs that would otherwise be implicitly enabled under a debugger.</span></span>

### <a name="application-specific-configuration-settings"></a><span data-ttu-id="094d3-191">Ustawienia konfiguracji specyficzne dla aplikacji</span><span class="sxs-lookup"><span data-stu-id="094d3-191">Application-Specific Configuration Settings</span></span>

<span data-ttu-id="094d3-192">Niektóre Asystenci można włączać, wyłączać i konfigurować pojedynczo w pliku konfiguracji MDA dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="094d3-192">You can enable, disable, and configure some assistants individually in the MDA configuration file for the application.</span></span> <span data-ttu-id="094d3-193">Aby umożliwić korzystanie z pliku konfiguracji aplikacji do konfigurowania MDA, należy ustawić klucz rejestru MDA lub zmienną środowiskową COMPLUS_MDA.</span><span class="sxs-lookup"><span data-stu-id="094d3-193">To enable the use of an application configuration file for configuring MDAs, either the MDA registry key or the COMPLUS_MDA environment variable must be set.</span></span> <span data-ttu-id="094d3-194">Plik konfiguracji aplikacji zwykle znajduje się w tym samym katalogu, co plik wykonywalny (exe) aplikacji.</span><span class="sxs-lookup"><span data-stu-id="094d3-194">The application configuration file is typically located in the same directory as the application's executable (.exe) file.</span></span> <span data-ttu-id="094d3-195">Nazwa pliku przyjmuje postać *ApplicationName*.mda.config; na przykład notepad.exe.mda.config. Asystenci, którzy są włączeni w pliku konfiguracji aplikacji, mogą mieć atrybuty lub elementy zaprojektowane specjalnie pod kątem kontrolowania zachowania tego asystenta.</span><span class="sxs-lookup"><span data-stu-id="094d3-195">The file name takes the form *ApplicationName*.mda.config; for example, notepad.exe.mda.config. Assistants that are enabled in the application configuration file may have attributes or elements specifically designed to control that assistant's behavior.</span></span>

<span data-ttu-id="094d3-196">Poniższy przykład pokazuje, jak włączyć i skonfigurować [kierowanie](marshaling-mda.md):</span><span class="sxs-lookup"><span data-stu-id="094d3-196">The following example shows how to enable and configure the [marshaling](marshaling-mda.md):</span></span>

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

<span data-ttu-id="094d3-197">`Marshaling`MDA emituje informacje o zarządzanym typie, który jest przekazywany do niezarządzanego typu dla każdego przejścia zarządzanego do niezarządzanego w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="094d3-197">The `Marshaling` MDA emits information about the managed type that is being marshaled to an unmanaged type for each managed-to-unmanaged transition in the application.</span></span> <span data-ttu-id="094d3-198">`Marshaling`MDA może również filtrować nazwy metod i pól struktury dostarczonych odpowiednio w elementach podrzędnych **MethodFilter** i **fieldFilter** .</span><span class="sxs-lookup"><span data-stu-id="094d3-198">The `Marshaling` MDA can also filter the names of the method and structure fields supplied in the **methodFilter** and **fieldFilter** child elements, respectively.</span></span>

<span data-ttu-id="094d3-199">Poniższy przykład pokazuje, jak włączyć wiele MDA przy użyciu ich ustawień domyślnych:</span><span class="sxs-lookup"><span data-stu-id="094d3-199">The following example shows how to enable multiple MDAs by using their default settings:</span></span>

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
> <span data-ttu-id="094d3-200">W przypadku określenia więcej niż jednego asystenta w pliku konfiguracji należy je wyświetlić w kolejności alfabetycznej.</span><span class="sxs-lookup"><span data-stu-id="094d3-200">When you specify more than one assistant in a configuration file, you must list them in alphabetical order.</span></span> <span data-ttu-id="094d3-201">Na przykład, jeśli chcesz włączyć zarówno obiekt, `virtualCERCall` jak i `invalidCERCall` MDA, należy dodać `<invalidCERCall />` wpis przed `<virtualCERCall />` wpisem.</span><span class="sxs-lookup"><span data-stu-id="094d3-201">For example, if you want to enable both the `virtualCERCall` and the `invalidCERCall` MDAs, you must add the `<invalidCERCall />` entry before the `<virtualCERCall />` entry.</span></span> <span data-ttu-id="094d3-202">Jeśli wpisy nie są w kolejności alfabetycznej, zostanie wyświetlony nieobsługiwany komunikat wyjątku pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="094d3-202">If the entries are not in alphabetical order, an unhandled invalid configuration file exception message is displayed.</span></span>

## <a name="mda-exceptions"></a><span data-ttu-id="094d3-203">Wyjątki MDA</span><span class="sxs-lookup"><span data-stu-id="094d3-203">MDA exceptions</span></span>

<span data-ttu-id="094d3-204">Gdy zdarzenie MDA jest włączone, jest aktywne nawet wtedy, gdy kod nie jest wykonywany w debugerze.</span><span class="sxs-lookup"><span data-stu-id="094d3-204">When an MDA is enabled, it's active even when your code is not executing under a debugger.</span></span> <span data-ttu-id="094d3-205">Jeśli zdarzenie MDA jest zgłaszane, gdy debuger nie jest obecny, komunikat o zdarzeniu jest wyświetlany w oknie dialogowym nieobsłużonego wyjątku, chociaż nie jest to nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="094d3-205">If an MDA event is raised when a debugger is not present, the event message is presented in an unhandled exception dialog box, although it is not an unhandled exception.</span></span> <span data-ttu-id="094d3-206">Aby uniknąć tego okna dialogowego, Usuń ustawienia włączania MDA, gdy kod nie jest wykonywany w środowisku debugowania.</span><span class="sxs-lookup"><span data-stu-id="094d3-206">To avoid the dialog box, remove the MDA-enabling settings when your code is not executing in a debugging environment.</span></span>

<span data-ttu-id="094d3-207">Gdy kod jest wykonywany w zintegrowanym środowisku programistycznym (IDE) programu Visual Studio, można uniknąć okna dialogowego wyjątek, które pojawia się dla określonych zdarzeń MDA.</span><span class="sxs-lookup"><span data-stu-id="094d3-207">When your code executes in the Visual Studio integrated development environment (IDE), you can avoid the exception dialog box that appears for specific MDA events.</span></span> <span data-ttu-id="094d3-208">W tym celu w menu **Debuguj** wybierz pozycję Ustawienia wyjątków **systemu Windows**  >  **Exception Settings**.</span><span class="sxs-lookup"><span data-stu-id="094d3-208">To do that, on the **Debug** menu, choose **Windows** > **Exception Settings**.</span></span> <span data-ttu-id="094d3-209">W oknie **Ustawienia wyjątku** rozwiń listę **Asystenci debugowania zarządzanego** , a następnie usuń zaznaczenie pola wyboru Przerwij, **gdy zostanie zgłoszone** dla pojedynczego elementu MDA.</span><span class="sxs-lookup"><span data-stu-id="094d3-209">In the **Exception Settings** window, expand the **Managed Debugging Assistants** list, and then clear the **Break When Thrown** check box for the individual MDA.</span></span> <span data-ttu-id="094d3-210">Tego okna dialogowego można także użyć, aby *włączyć* wyświetlanie okien dialogowych wyjątków MDA.</span><span class="sxs-lookup"><span data-stu-id="094d3-210">You can also use this dialog box to *enable* the display of MDA exception dialog boxes.</span></span>

## <a name="mda-output"></a><span data-ttu-id="094d3-211">Wyjście MDA</span><span class="sxs-lookup"><span data-stu-id="094d3-211">MDA Output</span></span>

<span data-ttu-id="094d3-212">Dane wyjściowe MDA są podobne do poniższego przykładu, który wyświetla dane wyjściowe z `PInvokeStackImbalance` MDA:</span><span class="sxs-lookup"><span data-stu-id="094d3-212">MDA output is similar to the following example, which shows the output from the `PInvokeStackImbalance` MDA:</span></span>

<span data-ttu-id="094d3-213">**Wywołanie funkcji PInvoke "MDATest! MDATest. program:: StdCall ' ma niezrównoważony stos. Prawdopodobnie jest to spowodowane tym, że zarządzana sygnatura PInvoke nie jest zgodna z niezarządzanym podpisem docelowym. Sprawdź, czy Konwencja wywoływania i parametry sygnatury PInvoke pasują do docelowego podpisu niezarządzanego.**</span><span class="sxs-lookup"><span data-stu-id="094d3-213">**A call to PInvoke function 'MDATest!MDATest.Program::StdCall' has unbalanced the stack. This is likely because the managed PInvoke signature does not match the unmanaged target signature. Check that the calling convention and parameters of the PInvoke signature match the target unmanaged signature.**</span></span>

## <a name="see-also"></a><span data-ttu-id="094d3-214">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="094d3-214">See also</span></span>

- [<span data-ttu-id="094d3-215">Debugowanie, śledzenie i profilowanie</span><span class="sxs-lookup"><span data-stu-id="094d3-215">Debugging, Tracing, and Profiling</span></span>](index.md)
