---
title: Wdrażanie aplikacji .NET core za pomocą programu Visual Studio
description: Dowiedz się, wdrażanie aplikacji .NET Core za pomocą programu Visual Studio
author: rpetrusha
ms.author: ronpet
ms.date: 04/18/2017
ms.openlocfilehash: 2829bb5a2f5857f6124e5c1f78f5247fe8d1f552
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43407452"
---
# <a name="deploying-net-core-apps-with-visual-studio"></a>Wdrażanie platformy .NET Core z aplikacji za pomocą programu Visual Studio

Możesz wdrożyć aplikację platformy .NET Core albo jako *wdrożenia zależny od struktury*, który zawiera pliki binarne aplikacji, ale zależy od obecności platformy .NET Core w systemie docelowym lub jako *niezależna wdrożenie*, który zawiera aplikację i pliki binarne .NET Core. Omówienie wdrażania aplikacji .NET Core, zobacz [wdrożenie aplikacji programu .NET Core](index.md).

Poniższe sekcje pokazują, jak używać programu Microsoft Visual Studio do tworzenia następujących rodzajów wdrożenia:

- Wdrożenie zależny od struktury
- Wdrażanie zależny od struktury za pomocą zależności innych firm
- Niezależne wdrożenia
- Niezależne wdrożenia przy użyciu zależności innych firm

Aby uzyskać informacje na temat korzystania z programu Visual Studio do opracowywania aplikacji platformy .NET Core, zobacz [wymagania wstępne dla platformy .NET Core w Windows](../windows-prerequisites.md#prerequisites-with-visual-studio-2017).

## <a name="framework-dependent-deployment"></a>Wdrożenie zależny od struktury

Wdrożenie zależny od struktury bez zależności innych firm po prostu polega na tworzenia, testowania i publikowania aplikacji. Prosty przykład napisany w języku C# przedstawiono proces.  

1. Utwórz projekt.

   Wybierz **pliku** > **nowe** > **projektu**. W **nowy projekt** okno dialogowe, wybierz opcję **platformy .NET Core** w **zainstalowane** okienku typów projektu, a następnie wybierz **Aplikacja konsoli (.NET Core)** szablon w środkowym okienku. Wprowadź nazwę projektu, takich jak "Dyskietki" w **nazwa** pola tekstowego. Wybierz **OK** przycisku.

1. Dodawanie kodu źródłowego aplikacji.

   Otwórz *Program.cs* w edytorze i Zastęp automatycznie wygenerowany kod następującym kodem. On monituje użytkownika o wprowadzenie tekstu i wyświetla poszczególne wyrazy wprowadzonej przez użytkownika. Używa wyrażenia regularnego `\w+` do oddzielania słów w tekście wejściowym.

   [!code-csharp[deployment#1](../../../samples/snippets/core/deploying/deployment-example.cs)]

1. Utworzenie kompilacja do debugowania aplikacji.

   Wybierz **kompilacji** > **Kompiluj rozwiązanie**. Można również skompilować i uruchomić kompilację debugowania aplikacji, wybierając **debugowania** > **Rozpocznij debugowanie**.

1. Wdrażanie aplikacji.

   Po utworzeniu debugowania i przetestować program, należy utworzyć plików do wdrożenia z aplikacją. Aby opublikować z programu Visual Studio, wykonaj następujące czynności:

      1. Zmień konfigurację przy użyciu rozwiązania **debugowania** do **wersji** na pasku narzędzi do kompilacji w wersji (a nie na debugowanie) wersję aplikacji.

      1. Kliknij prawym przyciskiem myszy nad projektem (nie rozwiązanie) **Eksploratora rozwiązań**i wybierz **Publikuj**.

      1. W **Publikuj** zaznacz **Publikuj**. Program Visual Studio zapisuje pliki, wchodzące w skład aplikacji w lokalnym systemie plików.

      1. **Publikuj** karta zawiera teraz jeden profil **FolderProfile**. Ustawienia konfiguracji w profilu są wyświetlane w **Podsumowanie** karcie.

   Pliki wynikowe są umieszczane w katalogu o nazwie `PublishOutput` znajdujący się w podkatalogu projektu *.\bin\release* podkatalogu.

Wraz z plikami aplikacji proces publikowania emituje plik bazy danych (PDB) program, który zawiera informacje o debugowaniu dotyczących aplikacji. Plik jest przydatne głównie do debugowania wyjątków. Istnieje możliwość nie spakujesz ją z plikami aplikacji. Jednak należy je zapisać, w przypadku, gdy chcesz debugować kompilację wydania aplikacji.

Wdróż kompletny zestaw plików aplikacji w jakikolwiek sposób, który chcesz. Na przykład, można umieścić je w pliku Zip, użyć prostego `copy` polecenie lub wdrożyć je przy użyciu dowolnego pakietu instalacyjnego wybranych przez użytkownika. Po zainstalowaniu, użytkownicy mogą następnie wykonać aplikacji przy użyciu `dotnet` polecenia i podając nazwę pliku aplikacji, takich jak `dotnet fdd.dll`.

Oprócz plików binarnych aplikacji Instalatora należy również pakietu Instalatora udostępnionego framework albo Wyszukaj jako warunek wstępny jako część instalacji aplikacji.  Instalacja udostępnionego framework wymaga dostępu administratora/root, ponieważ jest ono komputera.

## <a name="framework-dependent-deployment-with-third-party-dependencies"></a>Wdrażanie zależny od struktury za pomocą zależności innych firm

Wdrożenie zależny od struktury z co najmniej jeden zależności innych firm wymaga, aby wszystkie zależności dostępne dla projektu. Przed utworzeniem aplikacji wymagane są następujące dodatkowe czynności:

1. Użyj **Menedżera pakietów NuGet** Dodaj odwołanie do pakietu NuGet do projektu; i jeśli pakiet nie jest jeszcze dostępna w systemie, zainstaluj go. Aby otworzyć Menedżera pakietów, wybierz **narzędzia** > **Menedżera pakietów NuGet** > **Zarządzaj pakietami NuGet dla rozwiązania**.

1. Upewnij się, że `Newtonsoft.Json` jest zainstalowana w systemie, a jeśli tak nie jest, zainstaluj go. **Zainstalowane** karcie znajduje się lista pakietów NuGet, zainstalowanych w systemie. Jeśli `Newtonsoft.Json` nie ma na liście, wybierz **Przeglądaj** kartę, a następnie wprowadź "Newtonsoft.Json" w polu wyszukiwania. Wybierz `Newtonsoft.Json` i w okienku po prawej stronie, wybierz swój projekt przed wybraniem **zainstalować**.

1. Jeśli `Newtonsoft.Json` jest już zainstalowany w systemie, dodaj go do projektu, wybierając projekt w prawym okienku **Zarządzaj pakietami dla rozwiązania** kartę.

Należy pamiętać, że wdrożenie zależny od struktury z zależności innych firm tylko jako przenośne jako jego zależności innych firm. Na przykład jeśli biblioteki innych firm obsługuje tylko z systemem macOS, aplikacja nie jest przenośny z systemami Windows. Dzieje się tak, jeśli zależności innych firm, sama jest zależna od kodu natywnego. Dobrym przykładem jest [serwera Kestrel](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel), co wymaga zależności natywnych na [libuv](https://github.com/libuv/libuv). Podczas tworzenia Dyskietki dla aplikacji za pomocą tego rodzaju zależności innych firm opublikowane dane wyjściowe zawiera folder dla każdego [identyfikator środowiska uruchomieniowego (RID)](../rid-catalog.md) obsługującego natywnych zależności (i znajdujące się w pakiecie NuGet).

## <a name="simpleSelf"></a> Niezależne wdrożenia bez zależności innych firm

Wdrożenie niezależna bez zależności innych firm obejmuje tworzenie projektu i modyfikując *csproj* pliku, tworzenia, testowania i publikowania aplikacji. Prosty przykład napisany w języku C# przedstawiono proces.

1. Utwórz projekt.

   Wybierz **pliku** > **nowe** > **projektu**. W **Dodaj nowy projekt** okno dialogowe, wybierz opcję **platformy .NET Core** w **zainstalowane** okienku typów projektu, a następnie wybierz **Aplikacja konsoli (.NET Core)** szablon w środkowym okienku. Wprowadź nazwę projektu, takich jak "— SCD", w **nazwa** pola tekstowego, a następnie wybierz pozycję **OK** przycisku.

1. Dodawanie kodu źródłowego aplikacji.

   Otwórz *Program.cs* plik w edytorze i Zastąp kod wygenerowany automatycznie z następującym kodem. On monituje użytkownika o wprowadzenie tekstu i wyświetla poszczególne wyrazy wprowadzonej przez użytkownika. Używa wyrażenia regularnego `\w+` do oddzielania słów w tekście wejściowym.

   [!code-csharp[deployment#1](../../../samples/snippets/core/deploying/deployment-example.cs)]

1. Zdefiniuj platformy, dla których będzie dotyczyć aplikacji.

   1. Kliknij prawym przyciskiem myszy nad projektem (nie rozwiązanie) **Eksploratora rozwiązań**i wybierz **Edytuj SCD.csproj**.

   1. Tworzenie `<RuntimeIdentifiers>` tagów w `<PropertyGroup>` części Twojej *csproj* pliku, który definiuje Twojej aplikacji jest przeznaczony dla platform i podaj identyfikator środowiska uruchomieniowego (RID) każdej z platform docelowych. Należy zauważyć, że trzeba będzie również dodać średnika do rozdzielenia identyfikatorów RID. Zobacz [katalog identyfikatora środowiska uruchomieniowego](../rid-catalog.md) Lista identyfikatorów środowisk uruchomieniowych.

   Na przykład w poniższym przykładzie wskazuje, że aplikacja działa w 64-bitowych systemach operacyjnych Windows 10 i 64-bitowym systemie operacyjnym OS X w wersji 10.11.

```xml
<PropertyGroup>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
</PropertyGroup>
```

   Należy pamiętać, że `<RuntimeIdentifiers>` przejść do dowolnego elementu `<PropertyGroup>` zainstalowanej w swojej *csproj* pliku. Pełny przykład *csproj* plik pojawia się w dalszej części w tej sekcji.

1. Utworzenie kompilacja do debugowania aplikacji.

   Wybierz **kompilacji** > **Kompiluj rozwiązanie**. Można również skompilować i uruchomić kompilację debugowania aplikacji, wybierając **debugowania** > **Rozpocznij debugowanie**.

1. Opublikuj aplikację.

   Po utworzeniu debugowania i przetestować program, należy utworzyć pliki do wdrożenia z aplikacją, dotyczącymi poszczególnych platform, że jest ono przeznaczone dla.

   Aby opublikować aplikację z poziomu programu Visual Studio, wykonaj następujące czynności:

      1. Zmień konfigurację przy użyciu rozwiązania **debugowania** do **wersji** na pasku narzędzi do kompilacji w wersji (a nie na debugowanie) wersję aplikacji.

      1. Kliknij prawym przyciskiem myszy nad projektem (nie rozwiązanie) **Eksploratora rozwiązań** i wybierz **Publikuj**.

      1. W **Publikuj** zaznacz **Publikuj**. Program Visual Studio zapisuje pliki, wchodzące w skład aplikacji w lokalnym systemie plików.

      1. **Publikuj** karta zawiera teraz jeden profil **FolderProfile**. Ustawienia konfiguracji w profilu są wyświetlane w **Podsumowanie** karcie. **Docelowe środowisko uruchomieniowe** identyfikuje, które środowisko uruchomieniowe zostało opublikowane, a **lokalizacji docelowej** identyfikuje, gdzie zostały napisane pliki niezależne wdrożenia.

      1. Visual Studio domyślnie zapisuje pliki wszystkie opublikowane w jednym katalogu. Dla wygody najlepiej jest utworzyć osobne profile dla każdego docelowe środowisko uruchomieniowe i umieść pliki opublikowane w katalogu specyficzny dla platformy. Obejmuje to tworzenie oddzielny profil publikowania dla każdej platformy docelowej. Teraz ponownie skompiluj aplikację dla każdej platformy, wykonując następujące czynności:

         1. Wybierz **Utwórz nowy profil** w **Publikuj** okna dialogowego.

         1. W **wybierz lokalizację docelową publikowania** okno dialogowe, zmiana **wybierz folder** lokalizację *bin\Release\PublishOutput\win10 x64*. Wybierz **OK**.

         1. Wybierz nowy profil (**FolderProfile1**) na liście profilów i upewnij się, że **docelowe środowisko uruchomieniowe** jest `win10-x64`. Jeśli nie, wybierz **ustawienia**. W **ustawienia profilu** okno dialogowe, zmiana **docelowe środowisko uruchomieniowe** do `win10-x64` i wybierz **Zapisz**. W przeciwnym razie wybierz **anulować**.

         1. Wybierz **Publikuj** do publikowania aplikacji dla platformy Windows 10 w 64-bitowych.

         1. Wykonaj poprzednie kroki, aby utworzyć profil dla `osx.10.11-x64` platformy. **Lokalizacji docelowej** jest *bin\Release\PublishOutput\osx.10.11-x64*i **docelowe środowisko uruchomieniowe** jest `osx.10.11-x64`. Nazwa programu Visual Studio, przypisuje do tego profilu jest **FolderProfile2**.

      Należy pamiętać, że każda lokalizacja docelowa zawiera kompletny zestaw plików (pliki aplikacji i wszystkich plików z platformy .NET Core) potrzebnych do uruchomienia aplikacji.

Wraz z plikami aplikacji proces publikowania emituje plik bazy danych (PDB) program, który zawiera informacje o debugowaniu dotyczących aplikacji. Plik jest przydatne głównie do debugowania wyjątków. Istnieje możliwość nie spakujesz ją z plikami aplikacji. Jednak należy je zapisać, w przypadku, gdy chcesz debugować kompilację wydania aplikacji.

Wdrażanie plików publikowanych w jakikolwiek sposób, który chcesz. Na przykład, można umieścić je w pliku Zip, użyć prostego `copy` polecenie lub wdrożyć je przy użyciu dowolnego pakietu instalacyjnego wybranych przez użytkownika.

Poniżej przedstawiono pełne *csproj* pliku dla tego projektu.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp1.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

## <a name="self-contained-deployment-with-third-party-dependencies"></a>Niezależne wdrożenia przy użyciu zależności innych firm

Niezależna wdrożenie z co najmniej jeden zależności innych firm obejmuje dodawanie zależności. Przed utworzeniem aplikacji wymagane są następujące dodatkowe czynności:

1. Użyj **Menedżera pakietów NuGet** Dodaj odwołanie do pakietu NuGet do projektu; i jeśli pakiet nie jest jeszcze dostępna w systemie, zainstaluj go. Aby otworzyć Menedżera pakietów, wybierz **narzędzia** > **Menedżera pakietów NuGet** > **Zarządzaj pakietami NuGet dla rozwiązania**.

1. Upewnij się, że `Newtonsoft.Json` jest zainstalowana w systemie, a jeśli tak nie jest, zainstaluj go. **Zainstalowane** karcie znajduje się lista pakietów NuGet, zainstalowanych w systemie. Jeśli `Newtonsoft.Json` nie ma na liście, wybierz **Przeglądaj** kartę, a następnie wprowadź "Newtonsoft.Json" w polu wyszukiwania. Wybierz `Newtonsoft.Json` i w okienku po prawej stronie, wybierz swój projekt przed wybraniem **zainstalować**.

1. Jeśli `Newtonsoft.Json` jest już zainstalowany w systemie, dodaj go do projektu, wybierając projekt w prawym okienku **Zarządzaj pakietami dla rozwiązania** kartę.

Poniżej przedstawiono pełne *csproj* pliku dla tego projektu:

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp1.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
  </ItemGroup>
</Project>
```

Podczas wdrażania aplikacji, wszelkie zależności innych firm używanych w aplikacji znajdują się również z plikami aplikacji. Bibliotek innych firm nie są wymagane w systemie, na którym działa aplikacja.

Należy pamiętać, że można wdrożyć tylko niezależna wdrożenia przy użyciu biblioteki innej firmy na platformach obsługiwanych przez tej biblioteki. Jest to podobne do mających zależności innych firm za pomocą natywnego zależności w danym wdrożeniu zależny od struktury, gdzie zależności natywnych nie istnieje na platformie docelowej, chyba że zostały wcześniej zainstalowane istnieje.

## <a name="see-also"></a>Zobacz także

* [Wdrożenie aplikacji programu .NET core](index.md)
* [Katalog platformy .NET core środowiska uruchomieniowego identyfikator (RID)](../rid-catalog.md)
