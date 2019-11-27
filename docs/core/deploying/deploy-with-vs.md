---
title: Wdrażanie aplikacji .NET Core za pomocą programu Visual Studio
description: Dowiedz się, jak wdrożyć aplikację platformy .NET Core w programie Visual Studio.
ms.date: 09/03/2018
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: f80b483fedc600a1e1a48d36ce9b7b95c6de9f27
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428892"
---
# <a name="deploy-net-core-apps-with-visual-studio"></a>Wdrażanie aplikacji .NET Core za pomocą programu Visual Studio

Aplikację .NET Core można wdrożyć jako *wdrożenie zależne od platformy*, które obejmuje pliki binarne aplikacji, ale zależy od obecności platformy .NET Core w systemie docelowym lub jako *samodzielnego wdrożenia*, w tym plików binarnych aplikacji i programu .NET Core. Aby zapoznać się z omówieniem wdrażania aplikacji .NET Core, zobacz [wdrażanie aplikacji .NET Core](index.md).

W poniższych sekcjach pokazano, jak używać Microsoft Visual Studio do tworzenia następujących rodzajów wdrożeń:

- Wdrożenie zależny od struktury
- Wdrożenie zależne od platformy z zależnościami innych firm
- Niezależne wdrożenia
- Samodzielne wdrożenie z zależnościami innych firm

Aby uzyskać informacje dotyczące korzystania z programu Visual Studio w celu tworzenia aplikacji platformy .NET Core, zobacz [zależności i wymagania dotyczące platformy .NET Core](../install/dependencies.md?tabs=netcore30&pivots=os-windows).

## <a name="framework-dependent-deployment"></a>Wdrożenie zależny od struktury

Wdrażanie wdrożenia zależnego od platformy bez zależności innych firm polega jedynie na kompilowaniu, testowaniu i publikowaniu aplikacji. Prosty przykład zapisaniem C# ilustruje proces.  

1. Utwórz projekt.

   Wybierz pozycję **plik** > **Nowy** > **projekt**. W oknie dialogowym **Nowy projekt** C# rozwiń kategorie projektu języka (lub Visual Basic) w okienku **zainstalowane** typy projektów, wybierz pozycję **.NET Core**, a następnie w środkowym okienku wybierz szablon **Aplikacja konsolowa (.NET Core)** . Wprowadź nazwę projektu, na przykład "FDD", w polu tekstowym **Nazwa** . Wybierz przycisk **OK** .

1. Dodaj kod źródłowy aplikacji.

   Otwórz plik *program.cs* lub *program. vb* w edytorze i Zastąp automatycznie wygenerowany kod następującym kodem. Poprosi użytkownika o wprowadzenie tekstu i wyświetlenie pojedynczych słów wprowadzonych przez użytkownika. Używa wyrażenia regularnego `\w+`, aby rozdzielić słowa w tekście wejściowym.

   [!code-csharp[deployment#1](~/samples/snippets/core/deploying/cs/deployment-example.cs)]
   [!code-vb[deployment#1](~/samples/snippets/core/deploying/vb/deployment-example.vb)]

1. Utwórz kompilację debugowania aplikacji.

   Wybierz pozycję **kompilacja** > **Kompiluj rozwiązanie**. Możesz również skompilować i uruchomić kompilację debugowania aplikacji, wybierając pozycję **debuguj** > **Rozpocznij debugowanie**.

1. Wdróż aplikację.

   Po debugowaniu i przetestowaniu programu Utwórz pliki do wdrożenia przy użyciu aplikacji. Aby opublikować z programu Visual Studio, wykonaj następujące czynności:

      1. Zmień konfigurację rozwiązania z **Debuguj** na **Release** na pasku narzędzi, aby utworzyć wydanie (a nie debugowanie) wersji aplikacji.

      1. Kliknij prawym przyciskiem myszy projekt (a nie rozwiązanie) w **Eksplorator rozwiązań** i wybierz polecenie **Publikuj**.

      1. Na karcie **Publikowanie** wybierz pozycję **Publikuj**. Program Visual Studio zapisuje pliki wchodzące w skład aplikacji w lokalnym systemie plików.

      1. Karta **Publikowanie** zawiera teraz pojedynczy profil, **FolderProfile**. Ustawienia konfiguracji profilu są wyświetlane w sekcji **Podsumowanie** karty.

   Pliki otrzymane są umieszczane w katalogu o nazwie `Publish` w systemie Windows i `publish` w systemach UNIX, które znajdują się w podkatalogu podkatalogu *.\bin\release\netcoreapp2.1* projektu.

Podobnie jak w przypadku plików aplikacji, proces publikowania emituje plik bazy danych programu (. pdb), który zawiera informacje o debugowaniu aplikacji. Plik jest przydatny głównie do debugowania wyjątków. Możesz zrezygnować z spakowania go z plikami aplikacji. Należy jednak zapisać ją w zdarzeniu, które chcesz debugować kompilację wydania aplikacji.

Wdróż cały zestaw plików aplikacji w dowolny sposób. Na przykład możesz spakować je w pliku zip, użyć prostego polecenia `copy` lub wdrożyć je przy użyciu dowolnego wybranego pakietu instalacyjnego. Po zainstalowaniu użytkownicy mogą następnie wykonać swoją aplikację za pomocą polecenia `dotnet` i podać nazwę pliku aplikacji, taką jak `dotnet fdd.dll`.

Oprócz plików binarnych aplikacji Instalator powinien również powiązać Instalatora struktury udostępnionej lub sprawdzić go jako warunek wstępny w ramach instalacji aplikacji.  Instalacja struktury udostępnionej wymaga dostępu administratora/katalogu głównego, ponieważ jest to cały komputer.

## <a name="framework-dependent-deployment-with-third-party-dependencies"></a>Wdrożenie zależne od platformy z zależnościami innych firm

Wdrożenie wdrożenia zależnego od platformy z co najmniej jedną zależnością innej firmy wymaga, aby wszystkie zależności były dostępne dla projektu. Aby można było skompilować aplikację, wymagane są następujące dodatkowe kroki:

1. Użyj **Menedżera pakietów NuGet** , aby dodać odwołanie do pakietu NuGet do projektu; a jeśli pakiet nie jest jeszcze dostępny w systemie, zainstaluj go. Aby otworzyć Menedżera pakietów, wybierz pozycję **narzędzia** > **menedżer pakietów NuGet** > **Zarządzanie pakietami NuGet dla rozwiązania**.

1. Upewnij się, że zależności innych firm (na przykład `Newtonsoft.Json`) są zainstalowane w systemie i, jeśli nie, zainstaluj je. Karta **zainstalowane** zawiera listę pakietów NuGet zainstalowanych w systemie. Jeśli `Newtonsoft.Json` nie znajduje się na liście, wybierz kartę **Przeglądaj** i w polu wyszukiwania wprowadź ciąg "Newtonsoft. JSON". Wybierz pozycję `Newtonsoft.Json` i w prawym okienku wybierz swój projekt przed wybraniem opcji **Zainstaluj**.

1. Jeśli `Newtonsoft.Json` jest już zainstalowana w systemie, Dodaj ją do projektu, wybierając projekt w prawym okienku na karcie **Zarządzanie pakietami dla rozwiązania** .

Należy zauważyć, że wdrożenie zależne od platformy z zależnościami innych firm jest przenośne tylko jako elementy zależne od innych firm. Jeśli na przykład biblioteka innych firm obsługuje tylko macOS, aplikacja nie jest przenośna do systemów Windows. Dzieje się tak, jeśli zależność innej firmy zależy od kodu natywnego. Dobrym przykładem jest [serwer Kestrel](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel), który wymaga natywnej zależności od [libuv](https://github.com/libuv/libuv). Gdy FDD jest tworzona dla aplikacji z tym rodzajem zależności innych firm, opublikowane dane wyjściowe zawierają folder dla każdego [identyfikatora środowiska uruchomieniowego (RID)](../rid-catalog.md) , który obsługuje zależność natywną (i która istnieje w pakiecie NuGet).

## <a name="simpleSelf"></a>Samodzielne wdrażanie bez zależności innych firm

Wdrożenie samodzielnego wdrożenia bez zależności innych firm polega na tworzeniu projektu, modyfikowaniu pliku *csproj* , tworzeniu, testowaniu i publikowaniu aplikacji. Prosty przykład zapisaniem C# ilustruje proces. Zacznij od utworzenia, napisania i przetestowania projektu w taki sam sposób, jak w przypadku wdrożenia zależnego od platformy:

1. Utwórz projekt.

   Wybierz pozycję **plik** > **Nowy** > **projekt**. W oknie dialogowym **Nowy projekt** C# rozwiń kategorie projektu języka (lub Visual Basic) w okienku **zainstalowane** typy projektów, wybierz pozycję **.NET Core**, a następnie w środkowym okienku wybierz szablon **Aplikacja konsolowa (.NET Core)** . Wprowadź nazwę projektu, na przykład "SCD", w polu tekstowym **Nazwa** , a następnie wybierz przycisk **OK** .

1. Dodaj kod źródłowy aplikacji.

   Otwórz plik *program.cs* lub *program. vb* w edytorze i Zastąp automatycznie wygenerowany kod następującym kodem. Poprosi użytkownika o wprowadzenie tekstu i wyświetlenie pojedynczych słów wprowadzonych przez użytkownika. Używa wyrażenia regularnego `\w+`, aby rozdzielić słowa w tekście wejściowym.

   [!code-csharp[deployment#1](~/samples/snippets/core/deploying/cs/deployment-example.cs)]
   [!code-vb[deployment#1](~/samples/snippets/core/deploying/vb/deployment-example.vb)]

1. Określ, czy chcesz używać trybu niezmiennej globalizacji.

   Szczególnie jeśli aplikacja jest przeznaczona dla systemu Linux, można zmniejszyć łączny rozmiar wdrożenia, wykorzystując [tryb niezmienny globalizacji](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/globalization-invariant-mode.md). Tryb niezmiennej globalizacji jest przydatny w przypadku aplikacji, które nie są ogólnie obsługiwane i które mogą korzystać z Konwencji formatowania, konwencji dotyczących wielkości liter i porównywania ciągów oraz kolejności sortowania [niezmiennej kultury](xref:System.Globalization.CultureInfo.InvariantCulture).

   Aby włączyć tryb niezmienny, kliknij prawym przyciskiem myszy projekt (nie rozwiązanie) w **Eksplorator rozwiązań**i wybierz polecenie **Edytuj SCD. csproj** lub **Edytuj SCD. vbproj**. Następnie Dodaj następujące wyróżnione wiersze do pliku:

   [!code-xml[globalization-invariant-mode](~/samples/snippets/core/deploying/xml/invariant.csproj?highlight=6-8)]

1. Utwórz kompilację debugowania aplikacji.

   Wybierz pozycję **kompilacja** > **Kompiluj rozwiązanie**. Możesz również skompilować i uruchomić kompilację debugowania aplikacji, wybierając pozycję **debuguj** > **Rozpocznij debugowanie**. Ten krok debugowania pozwala identyfikować problemy z aplikacją, gdy jest ona uruchomiona na platformie hosta. Nadal będzie konieczne przetestowanie go na każdej platformie docelowej.

   Jeśli włączono tryb niezmienny globalizacji, należy sprawdzić, czy brak danych wrażliwych na kulturę jest odpowiednie dla aplikacji.

Po zakończeniu debugowania można opublikować własne wdrożenie:

<!-- markdownlint-disable MD025 -->

# <a name="visual-studio-156-and-earliertabvs156"></a>[Visual Studio 15,6 i starsze](#tab/vs156)

Po debugowaniu i przetestowaniu programu Utwórz pliki, które mają zostać wdrożone wraz z aplikacją dla każdej platformy, do której się odwołuje.

Aby opublikować aplikację z poziomu programu Visual Studio, wykonaj następujące czynności:

1. Zdefiniuj platformy, dla których aplikacja będzie docelowa.

   1. Kliknij prawym przyciskiem myszy projekt (nie rozwiązanie) w **Eksplorator rozwiązań** i wybierz polecenie **Edytuj SCD. csproj**.

   1. Utwórz tag `<RuntimeIdentifiers>` w sekcji `<PropertyGroup>` pliku *csproj* , który definiuje platformy, dla których aplikacja jest przeznaczona, i określ identyfikator czasu wykonywania (RID) dla każdej platformy docelowej. Należy pamiętać, że należy również dodać średnik, aby oddzielić RID. Listę identyfikatorów środowiska uruchomieniowego można znaleźć w [katalogu identyfikatorów środowiska uruchomieniowego](../rid-catalog.md) .

   Na przykład poniższy przykład wskazuje, że aplikacja działa w 64-bitowych systemach operacyjnych Windows 10 i 64-bitowy OS X Version 10,11 system operacyjny.

   ```xml
   <PropertyGroup>
      <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
   </PropertyGroup>
   ```

   Należy zauważyć, że element `<RuntimeIdentifiers>` może przejść do dowolnego `<PropertyGroup>`, które znajdują się w pliku *csproj* . Pełny przykładowy plik *csproj* pojawia się w dalszej części tej sekcji.

1. Opublikuj aplikację.

   Po debugowaniu i przetestowaniu programu Utwórz pliki, które mają zostać wdrożone wraz z aplikacją dla każdej platformy, do której się odwołuje.

   Aby opublikować aplikację z poziomu programu Visual Studio, wykonaj następujące czynności:

      1. Zmień konfigurację rozwiązania z **Debuguj** na **Release** na pasku narzędzi, aby utworzyć wydanie (a nie debugowanie) wersji aplikacji.

      1. Kliknij prawym przyciskiem myszy projekt (a nie rozwiązanie) w **Eksplorator rozwiązań** i wybierz polecenie **Publikuj**.

      1. Na karcie **Publikowanie** wybierz pozycję **Publikuj**. Program Visual Studio zapisuje pliki wchodzące w skład aplikacji w lokalnym systemie plików.

      1. Karta **Publikowanie** zawiera teraz pojedynczy profil, **FolderProfile**. Ustawienia konfiguracji profilu są wyświetlane w sekcji **Podsumowanie** na karcie. **docelowa wersja środowiska uruchomieniowego** określa, które środowisko uruchomieniowe zostało opublikowane, a **Lokalizacja docelowa** określa miejsce zapisania plików dla wdrożenia samodzielnego.

      1. Program Visual Studio domyślnie zapisuje wszystkie pliki opublikowane w jednym katalogu. Dla wygody najlepiej utworzyć osobne profile dla każdego docelowego środowiska uruchomieniowego i umieścić pliki opublikowane w katalogu specyficznym dla platformy. Obejmuje to utworzenie osobnego profilu publikowania dla każdej platformy docelowej. Teraz należy ponownie skompilować aplikację dla każdej platformy, wykonując następujące czynności:

         1. Wybierz pozycję **Utwórz nowy profil** w oknie dialogowym **publikowania** .

         1. W oknie dialogowym **Wybieranie elementu docelowego publikowania** Zmień lokalizację **Wybieranie lokalizacji folderu** na *bin\Release\PublishOutput\win10-x64*. Wybierz **przycisk OK**.

         1. Wybierz nowy profil (**FolderProfile1**) na liście profilów i upewnij się, że **docelowe środowisko uruchomieniowe** jest `win10-x64`. Jeśli nie, wybierz pozycję **Ustawienia**. W oknie dialogowym **Ustawienia profilu** Zmień **docelowy środowisko uruchomieniowe** na `win10-x64` i wybierz pozycję **Zapisz**. W przeciwnym razie wybierz pozycję **Anuluj**.

         1. Wybierz pozycję **Publikuj** , aby opublikować aplikację dla 64-bitowych platform Windows 10.

         1. Wykonaj ponownie powyższe kroki, aby utworzyć profil dla `osx.10.11-x64` platformy. **Lokalizacja docelowa** to *Bin\Release\PublishOutput\osx.10.11-x64*, a **docelowy środowisko uruchomieniowe** jest `osx.10.11-x64`. Nazwa, którą program Visual Studio przypisuje do tego profilu, to **FolderProfile2**.

      Należy pamiętać, że każda lokalizacja docelowa zawiera pełny zestaw plików (zarówno plików aplikacji, jak i wszystkich plików platformy .NET Core) potrzebnych do uruchomienia aplikacji.

Podobnie jak w przypadku plików aplikacji, proces publikowania emituje plik bazy danych programu (. pdb), który zawiera informacje o debugowaniu aplikacji. Plik jest przydatny głównie do debugowania wyjątków. Możesz zrezygnować z spakowania go z plikami aplikacji. Należy jednak zapisać ją w zdarzeniu, które chcesz debugować kompilację wydania aplikacji.

Wdróż opublikowane pliki w dowolny sposób. Na przykład możesz spakować je w pliku zip, użyć prostego polecenia `copy` lub wdrożyć je przy użyciu dowolnego wybranego pakietu instalacyjnego.

Poniżej znajduje się kompletny plik *csproj* dla tego projektu.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

# <a name="visual-studio-157-and-latertabvs157"></a>[Program Visual Studio 15,7 lub nowszy](#tab/vs157)

Po debugowaniu i przetestowaniu programu Utwórz pliki, które mają zostać wdrożone wraz z aplikacją dla każdej platformy, do której się odwołuje. Obejmuje to utworzenie osobnego profilu dla każdej platformy docelowej.

Dla każdej platformy, która jest przeznaczona dla aplikacji, wykonaj następujące czynności:

1. Utwórz profil dla platformy docelowej.

   Jeśli jest to pierwszy utworzony profil, kliknij prawym przyciskiem myszy projekt (a nie rozwiązanie) w **Eksplorator rozwiązań** i wybierz polecenie **Publikuj**.

   Jeśli utworzono już profil, kliknij prawym przyciskiem myszy projekt, aby otworzyć okno dialogowe **publikowania** , jeśli nie jest jeszcze otwarte. Następnie wybierz pozycję **Nowy profil**.

   Zostanie otwarte okno dialogowe **Wybieranie elementu docelowego publikowania** .
  
1. Wybierz lokalizację, w której program Visual Studio opublikuje aplikację.

   W przypadku publikowania tylko na jednej platformie można zaakceptować wartość domyślną w polu tekstowym **Wybierz folder** . publikuje zależne od platformy wdrożenie aplikacji do *\<katalogu projektu > katalogu \bin\Release\netcoreapp2.1\publish* .

   Jeśli publikujesz na więcej niż jednej platformie, dołącz ciąg, który identyfikuje platformę docelową. Na przykład jeśli dołączysz ciąg "Linux" do ścieżki pliku, program Visual Studio opublikuje zależne od platformy wdrożenie aplikacji do *\<Project-directory > Directory \bin\Release\netcoreapp2.1\publish\linux* .

1. Utwórz profil, wybierając ikonę listy rozwijanej obok przycisku **Publikuj** i wybierając pozycję **Utwórz profil**. Następnie wybierz przycisk **Utwórz profil** , aby utworzyć profil.

1. Wskaż, że publikujesz wdrożenie samodzielne i zdefiniujesz platformę, w której aplikacja będzie docelowa.

   1. W oknie dialogowym **Publikowanie** wybierz link **Konfiguruj** , aby otworzyć okno dialogowe **Ustawienia profilu** .

   1. W polu listy **Tryb wdrożenia** wybierz pozycję **samodzielna** .

   1. W polu listy **cel środowiska uruchomieniowego** wybierz jedną z platform, do której należy aplikacja.

   1. Wybierz pozycję **Zapisz** , aby zaakceptować zmiany i zamknąć okno dialogowe.

1. Nazwij swój profil.

   1. Wybierz **Akcje** , > **zmienić nazwy profilu** , aby określić nazwę profilu.

   2. Przypisz do profilu nazwę identyfikującą platformę docelową, a następnie wybierz pozycję **Zapisz*.

Powtórz te kroki, aby zdefiniować wszelkie dodatkowe Platformy docelowe, do których odwołuje się aplikacja.

Twoje profile zostały skonfigurowane i są teraz gotowe do opublikowania aplikacji. W tym celu:

   1. Jeśli okno **publikowania** nie jest aktualnie otwarte, kliknij prawym przyciskiem myszy projekt (a nie rozwiązanie) w **Eksplorator rozwiązań** i wybierz polecenie **Publikuj**.

   2. Wybierz profil, który chcesz opublikować, a następnie wybierz pozycję **Publikuj**. Zrób to dla każdego profilu do opublikowania.

   Należy pamiętać, że każda lokalizacja docelowa (w przypadku naszego przykładu bin\release\netcoreapp2.1\publish\\*Profile-Name* zawiera kompletny zestaw plików (zarówno plików aplikacji, jak i wszystkich plików platformy .NET Core) potrzebnych do uruchomienia aplikacji.

Podobnie jak w przypadku plików aplikacji, proces publikowania emituje plik bazy danych programu (. pdb), który zawiera informacje o debugowaniu aplikacji. Plik jest przydatny głównie do debugowania wyjątków. Możesz zrezygnować z spakowania go z plikami aplikacji. Należy jednak zapisać ją w zdarzeniu, które chcesz debugować kompilację wydania aplikacji.

Wdróż opublikowane pliki w dowolny sposób. Na przykład możesz spakować je w pliku zip, użyć prostego polecenia `copy` lub wdrożyć je przy użyciu dowolnego wybranego pakietu instalacyjnego.

Poniżej znajduje się kompletny plik *csproj* dla tego projektu.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
  </PropertyGroup>
</Project>
```

Ponadto program Visual Studio tworzy oddzielny profil publikacji (\*. pubxml) dla każdej platformy docelowej. Na przykład plik z naszym profilem systemu Linux (Linux. pubxml) jest wyświetlany w następujący sposób:

```xml
<?xml version="1.0" encoding="utf-8"?>
<!--
https://go.microsoft.com/fwlink/?LinkID=208121. 
-->
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <PropertyGroup>
    <PublishProtocol>FileSystem</PublishProtocol>
    <Configuration>Release</Configuration>
    <Platform>Any CPU</Platform>
    <TargetFramework>netcoreapp2.1</TargetFramework>
    <PublishDir>bin\Release\netcoreapp2.1\publish\linux</PublishDir>
    <RuntimeIdentifier>win-x86</RuntimeIdentifier>
    <SelfContained>true</SelfContained>
    <_IsPortable>false</_IsPortable>
  </PropertyGroup>
</Project>
```

---

## <a name="self-contained-deployment-with-third-party-dependencies"></a>Samodzielne wdrożenie z zależnościami innych firm

Wdrożenie samodzielnego wdrożenia z co najmniej jedną zależnością innych firm obejmuje dodanie zależności. Aby można było skompilować aplikację, wymagane są następujące dodatkowe kroki:

1. Użyj **Menedżera pakietów NuGet** , aby dodać odwołanie do pakietu NuGet do projektu; a jeśli pakiet nie jest jeszcze dostępny w systemie, zainstaluj go. Aby otworzyć Menedżera pakietów, wybierz pozycję **narzędzia** > **menedżer pakietów NuGet** > **Zarządzanie pakietami NuGet dla rozwiązania**.

1. Upewnij się, że zależności innych firm (na przykład `Newtonsoft.Json`) są zainstalowane w systemie i, jeśli nie, zainstaluj je. Karta **zainstalowane** zawiera listę pakietów NuGet zainstalowanych w systemie. Jeśli `Newtonsoft.Json` nie znajduje się na liście, wybierz kartę **Przeglądaj** i w polu wyszukiwania wprowadź ciąg "Newtonsoft. JSON". Wybierz pozycję `Newtonsoft.Json` i w prawym okienku wybierz swój projekt przed wybraniem opcji **Zainstaluj**.

1. Jeśli `Newtonsoft.Json` jest już zainstalowana w systemie, Dodaj ją do projektu, wybierając projekt w prawym okienku na karcie **Zarządzanie pakietami dla rozwiązania** .

Poniżej znajduje się kompletny plik *csproj* dla tego projektu:

# <a name="visual-studio-156-and-earliertabvs156"></a>[Visual Studio 15,6 i starsze](#tab/vs156)

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
  </ItemGroup>
</Project>
```

# <a name="visual-studio-157-and-latertabvs157"></a>[Program Visual Studio 15,7 lub nowszy](#tab/vs157)

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
  </ItemGroup>
</Project>
```

---

Podczas wdrażania aplikacji wszystkie zależności innych firm używane w aplikacji również są zawarte w plikach aplikacji. Biblioteki innych firm nie są wymagane w systemie, w którym jest uruchomiona aplikacja.

Należy pamiętać, że wdrożenie z niezależnym programem można wdrożyć tylko z bibliotekami innych firm na platformach obsługiwanych przez tę bibliotekę. Jest to podobne do występowania zależności innych firm z natywnymi zależnościami w ramach wdrożenia zależnego od platformy, w przypadku których natywne zależności nie będą istniały na platformie docelowej, chyba że zostały wcześniej zainstalowane.

## <a name="see-also"></a>Zobacz także

- [Wdrażanie aplikacji .NET Core](index.md)
- [Wykaz identyfikatorów środowiska uruchomieniowego platformy .NET Core (RID)](../rid-catalog.md)
