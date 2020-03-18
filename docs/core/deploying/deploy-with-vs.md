---
title: Wdrażanie aplikacji .NET Core za pomocą programu Visual Studio
description: Dowiedz się, jak wdrożyć aplikację .NET Core za pomocą programu Visual Studio.
ms.date: 09/03/2018
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 11a322278ce3ff38964fe2fa389e0b4a58897ec4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77449026"
---
# <a name="deploy-net-core-apps-with-visual-studio"></a>Wdrażanie aplikacji .NET Core za pomocą programu Visual Studio

Aplikację .NET Core można wdrożyć jako *wdrożenie zależne od struktury,* które obejmuje pliki binarne aplikacji, ale zależy od obecności programu .NET Core w systemie docelowym lub jako *samodzielne wdrożenie,* które obejmuje zarówno aplikację, jak i pliki binarne .NET Core. Aby zapoznać się z omówieniem wdrażania aplikacji .NET Core, zobacz [Wdrażanie aplikacji podstawowej .NET](index.md).

W poniższych sekcjach przedstawiono sposób tworzenia następujących rodzajów wdrożeń za pomocą programu Microsoft Visual Studio:

- Wdrożenie zależne od struktury
- Wdrożenie zależne od struktury z zależnościami innych firm
- Samodzielne wdrażanie
- Samodzielne wdrażanie z zależnościami innych firm

Aby uzyskać informacje dotyczące tworzenia aplikacji .NET Core za pomocą programu Visual Studio, zobacz [zależności i wymagania programu .NET Core](../install/dependencies.md?pivots=os-windows).

## <a name="framework-dependent-deployment"></a>Wdrożenie zależne od struktury

Wdrażanie wdrożenia zależneod struktury bez zależności innych firm po prostu polega na tworzeniu, testowania i publikowania aplikacji. Prosty przykład napisany w języku C# ilustruje proces.

1. Utwórz projekt.

   Wybierz **pozycję Plik** > **nowy** > **projekt**. W oknie dialogowym **Nowy projekt** rozwiń kategorie projektów języka (C# lub Visual Basic) w okienku **Zainstalowane** typy projektów wybierz pozycję **.NET Core**, a następnie wybierz szablon aplikacji konsoli **(.NET Core)** w środkowym okienku. Wprowadź nazwę projektu, na przykład "FDD", w polu tekstowym **Nazwa.** Wybierz przycisk **OK**.

1. Dodaj kod źródłowy aplikacji.

   Otwórz *plik Program.cs* lub *Program.vb* w edytorze i zastąp automatycznie wygenerowany kod następującym kodem. Monituje użytkownika o wprowadzenie tekstu i wyświetla poszczególne słowa wprowadzone przez użytkownika. Używa wyrażenia `\w+` regularnego do oddzielenia wyrazów w tekście wejściowym.

   [!code-csharp[deployment#1](~/samples/snippets/core/deploying/cs/deployment-example.cs)]
   [!code-vb[deployment#1](~/samples/snippets/core/deploying/vb/deployment-example.vb)]

1. Utwórz kompilację debugowania aplikacji.

   Wybierz **rozwiązanie kompilacji** > **Build Solution**. Można również skompilować i uruchomić kompilację debugowania aplikacji, wybierając **debugowanie** > **Rozpocznij debugowanie**.

1. Wdrażanie aplikacji.

   Po debugowania i przetestowaniu programu utwórz pliki do wdrożenia w aplikacji. Aby opublikować z programu Visual Studio, wykonaj następujące czynności:

      1. Zmień konfigurację rozwiązania z **Debug** do **Wydania** na pasku narzędzi, aby utworzyć wersję (a nie debugowanie) wersji aplikacji.

      1. Kliknij prawym przyciskiem myszy projekt (nie rozwiązanie) w **Eksploratorze rozwiązań** i wybierz polecenie **Publikuj**.

      1. Na karcie **Publikowanie** wybierz pozycję **Publikuj**. Program Visual Studio zapisuje pliki, które składają się na aplikację do lokalnego systemu plików.

      1. Na karcie **Publikuj** jest teraz wyświetlany pojedynczy **profil, FolderProfile**. Ustawienia konfiguracji profilu są wyświetlane w sekcji **Podsumowanie** na karcie.

   Pliki wynikowe są umieszczane `Publish` w `publish` katalogu o nazwie w systemie Windows i w systemach Unix, który znajduje się w podkatalogu podkatalogu projektu *.\bin\release\netcoreapp2.1.*

Wraz z plikami aplikacji proces publikowania emituje plik bazy danych programu (pdb), który zawiera informacje o debugowaniu aplikacji. Plik jest przydatny głównie do debugowania wyjątków. Można wybrać, aby nie pakować go z plikami aplikacji. Należy jednak zapisać go w przypadku, gdy chcesz debugować kompilacji wersji aplikacji.

Wdrażaj kompletny zestaw plików aplikacji w dowolny sposób. Na przykład można spakować je w pliku `copy` Zip, użyć prostego polecenia lub wdrożyć je z dowolnego pakietu instalacyjnego do wyboru. Po zainstalowaniu użytkownicy mogą następnie wykonać `dotnet` aplikację za pomocą polecenia i `dotnet fdd.dll`podając nazwę pliku aplikacji, takich jak .

Oprócz plików binarnych aplikacji instalator powinien również łączyć instalator udostępnionej struktury lub sprawdzać go jako warunek wstępny w ramach instalacji aplikacji.  Instalacja udostępnionej struktury wymaga dostępu administratora/katalogu głównego, ponieważ jest dostępna na całym komputerze.

## <a name="framework-dependent-deployment-with-third-party-dependencies"></a>Wdrożenie zależne od struktury z zależnościami innych firm

Wdrażanie wdrożenia zależneod struktury z co najmniej jedną zależnościami innych firm wymaga, aby wszystkie zależności były dostępne dla projektu. Aby można było utworzyć aplikację, wymagane są następujące dodatkowe kroki:

1. Użyj **Menedżera pakietów NuGet,** aby dodać odwołanie do pakietu NuGet do projektu; a jeśli pakiet nie jest jeszcze dostępny w systemie, zainstaluj go. Aby otworzyć menedżera pakietów, wybierz **narzędzia** > **NuGet Package Manager** > **Manage NuGet Packages for Solution**.

1. Upewnij się, że zależności innych firm `Newtonsoft.Json`(na przykład) są zainstalowane w systemie i, jeśli nie są, zainstaluj je. **Zainstalowana** karta zawiera listę pakietów NuGet zainstalowanych w systemie. Jeśli `Newtonsoft.Json` nie ma tam na liście, wybierz kartę **Przeglądaj** i wpisz "Newtonsoft.Json" w polu wyszukiwania. Zaznacz `Newtonsoft.Json` i w prawym okienku wybierz projekt przed wybraniem **opcji Zainstaluj**.

1. Jeśli `Newtonsoft.Json` jest już zainstalowany w systemie, dodaj go do projektu, wybierając projekt w prawym okienku karty **Zarządzanie pakietami dla rozwiązania.**

Wdrożenie zależne od struktury z zależnościami innych firm jest tylko tak przenośne, jak jego zależności innych firm. Jeśli na przykład biblioteka innej firmy obsługuje tylko system macOS, nie jest przenośna w systemach Windows. Dzieje się tak, jeśli zależność innej firmy sama zależy od kodu macierzystego. Dobrym tego przykładem jest [serwer Kestrel](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel), który wymaga natywnej zależności od [libuv](https://github.com/libuv/libuv). Gdy fdd jest tworzony dla aplikacji z tego rodzaju zależności innych firm, opublikowane dane wyjściowe zawiera folder dla każdego [identyfikatora wykonywania (RID),](../rid-catalog.md) który obsługuje zależności macierzystej (i który istnieje w pakiecie NuGet).

## <a name="simpleSelf"></a>Samodzielne wdrażanie bez zależności innych firm

Wdrażanie samodzielnego wdrożenia bez zależności innych firm wiąże się z tworzeniem projektu, modyfikowaniem pliku *csproj,* tworzeniem, testowaniem i publikowaniem aplikacji. Prosty przykład napisany w języku C# ilustruje proces. Rozpoczynasz od tworzenia, kodowania i testowania projektu tak samo, jak wdrożenie zależne od struktury:

1. Utwórz projekt.

   Wybierz **pozycję Plik** > **nowy** > **projekt**. W oknie dialogowym **Nowy projekt** rozwiń kategorie projektów języka (C# lub Visual Basic) w okienku **Zainstalowane** typy projektów wybierz pozycję **.NET Core**, a następnie wybierz szablon aplikacji konsoli **(.NET Core)** w środkowym okienku. Wprowadź nazwę projektu, na przykład "SCD", w polu tekstowym **Nazwa** i wybierz przycisk **OK.**

1. Dodaj kod źródłowy aplikacji.

   Otwórz *plik Program.cs* lub *Program.vb* w edytorze i zastąp automatycznie wygenerowany kod następującym kodem. Monituje użytkownika o wprowadzenie tekstu i wyświetla poszczególne słowa wprowadzone przez użytkownika. Używa wyrażenia `\w+` regularnego do oddzielenia wyrazów w tekście wejściowym.

   [!code-csharp[deployment#1](~/samples/snippets/core/deploying/cs/deployment-example.cs)]
   [!code-vb[deployment#1](~/samples/snippets/core/deploying/vb/deployment-example.vb)]

1. Określ, czy chcesz użyć trybu niezmiennego globalizacji.

   Szczególnie jeśli aplikacja jest przeznaczona dla systemu Linux, można zmniejszyć całkowity rozmiar wdrożenia, korzystając z [trybu niezmiennego globalizacji.](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md) Tryb niezmienny globalizacji jest przydatny w przypadku aplikacji, które nie są globalnie świadome i które mogą używać konwencji formatowania, konwencji wielkości liter oraz porównania i sortowania ciągów [kultury niezmiennej.](xref:System.Globalization.CultureInfo.InvariantCulture)

   Aby włączyć tryb niezmienny, kliknij prawym przyciskiem myszy projekt (nie rozwiązanie) w **Eksploratorze rozwiązań**i wybierz polecenie **Edit SCD.csproj** lub **Edit SCD.vbproj**. Następnie dodaj do pliku następujące wyróżnione wiersze:

   [!code-xml[globalization-invariant-mode](~/samples/snippets/core/deploying/xml/invariant.csproj?highlight=6-8)]

1. Utwórz kompilację debugowania aplikacji.

   Wybierz **rozwiązanie kompilacji** > **Build Solution**. Można również skompilować i uruchomić kompilację debugowania aplikacji, wybierając **debugowanie** > **Rozpocznij debugowanie**. Ten krok debugowania umożliwia identyfikowanie problemów z aplikacją, gdy jest uruchomiona na platformie hosta. Nadal będziesz musiał przetestować go na każdej z platform docelowych.

   Jeśli włączysz tryb niezmienny globalizacji, należy szczególnie sprawdzić, czy brak danych zależnych od kultury jest odpowiedni dla aplikacji.

Po zakończeniu debugowania można opublikować wdrożenie niezależne:

<!-- markdownlint-disable MD025 -->

# <a name="visual-studio-156-and-earlier"></a>[Visual Studio 15.6 i wcześniejsze](#tab/vs156)

Po debugowania i przetestowaniu programu, utwórz pliki do wdrożenia z aplikacją dla każdej platformy, na której jest przeznaczona.

Aby opublikować aplikację z programu Visual Studio, wykonaj następujące czynności:

1. Zdefiniuj platformy, na które będzie kierować aplikacja.

   1. Kliknij prawym przyciskiem myszy projekt (nie rozwiązanie) w **Eksploratorze rozwiązań** i wybierz **polecenie Edit SCD.csproj**.

   1. Utwórz `<RuntimeIdentifiers>` tag `<PropertyGroup>` w sekcji pliku *csproj,* który definiuje platformy, których dotyczy aplikacja, i określ identyfikator czasu wykonywania (RID) każdej platformy docelowej. Należy również dodać średnik, aby oddzielić identyfikatory IDENTYFIKATORY. Zobacz [katalog identyfikatorów identyfikatorów](../rid-catalog.md) środowiska uruchomieniowego.

   Na przykład poniższy przykład wskazuje, że aplikacja działa w 64-bitowych systemach operacyjnych Windows 10 i 64-bitowym systemie operacyjnym OS X w wersji 10.11.

   ```xml
   <PropertyGroup>
      <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
   </PropertyGroup>
   ```

   Element `<RuntimeIdentifiers>` może przejść `<PropertyGroup>` do każdego, który masz w pliku *csproj.* Pełny przykładowy plik *csproj* pojawi się w dalszej części tej sekcji.

1. Opublikuj aplikację.

   Po debugowania i przetestowaniu programu, utwórz pliki do wdrożenia z aplikacją dla każdej platformy, na której jest przeznaczona.

   Aby opublikować aplikację z programu Visual Studio, wykonaj następujące czynności:

      1. Zmień konfigurację rozwiązania z **Debug** do **Wydania** na pasku narzędzi, aby utworzyć wersję (a nie debugowanie) wersji aplikacji.

      1. Kliknij prawym przyciskiem myszy projekt (nie rozwiązanie) w **Eksploratorze rozwiązań** i wybierz polecenie **Publikuj**.

      1. Na karcie **Publikowanie** wybierz pozycję **Publikuj**. Program Visual Studio zapisuje pliki, które składają się na aplikację do lokalnego systemu plików.

      1. Na karcie **Publikuj** jest teraz wyświetlany pojedynczy **profil, FolderProfile**. Ustawienia konfiguracji profilu są wyświetlane w sekcji **Podsumowanie** na karcie. **Docelowy czas wykonywania** identyfikuje, który czas wykonywania został opublikowany, a **lokalizacja docelowa** określa, gdzie zostały zapisane pliki dla samodzielnego wdrożenia.

      1. Program Visual Studio domyślnie zapisuje wszystkie opublikowane pliki w jednym katalogu. Dla wygody najlepiej jest utworzyć oddzielne profile dla każdego docelowego czasu wykonywania i umieścić opublikowane pliki w katalogu specyficznym dla platformy. Obejmuje to utworzenie oddzielnego profilu publikowania dla każdej platformy docelowej. Więc teraz odbudować aplikację dla każdej platformy, wykonując następujące czynności:

         1. Wybierz **pozycję Utwórz nowy profil** w oknie dialogowym **Publikowanie.**

         1. W oknie **dialogowym Wybieranie obiektu docelowego publikowania** zmień pozycję **Wybierz lokalizację folderu** do *kosza\Release\PublishOutput\win10-x64*. Kliknij przycisk **OK**.

         1. Wybierz nowy profil **(FolderProfile1)** na liście profilów i upewnij się, `win10-x64`że docelowy czas **wykonywania** jest . Jeśli tak nie jest, wybierz **pozycję Ustawienia**. W oknie dialogowym **Ustawienia profilu** zmień docelowy **czas wykonywania** i `win10-x64` wybierz pozycję **Zapisz**. W przeciwnym razie wybierz **pozycję Anuluj**.

         1. Wybierz **pozycję Publikuj,** aby opublikować aplikację dla 64-bitowych platform systemu Windows 10.

         1. Wykonaj ponownie poprzednie kroki, aby `osx.10.11-x64` utworzyć profil dla platformy. **Lokalizacja docelowa** to *bin\Release\PublishOutput\osx.10.11-x64*, a `osx.10.11-x64`docelowy **m.in.** Nazwa, którą program Visual Studio przypisuje do tego profilu, to **FolderProfile2**.

      Każda lokalizacja docelowa zawiera kompletny zestaw plików (zarówno plików aplikacji, jak i wszystkich plików .NET Core) potrzebnych do uruchomienia aplikacji.

Wraz z plikami aplikacji proces publikowania emituje plik bazy danych programu (pdb), który zawiera informacje o debugowaniu aplikacji. Plik jest przydatny głównie do debugowania wyjątków. Można wybrać, aby nie pakować go z plikami aplikacji. Należy jednak zapisać go w przypadku, gdy chcesz debugować kompilacji wersji aplikacji.

Wdrażaj opublikowane pliki w dowolny sposób. Na przykład można spakować je w pliku `copy` Zip, użyć prostego polecenia lub wdrożyć je z dowolnego pakietu instalacyjnego do wyboru.

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

# <a name="visual-studio-157-and-later"></a>[Visual Studio 15.7 i nowsze](#tab/vs157)

Po debugowania i przetestowaniu programu, utwórz pliki do wdrożenia z aplikacją dla każdej platformy, na której jest przeznaczona. Wiąże się to z utworzeniem oddzielnego profilu dla każdej platformy docelowej.

Dla każdej platformy, na którą dotyczy aplikacji, wykonaj następujące czynności:

1. Utwórz profil dla swojej platformy docelowej.

   Jeśli jest to pierwszy utworzony profil, kliknij prawym przyciskiem myszy projekt (nie rozwiązanie) w **Eksploratorze rozwiązań** i wybierz polecenie **Publikuj**.

   Jeśli profil został już utworzony, kliknij prawym przyciskiem myszy projekt, aby otworzyć okno **dialogowe Publikowanie,** jeśli nie jest jeszcze otwarty. Następnie wybierz **pozycję Nowy profil**.

   Zostanie otwarte okno **dialogowe Wybieranie obiektu docelowego publikowania.**

1. Wybierz lokalizację, w której program Visual Studio publikuje aplikację.

   Jeśli publikujesz tylko na jednej platformie, możesz zaakceptować wartość domyślną w polu **tekstowym Wybierz folder;** spowoduje to opublikowanie wdrożenia aplikacji zależnego od struktury w * \<katalogu projektu>\bin\Release\netcoreapp2.1\publish* directory.

   Jeśli publikujesz na więcej niż jednej platformie, dołącz ciąg, który identyfikuje platformę docelową. Na przykład jeśli dościeżnica pliku zostanie dołączona ciąg "linux", program Visual Studio opublikuje zależne od struktury wdrożenie aplikacji do * \<katalogu projektu>\bin\Release\netcoreapp2.1\publish\linux.*

1. Utwórz profil, wybierając ikonę listy rozwijanej obok przycisku **Publikuj** i wybierając pozycję **Utwórz profil**. Następnie wybierz przycisk **Utwórz profil,** aby utworzyć profil.

1. Wskaż, że publikujesz niezależne wdrożenie i zdefiniuj platformę, na którą będzie kierować aplikację.

   1. W oknie **dialogowym Publikowanie** wybierz łącze **Konfigurowanie,** aby otworzyć okno dialogowe **Ustawienia profilu.**

   1. Wybierz **opcję Samodzielne w** polu listy Tryb **wdrażania.**

   1. W polu listy **Docelowe uruchomienie** wybierz jedną z platform, na których znajduje się aplikacja.

   1. Wybierz **pozycję Zapisz,** aby zaakceptować zmiany i zamknij okno dialogowe.

1. Nazwij swój profil.

   1. Wybierz **pozycję Akcje** > **Zmień nazwę profilu,** aby nazwać swój profil.

   2. Przypisz profil nazwę identyfikującą platformę docelową, a następnie wybierz **Zapisz*.

Powtórz te kroki, aby zdefiniować wszelkie dodatkowe platformy docelowe, które są przeznaczone dla aplikacji.

Skonfigurowato swoje profile i są teraz gotowe do opublikowania aplikacji. W tym celu:

   1. Jeśli okno **Publikowania** nie jest aktualnie otwarte, kliknij prawym przyciskiem myszy projekt (nie rozwiązanie) w **Eksploratorze rozwiązań** i wybierz polecenie **Publikuj**.

   2. Wybierz profil, który chcesz opublikować, a następnie wybierz **pozycję Publikuj**. Zrób to dla każdego profilu, który ma zostać opublikowany.

   Każda lokalizacja docelowa (w naszym przykładzie bin\release\netcoreapp2.1\publish\\*profile-name* zawiera kompletny zestaw plików (zarówno plików aplikacji, jak i wszystkich plików .NET Core) potrzebnych do uruchomienia aplikacji.

Wraz z plikami aplikacji proces publikowania emituje plik bazy danych programu (pdb), który zawiera informacje o debugowaniu aplikacji. Plik jest przydatny głównie do debugowania wyjątków. Można wybrać, aby nie pakować go z plikami aplikacji. Należy jednak zapisać go w przypadku, gdy chcesz debugować kompilacji wersji aplikacji.

Wdrażaj opublikowane pliki w dowolny sposób. Na przykład można spakować je w pliku `copy` Zip, użyć prostego polecenia lub wdrożyć je z dowolnego pakietu instalacyjnego do wyboru.

Poniżej znajduje się kompletny plik *csproj* dla tego projektu.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
  </PropertyGroup>
</Project>
```

Ponadto visual studio tworzy oddzielny profil\*publikowania (.pubxml) dla każdej platformy, na którą kierujesz. Na przykład plik dla naszego profilu linuksa (linux.pubxml) pojawia się w następujący sposób:

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

## <a name="self-contained-deployment-with-third-party-dependencies"></a>Samodzielne wdrażanie z zależnościami innych firm

Wdrażanie samodzielnego wdrożenia z co najmniej jedną zależnościami innych firm polega na dodawaniu zależności. Aby można było utworzyć aplikację, wymagane są następujące dodatkowe kroki:

1. Użyj **Menedżera pakietów NuGet,** aby dodać odwołanie do pakietu NuGet do projektu; a jeśli pakiet nie jest jeszcze dostępny w systemie, zainstaluj go. Aby otworzyć menedżera pakietów, wybierz **narzędzia** > **NuGet Package Manager** > **Manage NuGet Packages for Solution**.

1. Upewnij się, że zależności innych firm `Newtonsoft.Json`(na przykład) są zainstalowane w systemie i, jeśli nie są, zainstaluj je. **Zainstalowana** karta zawiera listę pakietów NuGet zainstalowanych w systemie. Jeśli `Newtonsoft.Json` nie ma tam na liście, wybierz kartę **Przeglądaj** i wpisz "Newtonsoft.Json" w polu wyszukiwania. Zaznacz `Newtonsoft.Json` i w prawym okienku wybierz projekt przed wybraniem **opcji Zainstaluj**.

1. Jeśli `Newtonsoft.Json` jest już zainstalowany w systemie, dodaj go do projektu, wybierając projekt w prawym okienku karty **Zarządzanie pakietami dla rozwiązania.**

Poniżej znajduje się kompletny plik *csproj* dla tego projektu:

# <a name="visual-studio-156-and-earlier"></a>[Visual Studio 15.6 i wcześniejsze](#tab/vs156)

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

# <a name="visual-studio-157-and-later"></a>[Visual Studio 15.7 i nowsze](#tab/vs157)

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

Podczas wdrażania aplikacji wszelkie zależności innych firm używane w aplikacji są również zawarte z plikami aplikacji. Biblioteki innych firm nie są wymagane w systemie, w którym aplikacja jest uruchomiona.

Wdrożenie samodzielne można wdrażać tylko z biblioteką innych firm na platformach obsługiwanych przez tę bibliotekę. Jest to podobne do zależności innych firm z zależnościami macierzystymi we wdrożeniu zależnym od struktury, gdzie zależności macierzyste nie będą istnieć na platformie docelowej, chyba że zostały wcześniej tam zainstalowane.

## <a name="see-also"></a>Zobacz też

- [Wdrożenie aplikacji podstawowej .NET](index.md)
- [Wykaz identyfikatora środowiska uruchomienionowego programu .NET Core (RID)](../rid-catalog.md)
