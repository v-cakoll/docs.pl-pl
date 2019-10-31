---
title: Fuslogvw.exe (Podgląd dziennika powiązań zasobów)
ms.date: 03/30/2017
helpviewer_keywords:
- failed assembly binds
- Fuslogvw.exe
- displaying failed assembly bind details
- assemblies [.NET Framework], failed assembly binds
- locating assemblies
- Assembly Binding Log Viewer
ms.assetid: e32fa443-0778-4cc3-bf36-5c8ea297d296
ms.openlocfilehash: 2f0018dca6e5add2c5bc531103a4078307a8c8c6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129845"
---
# <a name="fuslogvwexe-assembly-binding-log-viewer"></a><span data-ttu-id="0546c-102">Fuslogvw.exe (Podgląd dziennika powiązań zasobów)</span><span class="sxs-lookup"><span data-stu-id="0546c-102">Fuslogvw.exe (Assembly Binding Log Viewer)</span></span>

<span data-ttu-id="0546c-103">Podgląd dziennika powiązań zestawów wyświetla szczegóły dotyczące powiązań zestawu.</span><span class="sxs-lookup"><span data-stu-id="0546c-103">The Assembly Binding Log Viewer displays details for assembly binds.</span></span> <span data-ttu-id="0546c-104">Te informacje pomagają zdiagnozować, dlaczego .NET Framework nie może zlokalizować zestawu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="0546c-104">This information helps you diagnose why the .NET Framework cannot locate an assembly at run time.</span></span> <span data-ttu-id="0546c-105">Te błędy są zazwyczaj wynikiem wdrożenia zestawu w nieprawidłowej lokalizacji, obrazu macierzystego, który przestał być prawidłowy lub niezgodności numerów wersji lub kultur.</span><span class="sxs-lookup"><span data-stu-id="0546c-105">These failures are usually the result of an assembly deployed to the wrong location, a native image that is no longer valid, or a mismatch in version numbers or cultures.</span></span> <span data-ttu-id="0546c-106">Niepowodzenie zlokalizowania zestawu przez środowisko uruchomieniowe języka wspólnego jest zwykle wyświetlane jako <xref:System.TypeLoadException> w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0546c-106">The common language runtime's failure to locate an assembly typically shows up as a <xref:System.TypeLoadException> in your application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0546c-107">Program fuslogvw.exe musi być uruchomione z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="0546c-107">You must run fuslogvw.exe with administrator privileges.</span></span>

<span data-ttu-id="0546c-108">To narzędzie jest instalowane automatycznie z programem Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0546c-108">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="0546c-109">Aby uruchomić narzędzie, użyj wiersz polecenia dla deweloperów dla programu Visual Studio (lub wiersza polecenia programu Visual Studio w systemie Windows 7) z poświadczeniami administratora.</span><span class="sxs-lookup"><span data-stu-id="0546c-109">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7) with administrator credentials.</span></span> <span data-ttu-id="0546c-110">Aby uzyskać więcej informacji, zobacz [wiersza polecenia](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="0546c-110">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>

<span data-ttu-id="0546c-111">W wierszu polecenia wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="0546c-111">At the command prompt, type the following:</span></span>

```console
fuslogvw
```

<span data-ttu-id="0546c-112">Przeglądarka wyświetla wpis dla każdego nieudanego powiązania zestawu.</span><span class="sxs-lookup"><span data-stu-id="0546c-112">The viewer displays an entry for each failed assembly bind.</span></span> <span data-ttu-id="0546c-113">Dla każdego niepowodzenia przeglądarka opisuje aplikację, która zainicjowała powiązanie; zestaw, którego ono dotyczy, w tym nazwę, wersję, kulturę oraz klucz publiczny oraz datę i czas wystąpienia błędu.</span><span class="sxs-lookup"><span data-stu-id="0546c-113">For each failure, the viewer describes the application that initiated the bind; the assembly the bind is for, including name, version, culture and public key; and the date and time of the failure.</span></span>

### <a name="to-change-the-log-location-view"></a><span data-ttu-id="0546c-114">Aby zmienić widok dziennika lokalizacji</span><span class="sxs-lookup"><span data-stu-id="0546c-114">To change the log location view</span></span>

1. <span data-ttu-id="0546c-115">Wybierz przycisk opcji **domyślne** , aby wyświetlić błędy powiązania dla wszystkich typów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0546c-115">Select the **Default** option button to view bind failures for all application types.</span></span> <span data-ttu-id="0546c-116">Domyślnie wpisy dziennika są przechowywane na dysku w katalogach użytkowników, w pamięci podręcznej wininet.</span><span class="sxs-lookup"><span data-stu-id="0546c-116">By default, log entries are stored in per-user directories on disk in the wininet cache.</span></span>

2. <span data-ttu-id="0546c-117">Wybierz przycisk opcji **niestandardowa** , aby wyświetlić błędy powiązania w niestandardowym katalogu, który określisz.</span><span class="sxs-lookup"><span data-stu-id="0546c-117">Select the **Custom** option button to view bind failures in a custom directory that you specify.</span></span> <span data-ttu-id="0546c-118">Należy określić niestandardową lokalizację, w której środowisko uruchomieniowe ma przechowywać dzienniki, ustawiając w oknie dialogowym **ustawienia dziennika** niestandardową lokalizację dziennika na prawidłową nazwę katalogu.</span><span class="sxs-lookup"><span data-stu-id="0546c-118">You must specify the custom location where you want the runtime to store the logs by setting the custom log location in the **Log Settings** dialog to a valid directory name.</span></span> <span data-ttu-id="0546c-119">Ten katalog powinien być pusty i zawierać tylko pliki, które generuje środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="0546c-119">This directory should be clean, and only contain files that the runtime generates.</span></span> <span data-ttu-id="0546c-120">Jeśli zawiera plik wykonywalny, który generuje błąd, który ma zostać zapisany, błąd nie zostanie zapisany, ponieważ narzędzie spróbuje utworzyć katalog o takiej samej nazwie jak plik wykonywalny.</span><span class="sxs-lookup"><span data-stu-id="0546c-120">If it contains an executable that generates a failure to be logged, the failure will not be logged because the tool tries to create a directory with the same name as the executable.</span></span> <span data-ttu-id="0546c-121">Ponadto próba uruchomienia pliku wykonywalnego z lokalizacji dziennika nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="0546c-121">In addition, an attempt to run an executable from the log location will fail.</span></span>

    > [!NOTE]
    > <span data-ttu-id="0546c-122">Domyślna lokalizacja powiązania jest preferowana nad niestandardową lokalizacją powiązania.</span><span class="sxs-lookup"><span data-stu-id="0546c-122">The default bind location is preferable to the custom bind location.</span></span> <span data-ttu-id="0546c-123">Środowisko uruchomieniowe przechowuje w pamięci podręcznej usługi WinInet domyślną lokalizację powiązania i w związku z tym automatycznie czyści ją. W przypadku określenia niestandardowej lokalizacji powiązania użytkownik jest odpowiedzialny za jej czyszczenie.</span><span class="sxs-lookup"><span data-stu-id="0546c-123">The runtime stores the default bind location in the wininet cache, and therefore automatically cleans it out. If you specify a custom bind location, you are responsible for cleaning it out.</span></span>

### <a name="to-view-details-about-a-specific-failure"></a><span data-ttu-id="0546c-124">Aby wyświetlić szczegóły, dotyczące określonego błędu</span><span class="sxs-lookup"><span data-stu-id="0546c-124">To view details about a specific failure</span></span>

1. <span data-ttu-id="0546c-125">Wybierz nazwę aplikacji dla żądnego wpisu w przeglądarce.</span><span class="sxs-lookup"><span data-stu-id="0546c-125">Select the application name of the desired entry in the viewer.</span></span>

2. <span data-ttu-id="0546c-126">Kliknij przycisk **Wyświetl dziennik** .</span><span class="sxs-lookup"><span data-stu-id="0546c-126">Click the **View Log** button.</span></span> <span data-ttu-id="0546c-127">Można także kliknąć dwukrotnie wybrany wpis.</span><span class="sxs-lookup"><span data-stu-id="0546c-127">Alternately, you can double-click the selected entry.</span></span>

    <span data-ttu-id="0546c-128">W narzędziu są wyświetlane następujące szczegółowe informacje o błędzie wybranego powiązania:</span><span class="sxs-lookup"><span data-stu-id="0546c-128">The tool displays the following details about the selected bind failure:</span></span>

    - <span data-ttu-id="0546c-129">Konkretna przyczyna niepowodzenia powiązania, taka jak „nie odnaleziono pliku” lub „niezgodność wersji”.</span><span class="sxs-lookup"><span data-stu-id="0546c-129">The specific reason the bind failed, such as "file not found" or "version mismatch".</span></span>

    - <span data-ttu-id="0546c-130">Informacje o aplikacji, która zainicjowała powiązanie, w tym jej nazwa, katalog główny aplikacji (AppBase) i opis prywatnej ścieżki wyszukiwania, jeśli taka istnieje.</span><span class="sxs-lookup"><span data-stu-id="0546c-130">Information about the application that initiated the bind, including its name, the application's root directory (AppBase), and a description of the private search path, if there is one.</span></span>

    - <span data-ttu-id="0546c-131">Tożsamość zestawu, którego szuka narzędzie.</span><span class="sxs-lookup"><span data-stu-id="0546c-131">The identity of the assembly the tool is looking for.</span></span>

    - <span data-ttu-id="0546c-132">Opis dowolnych zastosowanych polityk wersji Aplikacji, Wydawcy lub Administratora.</span><span class="sxs-lookup"><span data-stu-id="0546c-132">A description of any Application, Publisher, or Administrator version policies that have been applied.</span></span>

    - <span data-ttu-id="0546c-133">Czy zestaw został znaleziony w [globalnej pamięci podręcznej zestawów](../app-domains/gac.md).</span><span class="sxs-lookup"><span data-stu-id="0546c-133">Whether the assembly was found in the [global assembly cache](../app-domains/gac.md).</span></span>

    - <span data-ttu-id="0546c-134">Lista wszystkich badających adresów URL.</span><span class="sxs-lookup"><span data-stu-id="0546c-134">A list of all probing URLs.</span></span>

<span data-ttu-id="0546c-135">Następujący przykładowy wpis dziennika zawiera szczegółowe informacje na temat nieudanych powiązań zestawu.</span><span class="sxs-lookup"><span data-stu-id="0546c-135">The following sample log entry shows detailed information about a failed assembly bind.</span></span>

```output
*** Assembly Binder Log Entry  (3/5/2007 @ 12:54:20 PM) ***

The operation failed.
Bind result: hr = 0x80070002. The system cannot find the file specified.

Assembly manager loaded from:  C:\WINNT\Microsoft.NET\Framework\v2.0.50727\fusion.dll
Running under executable  C:\Program Files\Microsoft.NET\FrameworkSDK\Samples\Tutorials\resourcesandlocalization\graphic\cs\graphicfailtest.exe
--- A detailed error log follows.

=== Pre-bind state information ===
LOG: DisplayName = graphicfailtest.resources, Version=0.0.0.0, Culture=en-US, PublicKeyToken=null
 (Fully-specified)
LOG: Appbase = C:\Program Files\Microsoft.NET\FrameworkSDK\Samples\Tutorials\resourcesandlocalization\graphic\cs\
LOG: Initial PrivatePath = NULL
LOG: Dynamic Base = NULL
LOG: Cache Base = NULL
LOG: AppName = NULL
Calling assembly : graphicfailtest, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.
===

LOG: Processing DEVPATH.
LOG: DEVPATH is not set. Falling through to regular bind.
LOG: Policy not being applied to reference at this time (private, custom, partial, or location-based assembly bind).
LOG: Post-policy reference: graphicfailtest.resources, Version=0.0.0.0, Culture=en-US, PublicKeyToken=null
LOG: Attempting download of new URL file:///C:/Program Files/Microsoft.NET/FrameworkSDK/Samples/Tutorials/resourcesandlocalization/graphic/cs/graphicfailtest.resources.DLL.
LOG: Attempting download of new URL file:///C:/Program Files/Microsoft.NET/FrameworkSDK/Samples/Tutorials/resourcesandlocalization/graphic/cs/graphicfailtest.resources/graphicfailtest.resources.DLL.
LOG: Attempting download of new URL file:///C:/Program Files/Microsoft.NET/FrameworkSDK/Samples/Tutorials/resourcesandlocalization/graphic/cs/graphicfailtest.resources.EXE.
LOG: Attempting download of new URL file:///C:/Program Files/Microsoft.NET/FrameworkSDK/Samples/Tutorials/resourcesandlocalization/graphic/cs/graphicfailtest.resources/graphicfailtest.resources.EXE.
LOG: All probing URLs attempted and failed.
```

### <a name="to-delete-a-single-entry-from-the-log"></a><span data-ttu-id="0546c-136">Aby usunąć pojedynczy wpis z dziennika</span><span class="sxs-lookup"><span data-stu-id="0546c-136">To delete a single entry from the log</span></span>

1. <span data-ttu-id="0546c-137">Wybierz wpis w przeglądarce.</span><span class="sxs-lookup"><span data-stu-id="0546c-137">Select an entry in the viewer.</span></span>

2. <span data-ttu-id="0546c-138">Kliknij przycisk **Usuń wpis** .</span><span class="sxs-lookup"><span data-stu-id="0546c-138">Click the **Delete Entry** button.</span></span>

### <a name="to-delete-all-entries-from-the-log"></a><span data-ttu-id="0546c-139">Aby usunąć wszystkie wpisy z dziennika</span><span class="sxs-lookup"><span data-stu-id="0546c-139">To delete all entries from the log</span></span>

- <span data-ttu-id="0546c-140">Kliknij przycisk **Usuń wszystko** .</span><span class="sxs-lookup"><span data-stu-id="0546c-140">Click the **Delete All** button.</span></span>

### <a name="to-refresh-the-user-interface"></a><span data-ttu-id="0546c-141">Aby odświeżyć interfejs użytkownika</span><span class="sxs-lookup"><span data-stu-id="0546c-141">To refresh the user interface</span></span>

- <span data-ttu-id="0546c-142">Kliknij przycisk **Odśwież** .</span><span class="sxs-lookup"><span data-stu-id="0546c-142">Click the **Refresh** button.</span></span> <span data-ttu-id="0546c-143">Przeglądarka nie wykrywa automatycznie nowych wpisów dziennika, kiedy jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="0546c-143">The viewer does not automatically detect new log entries while it is running.</span></span> <span data-ttu-id="0546c-144">Aby je wyświetlić, należy użyć przycisku **Odśwież** .</span><span class="sxs-lookup"><span data-stu-id="0546c-144">You must use the **Refresh** button to display them.</span></span>

### <a name="to-change-the-log-settings"></a><span data-ttu-id="0546c-145">Aby zmienić ustawienia dziennika</span><span class="sxs-lookup"><span data-stu-id="0546c-145">To change the log settings</span></span>

- <span data-ttu-id="0546c-146">Kliknij przycisk **Ustawienia** , aby otworzyć okno dialogowe **ustawienia dziennika** .</span><span class="sxs-lookup"><span data-stu-id="0546c-146">Click the **Settings** button to open the **Log Settings** dialog.</span></span>

### <a name="to-view-the-about-dialog"></a><span data-ttu-id="0546c-147">Aby wyświetlić okno dialogowe Informacje</span><span class="sxs-lookup"><span data-stu-id="0546c-147">To view the About dialog</span></span>

- <span data-ttu-id="0546c-148">Kliknij przycisk **informacje** .</span><span class="sxs-lookup"><span data-stu-id="0546c-148">Click the **About** button.</span></span>

## <a name="binding-logs-for-native-images"></a><span data-ttu-id="0546c-149">Dzienniki powiązań dla obrazów macierzystych</span><span class="sxs-lookup"><span data-stu-id="0546c-149">Binding Logs for Native Images</span></span>

<span data-ttu-id="0546c-150">Domyślnie Fuslogvw.exe rejestruje normalne żądania powiązania zestawów.</span><span class="sxs-lookup"><span data-stu-id="0546c-150">By default, Fuslogvw.exe logs normal assembly bind requests.</span></span> <span data-ttu-id="0546c-151">Alternatywnie można rejestrować powiązania zestawów dla obrazów natywnych, które zostały utworzone przy użyciu programu [Ngen. exe (Generator obrazu natywnego)](ngen-exe-native-image-generator.md).</span><span class="sxs-lookup"><span data-stu-id="0546c-151">Alternatively, you can log assembly binds for native images that were created using the [Ngen.exe (Native Image Generator)](ngen-exe-native-image-generator.md).</span></span>

#### <a name="to-log-assembly-binds-for-native-images"></a><span data-ttu-id="0546c-152">Aby rejestrować powiązania zestawów dla obrazów macierzystych</span><span class="sxs-lookup"><span data-stu-id="0546c-152">To log assembly binds for native images</span></span>

- <span data-ttu-id="0546c-153">W grupie **Kategorie dziennika** wybierz przycisk opcji **obrazy natywne** .</span><span class="sxs-lookup"><span data-stu-id="0546c-153">In the **Log Categories** group, select the **Native Images** option button.</span></span>

<span data-ttu-id="0546c-154">Następujący dziennik pokazuje błąd spowodowany przez zależność, która nie istniała, kiedy obraz macierzysty został utworzony dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0546c-154">The following log shows a failure caused by a dependency that did not exist when the native image was created for the application.</span></span> <span data-ttu-id="0546c-155">Jeżeli zależności w czasie wykonywania różnią się od zależności po uruchomieniu Ngen.exe, powiązanie z obrazem macierzystym jest niedozwolone.</span><span class="sxs-lookup"><span data-stu-id="0546c-155">If the dependencies at run time differ from the dependencies when Ngen.exe is run, binding to a native image is not allowed.</span></span>

```output
*** Assembly Binder Log Entry  (12/8/2006 @ 5:22:07 PM) ***

The operation failed.
Bind result: hr = 0x80070002. The system cannot find the file specified.

Assembly manager loaded from:  E:\Windows\Microsoft.NET\Framework64\v2.0.50727\mscorwks.dll
Running under executable  E:\test\App.exe
--- A detailed error log follows.

LOG: Start binding of native image App, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.
LOG: IL assembly loaded from E:\test\App.exe.
LOG: Start validating native image App, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.
LOG: Start validating all the dependencies.
LOG: [Level 1]Start validating native image dependency mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089.
LOG: Dependency evaluation succeeded.
LOG: [Level 1]Start validating IL dependency b, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.
WRN: Dependency assembly was not found at ngen time, but is found at binding time. Disallow using this native image.
WRN: No matching native image found.
LOG: Bind to native image assembly did not succeed. Use IL image.
```

<span data-ttu-id="0546c-156">Następujący dziennik wyświetla błąd powiązania obrazu macierzystego, który wystąpił, ponieważ ustawienia zabezpieczeń na komputerze, gdy aplikacja została uruchomiona, różniły się od ustawień zabezpieczeń w momencie utworzenia obrazu macierzystego.</span><span class="sxs-lookup"><span data-stu-id="0546c-156">The following log shows a native image binding failure that occurred because the security settings on the computer when the application was run were different from the security settings at the time the native image was created.</span></span>

```output
*** Assembly Binder Log Entry  (12/8/2006 @ 5:29:09 PM) ***

The operation failed.
Bind result: hr = 0x80004005. Unspecified error

Assembly manager loaded from:  E:\Windows\Microsoft.NET\Framework64\v2.0.50727\mscorwks.dll
Running under executable  E:\test\Application101622.exe
--- A detailed error log follows.

LOG: Start binding of native image Application101622, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.
LOG: IL assembly loaded from E:\test\Application101622.exe.
LOG: Start validating native image Application101622, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.
LOG: Start validating all the dependencies.
LOG: [Level 1]Start validating native image dependency mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089.
LOG: Dependency evaluation succeeded.
LOG: [Level 1]Start validating IL dependency Dependency101622, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.
LOG: Dependency evaluation succeeded.
LOG: Validation of dependencies succeeded.
LOG: Start loading all the dependencies into load context.
LOG: Loading of dependencies succeeded.
LOG: Bind to native image succeeded.
Native image has correct version information.
Attempting to use native image E:\Windows\assembly\NativeImages_v2.0.50727_64\Application101622\1ac7fadabec4f72575d807501e9fdc72\Application101622.ni.exe.
Rejecting native image because it failed the security check. The assembly's permissions must have changed since the time it was ngenned, or it is running with a different security context.
Discarding native image.
```

## <a name="the-log-settings-dialog"></a><span data-ttu-id="0546c-157">Okno dialogowe Ustawienia dziennika</span><span class="sxs-lookup"><span data-stu-id="0546c-157">The Log Settings Dialog</span></span>

<span data-ttu-id="0546c-158">Za pomocą okna dialogowego **ustawienia dziennika** można wykonać następujące czynności.</span><span class="sxs-lookup"><span data-stu-id="0546c-158">You can use the **Log Settings** dialog to perform the following actions.</span></span>

#### <a name="to-disable-logging"></a><span data-ttu-id="0546c-159">Aby wyłączyć rejestrowanie</span><span class="sxs-lookup"><span data-stu-id="0546c-159">To disable logging</span></span>

- <span data-ttu-id="0546c-160">Wybierz przycisk opcji **Dziennik wyłączony** .</span><span class="sxs-lookup"><span data-stu-id="0546c-160">Select the **Log disabled** option button.</span></span>  <span data-ttu-id="0546c-161">Należy zauważyć, że ta opcja jest domyślnie zaznaczona.</span><span class="sxs-lookup"><span data-stu-id="0546c-161">Note that this option is selected by default.</span></span>

#### <a name="to-log-assembly-binds-in-exceptions"></a><span data-ttu-id="0546c-162">Aby rejestrować powiązania zestawu w wyjątkach</span><span class="sxs-lookup"><span data-stu-id="0546c-162">To log assembly binds in exceptions</span></span>

- <span data-ttu-id="0546c-163">Wybierz przycisk opcji **Zaloguj się jako tekst wyjątku** .</span><span class="sxs-lookup"><span data-stu-id="0546c-163">Select the **Log in exception text** option button.</span></span> <span data-ttu-id="0546c-164">Tylko najmniej szczegółowe informacje dziennika łączenia są rejestrowane w tekście wyjątku.</span><span class="sxs-lookup"><span data-stu-id="0546c-164">Only the least detailed fusion log information is logged in exception text.</span></span> <span data-ttu-id="0546c-165">Aby wyświetlić pełne informacje, użyj jednego z innych ustawień.</span><span class="sxs-lookup"><span data-stu-id="0546c-165">To view full information, use one of the other settings.</span></span>

  <span data-ttu-id="0546c-166">Zobacz Ważne informacje dotyczące zestawów, które są ładowane, jako niezależne od domeny.</span><span class="sxs-lookup"><span data-stu-id="0546c-166">See the Important note regarding assemblies that are loaded as domain neutral.</span></span>

#### <a name="to-log-assembly-bind-failures"></a><span data-ttu-id="0546c-167">Aby rejestrować błędy powiązania zestawów</span><span class="sxs-lookup"><span data-stu-id="0546c-167">To log assembly bind failures</span></span>

- <span data-ttu-id="0546c-168">Wybierz przycisk opcji **Rejestruj błędy powiązań na dysku** .</span><span class="sxs-lookup"><span data-stu-id="0546c-168">Select the **Log bind failures to disk** option button.</span></span>

  <span data-ttu-id="0546c-169">Zobacz Ważne informacje dotyczące zestawów, które są ładowane, jako niezależne od domeny.</span><span class="sxs-lookup"><span data-stu-id="0546c-169">See the Important note regarding assemblies that are loaded as domain neutral.</span></span>

#### <a name="to-log-all-assembly-binds"></a><span data-ttu-id="0546c-170">Aby rejestrować wszystkie powiązania zestawów</span><span class="sxs-lookup"><span data-stu-id="0546c-170">To log all assembly binds</span></span>

- <span data-ttu-id="0546c-171">Wybierz przycisk opcji **Rejestruj wszystkie powiązania na dysku** .</span><span class="sxs-lookup"><span data-stu-id="0546c-171">Select the **Log all binds to disk** option button.</span></span>

  <span data-ttu-id="0546c-172">Zobacz Ważne informacje dotyczące zestawów, które są ładowane, jako niezależne od domeny.</span><span class="sxs-lookup"><span data-stu-id="0546c-172">See the Important note regarding assemblies that are loaded as domain neutral.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0546c-173">Gdy zestaw jest ładowany jako neutralny dla domeny, na przykład przez ustawienie właściwości <xref:System.AppDomainSetup.LoaderOptimization%2A> na <xref:System.LoaderOptimization.MultiDomain?displayProperty=nameWithType> lub <xref:System.LoaderOptimization.MultiDomainHost?displayProperty=nameWithType>, włączenie rejestrowania może spowodować przeciek pamięci w niektórych przypadkach.</span><span class="sxs-lookup"><span data-stu-id="0546c-173">When an assembly is loaded as domain neutral, for example by setting the <xref:System.AppDomainSetup.LoaderOptimization%2A> property to <xref:System.LoaderOptimization.MultiDomain?displayProperty=nameWithType> or <xref:System.LoaderOptimization.MultiDomainHost?displayProperty=nameWithType>, turning on logging might leak memory in some cases.</span></span> <span data-ttu-id="0546c-174">Może się to zdarzyć, jeśli wpis dziennika jest dodawany, gdy moduł niezależny od domeny jest ładowany do domeny aplikacji, a później domena aplikacji jest zwalniana.</span><span class="sxs-lookup"><span data-stu-id="0546c-174">This can happen if a log entry is made when a domain-neutral module is loaded into an application domain, and later the application domain is unloaded.</span></span> <span data-ttu-id="0546c-175">Wpis dziennika nie może być zwolniony do czasu zakończenia procesu.</span><span class="sxs-lookup"><span data-stu-id="0546c-175">The log entry might not be released until the process ends.</span></span> <span data-ttu-id="0546c-176">Niektóre debugery włączają rejestrowanie automatycznie.</span><span class="sxs-lookup"><span data-stu-id="0546c-176">Some debuggers automatically turn on logging.</span></span>

#### <a name="to-enable-a-custom-log-path"></a><span data-ttu-id="0546c-177">Aby włączyć niestandardową ścieżkę dziennika</span><span class="sxs-lookup"><span data-stu-id="0546c-177">To enable a custom log path</span></span>

1. <span data-ttu-id="0546c-178">Wybierz przycisk opcji **Włącz niestandardową ścieżkę dziennika** .</span><span class="sxs-lookup"><span data-stu-id="0546c-178">Select the **Enable custom log path** option button.</span></span>

2. <span data-ttu-id="0546c-179">Wprowadź ścieżkę do pola tekstowego **niestandardowa ścieżka dziennika** .</span><span class="sxs-lookup"><span data-stu-id="0546c-179">Enter the path into the **Custom log path** text box.</span></span>

> [!NOTE]
> <span data-ttu-id="0546c-180">[Podgląd dziennika powiązań zestawów (Fuslogvw. exe)](fuslogvw-exe-assembly-binding-log-viewer.md) używa pamięci podręcznej programu Internet Explorer (IE) do przechowywania dziennika powiązań.</span><span class="sxs-lookup"><span data-stu-id="0546c-180">The [Assembly Binding Log Viewer (Fuslogvw.exe)](fuslogvw-exe-assembly-binding-log-viewer.md) uses the Internet Explorer (IE) cache to store its binding log.</span></span> <span data-ttu-id="0546c-181">Ze względu na sporadyczne uszkodzenie w pamięci podręcznej programu IE, [Przeglądarka dzienników powiązań zestawu (Fuslogvw. exe)](fuslogvw-exe-assembly-binding-log-viewer.md) może czasami zatrzymać wyświetlanie nowych dzienników powiązań w oknie wyświetlania.</span><span class="sxs-lookup"><span data-stu-id="0546c-181">Due to occasional corruption in the IE cache, the [Assembly Binding Log Viewer (Fuslogvw.exe)](fuslogvw-exe-assembly-binding-log-viewer.md) can sometimes stop showing new binding logs in the viewing window.</span></span> <span data-ttu-id="0546c-182">W wyniku tego uszkodzenia infrastruktura powiązań .NET (fusion) nie może zapisywać w dzienniku powiązań ani z niego odczytywać.</span><span class="sxs-lookup"><span data-stu-id="0546c-182">As a result of this corruption, the .NET binding infrastructure (fusion) cannot write to or read from the binding log.</span></span> <span data-ttu-id="0546c-183">(Ten problem nie występuje, jeśli używasz niestandardowej ścieżki dziennika).  Aby naprawić uszkodzenie i umożliwić łączenie w celu ponownego wyświetlenia dzienników powiązań, wyczyść pamięć podręczną programu IE, usuwając tymczasowe pliki internetowe z okna dialogowego Opcje internetowe programu IE.</span><span class="sxs-lookup"><span data-stu-id="0546c-183">(This issue is not encountered if you use a custom log path.)  To fix the corruption and allow fusion to show binding logs again, clear the IE cache by deleting temporary internet files from within the IE Internet Options dialog.</span></span>
>
> <span data-ttu-id="0546c-184">Jeśli niezarządzana aplikacja obsługuje środowisko uruchomieniowe języka wspólnego przez implementację interfejsów `IHostAssemblyManager` i `IHostAssemblyStore`, wpisów dziennika nie można przechowywać w pamięci podręcznej WinINet.</span><span class="sxs-lookup"><span data-stu-id="0546c-184">If your unmanaged application hosts the common language runtime by implementing the `IHostAssemblyManager` and `IHostAssemblyStore` interfaces, log entries can't be stored in the wininet cache.</span></span>  <span data-ttu-id="0546c-185">Aby wyświetlić wpisy dziennika dla hostów niestandardowych, które implementują te interfejsy, należy określić alternatywną ścieżkę dziennika.</span><span class="sxs-lookup"><span data-stu-id="0546c-185">To view log entries for custom hosts that implement these interfaces, you must specify an alternate log path.</span></span>

#### <a name="to-enable-logging-for-apps-running-in-the-windows-app-container"></a><span data-ttu-id="0546c-186">Aby włączyć rejestrowanie dla aplikacji działających w kontenerze aplikacji systemu Windows</span><span class="sxs-lookup"><span data-stu-id="0546c-186">To enable logging for apps running in the Windows app container</span></span>

1. <span data-ttu-id="0546c-187">Należy włączyć niestandardową ścieżkę dziennika, jak opisano w poprzedniej procedurze.</span><span class="sxs-lookup"><span data-stu-id="0546c-187">Enable a custom log path, as described in the previous procedure.</span></span> <span data-ttu-id="0546c-188">Domyślnie aplikacje, które są uruchomione w kontenerze aplikacji systemu Windows mają ograniczony dostęp do dysku twardego.</span><span class="sxs-lookup"><span data-stu-id="0546c-188">By default, apps that are running in the Windows app container have limited access to the hard disk.</span></span> <span data-ttu-id="0546c-189">Katalog, który zostanie określony, będzie miał dostęp do odczytu i zapisu dla wszystkich aplikacji z kontenera aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0546c-189">The directory you specify will have read/write access for all apps in the app container.</span></span>

2. <span data-ttu-id="0546c-190">Zaznacz pole wyboru **Włącz rejestrowanie immersyjny** .</span><span class="sxs-lookup"><span data-stu-id="0546c-190">Select the **Enable immersive logging** check box.</span></span>

    > [!NOTE]
    > <span data-ttu-id="0546c-191">To pole jest włączone tylko w systemie Windows 8 lub nowszym.</span><span class="sxs-lookup"><span data-stu-id="0546c-191">This box is enabled only on Windows 8 or later.</span></span>

## <a name="see-also"></a><span data-ttu-id="0546c-192">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0546c-192">See also</span></span>

- <xref:System.TypeLoadException>
- [<span data-ttu-id="0546c-193">Narzędzia</span><span class="sxs-lookup"><span data-stu-id="0546c-193">Tools</span></span>](index.md)
- [<span data-ttu-id="0546c-194">Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="0546c-194">Global Assembly Cache</span></span>](../app-domains/gac.md)
- [<span data-ttu-id="0546c-195">Sposoby lokalizowania zestawów przez środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="0546c-195">How the Runtime Locates Assemblies</span></span>](../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="0546c-196">Wiersze polecenia</span><span class="sxs-lookup"><span data-stu-id="0546c-196">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
