---
title: Wdrażanie aplikacji .NET Core za pomocą programu Visual Studio
description: Dowiedz się, jak wdrożyć aplikację .NET Core w programie Visual Studio.
ms.date: 09/03/2018
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: f2299ac807c845dab482306cc4c710560bb7f1e7
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607865"
---
# <a name="deploy-net-core-apps-with-visual-studio"></a>Wdrażanie aplikacji .NET Core za pomocą programu Visual Studio

Aplikację .NET Core można wdrożyć jako *wdrożenie zależne od struktury,* które zawiera pliki binarne aplikacji, ale zależy od obecności programu .NET Core w systemie docelowym lub jako *samodzielne wdrożenie,* które obejmuje zarówno pliki binarne aplikacji, jak i rdzenia .NET. Aby zapoznać się z omówieniem wdrażania aplikacji .NET Core, zobacz [.NET Core Application Deployment](index.md).

W poniższych sekcjach pokazano, jak używać programu Microsoft Visual Studio do tworzenia następujących rodzajów wdrożeń:

- Wdrożenie zależne od struktury
- Wdrożenie zależne od struktury z zależnościami innych firm
- Samodzielne wdrożenie
- Samodzielne wdrażanie z zależnościami innych firm

Aby uzyskać informacje na temat tworzenia aplikacji .NET Core za pomocą programu Visual Studio, zobacz [zależności i wymagania dotyczące rdzenia .NET](../install/dependencies.md?pivots=os-windows).

## <a name="framework-dependent-deployment"></a>Wdrożenie zależne od struktury

Wdrażanie wdrożenia zależnego od struktury bez zależności innych firm po prostu obejmuje tworzenie, testowanie i publikowanie aplikacji. Prosty przykład napisany w języku C# ilustruje proces.

1. Utwórz projekt.

   Wybierz **pozycję Plik** > **nowy** > **projekt**. W oknie dialogowym **Nowy projekt** rozwiń kategorie projektów języka (C# lub Visual Basic) w okienku **Zainstalowane** typy projektów, wybierz pozycję **.NET Core**, a następnie wybierz szablon Aplikacja konsoli **(.NET Core)** w środkowym okienku. Wprowadź nazwę projektu, taką jak "FDD", w polu tekstowym **Nazwa.** Wybierz przycisk **OK**.

1. Dodaj kod źródłowy aplikacji.

   Otwórz *plik Program.cs* lub *Program.vb* w edytorze i zastąp automatyczniegenerowany kod następującym kodem. Monituje użytkownika o wprowadzenie tekstu i wyświetla poszczególne słowa wprowadzone przez użytkownika. Używa wyrażenia `\w+` regularnego do oddzielenia wyrazów w tekście wejściowym.

   [!code-csharp[deployment#1](~/samples/snippets/core/deploying/cs/deployment-example.cs)]
   [!code-vb[deployment#1](~/samples/snippets/core/deploying/vb/deployment-example.vb)]

1. Utwórz kompilację debugowania aplikacji.

   Wybierz **opcję Zbuduj** > **rozwiązanie kompilacji**. Można również skompilować i uruchomić kompilację debugowania aplikacji, wybierając **debugowanie** > **start debugowania**.

1. Wdrażanie aplikacji.

   Po debugowanie i przetestowanie programu, należy utworzyć pliki, które mają być wdrożone z aplikacją. Aby opublikować z programu Visual Studio, wykonaj następujące czynności:

      1. Zmień konfigurację rozwiązania z **Debugowania** na **Zwolnij** na pasku narzędzi, aby utworzyć wersję aplikacji w wersji (a nie debugowania).

      1. Kliknij prawym przyciskiem myszy projekt (nie rozwiązanie) w **Eksploratorze rozwiązań** i wybierz pozycję **Publikuj**.

      1. Na karcie **Publikowanie** wybierz pozycję **Publikuj**. Visual Studio zapisuje pliki, które składają się na aplikację do lokalnego systemu plików.

      1. Na karcie **Publikowanie** jest teraz wyświetlany pojedynczy profil **FolderProfile**. Ustawienia konfiguracji profilu są wyświetlane w sekcji **Podsumowanie** na karcie.

   Wynikowe pliki są umieszczane w `Publish` katalogu `publish` o nazwie w systemie Windows i w systemach Unix, który znajduje się w podkatalogu projektu *.\bin\release\netcoreapp2.1.*

Wraz z plikami aplikacji proces publikowania emituje plik bazy danych programu (pdb), który zawiera informacje debugowania o aplikacji. Plik jest przydatny przede wszystkim do debugowania wyjątków. Można wybrać opcję niepakować go z plikami aplikacji. Należy jednak zapisać go w przypadku, gdy chcesz debugować kompilacji wersji aplikacji.

Wdrażaj kompletny zestaw plików aplikacji w dowolny sposób. Na przykład można spakować je w pliku `copy` Zip, użyć prostego polecenia lub wdrożyć je z dowolnego pakietu instalacyjnego do wyboru. Po zainstalowaniu użytkownicy mogą następnie `dotnet` wykonać aplikację za pomocą polecenia i `dotnet fdd.dll`podając nazwę pliku aplikacji, na przykład .

Oprócz plików binarnych aplikacji instalator powinien również wiązać instalatora współużytkowania struktury udostępnionej lub sprawdzić, czy jest on wymagany jako warunek wstępny w ramach instalacji aplikacji.  Instalacja udostępnionej struktury wymaga dostępu administratora/administratora, ponieważ jest on dostępny na całej maszynie.

## <a name="framework-dependent-deployment-with-third-party-dependencies"></a>Wdrożenie zależne od struktury z zależnościami innych firm

Wdrażanie wdrożenia zależnego od struktury z co najmniej jedną lub kilkoma zależnościami innych firm wymaga, aby wszystkie zależności były dostępne dla projektu. Przed utworzeniem aplikacji wymagane są następujące dodatkowe kroki:

1. Użyj **Menedżera pakietów NuGet,** aby dodać odwołanie do pakietu NuGet do projektu; a jeśli pakiet nie jest jeszcze dostępny w systemie, zainstaluj go. Aby otworzyć Menedżera pakietów, wybierz pozycję **Tools** > **NuGet Package Manager** > **Manage NuGet Packages for Solution**.

1. Upewnij się, że zależności innych firm `Newtonsoft.Json`(na przykład) są zainstalowane w systemie, a jeśli nie, zainstaluj je. Karta **Zainstalowana** zawiera listę pakietów NuGet zainstalowanych w systemie. Jeśli `Newtonsoft.Json` nie ma tam na liście, wybierz kartę **Przeglądaj** i wpisz "Newtonsoft.Json" w polu wyszukiwania. Zaznacz `Newtonsoft.Json` i w prawym okienku wybierz projekt przed wybraniem opcji **Zainstaluj**.

1. Jeśli `Newtonsoft.Json` jest już zainstalowany w systemie, dodaj go do projektu, wybierając projekt w prawym okienku karty **Zarządzanie pakietami dla rozwiązania.**

Wdrożenie zależne od struktury z zależnościami innych firm jest tylko tak przenośne, jak zależności innych firm. Jeśli na przykład biblioteka innej firmy obsługuje tylko system macOS, aplikacja nie jest przenośna do systemów Windows. Dzieje się tak, jeśli sama zależność innych firm zależy od kodu macierzystego. Dobrym przykładem jest [serwer Kestrel,](/aspnet/core/fundamentals/servers/kestrel)który wymaga natywnej zależności od [libuv](https://github.com/libuv/libuv). Po utworzeniu FDD dla aplikacji z tego rodzaju zależności innych firm, opublikowane dane wyjściowe zawiera folder dla każdego [identyfikatora środowiska wykonawczego (RID),](../rid-catalog.md) który obsługuje zależność macierzystą (i który istnieje w pakiecie NuGet).

## <a name="self-contained-deployment-without-third-party-dependencies"></a><a name="simpleSelf"></a>Samodzielne wdrożenie bez zależności innych firm

Wdrażanie samodzielnego wdrożenia bez zależności innych firm wymaga utworzenia projektu, modyfikowania pliku *csproj,* tworzenia, testowania i publikowania aplikacji. Prosty przykład napisany w języku C# ilustruje proces. Można rozpocząć od tworzenia, kodowania i testowania projektu, tak jak wdrożenie zależne od struktury:

1. Utwórz projekt.

   Wybierz **pozycję Plik** > **nowy** > **projekt**. W oknie dialogowym **Nowy projekt** rozwiń kategorie projektów języka (C# lub Visual Basic) w okienku **Zainstalowane** typy projektów, wybierz pozycję **.NET Core**, a następnie wybierz szablon Aplikacja konsoli **(.NET Core)** w środkowym okienku. Wprowadź nazwę projektu, taką jak "SCD", w polu tekstowym **Nazwa** i wybierz przycisk **OK.**

1. Dodaj kod źródłowy aplikacji.

   Otwórz *plik Program.cs* lub *Program.vb* w edytorze i zastąp automatyczniegenerowany kod następującym kodem. Monituje użytkownika o wprowadzenie tekstu i wyświetla poszczególne słowa wprowadzone przez użytkownika. Używa wyrażenia `\w+` regularnego do oddzielenia wyrazów w tekście wejściowym.

   [!code-csharp[deployment#1](~/samples/snippets/core/deploying/cs/deployment-example.cs)]
   [!code-vb[deployment#1](~/samples/snippets/core/deploying/vb/deployment-example.vb)]

1. Określ, czy chcesz używać trybu niezmiennego globalizacji.

   Szczególnie jeśli aplikacja jest przeznaczona dla systemu Linux, można zmniejszyć całkowity rozmiar wdrożenia, korzystając z [trybu niezmiennego globalizacji.](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md) Tryb niezmienny globalizacji jest przydatny w przypadku aplikacji, które nie są globalnie świadome i które mogą używać konwencji formatowania, konwencji wielkości liter i porównywania ciągów i kolejności sortowania [kultury niezmiennej](xref:System.Globalization.CultureInfo.InvariantCulture).

   Aby włączyć tryb niezmienny, kliknij prawym przyciskiem myszy projekt (nie rozwiązanie) w **Eksploratorze rozwiązań**i wybierz polecenie **Edytuj SCD.csproj** lub **Edytuj SCD.vbproj**. Następnie dodaj do pliku następujące wyróżnione wiersze:

   [!code-xml[globalization-invariant-mode](~/samples/snippets/core/deploying/xml/invariant.csproj?highlight=6-8)]

1. Utwórz kompilację debugowania aplikacji.

   Wybierz **opcję Zbuduj** > **rozwiązanie kompilacji**. Można również skompilować i uruchomić kompilację debugowania aplikacji, wybierając **debugowanie** > **start debugowania**. Ten krok debugowania umożliwia identyfikowanie problemów z aplikacją, gdy jest uruchomiona na platformie hosta. Nadal będziesz musiał przetestować go na każdej z platform docelowych.

   Jeśli włączono tryb niezmienny globalizacji, należy szczególnie sprawdzić, czy brak danych wrażliwych na kulturę jest odpowiedni dla aplikacji.

Po zakończeniu debugowania można opublikować samodzielne wdrożenie:

<!-- markdownlint-disable MD025 -->

# <a name="visual-studio-156-and-earlier"></a>[Visual Studio 15.6 i starsze](#tab/vs156)

Po debugowanie i przetestowanie programu, należy utworzyć pliki, które mają być wdrożone z aplikacją dla każdej platformy, która jest przeznaczona.

Aby opublikować aplikację w programie Visual Studio, wykonaj następujące czynności:

1. Zdefiniuj platformy, na które będzie kierowana aplikacja.

   1. Kliknij prawym przyciskiem myszy swój projekt (nie rozwiązanie) w **Eksploratorze rozwiązań** i wybierz **pozycję Edytuj scd.csproj**.

   1. Utwórz `<RuntimeIdentifiers>` znacznik `<PropertyGroup>` w sekcji pliku *csproj,* który definiuje platformy docelowe aplikacji i określ identyfikator środowiska wykonawczego (RID) każdej platformy, na którą chcesz kierować reklamy. Należy również dodać średnik, aby oddzielić identyfikatory RYT. Zobacz [katalog IDentifier środowiska uruchomieniowego](../rid-catalog.md) dla listy identyfikatorów środowiska uruchomieniowego.

   Na przykład poniższy przykład wskazuje, że aplikacja działa na 64-bitowych systemach operacyjnych Windows 10 i 64-bitowym systemie operacyjnym OS X w wersji 10.11.

   ```xml
   <PropertyGroup>
      <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
   </PropertyGroup>
   ```

   Element `<RuntimeIdentifiers>` może przejść `<PropertyGroup>` do dowolnego, który masz w pliku *csproj.* Pełny przykładowy plik *csproj* pojawia się w dalszej części tej sekcji.

1. Opublikuj aplikację.

   Po debugowanie i przetestowanie programu, należy utworzyć pliki, które mają być wdrożone z aplikacją dla każdej platformy, która jest przeznaczona.

   Aby opublikować aplikację w programie Visual Studio, wykonaj następujące czynności:

      1. Zmień konfigurację rozwiązania z **Debugowania** na **Zwolnij** na pasku narzędzi, aby utworzyć wersję aplikacji w wersji (a nie debugowania).

      1. Kliknij prawym przyciskiem myszy projekt (nie rozwiązanie) w **Eksploratorze rozwiązań** i wybierz pozycję **Publikuj**.

      1. Na karcie **Publikowanie** wybierz pozycję **Publikuj**. Visual Studio zapisuje pliki, które składają się na aplikację do lokalnego systemu plików.

      1. Na karcie **Publikowanie** jest teraz wyświetlany pojedynczy profil **FolderProfile**. Ustawienia konfiguracji profilu są wyświetlane w sekcji **Podsumowanie** na **Target Location** **karcie.**

      1. Visual Studio domyślnie zapisuje wszystkie opublikowane pliki w jednym katalogu. Dla wygody najlepiej jest utworzyć oddzielne profile dla każdego docelowego środowiska uruchomieniowego i umieścić opublikowane pliki w katalogu specyficznym dla platformy. Obejmuje to tworzenie oddzielnego profilu publikowania dla każdej platformy docelowej. Więc teraz odbudować aplikację dla każdej platformy, wykonując następujące czynności:

         1. Wybierz **pozycję Utwórz nowy profil** w oknie dialogowym **Publikowanie.**

         1. W oknie **dialogowym Wybieranie miejsca docelowego publikowania** zmień lokalizację **folderu na** *bin\Release\PublishOutput\win10-x64*. Kliknij przycisk **OK**.

         1. Wybierz nowy profil (**FolderProfile1**) na liście profili i upewnij `win10-x64`się, że **docelowy czas uruchomieniowy** jest . Jeśli tak nie jest, wybierz pozycję **Ustawienia**. W oknie dialogowym **Ustawienia profilu** zmień **docelowy czas pracy** na `win10-x64` i wybierz pozycję **Zapisz**. W przeciwnym razie wybierz pozycję **Anuluj**.

         1. Wybierz **pozycję Publikuj,** aby opublikować aplikację dla 64-bitowych platform systemu Windows 10.

         1. Wykonaj ponownie poprzednie kroki, aby `osx.10.11-x64` utworzyć profil dla platformy. **Lokalizacja docelowa** to *bin\Release\PublishOutput\osx.10.11-x64*, a `osx.10.11-x64` **docelowy czas uruchomieniowy** to . Nazwa przypisywana przez program Visual Studio do tego profilu to **FolderProfile2**.

      Każda lokalizacja docelowa zawiera kompletny zestaw plików (zarówno plików aplikacji, jak i wszystkich plików .NET Core) potrzebnych do uruchomienia aplikacji.

Wraz z plikami aplikacji proces publikowania emituje plik bazy danych programu (pdb), który zawiera informacje debugowania o aplikacji. Plik jest przydatny przede wszystkim do debugowania wyjątków. Można wybrać opcję niepakować go z plikami aplikacji. Należy jednak zapisać go w przypadku, gdy chcesz debugować kompilacji wersji aplikacji.

Wdrażanie opublikowanych plików w dowolny sposób. Na przykład można spakować je w pliku `copy` Zip, użyć prostego polecenia lub wdrożyć je z dowolnego pakietu instalacyjnego do wyboru.

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

Po debugowanie i przetestowanie programu, należy utworzyć pliki, które mają być wdrożone z aplikacją dla każdej platformy, która jest przeznaczona. Wiąże się to z utworzeniem osobnego profilu dla każdej platformy docelowej.

Dla każdej platformy, na którą docelowych aplikacji, wykonaj następujące czynności:

1. Utwórz profil dla swojej platformy docelowej.

   Jeśli jest to pierwszy utworzony profil, kliknij prawym przyciskiem myszy projekt (a nie rozwiązanie) w **Eksploratorze rozwiązań** i wybierz pozycję **Publikuj**.

   Jeśli profil został już utworzony, kliknij go prawym przyciskiem myszy, aby otworzyć okno dialogowe **Publikowania,** jeśli nie zostało jeszcze otwarte. Następnie wybierz **pozycję Nowy profil**.

   Zostanie otwarte okno dialogowe **Wybieranie celu publikowania.**

1. Wybierz lokalizację, w której program Visual Studio publikuje aplikację.

   Jeśli publikujesz tylko na jednej platformie, możesz zaakceptować wartość domyślną w polu **tekstowym Wybierz folder;** w tym celu opublikowano zależne od struktury wdrożenie aplikacji w * \<katalogu projektu>\bin\Release\netcoreapp2.1\publish* directory.

   Jeśli publikujesz na więcej niż jednej platformie, dołącz ciąg identyfikujący platformę docelową. Na przykład jeśli dodasz ciąg "linux" do ścieżki pliku, program Visual Studio opublikuje zależne od struktury wdrożenie aplikacji do * \<katalogu projektu>\bin\Release\netcoreapp2.1\publish\linux* directory.

1. Utwórz profil, zaznaczając ikonę listy rozwijanej obok przycisku **Publikuj** i wybierając pozycję **Utwórz profil**. Następnie wybierz przycisk **Utwórz profil,** aby utworzyć profil.

1. Wskaż, że publikujesz samodzielne wdrożenie i zdefiniuj platformę, na którą będzie kierowana aplikacja.

   1. W oknie dialogowym **Publikowanie** wybierz **łącze Konfiguruj,** aby otworzyć okno dialogowe **Ustawienia profilu.**

   1. Wybierz **opcję Samodzielne** w polu listy **Tryb wdrażania.**

   1. W polu listy **Docelowy czas wykonywania** wybierz jedną z platform, na których docelowych aplikacji.

   1. Wybierz **pozycję Zapisz,** aby zaakceptować zmiany i zamknąć okno dialogowe.

1. Nazwij swój profil.

   1. Wybierz opcję**Zmień nazwę profilu** **akcji,** > aby nadać nazwę profilowi.

   2. Przypisz profil nazwę identyfikującą platformę docelową, a następnie wybierz **Zapisz*.

Powtórz te kroki, aby zdefiniować wszelkie dodatkowe platformy docelowe, które są docelowe aplikacji.

Skonfigurowano profile i możesz teraz opublikować aplikację. W tym celu:

   1. Jeśli okno **Publikowania** nie jest aktualnie otwarte, kliknij prawym przyciskiem myszy projekt (nie rozwiązanie) w **Eksploratorze rozwiązań** i wybierz pozycję **Publikuj**.

   2. Wybierz profil, który chcesz opublikować, a następnie wybierz pozycję **Publikuj**. Zrób to dla każdego profilu, który ma zostać opublikowany.

   Każda lokalizacja docelowa (w przypadku naszego przykładu bin\release\netcoreapp2.1\publish\\nazwa*profilu* zawiera kompletny zestaw plików (zarówno plików aplikacji, jak i wszystkich plików .NET Core) potrzebnych do uruchomienia aplikacji.

Wraz z plikami aplikacji proces publikowania emituje plik bazy danych programu (pdb), który zawiera informacje debugowania o aplikacji. Plik jest przydatny przede wszystkim do debugowania wyjątków. Można wybrać opcję niepakować go z plikami aplikacji. Należy jednak zapisać go w przypadku, gdy chcesz debugować kompilacji wersji aplikacji.

Wdrażanie opublikowanych plików w dowolny sposób. Na przykład można spakować je w pliku `copy` Zip, użyć prostego polecenia lub wdrożyć je z dowolnego pakietu instalacyjnego do wyboru.

Poniżej znajduje się kompletny plik *csproj* dla tego projektu.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
  </PropertyGroup>
</Project>
```

Ponadto program Visual Studio tworzy oddzielny\*profil publikowania ( pubxml) dla każdej platformy, która jest kierowana. Na przykład plik dla naszego profilu linuksa (linux.pubxml) jest wyświetlany w następujący sposób:

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

Wdrażanie samodzielnego wdrożenia z co najmniej jedną zależnośćą innych firm wymaga dodania zależności. Przed utworzeniem aplikacji wymagane są następujące dodatkowe kroki:

1. Użyj **Menedżera pakietów NuGet,** aby dodać odwołanie do pakietu NuGet do projektu; a jeśli pakiet nie jest jeszcze dostępny w systemie, zainstaluj go. Aby otworzyć Menedżera pakietów, wybierz pozycję **Tools** > **NuGet Package Manager** > **Manage NuGet Packages for Solution**.

1. Upewnij się, że zależności innych firm `Newtonsoft.Json`(na przykład) są zainstalowane w systemie, a jeśli nie, zainstaluj je. Karta **Zainstalowana** zawiera listę pakietów NuGet zainstalowanych w systemie. Jeśli `Newtonsoft.Json` nie ma tam na liście, wybierz kartę **Przeglądaj** i wpisz "Newtonsoft.Json" w polu wyszukiwania. Zaznacz `Newtonsoft.Json` i w prawym okienku wybierz projekt przed wybraniem opcji **Zainstaluj**.

1. Jeśli `Newtonsoft.Json` jest już zainstalowany w systemie, dodaj go do projektu, wybierając projekt w prawym okienku karty **Zarządzanie pakietami dla rozwiązania.**

Poniżej znajduje się kompletny plik *csproj* dla tego projektu:

# <a name="visual-studio-156-and-earlier"></a>[Visual Studio 15.6 i starsze](#tab/vs156)

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

Podczas wdrażania aplikacji wszystkie zależności innych firm używane w aplikacji są również zawarte w plikach aplikacji. Biblioteki innych firm nie są wymagane w systemie, w którym aplikacja jest uruchomiona.

Wdrożenie jest możliwe tylko z biblioteką innej firmy na platformach obsługiwanych przez tę bibliotekę. Jest to podobne do posiadania zależności innych firm z natywnymi zależnościami we wdrożeniu zależnym od struktury, gdzie natywne zależności nie będą istnieć na platformie docelowej, chyba że zostały tam wcześniej zainstalowane.

## <a name="see-also"></a>Zobacz też

- [Wdrożenie aplikacji core .NET](index.md)
- [Katalog identyfikatora IDentifier (RID) programu .NET Core](../rid-catalog.md)
