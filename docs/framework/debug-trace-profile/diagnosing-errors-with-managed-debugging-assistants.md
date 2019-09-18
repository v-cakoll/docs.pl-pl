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
ms.openlocfilehash: 6cb2a240a2e7e82b7015eb7a6d99c2117fa63045
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052900"
---
# <a name="diagnose-errors-with-managed-debugging-assistants"></a><span data-ttu-id="491b9-102">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="491b9-102">Diagnose Errors with Managed Debugging Assistants</span></span>

<span data-ttu-id="491b9-103">Zarządzane Asystenci debugowania (MDA) to pomoce debugowania, które działają w połączeniu ze środowiskiem uruchomieniowym języka wspólnego (CLR) w celu zapewnienia informacji o stanie środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="491b9-103">Managed debugging assistants (MDAs) are debugging aids that work in conjunction with the common language runtime (CLR) to provide information on runtime state.</span></span> <span data-ttu-id="491b9-104">Asystenci generują komunikaty informacyjne dotyczące zdarzeń środowiska uruchomieniowego, które nie mogą być pułapki w przeciwnym razie.</span><span class="sxs-lookup"><span data-stu-id="491b9-104">The assistants generate informational messages about runtime events that you cannot otherwise trap.</span></span> <span data-ttu-id="491b9-105">Możesz użyć MDA, aby wyizolować trudne do znalezienia usterki aplikacji występujące podczas przechodzenia między kodem zarządzanym i niezarządzanym.</span><span class="sxs-lookup"><span data-stu-id="491b9-105">You can use MDAs to isolate hard-to-find application bugs that occur when transitioning between managed and unmanaged code.</span></span>

<span data-ttu-id="491b9-106">Możesz [włączyć lub wyłączyć](#enable-and-disable-mdas) wszystkie MDA przez dodanie klucza do rejestru systemu Windows lub przez ustawienie zmiennej środowiskowej.</span><span class="sxs-lookup"><span data-stu-id="491b9-106">You can [enable or disable](#enable-and-disable-mdas) all MDAs by adding a key to the Windows registry or by setting an environment variable.</span></span> <span data-ttu-id="491b9-107">Konkretne MDA można włączyć za pomocą ustawień konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="491b9-107">You can enable specific MDAs by using application configuration settings.</span></span> <span data-ttu-id="491b9-108">Można ustawić dodatkowe ustawienia konfiguracji dla niektórych pojedynczych MDA w pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="491b9-108">You can set additional configuration settings for some individual MDAs in the application's configuration file.</span></span> <span data-ttu-id="491b9-109">Ponieważ te pliki konfiguracji są analizowane podczas ładowania środowiska uruchomieniowego, przed uruchomieniem aplikacji zarządzanej należy włączyć funkcję MDA.</span><span class="sxs-lookup"><span data-stu-id="491b9-109">Because these configuration files are parsed when the runtime is loaded, you must enable the MDA before the managed application starts.</span></span> <span data-ttu-id="491b9-110">Nie można go włączyć dla aplikacji, które zostały już uruchomione.</span><span class="sxs-lookup"><span data-stu-id="491b9-110">You cannot enable it for applications that have already started.</span></span>

<span data-ttu-id="491b9-111">Poniższa tabela zawiera listę MDA, które są dostarczane z .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="491b9-111">The following table lists the MDAs that ship with the .NET Framework:</span></span>

|||
|-|-|
|[<span data-ttu-id="491b9-112">asynchronousThreadAbort</span><span class="sxs-lookup"><span data-stu-id="491b9-112">asynchronousThreadAbort</span></span>](asynchronousthreadabort-mda.md)|[<span data-ttu-id="491b9-113">bindingFailure</span><span class="sxs-lookup"><span data-stu-id="491b9-113">bindingFailure</span></span>](bindingfailure-mda.md)|
|[<span data-ttu-id="491b9-114">callbackOnCollectedDelegate</span><span class="sxs-lookup"><span data-stu-id="491b9-114">callbackOnCollectedDelegate</span></span>](callbackoncollecteddelegate-mda.md)|[<span data-ttu-id="491b9-115">contextSwitchDeadlock</span><span class="sxs-lookup"><span data-stu-id="491b9-115">contextSwitchDeadlock</span></span>](contextswitchdeadlock-mda.md)|
|[<span data-ttu-id="491b9-116">dangerousThreadingAPI</span><span class="sxs-lookup"><span data-stu-id="491b9-116">dangerousThreadingAPI</span></span>](dangerousthreadingapi-mda.md)|[<span data-ttu-id="491b9-117">dateTimeInvalidLocalFormat</span><span class="sxs-lookup"><span data-stu-id="491b9-117">dateTimeInvalidLocalFormat</span></span>](datetimeinvalidlocalformat-mda.md)|
|[<span data-ttu-id="491b9-118">dirtyCastAndCallOnInterface</span><span class="sxs-lookup"><span data-stu-id="491b9-118">dirtyCastAndCallOnInterface</span></span>](dirtycastandcalloninterface-mda.md)|[<span data-ttu-id="491b9-119">disconnectedContext</span><span class="sxs-lookup"><span data-stu-id="491b9-119">disconnectedContext</span></span>](disconnectedcontext-mda.md)|
|[<span data-ttu-id="491b9-120">dllMainReturnsFalse</span><span class="sxs-lookup"><span data-stu-id="491b9-120">dllMainReturnsFalse</span></span>](dllmainreturnsfalse-mda.md)|[<span data-ttu-id="491b9-121">exceptionSwallowedOnCallFromCom</span><span class="sxs-lookup"><span data-stu-id="491b9-121">exceptionSwallowedOnCallFromCom</span></span>](exceptionswallowedoncallfromcom-mda.md)|
|[<span data-ttu-id="491b9-122">failedQI</span><span class="sxs-lookup"><span data-stu-id="491b9-122">failedQI</span></span>](failedqi-mda.md)|[<span data-ttu-id="491b9-123">fatalExecutionEngineError</span><span class="sxs-lookup"><span data-stu-id="491b9-123">fatalExecutionEngineError</span></span>](fatalexecutionengineerror-mda.md)|
|[<span data-ttu-id="491b9-124">gcManagedToUnmanaged</span><span class="sxs-lookup"><span data-stu-id="491b9-124">gcManagedToUnmanaged</span></span>](gcmanagedtounmanaged-mda.md)|[<span data-ttu-id="491b9-125">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="491b9-125">gcUnmanagedToManaged</span></span>](gcunmanagedtomanaged-mda.md)|
|[<span data-ttu-id="491b9-126">illegalPrepareConstrainedRegion</span><span class="sxs-lookup"><span data-stu-id="491b9-126">illegalPrepareConstrainedRegion</span></span>](illegalprepareconstrainedregion-mda.md)|[<span data-ttu-id="491b9-127">invalidApartmentStateChange</span><span class="sxs-lookup"><span data-stu-id="491b9-127">invalidApartmentStateChange</span></span>](invalidapartmentstatechange-mda.md)|
|[<span data-ttu-id="491b9-128">invalidCERCall</span><span class="sxs-lookup"><span data-stu-id="491b9-128">invalidCERCall</span></span>](invalidcercall-mda.md)|[<span data-ttu-id="491b9-129">invalidFunctionPointerInDelegate</span><span class="sxs-lookup"><span data-stu-id="491b9-129">invalidFunctionPointerInDelegate</span></span>](invalidfunctionpointerindelegate-mda.md)|
|[<span data-ttu-id="491b9-130">invalidGCHandleCookie</span><span class="sxs-lookup"><span data-stu-id="491b9-130">invalidGCHandleCookie</span></span>](invalidgchandlecookie-mda.md)|[<span data-ttu-id="491b9-131">invalidIUnknown</span><span class="sxs-lookup"><span data-stu-id="491b9-131">invalidIUnknown</span></span>](invalidiunknown-mda.md)|
|[<span data-ttu-id="491b9-132">invalidMemberDeclaration</span><span class="sxs-lookup"><span data-stu-id="491b9-132">invalidMemberDeclaration</span></span>](invalidmemberdeclaration-mda.md)|[<span data-ttu-id="491b9-133">invalidOverlappedToPinvoke</span><span class="sxs-lookup"><span data-stu-id="491b9-133">invalidOverlappedToPinvoke</span></span>](invalidoverlappedtopinvoke-mda.md)|
|[<span data-ttu-id="491b9-134">invalidVariant</span><span class="sxs-lookup"><span data-stu-id="491b9-134">invalidVariant</span></span>](invalidvariant-mda.md)|[<span data-ttu-id="491b9-135">jitCompilationStart</span><span class="sxs-lookup"><span data-stu-id="491b9-135">jitCompilationStart</span></span>](jitcompilationstart-mda.md)|
|[<span data-ttu-id="491b9-136">loaderLock</span><span class="sxs-lookup"><span data-stu-id="491b9-136">loaderLock</span></span>](loaderlock-mda.md)|[<span data-ttu-id="491b9-137">loadFromContext</span><span class="sxs-lookup"><span data-stu-id="491b9-137">loadFromContext</span></span>](loadfromcontext-mda.md)|
|[<span data-ttu-id="491b9-138">marshalCleanupError</span><span class="sxs-lookup"><span data-stu-id="491b9-138">marshalCleanupError</span></span>](marshalcleanuperror-mda.md)|[<span data-ttu-id="491b9-139">marshaling</span><span class="sxs-lookup"><span data-stu-id="491b9-139">marshaling</span></span>](marshaling-mda.md)|
|[<span data-ttu-id="491b9-140">memberInfoCacheCreation</span><span class="sxs-lookup"><span data-stu-id="491b9-140">memberInfoCacheCreation</span></span>](memberinfocachecreation-mda.md)|[<span data-ttu-id="491b9-141">moduloObjectHashcode</span><span class="sxs-lookup"><span data-stu-id="491b9-141">moduloObjectHashcode</span></span>](moduloobjecthashcode-mda.md)|
|[<span data-ttu-id="491b9-142">nonComVisibleBaseClass</span><span class="sxs-lookup"><span data-stu-id="491b9-142">nonComVisibleBaseClass</span></span>](noncomvisiblebaseclass-mda.md)|[<span data-ttu-id="491b9-143">notMarshalable</span><span class="sxs-lookup"><span data-stu-id="491b9-143">notMarshalable</span></span>](notmarshalable-mda.md)|
|[<span data-ttu-id="491b9-144">openGenericCERCall</span><span class="sxs-lookup"><span data-stu-id="491b9-144">openGenericCERCall</span></span>](opengenericcercall-mda.md)|[<span data-ttu-id="491b9-145">overlappedFreeError</span><span class="sxs-lookup"><span data-stu-id="491b9-145">overlappedFreeError</span></span>](overlappedfreeerror-mda.md)|
|[<span data-ttu-id="491b9-146">pInvokeLog</span><span class="sxs-lookup"><span data-stu-id="491b9-146">pInvokeLog</span></span>](pinvokelog-mda.md)|[<span data-ttu-id="491b9-147">pInvokeStackImbalance</span><span class="sxs-lookup"><span data-stu-id="491b9-147">pInvokeStackImbalance</span></span>](pinvokestackimbalance-mda.md)|
|[<span data-ttu-id="491b9-148">raceOnRCWCleanup</span><span class="sxs-lookup"><span data-stu-id="491b9-148">raceOnRCWCleanup</span></span>](raceonrcwcleanup-mda.md)|[<span data-ttu-id="491b9-149">reentrancy</span><span class="sxs-lookup"><span data-stu-id="491b9-149">reentrancy</span></span>](reentrancy-mda.md)|
|[<span data-ttu-id="491b9-150">releaseHandleFailed</span><span class="sxs-lookup"><span data-stu-id="491b9-150">releaseHandleFailed</span></span>](releasehandlefailed-mda.md)|[<span data-ttu-id="491b9-151">reportAvOnComRelease</span><span class="sxs-lookup"><span data-stu-id="491b9-151">reportAvOnComRelease</span></span>](reportavoncomrelease-mda.md)|
|[<span data-ttu-id="491b9-152">streamWriterBufferedDataLost</span><span class="sxs-lookup"><span data-stu-id="491b9-152">streamWriterBufferedDataLost</span></span>](streamwriterbuffereddatalost-mda.md)|[<span data-ttu-id="491b9-153">virtualCERCall</span><span class="sxs-lookup"><span data-stu-id="491b9-153">virtualCERCall</span></span>](virtualcercall-mda.md)|

<span data-ttu-id="491b9-154">Domyślnie .NET Framework aktywuje podzbiór MDA dla wszystkich zarządzanych debugerów.</span><span class="sxs-lookup"><span data-stu-id="491b9-154">By default, the .NET Framework activates a subset of MDAs for all managed debuggers.</span></span> <span data-ttu-id="491b9-155">Możesz wyświetlić domyślny zestaw w programie Visual Studio, wybierając pozycję**Ustawienia wyjątków** **systemu Windows** > w menu **Debuguj** , a następnie rozwijając listę **asystentów debugowania zarządzanego** .</span><span class="sxs-lookup"><span data-stu-id="491b9-155">You can view the default set in Visual Studio by choosing **Windows** > **Exception Settings** on the **Debug** menu, and then expanding the **Managed Debugging Assistants** list.</span></span>

![Okno ustawień wyjątków w programie Visual Studio](./media/diagnosing-errors-with-managed-debugging-assistants/exception-settings-mdas.png)

## <a name="enable-and-disable-mdas"></a><span data-ttu-id="491b9-157">Włączanie i wyłączanie MDA</span><span class="sxs-lookup"><span data-stu-id="491b9-157">Enable and Disable MDAs</span></span>

<span data-ttu-id="491b9-158">MDA można włączać i wyłączać za pomocą klucza rejestru, zmiennej środowiskowej i ustawień konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="491b9-158">You can enable and disable MDAs by using a registry key, an environment variable, and application configuration settings.</span></span> <span data-ttu-id="491b9-159">Należy włączyć klucz rejestru lub zmienną środowiskową, aby użyć ustawień konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="491b9-159">You must enable either the registry key or the environment variable to use the application configuration settings.</span></span>

> [!TIP]
> <span data-ttu-id="491b9-160">Zamiast wyłączać MDA, można zapobiec wyświetlaniu przez program Visual Studio okna dialogowego MDA przy każdym odebraniu powiadomienia MDA.</span><span class="sxs-lookup"><span data-stu-id="491b9-160">Instead of disabling MDAs, you can prevent Visual Studio from displaying the MDA dialog box whenever an MDA notification is received.</span></span> <span data-ttu-id="491b9-161">W tym celu wybierz pozycję**Ustawienia wyjątków** **systemu Windows** > w menu **debugowanie** , rozwiń listę **Asystenci debugowania zarządzanego** , a następnie zaznacz lub wyczyść pole wyboru **Przerwij, gdy zostanie zgłoszone dla pojedynczego przerzucania** .</span><span class="sxs-lookup"><span data-stu-id="491b9-161">To do that, choose **Windows** > **Exception Settings** on the **Debug** menu, expand the **Managed Debugging Assistants** list, and then select or clear the **Break When Thrown** check box for the individual MDA.</span></span>

### <a name="registry-key"></a><span data-ttu-id="491b9-162">Klucz rejestru</span><span class="sxs-lookup"><span data-stu-id="491b9-162">Registry Key</span></span>

<span data-ttu-id="491b9-163">Aby włączyć MDA, Dodaj **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. Podklucz NETFramework\MDA** (typ REG_SZ, wartość 1) w rejestrze systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="491b9-163">To enable MDAs, add the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\MDA** subkey (type REG_SZ, value 1) in the Windows registry.</span></span> <span data-ttu-id="491b9-164">Skopiuj poniższy przykład do pliku tekstowego o nazwie *MDAEnable. reg*. Otwórz Edytor rejestru systemu Windows (regedit. exe), a następnie z menu **plik** wybierz pozycję **Importuj**.</span><span class="sxs-lookup"><span data-stu-id="491b9-164">Copy the following example into a text file named *MDAEnable.reg*. Open the Windows Registry Editor (RegEdit.exe), and from the **File** menu choose **Import**.</span></span> <span data-ttu-id="491b9-165">Wybierz plik *MDAEnable. reg* , aby włączyć MDA na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="491b9-165">Select the *MDAEnable.reg* file to enable MDAs on that computer.</span></span> <span data-ttu-id="491b9-166">Ustawienie podklucza do wartości ciągu **1** (wartość nietypu DWORD **1**) umożliwia odczytywanie ustawień programu MDA z pliku *ApplicationName.* config.</span><span class="sxs-lookup"><span data-stu-id="491b9-166">Setting the subkey to string value of **1** (not DWORD value of **1**) enables the reading of MDA settings from the *ApplicationName.suffix*.mda.config file.</span></span> <span data-ttu-id="491b9-167">Na przykład plik konfiguracji MDA dla programu Notepad ma nazwę Notepad. exe. MDA. config.</span><span class="sxs-lookup"><span data-stu-id="491b9-167">For example, the MDA configuration file for Notepad would be named notepad.exe.mda.config.</span></span>

```text
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework]
"MDA"="1"
```

<span data-ttu-id="491b9-168">Jeśli na komputerze działa aplikacja 32-bitowa w 64-bitowym systemie operacyjnym, należy ustawić klucz MDA podobny do następującego:</span><span class="sxs-lookup"><span data-stu-id="491b9-168">If the computer is running a 32-bit application on a 64-bit operating system, then the MDA key should be set like the following:</span></span>

```text
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework]
"MDA"="1"
```

<span data-ttu-id="491b9-169">Aby uzyskać więcej informacji, zobacz [Ustawienia konfiguracji specyficzne dla aplikacji](#application-specific-configuration-settings) .</span><span class="sxs-lookup"><span data-stu-id="491b9-169">See [Application-Specific Configuration Settings](#application-specific-configuration-settings) for more information.</span></span> <span data-ttu-id="491b9-170">Ustawienie rejestru może być zastąpione przez zmienną środowiskową COMPLUS_MDA.</span><span class="sxs-lookup"><span data-stu-id="491b9-170">The registry setting can be overridden by the COMPLUS_MDA environment variable.</span></span> <span data-ttu-id="491b9-171">Aby uzyskać więcej informacji, zobacz [zmienna środowiskowa](#environment-variable) .</span><span class="sxs-lookup"><span data-stu-id="491b9-171">See [Environment Variable](#environment-variable) for more information.</span></span>

<span data-ttu-id="491b9-172">Aby wyłączyć MDA, ustaw podklucz MDA na **0** (zero) przy użyciu Edytora rejestru systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="491b9-172">To disable MDAs, set the MDA subkey to **0** (zero) using the Windows Registry Editor.</span></span>

<span data-ttu-id="491b9-173">Domyślnie niektóre MDA są włączane po uruchomieniu aplikacji dołączonej do debugera, nawet bez dodawania klucza rejestru.</span><span class="sxs-lookup"><span data-stu-id="491b9-173">By default, some MDAs are enabled when you run an application that is attached to a debugger, even without adding the registry key.</span></span> <span data-ttu-id="491b9-174">Te Asystenci można wyłączyć, uruchamiając plik *MDADisable. reg* zgodnie z wcześniejszym opisem w tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="491b9-174">You can disable these assistants by running the *MDADisable.reg* file as described earlier in this section.</span></span>

### <a name="environment-variable"></a><span data-ttu-id="491b9-175">Zmienna środowiskowa</span><span class="sxs-lookup"><span data-stu-id="491b9-175">Environment Variable</span></span>

<span data-ttu-id="491b9-176">Aktywację MDA można również kontrolować przy użyciu zmiennej środowiskowej COMPLUS_MDA, która zastępuje klucz rejestru.</span><span class="sxs-lookup"><span data-stu-id="491b9-176">MDA activation can also controlled by the environment variable COMPLUS_MDA, which overrides the registry key.</span></span> <span data-ttu-id="491b9-177">Ciąg COMPLUS_MDA to rozdzielana średnikami lista nazw MDA lub innych specjalnych ciągów sterujących.</span><span class="sxs-lookup"><span data-stu-id="491b9-177">The COMPLUS_MDA string is a case-insensitive, semicolon-delimited list of MDA names or other special control strings.</span></span> <span data-ttu-id="491b9-178">Uruchomienie w debugerze zarządzanym lub niezarządzanym domyślnie włącza zestaw MDA.</span><span class="sxs-lookup"><span data-stu-id="491b9-178">Starting under a managed or unmanaged debugger enables a set of MDAs by default.</span></span> <span data-ttu-id="491b9-179">Jest to realizowane przez niejawnie oczekującą listę rozdzielonych średnikami MDA włączonych domyślnie w obszarze debugery do wartości zmiennej środowiskowej lub klucza rejestru.</span><span class="sxs-lookup"><span data-stu-id="491b9-179">This is done by implicitly prepending the semicolon-delimited list of MDAs enabled by default under debuggers to the value of the environment variable or registry key.</span></span> <span data-ttu-id="491b9-180">Specjalne ciągi sterujące są następujące:</span><span class="sxs-lookup"><span data-stu-id="491b9-180">The special control strings are the following:</span></span>

- <span data-ttu-id="491b9-181">`0`— Dezaktywuje wszystkie MDA.</span><span class="sxs-lookup"><span data-stu-id="491b9-181">`0` - Deactivates all MDAs.</span></span>

- <span data-ttu-id="491b9-182">`1`-Odczytuje ustawienia MDA z pliku *ApplicationName*. MDA. config.</span><span class="sxs-lookup"><span data-stu-id="491b9-182">`1` - Reads MDA settings from *ApplicationName*.mda.config.</span></span>

- <span data-ttu-id="491b9-183">`managedDebugger`— Jawnie aktywuje wszystkie MDA, które są niejawnie aktywowane, gdy zarządzany plik wykonywalny jest uruchamiany w debugerze.</span><span class="sxs-lookup"><span data-stu-id="491b9-183">`managedDebugger` - Explicitly activates all MDAs that are implicitly activated when a managed executable is started under a debugger.</span></span>

- <span data-ttu-id="491b9-184">`unmanagedDebugger`— Jawnie aktywuje wszystkie MDA, które są niejawnie aktywowane, gdy niezarządzany plik wykonywalny jest uruchamiany w debugerze.</span><span class="sxs-lookup"><span data-stu-id="491b9-184">`unmanagedDebugger` - Explicitly activates all MDAs that are implicitly activated when an unmanaged executable is started under a debugger.</span></span>

<span data-ttu-id="491b9-185">Jeśli istnieją jakieś ustawienia powodujące konflikt, ostatnie ustawienia zastępują poprzednie ustawienia:</span><span class="sxs-lookup"><span data-stu-id="491b9-185">If there are conflicting settings, the most recent settings override previous settings:</span></span>

- <span data-ttu-id="491b9-186">`COMPLUS_MDA=0`wyłącza wszystkie MDA, włącznie z niejawnie włączonymi w debugerze.</span><span class="sxs-lookup"><span data-stu-id="491b9-186">`COMPLUS_MDA=0` disables all MDAs, including those implicitly enabled under a debugger.</span></span>

- <span data-ttu-id="491b9-187">`COMPLUS_MDA=gcUnmanagedToManaged`Włącza `gcUnmanagedToManaged` dodatek do wszystkich MDA, które są niejawnie włączone w debugerze.</span><span class="sxs-lookup"><span data-stu-id="491b9-187">`COMPLUS_MDA=gcUnmanagedToManaged` enables `gcUnmanagedToManaged` in addition to any MDAs that are implicitly enabled under a debugger.</span></span>

- <span data-ttu-id="491b9-188">`COMPLUS_MDA=0;gcUnmanagedToManaged`Włącza `gcUnmanagedToManaged` , ale wyłącza MDA, które w przeciwnym razie byłyby niejawnie włączone w debugerze.</span><span class="sxs-lookup"><span data-stu-id="491b9-188">`COMPLUS_MDA=0;gcUnmanagedToManaged` enables `gcUnmanagedToManaged` but disables MDAs that would otherwise be implicitly enabled under a debugger.</span></span>

### <a name="application-specific-configuration-settings"></a><span data-ttu-id="491b9-189">Ustawienia konfiguracji specyficzne dla aplikacji</span><span class="sxs-lookup"><span data-stu-id="491b9-189">Application-Specific Configuration Settings</span></span>

<span data-ttu-id="491b9-190">Niektóre Asystenci można włączać, wyłączać i konfigurować pojedynczo w pliku konfiguracji MDA dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="491b9-190">You can enable, disable, and configure some assistants individually in the MDA configuration file for the application.</span></span> <span data-ttu-id="491b9-191">Aby umożliwić korzystanie z pliku konfiguracji aplikacji do konfigurowania MDA, należy ustawić klucz rejestru MDA lub zmienną środowiskową COMPLUS_MDA.</span><span class="sxs-lookup"><span data-stu-id="491b9-191">To enable the use of an application configuration file for configuring MDAs, either the MDA registry key or the COMPLUS_MDA environment variable must be set.</span></span> <span data-ttu-id="491b9-192">Plik konfiguracji aplikacji zwykle znajduje się w tym samym katalogu, co plik wykonywalny (exe) aplikacji.</span><span class="sxs-lookup"><span data-stu-id="491b9-192">The application configuration file is typically located in the same directory as the application's executable (.exe) file.</span></span> <span data-ttu-id="491b9-193">Nazwa pliku przyjmuje postać *ApplicationName*. MDA. config; na przykład Notepad. exe. MDA. config. Asystenci, którzy są włączeni w pliku konfiguracji aplikacji, mogą mieć atrybuty lub elementy zaprojektowane specjalnie pod kątem kontrolowania zachowania tego asystenta.</span><span class="sxs-lookup"><span data-stu-id="491b9-193">The file name takes the form *ApplicationName*.mda.config; for example, notepad.exe.mda.config. Assistants that are enabled in the application configuration file may have attributes or elements specifically designed to control that assistant's behavior.</span></span>

<span data-ttu-id="491b9-194">Poniższy przykład pokazuje, jak włączyć i skonfigurować [kierowanie](marshaling-mda.md):</span><span class="sxs-lookup"><span data-stu-id="491b9-194">The following example shows how to enable and configure the [marshaling](marshaling-mda.md):</span></span>

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

<span data-ttu-id="491b9-195">`Marshaling` MDA emituje informacje o zarządzanym typie, który jest przekazywany do niezarządzanego typu dla każdego przejścia zarządzanego do niezarządzanego w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="491b9-195">The `Marshaling` MDA emits information about the managed type that is being marshaled to an unmanaged type for each managed-to-unmanaged transition in the application.</span></span> <span data-ttu-id="491b9-196">MDA może również filtrować nazwy metod i pól struktury dostarczonych odpowiednio w elementach podrzędnych **methodFilter** i **fieldFilter.** `Marshaling`</span><span class="sxs-lookup"><span data-stu-id="491b9-196">The `Marshaling` MDA can also filter the names of the method and structure fields supplied in the **methodFilter** and **fieldFilter** child elements, respectively.</span></span>

<span data-ttu-id="491b9-197">Poniższy przykład pokazuje, jak włączyć wiele MDA przy użyciu ich ustawień domyślnych:</span><span class="sxs-lookup"><span data-stu-id="491b9-197">The following example shows how to enable multiple MDAs by using their default settings:</span></span>

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
> <span data-ttu-id="491b9-198">W przypadku określenia więcej niż jednego asystenta w pliku konfiguracji należy je wyświetlić w kolejności alfabetycznej.</span><span class="sxs-lookup"><span data-stu-id="491b9-198">When you specify more than one assistant in a configuration file, you must list them in alphabetical order.</span></span> <span data-ttu-id="491b9-199">Na przykład, jeśli `virtualCERCall` chcesz włączyć zarówno obiekt, `invalidCERCall` jak i MDA `<invalidCERCall />` , należy `<virtualCERCall />` dodać wpis przed wpisem.</span><span class="sxs-lookup"><span data-stu-id="491b9-199">For example, if you want to enable both the `virtualCERCall` and the `invalidCERCall` MDAs, you must add the `<invalidCERCall />` entry before the `<virtualCERCall />` entry.</span></span> <span data-ttu-id="491b9-200">Jeśli wpisy nie są w kolejności alfabetycznej, zostanie wyświetlony nieobsługiwany komunikat wyjątku pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="491b9-200">If the entries are not in alphabetical order, an unhandled invalid configuration file exception message is displayed.</span></span>

## <a name="mda-exceptions"></a><span data-ttu-id="491b9-201">Wyjątki MDA</span><span class="sxs-lookup"><span data-stu-id="491b9-201">MDA exceptions</span></span>

<span data-ttu-id="491b9-202">Gdy zdarzenie MDA jest włączone, jest aktywne nawet wtedy, gdy kod nie jest wykonywany w debugerze.</span><span class="sxs-lookup"><span data-stu-id="491b9-202">When an MDA is enabled, it's active even when your code is not executing under a debugger.</span></span> <span data-ttu-id="491b9-203">Jeśli zdarzenie MDA jest zgłaszane, gdy debuger nie jest obecny, komunikat o zdarzeniu jest wyświetlany w oknie dialogowym nieobsłużonego wyjątku, chociaż nie jest to nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="491b9-203">If an MDA event is raised when a debugger is not present, the event message is presented in an unhandled exception dialog box, although it is not an unhandled exception.</span></span> <span data-ttu-id="491b9-204">Aby uniknąć tego okna dialogowego, Usuń ustawienia włączania MDA, gdy kod nie jest wykonywany w środowisku debugowania.</span><span class="sxs-lookup"><span data-stu-id="491b9-204">To avoid the dialog box, remove the MDA-enabling settings when your code is not executing in a debugging environment.</span></span>

<span data-ttu-id="491b9-205">Gdy kod jest wykonywany w zintegrowanym środowisku programistycznym (IDE) programu Visual Studio, można uniknąć okna dialogowego wyjątek, które pojawia się dla określonych zdarzeń MDA.</span><span class="sxs-lookup"><span data-stu-id="491b9-205">When your code executes in the Visual Studio integrated development environment (IDE), you can avoid the exception dialog box that appears for specific MDA events.</span></span> <span data-ttu-id="491b9-206">W tym celu w menu **Debuguj** wybierz pozycję**Ustawienia wyjątków** **systemu Windows** > .</span><span class="sxs-lookup"><span data-stu-id="491b9-206">To do that, on the **Debug** menu, choose **Windows** > **Exception Settings**.</span></span> <span data-ttu-id="491b9-207">W oknie **Ustawienia wyjątku** rozwiń listę **Asystenci debugowania zarządzanego** , a następnie usuń zaznaczenie pola wyboru Przerwij, **gdy zostanie zgłoszone** dla pojedynczego elementu MDA.</span><span class="sxs-lookup"><span data-stu-id="491b9-207">In the **Exception Settings** window, expand the **Managed Debugging Assistants** list, and then clear the **Break When Thrown** check box for the individual MDA.</span></span> <span data-ttu-id="491b9-208">Tego okna dialogowego można także użyć, aby *włączyć* wyświetlanie okien dialogowych wyjątków MDA.</span><span class="sxs-lookup"><span data-stu-id="491b9-208">You can also use this dialog box to *enable* the display of MDA exception dialog boxes.</span></span>

## <a name="mda-output"></a><span data-ttu-id="491b9-209">Wyjście MDA</span><span class="sxs-lookup"><span data-stu-id="491b9-209">MDA Output</span></span>

<span data-ttu-id="491b9-210">Dane wyjściowe MDA są podobne do poniższego przykładu, który wyświetla dane wyjściowe `PInvokeStackImbalance` z MDA:</span><span class="sxs-lookup"><span data-stu-id="491b9-210">MDA output is similar to the following example, which shows the output from the `PInvokeStackImbalance` MDA:</span></span>

<span data-ttu-id="491b9-211">**Wywołanie funkcji PInvoke "MDATest! MDATest. program:: StdCall ' ma niezrównoważony stos. Prawdopodobnie jest to spowodowane tym, że zarządzana sygnatura PInvoke nie jest zgodna z niezarządzanym podpisem docelowym. Sprawdź, czy Konwencja wywoływania i parametry sygnatury PInvoke pasują do docelowego podpisu niezarządzanego.**</span><span class="sxs-lookup"><span data-stu-id="491b9-211">**A call to PInvoke function 'MDATest!MDATest.Program::StdCall' has unbalanced the stack. This is likely because the managed PInvoke signature does not match the unmanaged target signature. Check that the calling convention and parameters of the PInvoke signature match the target unmanaged signature.**</span></span>

## <a name="see-also"></a><span data-ttu-id="491b9-212">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="491b9-212">See also</span></span>

- [<span data-ttu-id="491b9-213">Debugowanie, śledzenie i profilowanie</span><span class="sxs-lookup"><span data-stu-id="491b9-213">Debugging, Tracing, and Profiling</span></span>](index.md)
