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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dd27bebdc71c70226a61ad8d912135e0e1671dd8
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70851249"
---
# <a name="fuslogvwexe-assembly-binding-log-viewer"></a>Fuslogvw.exe (Podgląd dziennika powiązań zasobów)

Podgląd dziennika powiązań zestawów wyświetla szczegóły dotyczące powiązań zestawu. Te informacje pomagają zdiagnozować, dlaczego .NET Framework nie może zlokalizować zestawu w czasie wykonywania. Te błędy są zazwyczaj wynikiem wdrożenia zestawu w nieprawidłowej lokalizacji, obrazu macierzystego, który przestał być prawidłowy lub niezgodności numerów wersji lub kultur. Niepowodzenie zlokalizowania zestawu przez środowisko uruchomieniowe języka wspólnego jest zwykle wyświetlane <xref:System.TypeLoadException> w aplikacji.

> [!IMPORTANT]
> Program fuslogvw.exe musi być uruchomione z uprawnieniami administratora.

To narzędzie jest instalowane automatycznie z programem Visual Studio. Aby uruchomić narzędzie, użyj wiersz polecenia dla deweloperów dla programu Visual Studio (lub wiersza polecenia programu Visual Studio w systemie Windows 7) z poświadczeniami administratora. Aby uzyskać więcej informacji, zobacz [wiersza polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md).

W wierszu polecenia wpisz następujące polecenie:

```console
fuslogvw
```

Przeglądarka wyświetla wpis dla każdego nieudanego powiązania zestawu. Dla każdego niepowodzenia przeglądarka opisuje aplikację, która zainicjowała powiązanie; zestaw, którego ono dotyczy, w tym nazwę, wersję, kulturę oraz klucz publiczny oraz datę i czas wystąpienia błędu.

### <a name="to-change-the-log-location-view"></a>Aby zmienić widok dziennika lokalizacji

1. Wybierz przycisk opcji **domyślne** , aby wyświetlić błędy powiązania dla wszystkich typów aplikacji. Domyślnie wpisy dziennika są przechowywane na dysku w katalogach użytkowników, w pamięci podręcznej wininet.

2. Wybierz przycisk opcji **niestandardowa** , aby wyświetlić błędy powiązania w niestandardowym katalogu, który określisz. Należy określić niestandardową lokalizację, w której środowisko uruchomieniowe ma przechowywać dzienniki, ustawiając w oknie dialogowym **ustawienia dziennika** niestandardową lokalizację dziennika na prawidłową nazwę katalogu. Ten katalog powinien być pusty i zawierać tylko pliki, które generuje środowisko uruchomieniowe. Jeśli zawiera plik wykonywalny, który generuje błąd, który ma zostać zapisany, błąd nie zostanie zapisany, ponieważ narzędzie spróbuje utworzyć katalog o takiej samej nazwie jak plik wykonywalny. Ponadto próba uruchomienia pliku wykonywalnego z lokalizacji dziennika nie powiedzie się.

    > [!NOTE]
    > Domyślna lokalizacja powiązania jest preferowana nad niestandardową lokalizacją powiązania. Środowisko uruchomieniowe przechowuje w pamięci podręcznej wininet domyślną lokalizację powiązania i dlatego czyści ją automatycznie. Jeśli określisz niestandardową lokalizację powiązania, jesteś także odpowiedzialny za jej czyszczenie.

### <a name="to-view-details-about-a-specific-failure"></a>Aby wyświetlić szczegóły, dotyczące określonego błędu

1. Wybierz nazwę aplikacji dla żądnego wpisu w przeglądarce.

2. Kliknij przycisk **Wyświetl dziennik** . Można także kliknąć dwukrotnie wybrany wpis.

    W narzędziu są wyświetlane następujące szczegółowe informacje o błędzie wybranego powiązania:

    - Konkretna przyczyna niepowodzenia powiązania, taka jak „nie odnaleziono pliku” lub „niezgodność wersji”.

    - Informacje o aplikacji, która zainicjowała powiązanie, w tym jej nazwa, katalog główny aplikacji (AppBase) i opis prywatnej ścieżki wyszukiwania, jeśli taka istnieje.

    - Tożsamość zestawu, którego szuka narzędzie.

    - Opis dowolnych zastosowanych polityk wersji Aplikacji, Wydawcy lub Administratora.

    - Czy zestaw został znaleziony w [globalnej pamięci podręcznej zestawów](../../../docs/framework/app-domains/gac.md).

    - Lista wszystkich badających adresów URL.

Następujący przykładowy wpis dziennika zawiera szczegółowe informacje na temat nieudanych powiązań zestawu.

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

### <a name="to-delete-a-single-entry-from-the-log"></a>Aby usunąć pojedynczy wpis z dziennika

1. Wybierz wpis w przeglądarce.

2. Kliknij przycisk **Usuń wpis** .

### <a name="to-delete-all-entries-from-the-log"></a>Aby usunąć wszystkie wpisy z dziennika

- Kliknij przycisk **Usuń wszystko** .

### <a name="to-refresh-the-user-interface"></a>Aby odświeżyć interfejs użytkownika

- Kliknij przycisk **Odśwież** . Przeglądarka nie wykrywa automatycznie nowych wpisów dziennika, kiedy jest uruchomiona. Aby je wyświetlić, należy użyć przycisku **Odśwież** .

### <a name="to-change-the-log-settings"></a>Aby zmienić ustawienia dziennika

- Kliknij przycisk **Ustawienia** , aby otworzyć okno dialogowe **ustawienia dziennika** .

### <a name="to-view-the-about-dialog"></a>Aby wyświetlić okno dialogowe Informacje

- Kliknij przycisk **informacje** .

## <a name="binding-logs-for-native-images"></a>Dzienniki powiązań dla obrazów macierzystych

Domyślnie Fuslogvw.exe rejestruje normalne żądania powiązania zestawów. Alternatywnie można rejestrować powiązania zestawów dla obrazów natywnych, które zostały utworzone przy użyciu programu [Ngen. exe (Generator obrazu natywnego)](../../../docs/framework/tools/ngen-exe-native-image-generator.md).

#### <a name="to-log-assembly-binds-for-native-images"></a>Aby rejestrować powiązania zestawów dla obrazów macierzystych

- W grupie **Kategorie dziennika** wybierz przycisk opcji **obrazy natywne** .

Następujący dziennik pokazuje błąd spowodowany przez zależność, która nie istniała, kiedy obraz macierzysty został utworzony dla aplikacji. Jeżeli zależności w czasie wykonywania różnią się od zależności po uruchomieniu Ngen.exe, powiązanie z obrazem macierzystym jest niedozwolone.

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

Następujący dziennik wyświetla błąd powiązania obrazu macierzystego, który wystąpił, ponieważ ustawienia zabezpieczeń na komputerze, gdy aplikacja została uruchomiona, różniły się od ustawień zabezpieczeń w momencie utworzenia obrazu macierzystego.

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

## <a name="the-log-settings-dialog"></a>Okno dialogowe Ustawienia dziennika

Za pomocą okna dialogowego **ustawienia dziennika** można wykonać następujące czynności.

#### <a name="to-disable-logging"></a>Aby wyłączyć rejestrowanie

- Wybierz przycisk opcji **Dziennik wyłączony** .  Należy zauważyć, że ta opcja jest domyślnie zaznaczona.

#### <a name="to-log-assembly-binds-in-exceptions"></a>Aby rejestrować powiązania zestawu w wyjątkach

- Wybierz przycisk opcji **Zaloguj się jako tekst wyjątku** . Tylko najmniej szczegółowe informacje dziennika łączenia są rejestrowane w tekście wyjątku. Aby wyświetlić pełne informacje, użyj jednego z innych ustawień.

  Zobacz Ważne informacje dotyczące zestawów, które są ładowane, jako niezależne od domeny.

#### <a name="to-log-assembly-bind-failures"></a>Aby rejestrować błędy powiązania zestawów

- Wybierz przycisk opcji **Rejestruj błędy powiązań na dysku** .

  Zobacz Ważne informacje dotyczące zestawów, które są ładowane, jako niezależne od domeny.

#### <a name="to-log-all-assembly-binds"></a>Aby rejestrować wszystkie powiązania zestawów

- Wybierz przycisk opcji **Rejestruj wszystkie powiązania na dysku** .

  Zobacz Ważne informacje dotyczące zestawów, które są ładowane, jako niezależne od domeny.

> [!IMPORTANT]
> Gdy zestaw jest ładowany jako neutralny dla domeny, na przykład przez ustawienie <xref:System.AppDomainSetup.LoaderOptimization%2A> właściwości na <xref:System.LoaderOptimization.MultiDomain?displayProperty=nameWithType> lub <xref:System.LoaderOptimization.MultiDomainHost?displayProperty=nameWithType>, włączenie rejestrowania może spowodować przeciek pamięci w niektórych przypadkach. Może się to zdarzyć, jeśli wpis dziennika jest dodawany, gdy moduł niezależny od domeny jest ładowany do domeny aplikacji, a później domena aplikacji jest zwalniana. Wpis dziennika nie może być zwolniony do czasu zakończenia procesu. Niektóre debugery włączają rejestrowanie automatycznie.

#### <a name="to-enable-a-custom-log-path"></a>Aby włączyć niestandardową ścieżkę dziennika

1. Wybierz przycisk opcji **Włącz niestandardową ścieżkę dziennika** .

2. Wprowadź ścieżkę do pola tekstowego **niestandardowa ścieżka dziennika** .

> [!NOTE]
> [Podgląd dziennika powiązań zestawów (Fuslogvw. exe)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) używa pamięci podręcznej programu Internet Explorer (IE) do przechowywania dziennika powiązań. Ze względu na sporadyczne uszkodzenie w pamięci podręcznej programu IE, [Przeglądarka dzienników powiązań zestawu (Fuslogvw. exe)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) może czasami zatrzymać wyświetlanie nowych dzienników powiązań w oknie wyświetlania. W wyniku tego uszkodzenia infrastruktura powiązań .NET (fusion) nie może zapisywać w dzienniku powiązań ani z niego odczytywać. (Ten problem nie wystąpi, jeśli używana jest niestandardowa ścieżka dziennika).  Aby naprawić uszkodzenie i umożliwić programowi fusion ponowne wyświetlanie dzienników powiązań, należy wyczyścić pamięć podręczną programu IE poprzez usunięcie tymczasowych plików internetowych w oknie Opcji internetowych programu IE.
>
> Jeśli niezarządzana aplikacja obsługuje środowisko uruchomieniowe języka wspólnego przez `IHostAssemblyManager` implementację interfejsów i `IHostAssemblyStore` , wpisy dziennika nie mogą być przechowywane w pamięci podręcznej WinINet.  Aby wyświetlić wpisy dziennika dla hostów niestandardowych, które implementują te interfejsy, należy określić alternatywną ścieżkę dziennika.

#### <a name="to-enable-logging-for-apps-running-in-the-windows-app-container"></a>Aby włączyć rejestrowanie dla aplikacji działających w kontenerze aplikacji systemu Windows

1. Należy włączyć niestandardową ścieżkę dziennika, jak opisano w poprzedniej procedurze. Domyślnie aplikacje, które są uruchomione w kontenerze aplikacji systemu Windows mają ograniczony dostęp do dysku twardego. Katalog, który zostanie określony, będzie miał dostęp do odczytu i zapisu dla wszystkich aplikacji z kontenera aplikacji.

2. Zaznacz pole wyboru **Włącz rejestrowanie immersyjny** .

    > [!NOTE]
    > To pole jest włączone tylko w systemie Windows 8 lub nowszym.

## <a name="see-also"></a>Zobacz także

- <xref:System.TypeLoadException>
- [Narzędzia](../../../docs/framework/tools/index.md)
- [Global Assembly Cache](../../../docs/framework/app-domains/gac.md)
- [Sposoby lokalizowania zestawów przez środowisko uruchomieniowe](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [Wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
